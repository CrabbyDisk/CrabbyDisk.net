<script lang="ts">
    let cardList = [
    {
        ammount: 1,
        price: 1,
        ratio: 1
    },
    {
        ammount: 1,
        price: 1,
        ratio: 1
    }]

    let best: number;

    function addCard() {
        cardList = [...cardList, {ammount: 1, price: 1, ratio: 1}];
    }

    function removeCard(index: number) {
        cardList.splice(index, 1)
        cardList = cardList;
    }

    function changeRatio(index: number) {
        cardList[index].ratio = Math.round(cardList[index].ammount / cardList[index].price * 100) / 100;
        compare();
    }   
    function compare() {
        for(let i in cardList) {
            if(cardList[best].ratio < cardList[i].ratio) {
                best = i
            }
        }
        console.log(cardList[best].ratio);
        //TODO: visual indicator for the best
    }

    let unit = 'ml'
</script>

<section>
    {#each cardList as card, index}   
        <article class="compare-card">
            <button on:click={() => removeCard(index)}>Delete</button>
            <p>Value</p>
            <input bind:value={card.ammount} on:input={() => changeRatio(index)} type="number" min="0" max="1000000" />
            <p>Price</p>
            <input bind:value={card.price} on:input={() => changeRatio(index)} type="number" min="0" max="1000000" />
            <p>{card.ratio} {unit} per $</p>
            {#if best == index}
                <div class="best-card"><p>The Best</p></div>
            {/if}
        </article>
    {/each}

    <article class="add-card">
        <h1><button on:click={addCard}>+</button></h1>
    </article>
</section>

<style>
    .add-card {
        margin: 0;
    }

    section {
        display: grid;
        gap: 1.5rem;
        grid-template-columns: 1fr 1fr 1fr 1fr;
    }
    .compare-card {
        margin: 0;
    }
    .best-card {
        color: green;
    }
</style>