<template>
   <div class="container" style="margin-top:30px">

     <div class="row">
        <div class="col md-10"></div>
        <div class="col md-2"> <router-link :to="`/add`" class="text-light btn btn-primary float-right mb-3">New Record</router-link>
          
        </div>
     </div>
    <table class="table table-hover table-bordered" id="example">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Email</th>
          <th>Job Title</th>
          <th>Actions</th>
          
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <td>{{user.id}}</td>
          <td>{{user.name}}</td>
          <td>{{user.email}}</td>
          <td>{{user.job_title}}</td>
          <td>
            <span>
              <router-link :to="`/edit/${user.id}`">
                <i class="fas fa-edit mr-2"></i>
              </router-link> 
              <!-- <i class="fas fa-edit mr-2"></i> -->
              <i class="fas fa-trash-alt text-danger" @click="deleteUser(user.id)"></i> </span>  
          </td>
          
        </tr>
        
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

    export default {
        data() {
            return {
                users: []
            }
        },
        created() {
            let apiURL = 'https://www.testjsonapi.com/users/';
            axios.get(apiURL).then(res => {
                this.users = res.data;
            }).catch(error => {
                console.log(error)
            });
        },
        methods: {
            deleteUser(id){
                let apiURL = `http://localhost:4000/api/delete-student/${id}`;

                let indexOfArrayItem = this.users.findIndex(i => i.id === id);
                
                console.log("index =>",indexOfArrayItem);
                console.log(id);
                if (window.confirm("Do you really want to delete?")) {
                    // axios.delete(apiURL).then(() => {
                        //console.log('Index:',indexOfArrayItem);
                        this.users.splice(indexOfArrayItem, 1);
                    //}).catch(error => {
                    //    console.log(error)
                    //});
                }
            }
        }
    }

</script>

<style>

</style>