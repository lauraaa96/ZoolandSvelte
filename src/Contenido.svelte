<script>
  import { Route }  from "svelte-routing";
  import Inicio     from "./Inicio.svelte";
  import Articulos  from "./Animales.svelte";
  import Clientes   from "./Personal.svelte";
import Personal from "./Personal.svelte";
import Animales from "./Animales.svelte";
</script>

<style>
  main {
    padding: 20px;
    padding-top: 50px;
  }
</style>

<main id="contenido">
  <Route path="/" component={Inicio} />
  <Route path="/animales" component={Animales} />
  <Route path="/personal" component={Personal} />
</main>
