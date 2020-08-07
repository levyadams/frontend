<script>
  export let locations;
//cuz im lazy. binds to gameManager currentArea to watch for changes
  export let currentLocation;

  export let cookies;

  export let windowMessage = "";

  let daysToDisplayMessage = 0;

  export let inventory;

  let playerStrength = 0;

  export let currentDay = 0;

  let cookieEvent = false;

  export const increaseMessages = [
    { 0: `Feminist convention in`, 1: `prices are empowered!` },
    { 0: `MRA convention in`, 1: `prices go their own way..up!` },
    { 0: `Communism convention in`, 1: `prices flourish!` },
    { 0: `Gaming convention in`, 1: `prices are epic rn` },
    { 0: `Anime convention in`, 1: `prices bulge oWo` },
    { 0: `Furry convention in`, 1: `*prices bulge* oWo` },
  ];
  export const decreaseMessages = [
    { 0: `overstock in`, 1: `prices drop.` },
    { 0: `Chinese regulations lifted in`, 1: `prices disappear.` },
    { 0: `Fat tax removed in`, 1: `prices are lower than life expectancy.` },
    { 0: `Local supplier closes doors in`, 1: `prices are low.` },
    {
      0: `Toxic sugar alternative deregulated in`,
      1: `prices artificially deflate.`,
    },
    { 0: `Local competition goes under in`, 1: `prices are in the ground.` },
  ];

  //cookie event handler
  $: {
    if (currentDay > 1) {
      rollForCookieEvent();
      rollForCookiePriceChange();
      if(daysToDisplayMessage>0){
          daysToDisplayMessage -= 1;
      }
      else{
          windowMessage = "";
      }
    
    }
  }
  $:{
    if(inventory.guns.pistol){
      playerStrength = playerStrength +=  2;
    }
    if(inventory.guns.ak === true){
      playerStrength = playerStrength + 3;

    }
    if(inventory.guns.crate === true){
      playerStrength = playerStrength + 2;
    }
    inventory = inventory;
  }
//location event handler
  $:{
      currentLocation = currentLocation;
      rollForLocationEvent();
  }

  //sets local cookie prices and sets them determined by location and cookie type
  let weightedNumberGenerator = (spread, range, weight) => {
    let spreadVal = Math.round(Math.random() * 10);
    let rangeValue = Math.random() * (range[1] - range[0] + 1) + range[0];
    if (spreadVal <= spread) {
      let newVal = rangeValue * weight;
      return parseFloat(newVal.toFixed(2));
    } else {
      return parseFloat(rangeValue.toFixed(2));
    }
  };

  //iterate through location.localPrices and set the towns
  //local cookie prices based on the weightedNumberGenerator.
  let setCookiePrices = () => {
    locations.map((location) => {
      location.localPrices.map((cookiePrice) => {
        cookies.map((cookie) => {
          if (cookie.name === cookiePrice.name) {
            cookiePrice.price = weightedNumberGenerator(
              location.priceSpread,
              [cookie.minPrice, cookie.maxPrice],
              location.cookieWeight
            );
            locations = [...locations];
          }
        });
      });
    });
  };
  //runs on start to set all cookie prices
  setCookiePrices();

  let rollForCookieEvent = () => {
    //each day, roll for cookie event. ~15% chance.
    let randyVal = parseFloat((Math.random() * 10).toFixed(1));
    if (randyVal >= 8.1) {
      let randyVal1 = parseFloat((Math.random() * 10).toFixed(2));
      if (currentDay < 15) {
          let cookieReturnVal = 0;
        if (randyVal1 >= 5) {
         cookieReturnVal = randomizeCookie(true);
        } else {
         cookieReturnVal = randomizeCookie(false);
        }
        cookieEvent = true;
      }
      //cookie events drop after day 15 for added difficulty 9% chance.
      else {
          let cookieReturnVal = 0;
        if (randyVal >= 9.1) {
         cookieReturnVal = randomizeCookie(true);
        } else {
        cookieReturnVal = randomizeCookie(false);
        }
        cookieEvent = true;
      }
    }
  };

  let rollForCookiePriceChange =()=>{
    let randyNom = parseFloat((Math.random() * 10).toFixed(1));
    if(randyNom <= 3.5){
        setCookiePrices();
        return true;
    }
    else{
        return false;
    }
  };

  let randomizeCookie = (increase) => {
    let randoLocation = locations[Math.round(Math.random() * 3)];
    let randoCookie = randoLocation.localPrices[Math.round(Math.random() * 5)];

    if (increase) {
        windowMessage = returnRandoCookieMessage(
        true,
        randoLocation,
        randoCookie
    );
     return randoCookie.price = parseFloat(
        randoCookie.price * Math.round(Math.random() * 10).toFixed(2)
      );
      
    } else {
      let randyPrice = randoCookie.price / 3;
      windowMessage = returnRandoCookieMessage(
        false,
        randoLocation,
        randoCookie
      );
      return randoCookie.price = parseFloat(randyPrice.toFixed(2));
    }
  };

  let returnRandoCookieMessage = (increase, location, cookie) => {
    if (increase) {
      let oof = Math.floor(Math.random() * increaseMessages.length - 1);
      if (oof < 0) {
        oof = 0;
      }
      let message = increaseMessages[oof];
      daysToDisplayMessage = 2;
      return `${message[0]} ${location.name}, ${cookie.name} ${message[1]}`;
    } else {
      let oof = Math.floor(Math.random() * decreaseMessages.length - 1);
      if (oof < 0) {
        oof = 0;
      }
      let message = decreaseMessages[oof];
      daysToDisplayMessage = 2;
      return `${message[0]} ${location.name}, ${cookie.name} ${message[1]}`;
    }
  };

  let rollForLocationEvent = ()=>{
      if(currentDay>3){
       let randyManValueSavage = parseFloat((Math.random()*10).toFixed(1));
       if(randyManValueSavage>7.5){

       }
      }
  };
</script>

<style>
  .hidden {
    display: none;
  }
</style>

<main />
