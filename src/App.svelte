<script lang="ts">
  import type {SplitValue} from "./types";
  import ValueDisplay from "./ValueDisplay.svelte";

  export let title: string;

  let sliderValue: number = 0;

  let inverseSliderValue: number;
  $: inverseSliderValue = 10 - sliderValue;

  let splitValue: SplitValue;
  $: splitValue = {left: sliderValue, right: inverseSliderValue};

  function log() {
    console.log(sliderValue);
  }
</script>

<h1>{title}</h1>

<input type="range" min="0" max="10" step="1" bind:value={sliderValue}/>

<ValueDisplay value={splitValue}/>
<button on:click={log}>log value</button>