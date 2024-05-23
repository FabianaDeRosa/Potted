<script>
    import Gallery from "../../Gallery.svelte";

    export let name = "Coming soon";
    export let img;
    export let waterNeed;
    export let lightsNeed;
    export let petFriendly;
    export let price = "00";
    export let descr;
    export let quantity;
    let value = 0;
</script>



<section id="single-item">
<article>
    <img src="{img}" alt={name} />
    <div class="infos">
        <p>{waterNeed}</p>
        <p>{lightsNeed}</p>
        <p>{petFriendly ? "Pet Friendly" : "Not Pet Friendly"}</p>
    </div>
</article>

<article>
    <h2>{name}</h2>
    <span>{price}</span>
    <p>{descr}</p>
    <label>
        Quantity:
        {#if quantity > 0}
        <input type=number onKeyDown="return false" bind:value={value} min=0 max={quantity}>
        {:else}
        <input type=number disabled>
        {/if}
    </label>
    {#if quantity > 0}
        <button> <a href="/">Add to Cart</a></button>
    {:else}
        <button disabled>Out of Stock</button>
    {/if}
</article>
</section>

<Gallery/>



<style lang="scss">

    #single-item{
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(50ch, 1fr));
        place-items: center;
        padding-bottom: 7rem;
        padding-top: 3.5rem;

        article{
            &:first-child{
                display: grid;
                grid-template-rows: auto min-content;
                place-items: left;
                
                img{
                    height: 50ch;
                }

                .infos{
                    display: grid;
                    grid-template-rows: repeat(3, auto);
                    justify-content: center;
                    p {
                    font-weight: 200;
                    margin: .5rem 0;
                   
                    &:first-of-type{
                        
                        &:before {
                            content: "";
                            display: inline-block;
                            background: url("/src/lib/images/icons/drop.svg")
                                no-repeat center left;
                            width: 1.1em;
                            height: 1em;
                            padding-right: 0.5rem;
                            margin-left: 0.3rem;
                            vertical-align: middle;
                        }
                    }
                    &:nth-of-type(2){
                        &:before {
                            content: "";
                            display: inline-block;
                            background: url("/src/lib/images/icons/light.svg")
                                no-repeat  center left;
                            width: 1em;
                            height: 1.3em;
                            padding-right: 0.7rem;
                            vertical-align: middle;
                        }
                    }
                    &:nth-of-type(3){
                        &:before {
                            content: "";
                            display: inline-block;
                            background: url("/src/lib/images/icons/paw.svg")
                                no-repeat center left;
                            width: 1em;
                            height: 1em;
                            padding-right: 0.7rem;
                            vertical-align: middle;
                        }
                    }
                }
                }
                
            }

            &:nth-child(2){
                display: grid;
                grid-template-rows: repeat(5, min-content);
                margin-left: 3rem;
                margin-top: 2rem;
               
                h2{
                    font-size: 1.7rem;
                }

                span {
                    font-weight: 200;
                    color: map-get($colors, clay);
                    margin: 1.1rem;
                    margin-top: .8rem;
                    font-size: 1.2rem;
                    margin: 0;

                    &::after{
                        content: ",00£";
                    }
                }

                p{
                    font-weight: 200;
                    margin-right: 14rem;
                    line-height: 1.4rem;

                }

                label {
                    font-weight: 200;
                    font-size: .8rem;
                    margin-top: 1rem;
                    margin-bottom: 1.4rem;
                }

                input {
                    display: block;
                    width: 7ch;
                    height: 4ch;
                    border: 1px solid map-get($colors, forest-green );
                    background-color: transparent;
                    padding: .4rem;

                    margin-top: .5rem;
                    margin-left: 0;
                    font-size: 1rem;

                    &:focus{
                        outline: none;
                        outline: solid 2px map-get($colors , forest-green );
                        outline-offset: -2px;
                    }
                }

                input[type=number] {
                    line-height: 30px;
                }
                    
                input[type=number]::-webkit-inner-spin-button {
                    width: 30px;
                    height: 30px;
                }

                button{
                    @include btn-style;
                    justify-self: left;

                    &:hover{
                        background-color: map-get($colors , forest-green );
                        color: map-get($colors , primary );

                        a{
                            color: map-get($colors, primary); 
                        }
                    }

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
        }
    }
</style>

