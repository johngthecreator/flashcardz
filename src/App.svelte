<script>
  import { Router, Route, Link } from "svelte-routing";
  import Home from "./routes/Home.svelte";
  import Practice from "./routes/Practice.svelte";
  import { fly } from "svelte/transition";
  export let url = ""; //This property is necessary declare to avoid ignore the Router
  let mobileMenu;
  let visible = false;
  function showMobileMenu(){
      if (visible){
        visible = false;
      }else{
        visible = true;
      }
    }
</script>
<Router url="{url}">
  <nav>
    <Link to="/">
      <h2 style="color: white">CometNotes</h2>
    </Link>
    <div class="desktopNav">
     <Link class="link" to="flashcards">Flashcards</Link>
    </div>
    <!-- <button class="mobileButton" on:click={showMobileMenu}>menu</button> -->
   </nav>
  <!-- {#if visible}
    <div class="mobileNav" transition:fly="{{ y: -100, duration: 500 }}" bind:this={mobileMenu}>
     <Link to="/">Home</Link>
     <Link to="practice">Practice</Link>
    </div>
  {/if} -->
   <div>
     <Route path="flashcards" component="{Practice}" /> 
     <!--for now the router just support case sensitive,
         one workaround colud be add two time the route
         Example.
        <Route path="About" component="{About}" /> 
     -->
     <Route path="/"><Home /></Route>
   </div>
 </Router>