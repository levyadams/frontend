<script>
  export let cookieLabel;
  export let boxesOwned;
</script>

<style>
  h2 {
    font-size: 16px;
  }
  p,
  h2 {
    color: rgb(24, 131, 10);
    margin-bottom:5px;
  }
  .icon {
    font-size: 16px;
    color: rgb(13, 95, 13);
  }
  .icon-main {
    font-size: 4em;
  }
  .icon-expand {
    font-size: 4em;
    position: absolute;
    left: 28px;
    top: -64px;
  }

  .cookie-item {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items:center;
  }
  .expanded-container {
    position: relative;
  }
  .expanded{
      position: absolute;
      height:100%;
      width:100%;
      background:white;
  }
  .owned-container {
    display: flex;
    justify-content: center;
    align-items: center;
  
  }
  .owned-container>p{
    margin:5px 0 5px;
  }
  .money {
    color: rgb(5, 228, 5);
  }
  img{
    width:60px;
    height:60px;
  }
</style>

<div class="cookie-item" on:click>
  <h2>{cookieLabel}</h2>
 <img src='../images/{cookieLabel}.svg' alt="{cookieLabel} icon">
  <div class="owned-container">
    <div class="icon-database icon"></div>
    <p>: {boxesOwned}</p>
  </div>
</div>
