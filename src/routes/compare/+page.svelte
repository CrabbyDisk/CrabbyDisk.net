<script>
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
    }
    ]



    function addCard() {
        cardList = [...cardList, {ammount: 1, price: 1, ratio: 1}];
    }

    function removeCard(index) {
        cardList.splice(index, 1)
        cardList = cardList;
    }


    function changeRatio(index) {
        cardList[index].ratio = Math.round(cardList[index].ammount / cardList[index].price * 100) / 100;
        compare();
    }   
    function compare() {
        let best = 0;
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
        </article>
    {/each}

    <article class="add-card">
        <h1><button on:click={addCard}>+</button></h1>
    </article>
</section>

<style>
    .add-card {
    }

    section {
        display: grid;
        gap: 1.5rem;
        grid-template-columns: 1fr 1fr 1fr 1fr;
    }
    .compare-card {
        margin: 0;
    }
</style>