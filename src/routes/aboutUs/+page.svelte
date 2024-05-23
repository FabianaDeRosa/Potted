<svelte:head>
    <title>Potted - About Us</title>
    <meta name="About us" content="About us and our mission with Potted.">
</svelte:head>



<section>
    <div></div>
    <h2>About Us</h2>
    <p>Welcome to Potted, a business born out of a passion for plants.
        We bring together a carefully curated selection of houseplants, featuring some 
        lesser spotted varieties that you might not find in your local garden centre. We believe that
         plants are the perfect way to update your home or office and with numerous studies highlighting 
        their wellbeing benefits for you, your family or colleagues.</p>
    <div class="bg"></div>
    <p>It's not just our products that are green. We're proud that 100% of our packaging is now either recyclable 
        or compostable. As a company we've made a concerted effort to switch to sustainable packaging, it may 
        be a little more pricey, but we sleep better at night.</p>
    <a href="/shop"><button>Shop now</button></a>
</section>



<style lang="scss">
    div{
        height: 1.8rem;
        background-position: center;
        background-repeat: no-repeat;
        background-size:contain;
        background-image: url("assets/logoo.svg");
        
    }

    section {
        background-color: map-get($colors , forest-green );
        display: grid;
        grid-template-rows: repeat(6, auto);
        padding-top: 3rem;
        
        h2 {
            margin: 0;
            color: map-get($colors, primary );
            padding: 3rem;
            padding-bottom: 0;
            padding-top: 1rem;
            text-align: center;
        }

        p{
            font-weight: 200;
            font-size: 1rem;
            width: 45vw;
            line-height: 1.3rem;
            text-align: center;
            color: map-get($colors, primary );
            justify-self: center;
            padding: 2rem;
            padding-top: 1rem;
        }

        .bg{
            height: 80vh;
            background-image: url("$lib/images/assets/aboutUs.jpg");
            background-position: right;
            background-repeat: no-repeat;
            background-size: cover;
            background-position-y: calc(100% + 30rem);

        }

        a {
            justify-self: center;
            
            button {
            @include btn-style;
            color: map-get($colors, primary );
            border: solid 2px map-get($colors, primary );
            margin-bottom: 10rem;
            font-size: 1rem;
            margin-top: 0;
            
            
                &:hover{
                    background-color: map-get($colors, beige );
                    color: map-get($colors , dark );
                }
            }
        }
        

    }

    @media screen and (max-width: 600px) {
        section {
            .bg{
                background-position-y: 0;
            }

            p{
            width: 75vw;
        }
        }  
    }
</style>
