<script>
  export let name;
  import { url } from "@sveltech/routify";
</script>

<style>
  a {
    font-size: 1.5em;
    padding: 12px 24px;
  }
</style>

<div class="card" style="width: 312px;">
  <h1>{name}</h1>
</div>

<br />
<a href={$url('../../')}>Go back</a>
