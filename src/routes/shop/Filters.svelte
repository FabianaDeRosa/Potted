<script>
    const options = [
        {
            rooms: ["Bathroom", "Bedroom", "Hallway", "Kitchen", "Living room", "Kids' room"],
            size: ["Short", "Medium", "Tall", "Very Tall"],
            easeOfCare: ["Unkillable", "Easy Care", "Intermediate"],
            lightsNeed: ["Low", "Medium", "High"]
        }
    ];
</script>



<div id="filter-wrapper">
<div>
<h3>Filter By</h3>
<select>
    <option value="" selected default>Room</option>
	{#each options as option}
        {#each option.rooms as room}
            <option value={room}>{room}</option>
        {/each}
    {/each}
</select>

<select>
    <option value="" selected default>Size</option>
	{#each options as option}
        {#each option.size as size}
            <option value={size}>{size}</option>
        {/each}
    {/each}
</select>

<select>
    <option value="" selected default>Ease of Care</option>
	{#each options as option}
        {#each option.easeOfCare as easeOfCare}
            <option value={easeOfCare}>{easeOfCare}</option>
        {/each}
    {/each}
</select>

<select>
    <option value="" selected default>Lights Need</option>
	{#each options as option}
        {#each option.lightsNeed as lightsNeed}
            <option value={lightsNeed}>{lightsNeed}</option>
        {/each}
    {/each}
</select>
</div>

<div>
    <h3>Sort By</h3>
    <select>
        <option value="">Price Low to High</option>
        <option value="">Price High to Low</option>
    </select>
</div>
</div>

<div id="filter-wrapper-mobile">
    <button>
       Filters
    </button>
    <button>
        Sort By
    </button>    
</div>



<style lang="scss">

    #filter-wrapper {
        display: grid;
        grid-template-columns: auto min-content;
        padding: 1.5rem;
        padding-top: 3rem;

        h3 {
            margin: 0;
            padding-bottom: .5rem;
            font-weight: 200;
            font-size: 1rem;
        }
    }

    select{
        width: 20ch;
        border: 1px solid map-get($colors, forest-green );
        background-color: transparent;
        padding: .5rem;
        font-family: "CircularStd";
        font-weight: 200;

    }

    #filter-wrapper-mobile{
        display: none;
    }

    @media screen and (max-width: 1000px) {

        #filter-wrapper{
            display: none;
        }

        #filter-wrapper-mobile{
            display: grid;
            justify-content: space-between;
            grid-template-columns: auto auto;
            padding: 2rem;
            padding-bottom: 1rem;

            button{
                font-size: 1rem;
                padding: .5rem 1.5rem;
                border: 1px solid map-get($colors, forest-green );
                background-color: transparent;
                font-family: "CircularStd";
                font-weight: 200;

                &:active{
                    background-color: map-get($colors , forest-green );
                    color: map-get($colors , primary );
                }
            }
        }
    }
</style>

