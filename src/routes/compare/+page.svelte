<script>
    import Card from './Card.svelte'

    let cardList = [

    ]

    function addCard() {

    }
</script>

<section class="grid">

    <Card />
    <Card />
    <article class="add-card">
        <h1><button on:click={addCard}>+</button></h1>
    </article>
</section>

<style>
    .add-card {
        width: 400px;
    }
</style>