<script>
    import TodoCard from "./TodoCard.svelte";
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
                        <TodoCard content={"Belajar HTML"} />
                        <TodoCard content={"Belajar JS"} />
                        <TodoCard content={"Belajar Svelte"} />
                    </div>
                </div>
            </div>
        </div>
    </main>
</div>
