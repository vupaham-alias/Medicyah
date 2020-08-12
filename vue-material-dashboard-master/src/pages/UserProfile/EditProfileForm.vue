<template>
  <form>
    <md-card>
      <md-card-header :data-background-color="dataBackgroundColor">
        <h4 class="title">Hotel</h4>
        <p class="category">Complete your profile</p>
      </md-card-header>

      <md-card-content>
        <div class="md-layout">
          <div class="md-layout-item md-small-size-100 md-size-33">
            <md-field>
              <label>Hotel's name</label>
              <md-input v-model="item.name"></md-input>
            </md-field>
          </div>
          <div class="md-layout-item md-small-size-100 md-size-33">
            <md-field>
              <label>Hotel's phone number</label>
              <md-input v-model="item.phone" type="text"></md-input>
            </md-field>
          </div>
          <div class="md-layout-item md-size-100">
            <md-field maxlength="5">
              <label>Description</label>
              <md-textarea v-model="item.description"></md-textarea>
            </md-field>
          </div>
          <div id="my-strictly-unique-vue-upload-multiple-image" style="display: flex; justify-content: center;">
            <vue-upload-multiple-image
              @upload-success="uploadImageSuccess"
              @before-remove="beforeRemove"
              @edit-image="editImage"
              :data-images="images"
              idUpload="myIdUpload"
              editUpload="myIdEdit"
            ></vue-upload-multiple-image>
          </div>
          <div class="md-layout-item md-size-100 text-right">
            <md-button class="md-raised md-success" @click="saveItem">Save</md-button>
          </div>
        </div>
      </md-card-content>
    </md-card>
  </form>
</template>

<script>
import VueUploadMultipleImage from 'vue-upload-multiple-image'

export default {
  components: {
    VueUploadMultipleImage,
  },
  name: "edit-profile-form",
  props: {
    dataBackgroundColor: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      imgList: null,
      images: [],
      item:{
        name: '',
        description: '',
        phone: ''
      },
    };
  },
  methods: {
    saveItem(){
      let emptyList = ''
      if(this.item.name.trim() == ''){
        emptyList = emptyList + 'name'
      }
      if(this.item.description.trim() == ''){
        if(emptyList.trim() == 0) emptyList = emptyList + 'description'
        else emptyList = emptyList + ', description'
      }
      if(this.item.phone.trim() == ''){
        if(emptyList.trim() == 0) emptyList = emptyList + 'phone'
        else emptyList = emptyList + ', phone'
      }
      if(this.imgList != null){
        if(this.imgList.length == 0){
          if(emptyList.trim() == 0) emptyList = emptyList + 'image'
          else emptyList = emptyList + ', image'
        }  
      }else{
        if(emptyList.trim() == 0) emptyList = emptyList + 'image'
        else emptyList = emptyList + ', image'
      }
      if(emptyList.trim() != ''){
        alert('Please fill '+emptyList)
        return
      }
      else{
        this.item.images = this.imgList
        console.log(this.item)
        // alert('Hotel has been created!')
      } 
      this.item = {
        name: '',
        description: '',
        phone: ''
      }
      this.images = []
      this.imgList = null
      emptyList = ''
    },
    uploadImageSuccess(formData, index, fileList) {
      this.imgList = fileList
      // Upload image api
      // axios.post('http://your-url-upload', formData).then(response => {
      //   console.log(response)
      // })
    },
    beforeRemove (index, done, fileList) {
      this.imgList = fileLis
      var r = confirm("remove image")
      if (r == true) {
        done()
      } else {
      }
    },
    editImage (formData, index, fileList) {
      this.imgList = fileLis
    }
  }
};
</script>
<style></style>
