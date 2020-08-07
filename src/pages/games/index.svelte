<script>
  import { url } from "@sveltech/routify";
</script>


<main>
<div style="padding-top: 20px">
  <h1>PLAY</h1>
</div>
  <a class="card" href={$url('../cookiewars', {  })}>
    <h2 class="item">Cookie Wars!</h2>
    <p class="cookiewars-description">Sling overpriced, re-packaged cookies while keeping it<br><b><u> 100 </u></b><br> if you know what im sayin <br>;)</p>
  </a>
</main>

<style>
  .cookiewars-description{
    font-size:20px;
    padding:0 15px;
  }
  h1{
    color:rgb(211, 196, 247);
  }
  
</style>
