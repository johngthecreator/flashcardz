<script>
  import { Router, Link, Route } from "svelte-routing";
  import Home from "./routes/Home.svelte";
  import Practice from "./routes/Practice.svelte";
  export let url = "";
</script>
  <Router url={url}>
    <nav>
      <Link to="/">
        <h2 style="color: white">CometNotes</h2>
      </Link>
      <div class="desktopNav">
        <Link class="link" to="flashcards" >Flashcards</Link>
      </div>
    </nav>
    <div>
      <Route path="flashcards" component="{Practice}" />
      <Route path="/"><Home /></Route>
    </div>
  </Router>