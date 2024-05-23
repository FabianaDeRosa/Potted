<script>
    export let name = "Coming soon";
    export let img;
    export let price = "00";
    export let available = false;
    export let id;
</script>



<article>
    <a href="/shop/{id-1}"><img src={img} alt={name} /></a>
    <h3>{name}</h3>
    <p>{price}</p>
    {#if available}
        <button> <a href="/">Add to Cart</a></button>
    {:else}
        <button disabled>Out of Stock</button>
    {/if}
</article>



<style lang="scss">
    article {
        @include card-style;
        display: grid;
        grid-template-rows: min-content min-content min-content;
        place-items: center;
        padding-bottom: 6rem;

        button {
            &:disabled {
                color: lightgray;
                border-color: lightgray;
                &:hover {
                    color: lightgray;
                    background-color: transparent;
                }
            }

            a {
                text-decoration: none;
                color: map-get($colors, forest-green);
            }
        }
    }
</style>
