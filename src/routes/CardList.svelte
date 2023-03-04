<script>
    import { createEventDispatcher } from "svelte";
    import TodoCard from "./TodoCard.svelte";

    export let cards;
    export let listName;

    $: todo = "";

    const dispatch = createEventDispatcher();
    
    const handleAddCard = () => dispatch("addCard", { todo, listName });
    const handleDeleteCard = (event) => {
        const data = event.detail;
        dispatch('deleteCard', {index: data.index, listName})
    }
</script>

<div class="column is-4">
    <div class="card has-background-light">
        <div class="card-header">
            <p class="card-header-title">{listName}</p>
        </div>
        <div class="card-content">
            {#each cards as card, index}
                <TodoCard content={card.todo} {listName} {index} on:deleteCard={handleDeleteCard} />
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
