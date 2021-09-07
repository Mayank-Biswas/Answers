<template>
<div class="awesome-table">
    <table>
      <thead>
        <tr>
          <th v-for="(obj,ind) in config" :key="ind">
                {{obj.title}}
          </th>
        </tr>
      </thead>
      
      <tbody>
        <tr v-for="(row,index) in theData" :key="index">
          
          <td v-for="(obj,ind) in config" :key="ind">
               {{ row[obj.key] }}
          
          <span v-if="obj.type === 'text'">{{ row[obj.key] }}</span>
          
          <figure v-if="obj.type === 'image'">
              <img :src="row[obj.key]">
          </figure>
          </td>
        </tr>
      </tbody>
    </table>
</div>
</template>

<script>
export default {
     props: ['theData','config']
}
</script>

<!--CSS-->
<style scope>
 .awesome-table
 {
   border: 1px solid black;
   border-radius: 5px;
   color: rgb(61, 60, 60);
   overflow: auto;
 }
 .figure
 {
   margin-block-start: 0;
   margin-block-end: 0;
   margin-inline-start: 0;
   margin-inline-end: 0;
 }
 .img
 {
   border-radius: 50%;
   overflow: hidden;
 }
 .table 
{
  width: 100%;
}
.th
{
  position: fixed;
  top: 2;
  padding: 10px 5px;
  text-align: center;
}
.td
{
 padding: 10px 5px;
 text-align: center;
}
</style>
