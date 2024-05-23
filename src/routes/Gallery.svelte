<section id="social-media-section">

    <div id="follow-title">
        <h4>Follow us on Instagram</h4>
        <a href="/">@potted.co</a>
    </div>
   
    <div id="gallery">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </div>
</section>



<style lang="scss">
    #social-media-section {
        background-color: map-get($colors, forest-green);
        display: grid;
        grid-template-rows: auto auto;
        padding-bottom: 10rem;
        padding-top: 8rem;

        #follow-title {
            padding-bottom: 2rem;
            place-self: center;
            text-align: center;

            h4{
                margin: 0;
                color: map-get($colors, primary );
                font-size: 1.6rem;
                font-weight: 200;     
                margin-bottom: .7rem; 
            }

            a{
                text-decoration: none;
                color: map-get($colors, primary );
                font-size: 1.4rem;
                font-weight: 200;

                &:hover{
                    color: map-get($colors, clay );
                }
            }
        }
        
        #gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(25ch, 1fr));
            grid-template-rows: repeat(auto-fit, minmax(20ch, 1fr));

            div {
            min-height: 37vh;
            background-position: center;
            background-repeat: no-repeat;
            background-size:cover;
            
            &:first-child{
                background-image: url("assets/social-media/potting2.jpg");
            }
            &:nth-child(2){
                background-image: url("assets/social-media/japanInspo.png");
            }
            &:nth-child(3){
                background-image: url("assets/social-media/plantOnTable.jpg");    
            }
            &:nth-child(4){
                background-image: url("assets/social-media/diningRoom.jpg");
            }
            &:nth-child(5){
                background-image: url("assets/social-media/potting.jpg");
                grid-column: 3 / 5;
                grid-row: 1 / 3; 
            }
            &:nth-child(6){
                background-image: url("assets/social-media/plantOnBooks.jpg");
            }
            &:nth-child(7){
                background-image: url("assets/social-media/ourStudio.jpg");
            }

            &:hover {
                cursor: pointer;
                box-shadow: inset 0 0 0 1000px rgba(32,50,32,.5);
            }
            }  
        }
    }



    @media screen and (max-width: 1300px) {

        div {
            &:nth-child(5), 
            &:nth-child(6), 
            &:nth-child(7){
                display: none;
            }
        }
    }

    @media screen and (max-width: 1200px) {

        div {
            &:nth-child(4){
                display: none;
            }
        }
    }

    @media screen and (max-width: 1000px) {

    div {
        &:nth-child(3){
            display: none;
        }
    }
    }
</style>
