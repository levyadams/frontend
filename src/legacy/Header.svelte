<style type="text/scss">
.intro-container{
  height:100%;
  position: absolute;
  background: rgb(37, 37, 99);
  transition:opacity 1.5s;
  .header-primary {
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
    padding-top: 0.75em;
    margin-bottom: 1em;
    color: white;
    -webkit-text-fill-color: rgb(
      211,
      186,
      186
    ); /* Will override color (regardless of order) */
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: rgb(
      211,
      186,
      186
    );
    letter-spacing: 0.125em;
    text-shadow: .25px 2px 3px rgb(104, 2, 2);
  }
  .header-secondary {
    margin:0 1em 0 1em;
    font-size: 2.25em;
    color: rgb(140, 140, 245);
    text-shadow: .75px .75px 0 rgb(22, 11, 75), 0px 0px 0 rgb(29, 12, 107),
      0px 0px 0 rgb(29, 12, 107), 0px 0px 0 rgb(29, 12, 107),
      0px 0px 0 rgb(29, 12, 107);
  }
  p{
    margin:0 .75em 2em .75em;
    color:#5c5cd8;
    font-size:1.25em;
  }

}
.fadeout{
  opacity:0;
}
  
</style>

<script>
let headlineMain = 'Joystick Nebula';
let headlineTwoEyebrow = 'Shine deep..';
let headlineTwo = '';

let introContainer;
let introRan = false;

let musicHeadlines = [
  {eyebrow:"Superstars dont sparkle",headline:"We shine deep"},
  {eyebrow:"Whipping me into a storm",headline:"Shaking me down to the core"},
  {eyebrow:"now I notice that I drink too much",headline:"In the turning of the universe"},
  {eyebrow:"Burning incandescently",headline:"Like a bastard on the burning sea"},
  {eyebrow:"I don't talk",headline:"I speak"},
  {eyebrow:"You come beating like moth's wings",headline:"Spastic and violently"}
];

let rollDice =()=>{
  let randy = Math.floor(Math.random() * 11);
  if(randy>2){
    let pickASong = Math.floor(Math.random() * musicHeadlines.length);

    headlineTwoEyebrow = musicHeadlines[pickASong].eyebrow;
    headlineTwo = musicHeadlines[pickASong].headline;

  }
  else{

  }
};

let fadeScreen =()=>{
 setTimeout(function(){introRan = true;}, 3000);
}
fadeScreen();
rollDice();

</script>

<div class:fadeout={introRan} class="intro-container">
  <h1 class="header-primary">{headlineMain}</h1>
  <p>{headlineTwoEyebrow}</p>
  <h2 class="header-secondary">{headlineTwo}</h2>
</div>
