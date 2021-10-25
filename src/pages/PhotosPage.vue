<template>
  <v-container>
    <PhotoForm
      v-if="$store.getters.getAllPhotos.length < 15"
      @addPhotoToList="addPhotoToList"
    />
    <div v-else>Вы не можете добавить больше фотографий</div>
    <v-row>
      <Photo
        v-for="photo in $store.getters.getAllPhotos"
        :key="photo.id"
        :photo="photo"
      />
    </v-row>
    <PhotoDialog />
  </v-container>
</template>

<script>
import Photo from "@/components/photo/Photo";
import PhotoForm from "@/components/photo/PhotoForm";
import PhotoDialog from "@/components/photo/PhotoDialog";
import { mapActions, mapMutations } from "vuex";

export default {
  components: {
    Photo,
    PhotoForm,
    PhotoDialog,
  },
  mounted() {
    this.fetchPhotos();
  },
  methods: {
    ...mapActions(["fetchPhotos"]),
    ...mapMutations(["addPhoto"]),
    addPhotoToList(photo) {
      this.addPhoto(photo);
    },
    openPhoto(photo) {
      this.currentPhoto = photo;
      this.dialogVisible = true;
    },
  },
};
</script>

<style lang="scss" scoped></style>
