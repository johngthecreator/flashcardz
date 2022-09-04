<script>
  import CardInput from '../lib/CardInput.svelte';
  import Flashcard from '../lib/Flashcard.svelte';
  import {cardList} from '../stores.js'
  let cardCache;
  if (localStorage.getItem('cards')){
    cardCache = JSON.parse(localStorage.getItem('cards'));
  }
</script>

<main>
  <CardInput />
  {#if ($cardList.length >= 1)}
    {#each $cardList as card}
      <Flashcard title={card.item.split(":")[0] ? card.item.split(":")[0].replace("-",""):"" } def={card.item.split(":")[0] ? card.item.split(":")[1].replace("-",""):""} />
    {/each}
  {:else if (cardCache)}
    {#each cardCache as card}
      <Flashcard title={card.item.split(":")[0] ? card.item.split(":")[0].replace("-",""):"" } def={card.item.split(":")[0] ? card.item.split(":")[1].replace("-",""):""} />
    {/each}
  {:else}
    <h3>Make A New Flashcard Set!</h3>
  
  {/if}

</main>

<style>
  main {
    display:grid;
    justify-content: center;
  }
</style>