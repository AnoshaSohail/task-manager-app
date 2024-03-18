<template>
  <div>
    <form action="">
      <input type="text" v-model="newTask" />
      <button @click="addTask">Add Task</button>
    </form>
  </div>
</template>
<script>
export default {
   props: ['tasks'],
  data(){
    return{
        newTask:''
    }
  },
  methods:{
    addTask(){
        if(this.newTask.trim()!==''){
            this.$emit('add-task', this.newTask);
            this.newTask='';
        }
    }
  }
};
</script>