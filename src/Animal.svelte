<script>
  export let animal = {};
</script>

<style>
  .title {
    font-weight: bold;
  }
  .card {
    background-color: #d3fdc9;
    box-shadow: 0 4px 8px 0 rgba(17, 49, 33, 0.2);
    border-radius: 5px;
    transition: 0.3s;
    padding: 10px;
    margin: 10px;
  }

  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(17, 49, 33, 0.2);
  }

  input {
    background-color: inherit;
    padding: 10px;
    font-size: 14px;
    color: black;
    border: 0;
    outline: none;
    margin-left: 5px;
    margin-bottom: 4px;
    max-width: 140px;
  }

  input[type="String"] {
    text-align: left;
    width: 100px;
  }
  input:focus {
    background-color: rgb(192, 245, 179);
  }

  input:required:invalid,
  input:focus:invalid {
    background-color: lightpink;
  }
</style>

<div class="card">
  <input bind:value={animal.nombre} class="title" />
  <input
    type="String"
    bind:value={animal.tipo} /> 
  <slot />
</div>
