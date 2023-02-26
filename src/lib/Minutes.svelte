<script lang="ts">
    export let value;
    export let inverted: boolean = false;
</script>

<button on:click class="hover:scale-110 transition-transform duration-200 z--1 font-bold text-4xl px-4 py-2 rounded-md border-2 {inverted ? "text-red-500 bg-white border-red-500 shadow-xl" : "text-white bg-red-500 border-white"}">
    <span>{value}</span>
</button>