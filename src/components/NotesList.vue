<template>
  <div class="w-full flex flex-col justify-center">
    <input
      type="text"
      class="w-full shadow appearance-none border rounded py-2 px-3 mb-8 text-gray-900 lg:w-1/2"
      placeholder="Enter your thoughts here"
      v-model="newNote"
      @keyup.enter="addNote"
    />
    <div class="flex flex-fow justify-between mb-1 lg:w-1/2" v-for="(note, index) in notes" :key="note.id">
      <div v-if="!note.editing" @dblclick="editNote(note)" class="text-lg ml-1">
        {{ note.text }}
      </div>
      <input
        v-else
        class="shadow appearance-none border rounded py-1 px-2"
        type="text"
        v-model="note.text"
        @keyup.esc="cancelEditing(note)"
        @blur="doneEditing(note)"
        @keyup.enter="doneEditing(note)"
        v-focus
      />
      <button class="mr-1 font-medium" @click="removeNote(index)">x</button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newNote: '',
      textBeforeEdit: '',
      notes: [],
    };
  },
  directives: {
    focus: {
      //directives definition
      inserted: function (el) {
        el.focus();
      },
    },
  },
  computed: {},
  props: {},
  methods: {
    addNote() {
      if (this.newNote.trim().length == 0) {
        return;
      }
      this.notes.push({
        id: this.noteId,
        text: this.newNote,
      });

      this.newNote = '';
      this.noteId++;
    },
    removeNote(index) {
      this.notes.splice(index, 1);
    },
    editNote(note) {
      this.textBeforeEdit = note.text;
      note.editing = true;
    },
    cancelEditing(note) {
      note.text = this.textBeforeEdit;
      note.editing = false;
    },
    doneEditing(note) {
      if (note.text.trim() == '') {
        note.text = this.textBeforeEdit;
      }
      note.editing = false;
    },
  },
};
</script>
