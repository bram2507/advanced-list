<script lang="ts">
  
  import type List  from './Interfaces/List';
  import InputNote from './components/InputComponent/InputNote.svelte';
  
  
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

  <div class="card-list-group border-radius-sm">
    {#if listOfNotes != null}
      {#each listOfNotes  as item}
        <span class="card-list-group-item" on:click={selectedItemOfList(item)}> 
          {item.value} 
        </span><br>
      {/each}
    {/if}
  </div>
   
</main>

<style scoped>
  .card-list-group{
    background-color: white;
    width: 30rem;
    min-height: 50rem;

  }
</style>
