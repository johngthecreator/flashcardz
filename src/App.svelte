<script>
  import Router,{link} from "svelte-spa-router";
  import Home from "./routes/Home.svelte";
  import Practice from "./routes/Practice.svelte";
  let mobileMenu;
  let visible = false;
  function showMobileMenu(){
      if (visible){
        visible = false;
      }else{
        visible = true;
      }
    }
  const routes={
    '/':Home,
    '/flashcards':Practice
  } 
</script>
  <nav>
  <a href="/">
    <h2 style="color: white">CometNotes</h2>
  </a>
  <div class="desktopNav">
    <a class="link" href="/flashcards" use:link>Flashcards</a>
  </div>
  <!-- <button class="mobileButton" on:click={showMobileMenu}>menu</button> -->
  </nav>
  <Router {routes} />
  <!-- {#if visible}
    <div class="mobileNav" transition:fly="{{ y: -100, duration: 500 }}" bind:this={mobileMenu}>
     <Link to="/">Home</Link>
     <Link to="practice">Practice</Link>
    </div>
  {/if} -->