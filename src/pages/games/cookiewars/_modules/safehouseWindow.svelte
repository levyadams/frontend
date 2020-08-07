<main>
<div class:hidden={windowHidden} class="safehouse-container">
<button on:click={()=>stashing?stashing=false:stashing=true}>{stashing? 'grab cash!':'stash cash!'}</button>
<p>Your cash : ${stashing? cash-amountToStash:cash+amountToStash}</p>
<p>{stashing?'Amount to stash':'Amount to grab'} : ${amountToStash}</p>

  <input
        type="range"
        bind:value={amountToStash}
        min="0"
        max={stashing ? cash : currentLocation.safehouseLoot}
        class="big-slider"
        id="myRange" />
        <button on:click={stashing?stashCash():grabCash()}>{stashing?'stash it':'grab it'}</button>
<p>Stashed : ${currentLocation.safehouseLoot}</p>
<button on:click={()=>windowHidden=true}>back</button>
</div>

</main>

<script>
    export let windowHidden = true;
    export let cash;
    export let currentLocation;
    export let amountToStash =0;
    export let stashing = true;

    export let stashCash =()=>{
        cash = cash - amountToStash;
        currentLocation.safehouseLoot = currentLocation.safehouseLoot + amountToStash;
        currentLocation = currentLocation;
        amountToStash = 0;
    };

    export let grabCash =()=>{
        cash = cash + amountToStash;
        currentLocation.safehouseLoot = currentLocation.safehouseLoot - amountToStash;
        currentLocation = currentLocation;
        amountToStash = 0;
    };
</script>

<style>
.safehouse-container{
     width: calc(100% - 30px);
    display: flex;
    flex-direction: column;
    align-items: center;
    position: fixed;
    background: rgb(90, 187, 90);
    height: 100%;
    z-index: 2;
    left: 15px;
    top: 0;
}
.hidden{
    display:none;
}
</style>