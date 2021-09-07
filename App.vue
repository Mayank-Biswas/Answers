<template>
  <div id="app">
    <Table v-if="tableData" :theData="tableData" :config="config" />
  </div>
</template>

<script>
import Table from './components/Table'

export default {
  components: {
        Table
 },
 data: () => ({
     tableData: undefined,
     config: [
         {
           key: 'id',
           title: 'ID',
         },
         {
           key: 'email-add',
           title: 'Email address'
         },
         {
           key: 'first_name',
           title: 'First-Name'
         },
         {
           key: 'last_name',
           title: 'Last-Name'
         },
         {
           key: 'photo',
           title: 'Avatar'
         }
     ]
   }),
   mounted() { 
    this.$axios.get('https://reqres.in/api/users?page=2')
    .then(({data}) => {
             this.tableData = data
    })
  }
}
</script>

<style>
</style>
