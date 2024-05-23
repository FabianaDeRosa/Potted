<svelte:head>
    <title>Potted</title>
    <meta name="Potted" content="A shop for plants and pottery lovers">
</svelte:head>



<script>
    import Hero from "./Hero.svelte";
    import ContentCard from "./ContentCard.svelte";
    import Gallery from "./Gallery.svelte";
    import items from "$lib/JSON/items.json"
    import plantCare from "$lib/JSON/plantCare.json"
    import ItemCard from "./shop/ItemCard.svelte";
    import Sketch from "./Sketch.svelte";
    $: filteredItems = items.slice(0, 3);
    $: filteredContent = plantCare.slice(0, 3);
</script>



<div id="header_hero">
    <Hero />
</div>

<section id="three-items-section">
    <div>
        <h2>Our Top 3 sellers</h2>
    </div>

    <div id="three-items-article-grid">
        {#each filteredItems as item}
            <ItemCard {...item} />
        {/each}
    </div> 
</section>

<section id="p5-section">
    <div class="title">
        <h2>Click on the empty area to reveal the upcoming arrivals in our catalogue!</h2>
    </div>
    <div class="sketch">
            <div></div>
            <Sketch/>
            <div></div>
    </div>
</section>


<section id="homepage-content">
    {#each filteredContent as content}
        <ContentCard {...content} />
    {/each}
</section>

<Gallery />



<style lang="scss">

    #header_hero{
      background-color: map-get($colors, beige );
      height: 100vh;
      background-image: url("$lib/images/assets/hero/hero_desktop.png");
      background-position: right;
      background-repeat: no-repeat;
      background-size: contain;
      background-position-y: calc(100%);
      background-position-x: calc(100% - 3rem);

    }

    #three-items-section{
        display: grid;
        grid-template-rows: min-content 1fr;
        padding: 4rem;
        padding-bottom: 1rem;

        div > h2{
            font-size: 1.6rem;
            margin: 0;
            margin-bottom: 1rem;
        }

        #three-items-article-grid{
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(30ch, 1fr));
            place-items: center;
        }
    }

    #p5-section{
        display: grid;
        grid-template-rows: min-content 1fr;
        padding: 3rem;
        padding-bottom: 6rem;

        .title {
            justify-self: center;

            h2{
            font-size: 1.6rem;
            line-height: 2.2rem;
            margin: 0;
            margin-bottom: 3rem;
            text-align: center;
            width: 40ch;
        }
        }

        .sketch{
            display: grid;
            grid-template-columns: auto min-content auto;
          
            div{
                height: 1.8rem;
                align-self: center; 
                background-position: center;
                background-repeat: no-repeat;
                background-size:contain;
                background-image: url("assets/logoo2.svg");
                &:first-child{
                    transform: translate(9em)rotate(-90deg);
                }
                &:nth-child(3){
                    transform:translate(-9em) rotate(90deg);
                }
            }
        }
    }

    #homepage-content {
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
    #header_hero{
        height: 100vh;
        background-image: url("$lib/images/assets/hero/hero_mobile.png");
        background-position: right;
        background-repeat: no-repeat;
        background-size: contain;
        background-position-y: calc(100% + 1.3rem);
        background-position-x: calc(100% + 4rem);

    }
   
}

@media screen and (max-width: 1000px) {

    #p5-section .sketch{  
        display: grid;
        grid-template-columns: 1fr;
        justify-items: center;
            div{
              
                &:first-child{
                  display: none;
                }

                &:nth-child(3){
                    display: none;
                }
            }
        }
}

</style>