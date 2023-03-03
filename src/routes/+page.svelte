<script>
    import CardList from "./CardList.svelte";
    let taskCards = [];
    let inProgressCards = [];
    let doneCards = [];

    const handleEventAddCard = (event) => {
        console.log(event);
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
            />
            <CardList
                cards={inProgressCards}
                listName={"In Progress"}
                on:addCard={handleEventAddCard}
            />
            <CardList
                cards={doneCards}
                listName={"Done"}
                on:addCard={handleEventAddCard}
            />
        </div>
    </main>
</div>
