<template>
  <div>
    <div v-for="note in notes()" :key="note.id">
      <div @click="openNote(note)">
        <note-list-item :title="note.title" />
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
import NoteListItem from "@/components/NoteList/NoteListItem.vue";

export default {
  name: "card-list",
  components: {
    "note-list-item": NoteListItem
  },
  computed: {
    ...mapGetters(["notes", "noteById", "isLoading"])
  },
  methods: {
    ...mapActions(["loadNotes", "selectNote"]),
    openNote(note) {
      this.selectNote(note);
    }
  },
  created() {
    this.loadNotes();
  }
};
</script>

<style></style>
