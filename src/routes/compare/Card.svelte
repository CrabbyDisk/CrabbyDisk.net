<script>
    let ammount = 1;
    let price = 1;
    let ratio = ammount / price;
    let unit = 'ml'
    function changeRatio() {
        ratio = Math.round(ammount / price * 100) / 100;
    }   
</script>

<article class="compare-card">
    <p>Value</p>
    <input bind:value={ammount} on:input={changeRatio} type="number" min="0" max="1000000" />
    <p>Price</p>
    <input bind:value={price} on:input={changeRatio} type="number" min="0" max="1000000" />
    <p>{ratio} {unit}/$</p>
</article>

<style>
    .compare-card {
        width: 400px;
    }
</style>