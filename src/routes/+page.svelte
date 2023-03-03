<script>
    import TodoCard from "./TodoCard.svelte";
    let cards = [
        {
            todo: "Belajar HTML",
            list: "tasks",
        },
        {
            todo: "Belajar JS",
            list: "tasks",
        },
        {
            todo: "Belajar Svelte",
            list: "tasks",
        },
    ];

    $: todo = "";
    const handleAddCard = () => (cards = [...cards, { todo, list: "tasks" }]);
</script>

<svelte:head>
    <title>Todo App</title>
</svelte:head>

<div class="container">
    <header>
        <h1 class="is-size-3">Todo App</h1>
    </header>
    <main>
        <div class="columns">
            <div class="column is-4">
                <div class="card has-background-light">
                    <div class="card-header">
                        <p class="card-header-title">Tasks</p>
                    </div>
                    <div class="card-content">
                        {#each cards as card}
                            <TodoCard content={card.todo} />
                        {/each}
                        <div class="field">
                            <div class="control">
                                <input
                                    type="text"
                                    class="input is-primary"
                                    bind:value={todo}
                                />
                            </div>
                        </div>
                        <div class="field">
                            <div class="control">
                                <button
                                    on:click={() => {
                                        handleAddCard(), (todo = "");
                                    }}
                                    class="button is-primary">Add Card</button
                                >
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</div>
