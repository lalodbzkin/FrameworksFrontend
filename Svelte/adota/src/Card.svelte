  <div class="card" style="width: 18rem;">
    <img src={img} class="card-img-top" alt="...">
    <div class="card-body" style="text-align:center">
      <h5 class="card-title">{nome}</h5>
      <p class="card-text">{desc}</p>
      <!-- svelte-ignore a11y-missing-attribute -->
      <a class="btn btn-primary" style="color:white !important" on:click={showModal}>Ver informações</a>
      <!-- svelte-ignore a11y-missing-attribute -->
      <a class="btn btn-danger" style="color:white !important; margin-left: 15px" on:click={showModalEdicao}>Editar</a>

    </div>
  </div>

  {#if show === true}
    <Info nome = {nome} desc = {desc} index = {index} on:adocao1={remover}></Info>
  {/if}

  
  {#if showEdicao === true}
    <Edicao nome = {nome} desc = {desc} img = {img} index = {index} on:editar={editar}></Edicao>
  {/if}


<script>
import Info from './Info.svelte'
import Edicao from './Edicao.svelte'
import { createEventDispatcher } from 'svelte'

export let nome
export let desc
export let img
export let index
let show = false;
let showEdicao = false;
const dispatcher = createEventDispatcher()

console.log(nome)
        
function showModal(){
      show = !show;
 }

 function showModalEdicao(){
     showEdicao = !showEdicao;
 }

 function editar(event){
    console.log(event)
    dispatcher('editar', event.detail)
 }

 function remover(event){
    dispatcher('adocao2', event.detail)
 }
</script>