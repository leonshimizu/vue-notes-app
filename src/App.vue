<template>
  <div id="app">
    <Toolbar />
    <NoteContainer 
      v-bind:notes="notes"
      v-bind:selectedNoteId="selectedNoteId"
      v-on:selectNote="selectNote"
    />
    <br>
    <hr>
    <br>
    <h1>Single Select</h1>
    <multiselect v-model="value" :options="options"></multiselect>
    <br>
    <hr>
    <br>
    <h1>Auto Complete</h1>
    <autocomplete
      source="https://api.github.com/search/repositories?q="
      results-property="items"
      results-display="full_name">
    </autocomplete>
  </div>
</template>

<script>
import Toolbar from './components/Toolbar.vue'
import NoteContainer from './components/NoteContainer.vue'
import Multiselect from 'vue-multiselect'
import Vue from 'vue'
import Autocomplete from 'vuejs-auto-complete'
export default {
  components: {
    Toolbar,
    NoteContainer,
    Multiselect,
    Autocomplete
  },
  data: function () {
    return {
      notes: [
        { id: 1, body: "This is the first test", timestamp: Date.now() },
        { id: 2, body: "This is the second test", timestamp: Date.now() },
        { id: 3, body: "This is the third test", timestamp: Date.now() }
      ],
      selectedNoteId: 1,
      value: null,
      options: ['list', 'of', 'options']
    }
  },
  methods: {
    selectNote: function(note) {
      this.selectedNoteId = note.id;
    }
    },
  name: 'app'
};
</script>

<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>

<!-- 
<style>
/* RESET */
* {
  margin: 0;
  padding: 0;
  border: 0;
  outline: none;
  box-sizing: border-box;
}

/* LAYOUT */
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.toolbar {
  padding: 0.5em;
}
.toolbar-button, .toolbar-search {
  padding: inherit;
  border-radius: 0.3em;
}
.toolbar-search {
  float: right;
}
.note-container {
  display: flex;
  flex: 1;
}
.note-selectors {
  flex: 0 0 13em;
}
.note-selector {
  padding: 1em;
}
.note-selector p {
  margin: 0;
}
.note-editor {
  display: flex;
  flex: 1;
  flex-direction: column;
}
.note-editor-info {
  padding: 0.5em;
  text-align: center;
}
.note-editor-input {
  display: flex;
  flex: 1;
  width: 100%;
  padding: 0 2em 0 2em;
}

/* COLORS */
* {
  color: #454545;
  background-color: #FAFAF8;
}
.toolbar {
  background-color: #DCDADC;
}
.toolbar-button {
  background-color: #FFFFFF;
}
.toolbar-button:active {
  background-color: #AAAAAA;
}
.note-selectors {
  border-right: 1px solid #DCDADC;
}
.note-selector {
  border-bottom: 1px solid #DCDADC;
}
.note-selector.active {
  background-color: #FCE18D;
}
.note-selector-title {
  background-color: inherit;
}
.note-selector-timestamp {
  color: #626262;
  background-color: inherit;
}
.note-editor-info {
  color: #DCDADC;
}

/* TYPOGRAPHY */
body {
  font-family: sans-serif;
}
.note-selector-title {
  font-weight: bold;
}
.note-selector-timestamp {
  font-size: 0.7em;
}
.note-editor, .note-editor-input {
  font-size: 0.9em;
}
</style>
-->