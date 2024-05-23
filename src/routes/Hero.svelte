<section>
    <h1>Discover our selection of plants and revive your place.</h1>
    <a href="/shop"><button>Shop now</button></a>
</section>



<style lang="scss">
    section{
        padding: 12.5rem 5rem;

        h1{
            margin: 0;
            font-size: clamp(2em,3vw,2.7rem);
            max-width: 34.5%;
            line-height: 1.2em;
            font-weight: 300;   
            color: map-get($colors, dark );
        }
        
        a {
            text-decoration: none;
            color: map-get($colors, forest-green );
            padding: .8rem 0;

            button {
            @include btn-style;
                &:hover{
                    color: map-get($colors, beige );
                    background-color: map-get($colors , forest-green );
                }
            
            }   
        }  
    }


    
@media screen and (max-width: 600px) {

    section {
        
        padding-left: 4rem;

        h1 {
            max-width: 91%;
            margin-top: 13rem;
        }
    }
   
}
</style>