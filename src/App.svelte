<script lang="ts">
  import './app.css';
  import type List  from './Interfaces/List';
  import InputNote from './components/InputComponent/InputNote.svelte';
  import app from './main';
  
  
  var listOfNotes:Array<List>;

  const selectedItemOfList = (list:List):void =>{
    console.log("Nota seleccionada",list.id, list.value);
    return;
  };

  const getAllItems = (currentNotes:CustomEvent) => {
    listOfNotes = [...currentNotes.detail];
  };
</script>


<main>

  <div>
   <InputNote on:updateList={getAllItems}/>
  </div>

  <div class="w-64 h-64 grid grid-cols-4 gap-4 bg-slate-800">
    {#if listOfNotes != null}
      {#each listOfNotes  as item}
        <div class="card-list-group-item" on:click={selectedItemOfList(item)}> 
          {item.value} 
        </div>
      {/each}
    {/if}
  </div>
   
</main>

<style scoped>
  .card-list-group{
  

  }
</style>
