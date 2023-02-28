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
                        <div class="card mb-3 has-background-primary-light">
                            <div class="card-content">
                                <p class="has-text-primary-dark">Belajar HTML</p>
                            </div>
                        </div>
                        <div class="card mb-3 has-background-primary-light">
                            <div class="card-content">
                                <p class="has-text-primary-dark">Belajar JS</p>
                            </div>
                        </div>
                        <div class="card mb-3 has-background-primary-light">
                            <div class="card-content">
                                <p class="has-text-primary-dark">Belajar Svelte</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>   
</div>