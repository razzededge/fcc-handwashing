<script>
import { createEventDispatcher } from 'svelte';
import ProgressBar from './ProgressBar.svelte';
const totalSeconds = 20;
let secondsLeft = totalSeconds;
$: progress = (secondsLeft / totalSeconds) * 100;;

const dispatch = createEventDispatcher();

let interval;

function startTimer() {
secondsLeft = totalSeconds;
progress = 100;
clearInterval(interval);

interval = setInterval(() => {
    secondsLeft -= 1;
    if(!secondsLeft) {
        clearInterval(interval);
        dispatch('end', 'end timer');
    }
}, 1000);
}




</script>

<style>
h2 {
    margin: 0;
}

.start {
    background-color: rgb(154, 73, 73);
    width: 100%;
    margin: 10px 0;
}

</style>

<div bp="grid">
    <h2 bp="offset-5@md 4@md 12@sm">
        Seconds left: {secondsLeft}
    </h2>
</div>

<ProgressBar progress="{progress}" />

<div bp="grid">

<button on:click={startTimer} bp="offset-5@md 4@md 12@sm" class="start">Start</button>
</div>
