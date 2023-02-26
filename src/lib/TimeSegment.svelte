<script>
export let value;
</script>

<article class="bg-white text-red-500 font-bold text-7xl py-10 px-4 grid place-items-center rounded-md">
    <span>{value < 10 ? "0" + value : value}</span>
</article>