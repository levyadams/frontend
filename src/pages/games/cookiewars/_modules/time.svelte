<script>
  export let day = 1;

  export function nextDay() {
    day += 1;
  }
</script>

<style>
  main {
    display: flex;
    flex-direction: column;
  }

  h1 {
    color: #ffffff;
    text-transform: uppercase;
    font-size: 24px;
    font-weight: 100;
    margin-top: 0;
    margin-bottom: 10px;
  }
  .icon-history{
    transform:scaleX(-1);
  }

</style>

<main>
  <button on:click={()=> nextDay()}><div class="icon-history"></div></button>
</main>
