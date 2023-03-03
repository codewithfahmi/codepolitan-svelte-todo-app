<script>
    export let content;
    export let listName;
</script>

<div class="card mb-3 has-background-primary-light">
    <div class="card-content has-text-primary-dark">
        <div class="columns">
            {#if listName !== "Tasks"}
                <div class="column is-1">
                    <span class="icon">
                        <i class="fa-solid fa-chevron-left" />
                    </span>
                </div>
            {/if}
            <div class={`column ${listName === "In Progress" ? "is-8" : "is-9"}`}>
                <p>{content}</p>
            </div>
            <div class="column is-1">
                <span class="icon has-text-danger">
                    <i class="fa-solid fa-trash" />
                </span>
            </div>
            {#if listName !== "Done"}
                <div class="column is-1">
                    <span class="icon">
                        <i class="fa-solid fa-chevron-right" />
                    </span>
                </div>
            {/if}
        </div>
    </div>
</div>
