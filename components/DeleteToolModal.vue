<template>
   <div>    
    <b-modal id="deleteToolModal" title="Delete Tool" ok-title="Delete Tool" @ok="onDelete">
      Do you want to continue? <br>
      {{tool.name}}
    </b-modal>  
  </div>
</template>

<script>
export default {
  props: {
    tool: {}
  },
  methods: {
    async onDelete(){
      this.$axios.delete('/api/tools/' + this.tool.id)
      .then((res)=>{
        if(res.status==202){
          alert("Tool Succesfully Deleted")
          this.$emit('onDeleteEntry')
        }
      })
    }
  }
}
</script>

<style>

</style>
