<template>
  <div style="display: flex;
  align-items: center;
  justify-content: center;">
    <form id="form" ref="form" style="align-content: center">
      <div style="height: 30px"></div>
      <input type="file" name="file" required>
      <div style="height: 60px"></div>
      <button type="button" v-on:click="submitFile">Subir Archivo</button>
    </form>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'App',
    data() {
      return {
        return: {
          file: null,
        }
      }
    },
    methods: {
      async submitFile() {
        // Selects the form
        let formData = new FormData(document.querySelector('form'));

        // Sends the request
        await axios({
          method: 'post',
          url: `https://udixaoaue6.execute-api.us-east-1.amazonaws.com/default/rustynail-upload-image`,
          data: formData,
          headers: {'content-type': 'multipart/form-data;'},
          withCredentials: true
        });
      }
    }
  }
</script>

<style scoped></style>
