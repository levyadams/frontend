<script>
  import { cash } from "./../_stores/store.js";
  import {
    locations as _locations,
    cookies as _cookies,
    inventory as _inventory,
  } from "./dataObjects.svelte";
  import Time from "./time.svelte";
  import CookieButton from "./cookieButton.svelte";
  import MarketWindow from "./marketWindow.svelte";
  import LocationsWindow from "./locationsWindow.svelte";
  import EventManager from "./eventManager.svelte";
  import EventWindow from "./eventWindow.svelte";
  import AssetWindow from "./assetWindow.svelte";
  import InfoWindow from "./infoWindow.svelte";
  import SafehouseWindow from "./safehouseWindow.svelte";

  let locations = _locations;
  let cookies = _cookies;
  let inventory = _inventory;

  let formattedCash;
  $: {
    formattedCash = formatMoney($cash);
  }
  $:{
    inventory = inventory;
  }

  let itemExpanded = false;

  export let currentArea = locations[0];

  export let currentDay = 1;

  let marketWindow;
  let marketWindowClosed = true;
  let marketWindowTitle;
  let marketWindowIcon;
  let windowCookiePrice;
  let marketCookiesOwned;

  $: {
    cookies.map((cookie) => {
      if (marketWindowTitle === cookie.name) {
        cookie.boxesOwned = marketCookiesOwned;
        cookies = cookies;
      }
    });
  }

  let locationsWindow;
  let locationWindowHidden = true;

  let assetWindow;
  let loanPaid;
  let assetWindowHidden = true;

  let eventWindowMessage;
  let eventMessage;

  let safehouseWindow;
  let safehouseWindowHidden = true;

  $: {
    eventWindowMessage = eventMessage;
  }

  //working with stores inside of svelte. Works great for global
  //data that is too distant from each other to simply raise state
  function addOrRemoveCash(val, add) {
    if (add) {
      cash.update((n) => n + val);
    } else {
      cash.update((n) => n - val);
    }
  }

  function toggleCookieWindow(cookieName, cookiesOwned) {
    marketWindowTitle = cookieName;
    marketCookiesOwned = cookiesOwned;
    currentArea.localPrices.map((localPrice) => {
      if (localPrice.name === cookieName) {
        windowCookiePrice = localPrice.price;
      }
    });
    if (marketWindowClosed) {
      marketWindowClosed = false;
    } else {
      marketWindowClosed = true;
    }
  }

  function toggleLocationsWindow() {
    if (locationWindowHidden) {
      locationWindowHidden = false;
    } else {
      locationWindowHidden = true;
    }
  }
  function toggleAssetWindow() {
    if (assetWindowHidden) {
      assetWindowHidden = false;
    } else {
      locationWindowHidden = true;
    }
  }
  function toggleSafehouseWindow() {
    safehouseWindowHidden
      ? (safehouseWindowHidden = false)
      : (safehouseWindowHidden = true);
  }
  function formatMoney(
    amount,
    decimalCount = 2,
    decimal = ".",
    thousands = ","
  ) {
    try {
      decimalCount = Math.abs(decimalCount);
      decimalCount = isNaN(decimalCount) ? 2 : decimalCount;

      const negativeSign = amount < 0 ? "-" : "";

      let i = parseInt(
        (amount = Math.abs(Number(amount) || 0).toFixed(decimalCount))
      ).toString();
      let j = i.length > 3 ? i.length % 3 : 0;

      return (
        negativeSign +
        (j ? i.substr(0, j) + thousands : "") +
        i.substr(j).replace(/(\d{3})(?=\d)/g, "$1" + thousands) +
        (decimalCount
          ? decimal +
            Math.abs(amount - i)
              .toFixed(decimalCount)
              .slice(2)
          : "")
      );
    } catch (e) {
      console.log(e);
    }
  }
</script>

<style>
  p,
  h2 {
    margin: 0 0 5px 0;
    color: rgb(19, 15, 15);
  }
  .cash-header {
    color: rgb(39, 248, 39);
  }
  .location-header {
    color: rgb(195, 241, 199);
  }
  .cookie-container {
    display: flex;
    flex-wrap: wrap;
    background: rgb(255, 255, 255);
    border-radius: 5px;
  }
  .layout-container {
    background: beige;
    margin: 2px;
    width: 48%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .nav-container {
    display: flex;
    justify-content: space-between;
  }
  .nav-button {
    width: 32.5%;
  }

  .local-price {
    margin-bottom: 15px;
  }
  .hidden {
    display: none;
  }
</style>

<main>
  <InfoWindow bind:cash={$cash} bind:currentDay />
  <h2>Day {currentDay}</h2>
  <h2 class="cash-header">${formattedCash}</h2>

  <MarketWindow
    bind:hidden={marketWindowClosed}
    bind:this={marketWindow}
    windowTitle={marketWindowTitle}
    windowIcon={marketWindowIcon}
    bind:cash={$cash}
    cookiePrice={windowCookiePrice}
    bind:boxesOwned={marketCookiesOwned}
    bind:loanPaid />

  <h2 class="location-header">{currentArea.name}</h2>

  <EventWindow bind:windowMessage={eventWindowMessage} />

  <div class="cookie-container">
    {#each cookies as cookie}
      <div class="layout-container">
        <CookieButton
          on:click={(el) => toggleCookieWindow(cookie.name, cookie.boxesOwned)}
          cookieLabel={cookie.name}
          boxesOwned={cookie.boxesOwned} />
        {#each locations as location}
          {#if location.name === currentArea.name}
            {#each location.localPrices as localCookiePrice}
              {#if localCookiePrice.name === cookie.name}
                <p class="local-price">Local :${localCookiePrice.price}</p>
              {/if}
            {/each}
          {/if}
        {/each}
      </div>
    {/each}
  </div>

  <LocationsWindow
    bind:this={locationsWindow}
    {locations}
    bind:currentLocation={currentArea}
    bind:menuHidden={locationWindowHidden}
    bind:currentDay />

  <div class="nav-container">

    <div class="nav-button">
      <Time bind:day={currentDay} />
    </div>
    <div class="nav-button">
      <button on:click={() => toggleLocationsWindow()}>
        <div class="icon-truck" />
      </button>
    </div>

    <div class="nav-button">
      <EventManager
        bind:locations
        bind:cookies
        bind:windowMessage={eventMessage}
        bind:currentDay
        bind:currentLocation={currentArea}
        bind:inventory
         />
      <AssetWindow
        bind:assetWindowHidden
        bind:this={assetWindow}
        bind:cash={$cash}
        bind:currentLocation={currentArea}
        bind:inventory
         />
    </div>

    <div class="extras-container">
      <div class="nav-buttons">
        <SafehouseWindow
          bind:cash={$cash}
          bind:currentLocation={currentArea}
          bind:windowHidden={safehouseWindowHidden} />
        <button
          class:hidden={!currentArea.safehouse}
          on:click={() => toggleSafehouseWindow()}>
          <div>$</div>
        </button>

      </div>
    </div>

  </div>
</main>
