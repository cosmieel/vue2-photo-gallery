<template>
  <v-dialog
    v-model="$store.getters.getDialogVisible"
    max-width="600"
    @click:outside="hidePhotoDialog"
  >
    <v-card>
      <v-card-title>{{ full_title }}</v-card-title>
      <v-card-text>
        <v-img :src="$store.getters.getCurrentPhoto.url" />
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
import { mapMutations } from "vuex";
export default {
  methods: {
    ...mapMutations(["hideDialog"]),
    hidePhotoDialog() {
      this.hideDialog();
    },
  },
  computed: {
    full_title() {
      return `Название фотографии - ${this.$store.getters.getCurrentPhoto.title}`;
    },
  },
};
</script>

<style lang="scss" scoped></style>
