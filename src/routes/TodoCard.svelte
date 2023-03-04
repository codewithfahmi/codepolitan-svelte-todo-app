<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    export let content, listName, index;
    const handleDeleteCard = () => {
        dispatch("deleteCard", { index });
    };
    const handleMoveRight = () => {
        dispatch("moveRight", { index });
    };

    const handleMoveLeft = () => {
        dispatch("moveLeft", { index });
    };
</script>

<div class="card mb-3 has-background-primary-light">
    <div class="card-content has-text-primary-dark">
        <div class="columns">
            {#if listName !== "Tasks"}
                <div class="column is-1" on:click={handleMoveLeft}>
                    <span class="icon">
                        <i class="fa-solid fa-chevron-left" />
                    </span>
                </div>
            {/if}
            <div
                class={`column ${listName === "In Progress" ? "is-8" : "is-9"}`}
            >
                <p>{content}</p>
            </div>
            <div class="column is-1" on:click={handleDeleteCard}>
                <span class="icon has-text-danger">
                    <i class="fa-solid fa-trash" />
                </span>
            </div>
            {#if listName !== "Done"}
                <div class="column is-1" on:click={handleMoveRight}>
                    <span class="icon">
                        <i class="fa-solid fa-chevron-right" />
                    </span>
                </div>
            {/if}
        </div>
    </div>
</div>
