<main>
    <button on:click={()=> assetWindowHidden ? assetWindowHidden = false:assetWindowHidden = true}><div class="icon-book"></div></button>
    <div class:hidden={assetWindowHidden} class="asset-container">
        <button on:click={()=>paybackLoan()}>Pay back loan</button>
        <button class:hidden={currentLocation.safehouse} on:click={()=>buySafehouseAtLocation()}>buy safehouse ($2000)</button>
        <button on:click={()=>gunshopWindowHidden=false}>Gunshop</button>
        <button  on:click={()=>assetWindowHidden = true}>back</button>
    </div>
    <div class:hidden={gunshopWindowHidden} class="gunshop-window">
        <button class:hidden="{inventory.guns.pistol === true}" on:click={()=>buyGun('pistol')}>pistol : $1,000</button>
        <button class:hidden={!inventory.guns.ak} on:click={()=>buyGun('ak')}>AK : $10,000</button>
        <button class:hidden={!inventory.guns.crate} on:click={()=>buyGun('crate')}>Military Crate: $40,000</button>
        <button on:click={()=>gunshopWindowHidden=true}>close</button>
    </div>
</main>

<script>
export let currentLocation;

export let inventory;

export let assetWindowHidden = true;

export let gunshopWindowHidden = true;

export let loanPaid = false;

export let cash = 0;

let paybackLoan =()=>{
    if(cash>=5000){
        cash = cash - 5000;
        loanPaid = true;
        alert("Ma': 'great work..Good luck out there, sweetheart!'");
    }
    else{
        alert("Ma':'You dont have enough cash, sweetheart!'");
    }
};

let buySafehouseAtLocation =()=>{
    if(!currentLocation.safehouse){
        if(cash>=currentLocation.safehousePrice){
            cash = cash - currentLocation.safehousePrice;
            currentLocation.safehouse = true;
            alert('Thanks! Here are the keys!');
        }
    }
};

let buyGun=(type)=>{
    switch(type){
        case 'pistol':
            console.log('buy pistol!');
            inventory.guns.pistol = true;
        break;
        case 'ak':
            inventory.guns.ak = true;
            inventory.guns = inventory.guns;
        break;
        case 'crate':
            inventory.guns.crate = true;
            inventory.guns = inventory.guns;
        break;
    }
}
</script>

<style>
.asset-container,.gunshop-window{
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