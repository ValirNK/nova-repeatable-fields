<template>
    <div>
        <file-upload :url="url" :id="id" :label="label"></file-upload>
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
  import {fileUpload} from '@yazan.alnughnugh/file-upload'
  export default {
    components: {
        fileUpload
    },
    name: 'ImageUpload',
    // props: [
    //     'subField',
    //     'value'
    // ],
    data() {
      return {
        // uploadedFiles: [],
        // uploadError: null,
        // currentStatus: null,
        // uploadFieldName: 'photos'
      }
    },
    computed: {
    //   isInitial() {
    //     return this.currentStatus === STATUS_INITIAL;
    //   },
    //   isSaving() {
    //     return this.currentStatus === STATUS_SAVING;
    //   },
    //   isSuccess() {
    //     return this.currentStatus === STATUS_SUCCESS;
    //   },
    //   isFailed() {
    //     return this.currentStatus === STATUS_FAILED;
    //   }
    },
    methods: {
    //   reset() {
    //     // reset form to initial state
    //     this.currentStatus = STATUS_INITIAL;
    //     this.uploadedFiles = [];
    //     this.uploadError = null;
    //   },
    //   save(formData) {
    //     // upload data to the server
    //     this.currentStatus = STATUS_SAVING;

    //     upload(formData)
    //       .then(x => {
    //         this.uploadedFiles = [].concat(x);
    //         this.currentStatus = STATUS_SUCCESS;
    //       })
    //       .catch(err => {
    //         this.uploadError = err.response;
    //         this.currentStatus = STATUS_FAILED;
    //       });
    //   },
    //   filesChange(fieldName, fileList) {
    //     // handle file changes
    //     const formData = new FormData();

    //     if (!fileList.length) return;

    //     // append the files to FormData
    //     Array
    //       .from(Array(fileList.length).keys())
    //       .map(x => {
    //         formData.append(fieldName, fileList[x], fileList[x].name);
    //       });

    //     // save it
    //     console.log(formData)
    //     this.save(formData);
    //   }
    },
    mounted() {
    //   this.reset();
    },
  }

</script>


<style lang="scss">
  .dropbox {
    outline: 2px dashed grey; /* the dash box */
    outline-offset: -10px;
    background: lightcyan;
    color: dimgray;
    padding: 10px 10px;
    // min-height: 200px; /* minimum height */
    position: relative;
    cursor: pointer;
  }
  
  .input-file {
    opacity: 0; /* invisible but it's there! */
    width: 100%;
    // height: 200px;
    position: absolute;
    cursor: pointer;
  }
  
  .dropbox:hover {
    background: lightblue; /* when mouse over to the drop zone, change color */
  }
  
  .dropbox p {
    font-size: 1.2em;
    text-align: center;
    padding: 10px 0;
  }
</style>