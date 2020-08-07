<main>
    <div class:hidden={infoWindowHidden} class="info-container">
        <div class:hidden={!startGame} class="firstContainer">
        <p>'Ma brings you close</p>
        <p>"My time is almost up, my love.."</p>
        <p>"It's your turn to take over the biz!"</p>
        <p>Take a $2,500 loan from grandma and turn it into your fortune.</p>
        <p>In 45 days...</p>
        <p>Don't forget to cut 'Ma in</p>
        <p>And watch out for fools trying to snatch your stash!</p>
        </div>
        <p class:hidden={!endGame}>{finishMessage}</p>
        <button on:click={()=>startingMessageFunction()}>OK!</button>
    </div>
</main>

<script>
    export let currentDay = 0;
    export let cash;
    export let finishMessage = `Game over! Your score was ${cash}`;
    export let startGame = true;
    export let endGame = false;
    export let infoWindowHidden = false;

    $:{
        if(currentDay === 46){
            infoWindowHidden = false;

            endGame = true;
        }
    }

     let startingMessageFunction=()=>{
         if(startGame){

             startGame = false;
         infoWindowHidden = true;
         return;
         }
         else{
             location.reload();
         }
    };

</script>

<style>

.info-container{
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