<template>
  <div class="app-container">
    <Navbar />
    <h1 class="title">Image Uploader</h1>
    <FileUploader @file-uploaded="handleFileUploaded" />
    <PreviewImage v-if="imageUrl" :imageUrl="imageUrl" />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import FileUploader from './components/FileUploader.vue';
import PreviewImage from './components/PreviewImage.vue';

export default {
  components: {
    Navbar,
    FileUploader,
    PreviewImage
  },
  data() {
    return {
      imageUrl: ''
    };
  },
  methods: {
    handleFileUploaded(url) {
      this.imageUrl = url;
    }
  }
};
</script>