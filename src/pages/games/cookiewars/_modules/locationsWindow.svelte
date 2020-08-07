<main>
    <div class="locations-container" class:hidden={menuHidden}>
    {#each locations as location}
    {#if location.name != currentLocation.name}
        <button on:click={()=>changeCurrentLocation(location)}>{location.name}</button>
        {/if}
    {/each}
    <button on:click={()=> menuHidden = true}>back</button>
    </div>
</main>
<script>
export let locations;
export let currentLocation = locations[0];
export let menuHidden = false;
export let currentDay = 0;
export function changeCurrentLocation(location){
    if(rollForEvent(location.riskValue)){
        currentLocation = location;
        menuHidden = true;
        currentDay++;
        return;
    }
    currentLocation = location;
    menuHidden = true;
currentDay++;
    return;
};

export function rollForEvent(riskVal){
    let randy = Math.round(Math.random() * 10);
    if(riskVal<=randy){
        return false;
    }
    else{
        return true;
    }
};

</script>
<style>
button{
    background:grey;
}

.locations-container{
     width:calc(100% - 30px);
    display: flex;
    flex-direction: column;
    align-items:center;
    position: fixed;
    background:rgb(90, 187, 90);
    height:100%;
    z-index: 2;
    left:15px;
    top:0;
}
.hidden{
    display:none;
}
</style>