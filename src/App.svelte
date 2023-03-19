<script lang="ts">
  let tipoDeCalculacion = "a+b";
  let a;
  let b;
  let submitted = false;
  let res;
  function calcula(a, b, tipo){
    let res;
    if (tipo == "a+b"){
      res = Math.sqrt((Math.pow(a, 2) + Math.pow(b, 2)))
    } else if (tipo == "a-b"){
      res = Math.sqrt((Math.pow(a, 2) - Math.pow(b, 2)))
    }
    return res
  }
</script>

<h1 class="title is-1">Halla el teorema de pitagoras</h1>

<label for="calc">
  <p>
    Selecciona el tipo de calculacion :
  </p>
</label>

<div class="select is-info">
  <select name="calcular" id="calc" bind:value={tipoDeCalculacion}>
    <option value="a+b">Calcular la Hipotenusa</option>
    <option value="a-b">Calcular un Cateto</option>
  </select> 
</div>


<form on:submit|preventDefault={() => {
  res = calcula(a, b, tipoDeCalculacion)
  submitted = true;
}}>
  {#if tipoDeCalculacion == "a+b"}
    <h1 class="title is-3">Cateto B</h1>
    <div>
      <input type="text" bind:value={a}>
    </div>
    <h1 class="title is-3">Cateto C</h1>
    <div>
      <input type="text" bind:value={b}>
    </div>
  {:else if tipoDeCalculacion == "a-b"}
    <h1 class="title is-3">Hipotenusa</h1>
    <div>
      <input type="text" bind:value={a}>
    </div>
    <h1 class="title is-3">Cateto b/c</h1>
    <div>
      <input type="text" bind:value={b}>
    </div>
  {/if}
  <div>
    <input type="submit" value="Calcula" class="button is-info is-light">
  </div>
</form>

{#if submitted}
  <p>Resultado: {res}</p>
{/if}

<style>
  @import "https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css";

  h1{
    text-align: center;
  }

  div{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 2rem;
  }

  p{
    text-align: center;
    margin-bottom: 2rem;
  }
</style>