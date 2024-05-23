<script>
    import ItemCard from "./ItemCard.svelte";
    import items from "$lib/JSON/items.json"
    import Filters from "./Filters.svelte";
</script>



<svelte:head>
    <title>Potted - Shop All</title>
    <meta name="Shop All" content="Shop from all our selection of potted plants">
</svelte:head>



<Filters/>

<div id="all-items-wrapper">
    <h2>All Plants</h2>
    <section>
        {#each items as item}
            <ItemCard {...item} />
         {/each}
    </section>
</div>



<style lang="scss">

    #all-items-wrapper{
        background-color: map-get($colors, primary );
        display: grid;
        grid-template-rows: min-content auto;
        padding: 1.3rem;
        padding-top: 3rem;
        padding-bottom: 7rem;

        h2{
            margin: 0;
            justify-self: center;
            font-size: 1.8rem;
            font-weight: 300;
        }

        section{
           padding-top: 3rem;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(40ch, 1fr));
        }
    }
</style>