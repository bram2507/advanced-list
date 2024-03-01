
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
    <label for="company" class="block text-sm font-semibold leading-6 text-gray-900">Escribe una nota</label>
    <div class="mt-2.5">
      <input type="text" name="company" id="company" autocomplete="organization" class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" bind:value={input} on:keyup="{keyUpEvent}">
    </div>
</main>

 