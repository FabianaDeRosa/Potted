<script>
    export let title;
    export let img;
</script>



<article id="art-plant-care">
    <div style="background-image:url({img});"></div>
    <div class="descr">
        <h4>{title}</h4>
        <button>Learn more</button>
    </div>
</article>



<style lang="scss">

    article {
        display: grid;
        grid-template-columns:repeat(auto-fit, minmax(40ch, 1fr));
        
        .descr{
            color: map-get($colors, primary);
            display: grid;
            place-content: center;
            max-width: 65ch;

            h4{
                font-weight: 200;
                font-size: 2.5rem;
                padding-bottom: 0;
                margin: 0;
                margin-left: 3rem;
            }

            button {
                @include btn-style;
                color: map-get($colors, primary );
                border: solid 2px map-get($colors, primary );
                justify-self: left;
                margin-left: 3rem; 

                &:hover{
                    background-color: map-get($colors, beige );
                    color: map-get($colors , clay );
                }
            }
        }

    }


    div{
       height: 90vh;
       background-position: center;
       background-repeat: no-repeat;
       background-size:cover;
    }
</style>