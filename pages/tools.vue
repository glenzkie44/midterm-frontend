<template>
  <div>
    <NavBar/>
    <EditToolModal :tool="selectedTool"/>
    <DeleteToolModal :tool="selectedTool" @onDeleteEntry="getAll" />
    <div class="container">
        <h1>
          <ToolEntryModal class="float-right mb-2" @onAddEntry="getAll"/>
          Tools
          </h1>
      <table class="table table-striped">
        <thead class="bg-info text-light">
          <th>Name</th>
          <th>Brand</th>
          <th>Description</th>
          <th>Price</th>
          <th>Date Acquired</th>
          <th>&nbsp;</th>
          <th>&nbsp;</th>
        </thead>
        <tbody>
          <tr v-for="tool in tools" :key="tool.id">
            <td>{{tool.name}}</td>
            <td>{{tool.brand}}</td>
            <td>{{tool.description}}</td>
            <td>{{tool.price}}</td>
            <td>{{tool.acquired_on}}</td>
            <td>
              <b-button @click="onEdit(tool)" variant="secondary" size="sm">Edit</b-button>
            </td>
            <td>
              <b-button @click="onDelete(tool)" variant="danger" size="sm">Delete</b-button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return {
      tools: [],
      selectedTool: {}
    }
  },
  methods: {
    async getAll(){
      await this.$axios.get('/api/tools')
      .then((res)=>{
        if(res.status==200){
          this.tools = res.data
        }
      })
    },
    onEdit(selectedTool){
      this.selectedTool = selectedTool
      this.$bvModal.show('editToolModal')
    },
    onDelete(selectedTool){
      this.selectedTool = selectedTool
      this.$bvModal.show('deleteToolModal')
    }
  },
  created(){
    this.getAll()  
  }
}
</script>

<style>

</style>