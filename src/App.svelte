<script>
    import Timer from './Timer.svelte';
    import HowTo from './HowTo.svelte';

    let audio;
    function timerEnds(e) {
        audio.play();
    }
</script>

<style>
 h1, h3 {
     text-align: center;

 }
</style>

<h1>Handwashing app</h1>

<Timer on:end={timerEnds} />

<HowTo />

<h3>
<a href="http://who.int">Picture source WHO</a>
</h3>


<audio bind:this={audio}>
    <source src="assets/sound.wav" />
</audio>