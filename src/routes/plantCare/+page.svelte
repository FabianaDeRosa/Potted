<script>
    import ContentCard from "../ContentCard.svelte";
    import plantCare from "$lib/JSON/plantCare.json"
</script>



<svelte:head>
    <title>Potted - Plant Care</title>
    <meta name="Plant Care" content="Take care of your plants with our tips">
</svelte:head>



<section id="title-sect">
    <h2>Plant Care</h2>
    <p>Learn more on how to take care of your house plants.</p>
</section>
<section id="plant-care-content">

    {#each plantCare as content}
        <ContentCard {...content} />
    {/each}
</section>



<style lang="scss">

    #title-sect{
        background-color: map-get($colors, beige );
        padding-top: 2rem;
        height: 9rem;

        h2 {
            margin: 0;
            color: map-get($colors, dark );
            padding: 3rem;
            padding-bottom: 0;
            text-align: center;
        }

        p{
            font-weight: 200;
            text-align: center;
            margin: 0;
            padding-top: .5rem;
            font-size: 1rem;
        }
    }

    #plant-care-content {
        display: grid;
        background-color: map-get($colors, clay );

        :global article:nth-child(even) .descr{
            grid-column: 1;    
            grid-row: 1;  
            justify-self: right;
            margin-right: 3rem;  
            text-align: right;
            
            button{
                justify-self: right; 
            }
        } 
    }


    @media screen and (max-width: 1000px) {

    :global(#art-plant-care){


        &:nth-child(2) {
            grid-column: 1;    
            grid-row: 3; 
        }

        &:nth-child(3) {
            grid-column: 1;    
            grid-row: 2; 
        }

    }
}
</style>
