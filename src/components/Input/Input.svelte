
<script lang="ts">

import type Note  from '../../Interfaces/Note.js';
import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();
let input:String = "";
export let Notes:Array<Note>;

const keyUpEvent = (event:KeyboardEvent) => {
    if (event.key === "Enter"){
        const value = {id: Math.floor(Math.random() * 100) , value: input};
        console.log(value);
        Notes = [...Notes,value];
        input="";
        dispatch('updateList',Notes);
    }
};

</script>

<main class="isolate bg-white px-6 py-24 sm:py-10 lg:px-8 rounded-sm shadow-sm">
  <div class="sm:col-span-2">
    <label for="company" class="block text-sm font-semibold leading-6 text-primary font-medium text-base">Escribe una nota</label>
    <div class="mt-2.5">
      <input type="text" name="company" id="company" autocomplete="organization" class="block w-full rounded-sm border-0  px-3.5 py-2 ring-2 ring-inset ring-primary/50 focus:ring-primary/50 sm:text-sm sm:leading-6"  placeholder="Escribe una nota" bind:value={input} on:keyup="{keyUpEvent}">
    </div>
</main>

 