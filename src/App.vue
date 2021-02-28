<template>
  <Navbar @onNoteAdd="addNote"/>
  <NoteList :data="noteList" @onNoteDelete="deleteNote" @onNoteAttributeChange="onNoteAttributeChange"/>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import NoteList from "./components/NoteList.vue";
import { v4 as uuidv4} from 'uuid';

export default {
  name: "App",
  components: {
    Navbar,
    NoteList,
  },
  data() {
    return {
      noteList: [],
    }
  },
  methods: {
    addNote(){
      this.noteList.push({
        title: 'New Note',
        content: 'blabla',
        uuid: uuidv4(),
      })
      console.log(this.noteList);
    },
    deleteNote(uuid) {
      const index = this.noteList.findIndex( note => note.uuid === uuid);
      this.noteList.splice(index, 1);
      console.log(uuid);
    },
    onNoteAttributeChange({value, attribute, uuid}) {
      const note = this.noteList.find( note => note.uuid === uuid);
      note[attribute] = value;
      console.log(attribute);
    }
  },

};
</script>

<style lang="scss">
$primary: rgb(201, 174, 219);
@import "~bulma";

</style>
