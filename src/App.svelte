<script>
  import "./app.css";
  import Navbar from "./lib/Navbar.svelte";
  import { Router, Route } from "svelte-navigator";
  import PokemonGrid from "./lib/PokemonGrid.svelte";
  import Button from "./lib/Button.svelte";
  import Pokemon from "./lib/Pokemon.svelte";

  let offset = 0;

  const incrementOffset = () => {
    offset += 20;
  };

  const decrementOffset = () => {
    offset -= 20;
  };
</script>

<main class="flex flex-col justify-center items-center p-4">
  <Router>
    <Navbar />
    <Route path="/">
      <div class="flex justify-center items-center w-fit">
        {#if offset}
          <Button on:changeOffset={decrementOffset}>Prev</Button>
        {/if}
        <Button on:changeOffset={incrementOffset}>Next</Button>
      </div>
      <PokemonGrid {offset} />
    </Route>
    <Route path="/:name" let:params>
      <Pokemon name={params.name} />
    </Route>
  </Router>
</main>
