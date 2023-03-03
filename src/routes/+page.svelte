<script>
    import CardList from "./CardList.svelte";
    let taskCards = [];
    let inProgressCards = [];
    let doneCards = [];
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
            <CardList cards={taskCards} listName={"Tasks"} />
            <CardList cards={inProgressCards} listName={"In Progress"} />
            <CardList cards={doneCards} listName={"Done"} />
        </div>
    </main>
</div>
