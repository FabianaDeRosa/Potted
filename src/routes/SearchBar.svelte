<script>
    import Fa from "svelte-fa";
    import { faMagnifyingGlass } from "@fortawesome/free-solid-svg-icons";
   
    let hidden = true;
    function barVisibility() {
        hidden = !hidden;
    }
</script>



<button on:click={barVisibility} class="mobile-search-btn"><a href="/"><Fa icon={faMagnifyingGlass} size="1.5x" color="black"/></a></button>
<input class:hidden type="text" placeholder="Search..." id="mobile-search-input">



<style lang="scss">

    button {
        justify-self: left;
        align-self: center;
        background: none;
        cursor: pointer;
        border: none;
    }

    input {
        width: 30ch;
        border: 1px solid map-get($colors, forest-green );
        background-color: transparent;
        padding-left: .7rem;
        margin-left: .5rem;
        

        &:focus{
            outline: solid 2px map-get($colors , forest-green );
            outline-offset: -2px;
        }
    }

    .hidden {
        visibility:hidden;
    }
</style>