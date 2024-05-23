<script>
    import HamburgerMenu from "$lib/images/icons/hamburger_menu.png";
    import { page } from '$app/stores';
    import SearchBar from "./SearchBar.svelte";

    let hidden = true;
    function changeVisibility() {
        hidden = !hidden;
    }

    let showMenu = true;
    function changeVisibilityMenu() {
        showMenu = !showMenu;
    }

    let filter = false;
    function changeFilter() {
        filter = !filter;
    }

    let openMenu = false;
    function openMenuArrow() {
        openMenu = !openMenu;
    }

    let dim;
    $: condition = dim > 600;
</script>



<nav>
    <div class:hidden>
    <a on:click={changeVisibilityMenu} on:click={openMenuArrow}  class:openMenu href="/" aria-current={$page.url.pathname === '/shop' ? 'page' : undefined}>Shop</a>
    <a href="/plantCare" aria-current={$page.url.pathname === '/plantCare' ? 'page' : undefined}>Plant care</a>
    <a href="/aboutUs" aria-current={$page.url.pathname === '/aboutUs' ? 'page' : undefined}>About</a>
    {#if !hidden}
        <SearchBar/>
        <button id="login-btn">Login</button>
    {/if}
    </div>
  

    {#if !condition}
    <button on:click={changeVisibility} on:click={changeFilter} class:filter><img src="{HamburgerMenu}" alt="Hamburger menu"></button>
    {/if}
    <section id="sub-menu" class:showMenu>
        <section>
            <article>
                <h2>Plants</h2>
                <ul>
                    <li><a on:click={changeVisibilityMenu} href="/shop">Shop All</a></li>
                    <li><a href="/">Best Sellers</a></li>
                    <li><a href="/">Pet Friendly</a></li>
                </ul>
            </article>
            <article>
                <h2>By Room</h2>
                <ul>
                    <li><a href="/">Bathroom</a></li>
                    <li><a href="/">Bedroom</a></li>
                    <li><a href="/">Hallway</a></li>
                    <li><a href="/">Kitchen</a></li>
                    <li><a href="/">Living Room</a></li>
                    <li><a href="/">Kids' Room</a></li>
                </ul>
            </article>
            <article>
                <h2>By Size</h2>
                <ul>
                    <li><a href="/">Short (0 - 40cm)</a></li>
                    <li><a href="/">Medium (40 - 80cm)</a></li>
                    <li><a href="/">Tall (80 - 120cm)</a></li>
                    <li><a href="/">Very Tall ( + 120cm)</a></li>
                </ul>
            </article>
            <article>
                <h2>By Lights Need</h2>
                <ul>
                    <li><a href="/">Low</a></li>
                    <li><a href="/">Medium</a></li>
                    <li><a href="/">High</a></li>
                </ul>
            </article>
            <article>
                <h2>By Ease of Care</h2>
                <ul>
                    <li><a href="/">Unkillable</a></li>
                    <li><a href="/">Easy Care</a></li>
                    <li><a href="/">Intermediate</a></li>
                </ul>
            </article>
            <article>
                <h2>Gift Guide</h2>
            </article>
        </section>
    </section>
</nav>



<style lang="scss">
    
    nav {
        
        div {
        display: grid;
        grid-template-columns: repeat(3, auto);
        place-content: center;
        
        a{
            text-decoration: none;
            color: map-get($colors, dark);
            margin: 0 1rem;
            font-size: 1.1rem;
            font-weight: 200;
            border-bottom: 2px solid transparent;
            transition: border-color 0.2s;

            &:first-child {
                &::after{
                    content: "";
                    display: inline-block;
                    background: url("/src/lib/images/icons/arrow.svg")
                        no-repeat center left;
                    width: .6em;
                    height: .3em;
                    margin-left: 0.5rem;
                    margin-bottom: 0.15rem;
                    vertical-align: middle;
                }
            }
            
            &[aria-current='page'] {
                border-color: map-get($colors, dark );
            }

            &:hover{
                color: map-get($colors, clay );
            }
        }
    }

        button {
            display: none;
        }

        #sub-menu {
            left:0;
            position: absolute;
            margin-top: 1.4em;
            height: fit-content;
            width: 100%;
            padding-bottom: 1.7rem;
            background-color: map-get($colors, forest-green );
            z-index: 1;


            >section{
                padding: 1rem;
                padding-top: 2rem;
                display: grid;
                grid-template-columns: repeat(  auto-fit, minmax( 10rem, 1fr)   );
                justify-items: center;
                
            }

            h2{
                margin: 0;
                color: map-get($colors, primary );
                font-weight: 400;
                font-size: 1.1rem;
            }

            ul {
               padding: 0;           
            }

            li {
                list-style-type: none;

                a {
                    text-decoration: none;
                    color: map-get($colors, primary );
                    line-height: 2em;
                    font-size: 1em;    
                    font-weight: 200;

                    &:hover {
                    color: map-get($colors, clay );
                    cursor: pointer;
                }
                }
            }

        }
        
    }
    
    .showMenu {
        display: none;
    }
    
    .openMenu{
        
        &::after{
            transform: rotate(180deg);

            
        }
    }
 
    @media screen and (max-width: 600px) {
        nav {
            div {
                position: fixed;
                top: 0;
                padding: 6rem;
                padding-top: 8.5rem;
                padding-left: 1rem;
                align-content: start;
                left: 0;
                display: grid;
                grid-template-columns: 1fr;
                grid-template-rows: repeat(3, min-content);
                height: 100%;
                background-color: map-get($colors, forest-green );

                a {
                    margin-bottom: 2rem;
                    color: map-get($colors , primary );
                    border-bottom: none;

                    &:first-child {
                        &::after{
                            filter: invert(1);
                            rotate: -90deg;
                            width: .5em;
                            margin-left: 1rem;
                            
                        }
                    }
                }
            }

            #login-btn{
                font-size: 1.05rem;
                padding-left: 1rem;
                margin-top: 27rem;
                color: map-get($colors , primary );
                text-decoration: underline;
                letter-spacing: .03rem;
            }

            button {
                display: block;
                background: none;
                cursor: pointer;
                border: none;
                position: absolute;
                top: 1.2rem;
                left: 1.2rem;

                img {
                    height: 2rem;
                }
            }
        }

        .hidden {
            display: none;
        }

        .filter {
            filter: invert(1);
            transform:rotate(90deg);
            transition-duration: .50s;
        }

        .openMenu{
        
        &::after{
            transform: rotate(0deg);
        }
    }

        :global(.mobile-search-btn) {
            filter: invert(1);
            display: none;
    
        }

        :global(#mobile-search-input){
            visibility: visible;
            width: 23ch;
            background-color: map-get($colors, primary );
            opacity: 80%;
            border: 1px solid map-get($colors, primary );
            padding-left: .7rem;
            margin-left: 1rem;
            margin-top: 3rem;
            padding: .6rem;
            color: map-get($colors, forest-green );

            &:focus{
                outline: solid 2px map-get($colors , clay );
                outline-offset: -2px;
            }
        }
    }
</style>