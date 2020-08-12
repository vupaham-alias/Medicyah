<template>
  <div>
    <md-table v-model="users" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Hotel's name"><input type="text" :readonly="item.edit" v-model="item.name"></md-table-cell>
        <md-table-cell md-label="description"><input type="text" :readonly="item.edit" v-model="item.description"></md-table-cell>
        <md-table-cell md-label="Hotel's phone number"><input type="text" :readonly="item.edit" v-model="item.phone"></md-table-cell>
        <md-table-cell md-label="Action" style="width:250px">
          <md-button class="md-raised md-success" @click="updateHotel(item)">{{ item.btn }}</md-button>
          <md-button class="md-raised md-success" @click="deleteHotel(item)">delete</md-button>
        </md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
export default {
  name: "simple-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      actionType: 'Update',
      disableFile: true,
      selected: [],
      users: [
        {
          id: 1,
          name: "Dakota Rice",
          description: "$36,738",
          phone: "Niger",
          edit: true,
          btn: 'Update'
        },
        {
          id: 2,
          name: "Dakota Rice",
          description: "$36,738",
          phone: "Niger",
          edit: true,
          btn: 'Update'
        },
        {
          id: 3,
          name: "Dakota Rice",
          description: "$36,738",
          phone: "Niger",
          edit: true,
          btn: 'Update'
        },
        {
          id: 4,
          name: "Dakota Rice",
          description: "$36,738",
          phone: "Niger",
          edit: true,
          btn: 'Update'
        },
        {
          id: 5,
          name: "Dakota Rice",
          description: "$36,738",
          phone: "Niger",
          edit: true,
          btn: 'Update'
        },
      ]
    };
  },
  methods: {
    updateHotel(item){
      if(item.btn == 'Update'){
        item.btn = 'Save'
        item.edit = false
        let id = item.name
        // alert(id)
 
      }else{

        let emptyList = ''
        if(item.name.trim() == ''){
          emptyList = emptyList + 'name'
        }
        if(item.description.trim() == ''){
          if(emptyList.trim() == 0) emptyList = emptyList + 'description'
          else emptyList = emptyList + ', description'
        }
        if(item.phone.trim() == ''){
          if(emptyList.trim() == 0) emptyList = emptyList + 'phone'
          else emptyList = emptyList + ', phone'
        }

        if(emptyList.trim() != ''){
          alert('Please fill '+emptyList)
          return
        }
        else{
          item.edit = true
          item.btn = 'Update'
          alert('Item has been updated!'+ item.description)
        }
      }
    },
    deleteHotel(id){
      if(confirm("Do you really want to delete?")){
        axios.delete('/api/artist/'+id)
        .then(resp => {
            this.artists.data.splice(index, 1);
            alert('Item has been deleted!')
        })
        .catch(error => {
            console.log(error)
        })
      }
    }
  }
};
</script>
<style>
.md-raised.md-success{
  margin-left:10px !important;
}
</style>