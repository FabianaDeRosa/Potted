<script>
    import Logo from "$lib/images/icons/logo.svg";
    import Cart_icon from "$lib/images/icons/shopping_bag.png";
    import Menu from "./Menu.svelte";
    import SearchBar from "./SearchBar.svelte";
    
    let dim;
    $: innerWidth = dim;
    $: condition = innerWidth > 600;

</script>

<svelte:window bind:innerWidth = {dim} />



<div id="header-wrapper">
    <header>
        {#if condition}
            <SearchBar />
        {/if}
        <a href="/" id="logo-icon"><img src={Logo} alt="Potted logo"/></a>
        <button id="login-btn">Login</button>
        <button><img class="cart-icon" src={Cart_icon} alt="Cart icon"/></button>
    </header>

    <Menu />
</div>



<style lang="scss">
    
    #header-wrapper {
        display: grid;
        grid-template-rows: auto auto;
        background-color: map-get($colors , beige );

        header {
        display: grid;
        grid-template-columns: min-content min-content auto min-content min-content;
        padding-bottom: 1.7rem;

        button {
            justify-self: left;
            align-self: center;
            background: none;
            cursor: pointer;
            border: none;

            &:hover{
                text-decoration: underline;
            }

            .cart-icon{
                height: 2rem;
            }          
        }

        #login-btn{
            font-size: 1rem;
            padding-left: 11.5rem;
        }

        #logo-icon{
            width: 10ch;
            align-self: center;
            justify-self: center; 

        }
    }
}

@media screen and (max-width: 600px) {

    #login-btn{
        display: none;
    }

    #header-wrapper{
        grid-template-rows: auto auto;
       

        header {
            grid-column: 2;
            padding-left: 2.5rem;
        }

        button {
            grid-column: 3;
            justify-self: right !important;
        }
    }

}  
</style>