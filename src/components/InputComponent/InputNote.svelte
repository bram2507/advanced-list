

<script lang="ts">

import type List  from './../../Interfaces/List.ts';
import { createEventDispatcher } from 'svelte';

  

const dispatch = createEventDispatcher()
var inputValue:String = "";
var listGroup:Array<List> = new Array();
var id:number = 0;


const keyUp = (event:KeyboardEvent) => {
    if (event.key === "Enter"){
        listGroup.push({
          id: id++,
          value: inputValue});
        dispatch('updateList',listGroup);
    }
    
};


</script>

<div>
  <label for="inpunt">Escriba una nota</label><br>
  <input type="text" bind:value={inputValue} on:keyup="{keyUp}">
</div>

<style scoped>

</style>