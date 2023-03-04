<script>
    import CardList from "./CardList.svelte";
    let taskCards = [];
    let inProgressCards = [];
    let doneCards = [];

    const handleEventAddCard = (event) => {
        const data = event.detail;
        switch (data.listName) {
            case "Tasks":
                taskCards = [...taskCards, { todo: data.todo }];
                break;
            case "In Progress":
                inProgressCards = [...inProgressCards, { todo: data.todo }];
                break;
            default:
                doneCards = [...doneCards, { todo: data.todo }];
                break;
        }
    };

    const handleEventDeleteCard = (event) => {
        const data = event.detail;
        if (data.listName === "Tasks") {
            taskCards.splice(data.index, 1);
            taskCards = taskCards;
        } else if (data.listName === "In Progress") {
            inProgressCards.splice(data.index, 1);
            inProgressCards = inProgressCards;
        } else {
            doneCards.splice(data.index, 1);
            doneCards = doneCards;
        }
    };

    const handleEventMoveRight = (event) => {
        const data = event.detail;
        if (data.listName === "Tasks") {
            const cardToMove = taskCards.splice(data.index, 1);
            taskCards = taskCards;
            inProgressCards = [...inProgressCards, cardToMove[0]];
        } else {
            const cardToMove = inProgressCards.splice(data.index, 1);
            inProgressCards = inProgressCards;
            doneCards = [...doneCards, cardToMove[0]];
        }
    };

    const handleEventMoveLeft = (event) => {
        const data = event.detail;
        if (data.listName === "In Progress") {
            const moveToCard = inProgressCards.splice(data.index, 1);
            inProgressCards = inProgressCards;
            taskCards = [...taskCards, moveToCard[0]];
        } else {
            const moveToCard = doneCards.splice(data.index, 1);
            doneCards = doneCards;
            inProgressCards = [...inProgressCards, moveToCard[0]];
        }
    };
</script>

<svelte:head>
    <title>Todo App</title>
</svelte:head>

<div class="container">
    <header class="py-5">
        <h1 class="title is-size-3">Todo App</h1>
    </header>
    <main>
        <div class="columns is-variable is-5">
            <CardList
                cards={taskCards}
                listName={"Tasks"}
                on:addCard={handleEventAddCard}
                on:deleteCard={handleEventDeleteCard}
                on:moveRight={handleEventMoveRight}
            />
            <CardList
                cards={inProgressCards}
                listName={"In Progress"}
                on:addCard={handleEventAddCard}
                on:deleteCard={handleEventDeleteCard}
                on:moveRight={handleEventMoveRight}
                on:moveLeft={handleEventMoveLeft}
            />
            <CardList
                cards={doneCards}
                listName={"Done"}
                on:addCard={handleEventAddCard}
                on:deleteCard={handleEventDeleteCard}
                on:moveLeft={handleEventMoveLeft}
            />
        </div>
    </main>
</div>
