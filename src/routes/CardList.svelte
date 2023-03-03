<script>
    export let cards;
    export let listName;

    import TodoCard from "./TodoCard.svelte";

    $: todo = "";
    const handleAddCard = () => (cards = [...cards, { todo, list: "tasks" }]);
</script>

<div class="column is-4">
    <div class="card has-background-light">
        <div class="card-header">
            <p class="card-header-title">{listName}</p>
        </div>
        <div class="card-content">
            {#each cards as card}
                <TodoCard content={card.todo} />
            {/each}
            <section role="form">
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
            </section>
        </div>
    </div>
</div>
