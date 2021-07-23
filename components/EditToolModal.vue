<template>
  <div>    
    <b-modal id="editToolModal" title="Edit tool" ok-title="Save tool" @ok="onEdit">
      <form action="#">
        <b-form-group
         label="Name" 
         label-for="name">
          <b-form-input id="name" v-model="tool.name" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Brand" 
         label-for="brand">
          <b-form-input id="brand" v-model="tool.brand" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Description" 
         label-for="description">
          <b-form-input id="description" v-model="tool.description" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Price" 
         label-for="price">
          <b-form-input id="price" type="number" v-model="tool.price" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Date Acquired" 
         label-for="acquired_on">
          <b-form-input id="acquired_on" type="date" v-model="tool.acquired_on" trim></b-form-input>
        </b-form-group>
      </form>
    </b-modal>  
  </div>
</template>

<script>
export default {
  props: {
    tool: {}
  },
  methods: {
    async onEdit(){
      this.$axios.put('/api/tools/' + this.tool.id, this.tool)
      .then((res)=>{
        if(res.status==202){
          alert("Tool Succesfully Edited")
        }
      })
      .catch((err)=>{
        alert(err.message)
      })
    }
  }
}
</script>

<style>

</style>