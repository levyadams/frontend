<script>
 import Header from './modules/Header.svelte';
 import List from './modules/List.svelte';
</script>
<main>
<Header/>
<List/>
</main>

<link
  href="https://fonts.googleapis.com/css2?family=VT323&display=swap"
  rel="stylesheet" />
<meta name="viewport" content="width=device-width, initial-scale=1" />

<style type="text/scss">
:global(html){
  background: rgb(87, 1, 87);
}

  :global(body, h1, h2, h3, h4, html) {
    margin: 0;
    padding: 0;
  }


  main {
    width: 100%;
    height: 100%;
    font-family: "VT323", monospace;
    text-align: center;
    background: rgb(20, 36, 43);
    margin: 0;
    padding: 0;
  }

</style>