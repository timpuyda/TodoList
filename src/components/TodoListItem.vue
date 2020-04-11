<template>
        <div class="col-6 offset-3">
          <div class="card my-1">
            <div class="card-body border-dark" v-show="!isEditing">
              <h5 class="card-title mb-0"> {{todo.todoTitle}} </h5>
              <p class="text-muted"> {{todo.todoDesc}}</p>
              <div class="d-flex justify-content-between">
                <div>
                 <button v-show="!todo.done" v-on:click="todo.done=true" class="btn btn-success px-2 py-1 rounded" style="cursor:pointer"> ✓</button>
                </div>
                <div>
                  <span  style="cursor:pointer" v-on:click="editItem"> ✎ </span>
                  <br>
                  <span style="cursor:pointer" v-on:click="deleteItem(todo)"> ❌ </span>
                </div>
              </div>
            </div>
            <div v-show="todo.done" class="card-footer border border-success">
              <p class="text-success text-center font-weight-bold">Completed</p>
            </div>
             <div v-show="!todo.done" class="card-footer border border-danger">
              <p class="text-danger text-center font-weight-bold">Pending</p>
            </div>

            <div class="card-body" v-show="isEditing"> 
            <form>
              <div class="form-group">
                <label>Title</label>
                <input v-model="todo.todoTitle" type="text" class="form-control" placeholder="placeholder">
              </div>
              <div class="form-group">
                <label>Description</label>
                <input v-model="todo.todoDesc" type="text" class="form-control" placeholder="placeholder">
              </div>
                  <button v-on:click="editItem(todo)" type="button" class="btn btn-outline-primary btn-block">Close X</button>
            </form>
          </div>
          </div>
        </div>
</template>

<script>
export default {
  props:['todo'],
  data(){
    return{
      isEditing: false
    }
  },
  methods:{
    deleteItem(todo){
      this.$emit('delete-todo',todo)
    },
    editItem(){
      this.isEditing = !this.isEditing
    }
  }
}
</script>
