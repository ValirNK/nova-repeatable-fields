<template>
    <div>
        <div
          class="imagePreviewWrapper"
          :style="{ 'background-image': `url(${previewImage})` }"
          @click="selectImage">
        </div>
        <input
          ref="fileInput"
          type="file"
          @input="pickFile"
          autocomplete="off"
          accept="image/png,image/jpeg,image/bmp,image/tiff"
          class="custom-file-input"
        >
        <input 
          type="text" 
          :name="subField.name" 
          :value="previewImage"
          v-bind="subField.attributes"
          id="FileInput"
          ref="uploadAvatar"
        >
        <!-- <input
            :id="subField.name"
            :name="subField.name"
            type="file"
            class="w-full form-control form-input form-input-bordered"
            v-bind="subField.attributes"
        /> -->
    </div>
</template>

<script>
export default {
  props: [
    'subField',
    'value'
  ],
  data() {
      return {
        previewImage: null,
        imageValue: null
      };
  },
  mounted() {
    this.previewImage = this.value
  },
  watch: {
    previewImage: function(val, oldVal) {
      this.$emit('input', val)
    }
  },
  methods: {
      selectImage () {
          this.$refs.fileInput.click()
      },
      pickFile () {
        let input = this.$refs.fileInput
        let file = input.files
        if (file && file[0]) {
          let reader = new FileReader
          reader.onload = e => {
            this.previewImage = e.target.result
          }
          reader.readAsDataURL(file[0])
          this.imageValue = file[0]
          console.log(this.imageValue)
          this.$emit('input', file[0])
        }
      }
  }
}
</script>

<style scoped lang="scss">
.imagePreviewWrapper {
    width: 85px;
    height: 85px;
    display: block;
    cursor: pointer;
    background-size: cover;
    background-position: center center;
    margin: 0 auto;
    margin-top: 10px;
}
#FileInput{
  display: none;
}
.custom-file-input::-webkit-file-upload-button {
  visibility: hidden;
}
.custom-file-input::before {
  content: 'Выберите изображение';
  display: block;
  background: linear-gradient(top, #f9f9f9, #e3e3e3);
  border: 1px solid #999;
  border-radius: 3px;
  padding: 5px 8px;
  outline: none;
  white-space: nowrap;
  -webkit-user-select: none;
  cursor: pointer;
  text-shadow: 1px 1px #fff;
  font-weight: 700;
  font-size: 10pt;
  width: 207px;
  word-wrap: break-word;
  text-align: center;
  margin: 0 auto;
  margin-top: 10px;
}
.custom-file-input:hover::before {
  border-color: black;
}
.custom-file-input:active::before {
  background: -webkit-linear-gradient(top, #e3e3e3, #f9f9f9);
}
</style>