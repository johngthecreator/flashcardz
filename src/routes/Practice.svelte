<script>
  import CardInput from '../lib/CardInput.svelte';
  import Flashcard from '../lib/Flashcard.svelte';
  import {cardList} from '../stores.js'
  let cardCache;
  if (localStorage.getItem('cards')){
    cardCache = JSON.parse(localStorage.getItem('cards'));
  }
  let switchCards = true;
</script>

<main>
  <CardInput />
  <button on:click={()=>{(switchCards ? switchCards = false: switchCards = true)}}>Switch Cards</button>
  {#if switchCards}
    {#if ($cardList.length >= 1)}
      {#each $cardList as card}
        <Flashcard title={card.item.split(":")[0] ? card.item.split(":")[0].replace("-",""):"" } def={card.item.split(":")[1] ? card.item.split(":")[1]:""} />
      {/each}
    {:else if (cardCache)}
      {#each cardCache as card}
        <Flashcard title={card.item.split(":")[0] ? card.item.split(":")[0].replace("-",""):"" } def={card.item.split(":")[1] ? card.item.split(":")[1]:""} />
      {/each}
    {:else}
      <h3>Make A New Flashcard Set!</h3>
    
    {/if}

  {:else}

  <!-- This is a ghetto feature of def on front and terms on back -->
    {#if ($cardList.length >= 1)}
      {#each $cardList as card}
        <Flashcard title={card.item.split(":")[1] ? card.item.split(":")[1].replace("-",""):"" } def={card.item.split(":")[0] ? card.item.split(":")[0]:""} />
      {/each}
    {:else if (cardCache)}
      {#each cardCache as card}
        <Flashcard title={card.item.split(":")[1] ? card.item.split(":")[1].replace("-",""):"" } def={card.item.split(":")[0] ? card.item.split(":")[0]:""} />
      {/each}
    {:else}
      <h3>Make A New Flashcard Set!</h3>
    {/if}
  {/if}
  <!---End of ghetto feature--->

</main>

<style>
  main {
    display:grid;
    justify-content: center;
  }
  button{
        font-weight: 700;
        width: auto; 
        color: white; 
        padding: 15px;
        border-radius: 10px;
        align-items: center; 
        background-color: #256EFF; 
        border: 2px solid #256EFF ;
        transition: .3s;
    }
    button:hover{
        color: #256EFF;
        border: 2px solid #256EFF ;
        background-color: white ;
    }
</style>