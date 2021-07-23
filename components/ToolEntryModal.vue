<template>
  <div>
    <b-button v-b-modal.toolEntryModal variant="primary">Add Tool</b-button>
    
    <b-modal id="toolEntryModal" title="Add Tool" ok-title="Save Tool" @ok="onAdd">
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
  data(){
    return {
      tool: {}
    }
  },
  methods: {
    async onAdd(){
      this.$axios.post('/api/tools', this.tool)
      .then((res)=>{
        if(res.status==202){
          alert("Tool Succesfully added")
          this.$emit('onAddEntry')
        }
      })
    }
  }
}
</script>

<style>

</style>