<script>
	import GameManager from './_modules/gameManager.svelte';
</script>

<main>
<GameManager />
</main>

<style>
:global(html) {
    background: rgb(77, 128, 43);
  }
:global(button){
    background:rgb(2, 167, 2);
    border:none;
	color:rgb(255, 255, 255);
	border-radius: 10px;
  width:100%;
  height:50px;
  font-size:30px;
}
:global(h2){
	margin-bottom:0;
	padding-bottom:0;

}
	main {
		text-align: center;
		padding: 0 15px 15px 15px;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	@font-face {
  font-family: 'icomoon';
  src:  url('../fonts/icomoon.eot?6pcrul');
  src:  url('../fonts/icomoon.eot?6pcrul#iefix') format('embedded-opentype'),
    url('../fonts/icomoon.ttf?6pcrul') format('truetype'),
    url('../fonts/icomoon.woff?6pcrul') format('woff'),
    url('../fonts/icomoon.svg?6pcrul#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
  font-display: block;
}

:global([class^="icon-"], [class*=" icon-"]) {
  /* use !important to prevent issues with browser extensions that change fonts */
  font-family: 'icomoon' !important;
  speak: never;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  line-height: 1;

  /* Better Font Rendering =========== */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
:global(.icon-droplet:before) {
  content: "\e90b";
}
:global(.icon-pacman:before) {
  content: "\e916";
}
:global(.icon-coin-dollar:before) {
  content: "\e93b";
}
:global(.icon-clock:before) {
  content: "\e94e";
}
:global(.icon-tv:before) {
  content: "\e95b";
}
:global(.icon-database:before) {
  content: "\e964";
}
:global(.icon-spinner:before) {
  content: "\e97a";
}
:global(.icon-spinner2:before) {
  content: "\e97b";
}
:global(.icon-spinner3:before) {
  content: "\e97c";
}
:global(.icon-spinner4:before) {
  content: "\e97d";
}
:global(.icon-spinner5:before) {
  content: "\e97e";
}
:global(.icon-spinner7:before) {
  content: "\e980";
}
:global(.icon-spinner8:before) {
  content: "\e981";
}
:global(.icon-spinner9:before) {
  content: "\e982";
}
:global(.icon-spinner10:before) {
  content: "\e983";
}
:global(.icon-pie-chart:before) {
  content: "\e99a";
}
:global(.icon-contrast:before) {
  content: "\e9d5";
}
:global(.icon-heart:before) {
  content: "\e9da";
}
:global(.icon-wink:before) {
  content: "\e9e7";
}
:global(.icon-wink2:before) {
  content: "\e9e8";
}
:global(.icon-hipster:before) {
  content: "\e9f9";
}
:global(.icon-hipster2:before) {
  content: "\e9fa";
}
:global(.icon-cross:before) {
  content: "\ea0f";
}
:global(.icon-checkmark:before) {
  content: "\ea10";
}
:global(.icon-play2:before) {
  content: "\ea15";
}
:global(.icon-pause:before) {
  content: "\ea16";
}
:global(.icon-stop:before) {
  content: "\ea17";
}
:global(.icon-radio-checked:before) {
  content: "\ea54";
}
:global(.icon-radio-checked2:before) {
  content: "\ea55";
}
:global(.icon-radio-unchecked:before) {
  content: "\ea56";
}
:global(.icon-IcoMoon:before) {
  content: "\eaea";
}
:global(.icon-book:before) {
  content: "\e91f";
}
:global(.icon-truck:before) {
  content: "\e9b0";
}
:global(.icon-history:before) {
  content: "\e94d";
  transform:scaleX(-1);
}
:global(.icon-history:before) {
  content: "\e94d";
}
</style>