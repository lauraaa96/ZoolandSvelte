<script>
  import { onMount, getContext } from "svelte";
  import { jsonData }            from "./store.js";

  import Buscar                  from "./Buscar.svelte";
  import Persona                 from "./Persona.svelte";
  import Boton                   from "./Boton.svelte";

  const URL = getContext("URL");

  let busqueda = "";
  let persona = {};

  onMount(async () => {
    const response = await fetch(URL.personal);
    const data = await response.json();
    $jsonData = data;
  });

  $: regex = new RegExp(busqueda, "i");
  $: datos = busqueda 
    ? $jsonData.filter(item => regex.test(item.nombre))
    : $jsonData;

</script>

<style>
  .container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: left;
    flex-wrap: wrap;
  }
</style>

<h1>PERSONAL</h1>
<br>
<Buscar bind:busqueda />

<div class="container">
  <Persona bind:persona>
    <div style="text-align: right">
      <Boton documento={persona} tipo="insertar" coleccion="personal" />
    </div>
  </Persona>
</div>

<div class="container">
  {#each datos as persona}
    <Persona {persona}>
      <div style="text-align: right">
        <Boton documento={persona} tipo="modificar" coleccion="personal" />
        <Boton documento={persona} tipo="eliminar" coleccion="personal" />
      </div>
    </Persona>
  {/each}
</div>