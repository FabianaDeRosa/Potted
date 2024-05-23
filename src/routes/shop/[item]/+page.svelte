<script>
    import SingleItemCard from "./SingleItemCard.svelte";
    import items from "$lib/JSON/items.json";
    import { page } from "$app/stores";

    const item = items[$page.params.item];
</script>



<svelte:head>
    <title>Potted - {item.name}</title>
    <meta name="Shop All" content="Shop from all our selection of potted plants">
</svelte:head>



<div id="single-item-wrapper">

    <SingleItemCard {...item} />

</div>



