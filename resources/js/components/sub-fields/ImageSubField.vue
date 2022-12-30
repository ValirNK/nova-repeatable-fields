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
        >
        <input 
          type="text" 
          :name="subField.name" 
          :value="previewImage"
          v-bind="subField.attributes"
          v-model="previewImage"
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
    width: 50px;
    height: 50px;
    display: block;
    float: left;
    cursor: pointer;
    background-size: cover;
    background-position: center center;
}
#FileInput{
  display: none;
}
</style>