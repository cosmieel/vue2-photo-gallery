<template>
  <v-container>
    <v-row class="d-flex">
      <v-text-field
        v-model="imgTitle"
        placeholder="Введите название изображения"
      />
      <v-file-input v-model="img" placeholder="Загрузите файл изображения" />
      <v-btn @click="addPhoto">Добавить</v-btn>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      imgTitle: "",
      img: null,
    };
  },
  methods: {
    addPhoto() {
      const reader = new FileReader();
      reader.onload = () => {
        let photo = {
          id: Date.now(),
          title: this.imgTitle,
          url: reader.result,
        };
        this.$emit("addPhotoToList", photo);
      };
      reader.readAsDataURL(this.img);
    },
  },
};
</script>

<style lang="scss" scoped></style>
