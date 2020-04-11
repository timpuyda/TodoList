<template>
  <div class="row">
   <div class="col-6 offset-3">
     <button v-show="!isCreating" v-on:click="isCreating=true" class="btn btn-primary btn-block">Create new todo</button>
     <div v-show="isCreating" class="card my-1">
      <div class="card-body"> 
        <form>
          <div class="form-group">
            <label>Title</label>
            <input type="text" v-model="createTitle" class="form-control">
          </div>
          <div class="form-group">
            <label>Description</label>
            <input type="text" v-model="createDesc" class="form-control" >
          </div>
          <div class="btn-group d-flex justify-content-end">  
            <button type="button" v-on:click="createItem" class="btn btn-outline-primary">Create</button>
            <button type="button" v-on:click="isCreating=false" class="btn btn-outline-danger">Cancel</button>
            <input class="btn btn-outline-warning" type="reset" value="Reset">
          </div>
        </form>
      </div>
    </div>   
  </div>
</div>
</template>

<script>
export default {
 props:['todos'],
 data(){
  return{
    isCreating: false,
    createTitle: '',
    createDesc: '',
    idCount:4
  }
 },
 methods:{
  createItem(){
    if(this.createTitle.length>0)
    this.$emit('add-todo',{
      todoTitle: this.createTitle,
      todoDesc: this.createDesc,
      done: false,
      id:this.idCount 
    });
    this.isCreating= false;
    this.createTitle= '';
    this.createDesc= '';
    this.idCount++
  }
 }
}
</script>
