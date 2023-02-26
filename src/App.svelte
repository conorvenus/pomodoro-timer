<script lang="ts">
    import TimeSegment from "./lib/TimeSegment.svelte";
    import Minutes from "./lib/Minutes.svelte";
    import ControlButton from "./lib/ControlButton.svelte";
    import Navbar from "./lib/Navbar.svelte";

    let minutes: number = 25;
    let seconds: number = 0;
    let isPlaying: boolean = false;
    let interval;

    function setTimer(_minutes: number) {
      minutes = _minutes
      seconds = 0
    }

    function updateTimer() {
      if (seconds === 0) {
        seconds = 60
        minutes--
      }
      seconds--
    }

    function togglePlaying() {
      isPlaying = !isPlaying
      if (!isPlaying)
        clearInterval(interval)
      else
        interval = setInterval(() => {
          updateTimer()
        }, 1000)
    }
</script>

<Navbar />
<main class="h-screen flex flex-col justify-center items-center gap-10">
  <div class="flex gap-4 items-center">
    <TimeSegment value={minutes} />
    <div class="font-bold text-white text-7xl mt-[-0.6rem]">:</div>
    <TimeSegment value={seconds} />
  </div>
  <ul class="flex gap-4 relative justify-center minutes-list">
    {#each {length: 5} as _, i}
      <Minutes value={15 + i * 5} inverted={i == 2} on:click={() => setTimer(15 + i * 5)} />
    {/each}
  </ul> 
  <ControlButton on:click={togglePlaying} isPlaying={isPlaying} />
</main>