<template>
  <div class="p-10">
    <h1 class="font-extrathin text-4xl tracking-wide">Notes</h1>
    <p class="text-xs italic text-gray-600">Add your note by pressing Enter.</p>
    <p class="text-xs italic text-gray-600">Remove a note from the list by pressing the x.</p>
    <p class="text-xs italic text-gray-600">Edit your notes by double clicking on it</p>
    <p class="text-xs italic text-gray-600 mb-3">Cancel editing by pressing escape and finish editing by pressing Enter</p>
    <NotesList />
  </div>
</template>

<script setup>
import NotesList from './components/NotesList.vue';

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
