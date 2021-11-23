<template>
  <div class="note-selectors">
    <NoteSelector 
      v-for="note in notes"
      v-bind:key="note.id"
      v-bind:note="note"
      v-bind:selectedNoteId="selectedNoteId"
      v-on:selectNote="selectNote"
    />

  </div>
</template>

<script>
import NoteSelector from './NoteSelector.vue'
  export default {
    components: {
      NoteSelector
    },
    methods: {
      selectNote: function(note) {
        this.$emit("selectNote", note)
      }
    },
    props: ['notes', 'selectedNoteId']
  }
</script>