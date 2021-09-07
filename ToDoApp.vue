<template>
  <div class="container">
    <h2>To Do:</h2>
   <!--input-->
    <div class="d-flex">
     <input v-model="task" type="text" placeholder="add here" class="form-control" width="500px">
    <button @click="submit" class="btn btn-primary rounded-100">Add item</button>
    </div>
    <!--table for lists-->
    <table class="table table-bordered">
   <thead>
    <tr>
      <th scope="col">Tasks for today</th>
      <th scope="col">Completed</th>
    </tr>
  </thead>
  <!--bootstrap table body-->
  <tbody>
    <tr v-for="(task,index) in tasks" :key="index">
      <td>{{task.name}}</td>
      <!--clickable status change-->
      <td>
        <span @click="ChangeStatus(index)" class="pointer">
          {{task.status}}
        </span>
      </td> 
    </tr>
  </tbody>
</table>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  data() {
    return {
      task:'',
      available: ['to be done','yes'],
      tasks: [{}] 
    }
  },
   
   methods: {
       submit() {
         if(this.task.length === 0) /*if no word, then return nothing*/
         return;
         
         this.tasks.push ({
               name:this.task,
               status: 'to-do'
         })
       },
       // eslint-disable-next-line no-unused-vars
       ChangeStatus(_index){
        
          let newIndex = this.available.indexOf(this.tasks[_index].status);
          if(++newIndex > 1)
           newIndex = 0;
          /*on-click status change */
           this.tasks[_index].status = this.available[newIndex];
       } 
   }
};
</script>
<style scoped>
/*minimum css applied*/
.form-control
{
  display: flex;
  justify-content: center;
  position: absolute;
  left: 30%;
  padding-top: 12px;
  padding-bottom: 12px;
  margin-top: 25px;
  width: 32vw;
  border-radius: 100px;
}
.btn {
  position: absolute;
  left: 62.5%;
  margin-top: 30px;
  border-radius: 100px;
}
.table {
  position: absolute;
  left: 25%;
  width: 50vw;
  margin-top: 85px;
}
.pointer {
  cursor: pointer;
}
</style>
