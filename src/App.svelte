<script lang="ts">
  import './app.css';
  import type Note  from './Interfaces/Note';
  import Input from './components/Input/Input.svelte';
  
  var AllNotes:Array<Note> = new Array<Note>();

  const delteItemOfList = (list:Note):void => {
    const filterNotes = AllNotes.filter(l => { return list.id !== l.id});
    AllNotes = filterNotes;
  };

  const getAllItems = (currentNotes:CustomEvent) => {
    AllNotes = currentNotes.detail;
  };
</script>

<main class=" bg-primary min-w-screen flex flex-col h-screen justify-center">
  <div class="w-80 h-fit rounded-md shadow-sm m-auto  flex-col content-center">
    <Input on:updateList={getAllItems} Notes={AllNotes}/>
    {#if AllNotes != null}
      {#each AllNotes  as item}
        <div class="w-100 h-10 m-auto bg-white rounded-sm mt-2 mb-2 shadow-md flex justify-center content-center"  
                         on:keypress={(event) => {}} 
                         on:click={delteItemOfList(item)} > 
          {item.value} 
        </div>
      {/each}
    {/if}
  </div>
   
</main>
