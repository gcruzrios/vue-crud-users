<template>
   <div class="row justify-content-center">
        <div class="col-md-6">
            <h3 class="text-center">Create User</h3>
            <form @submit.prevent="handleSubmitForm">
                <div class="form-group">
                    <label>Name</label>
                    <input type="text" class="form-control" v-model="user.name" required>
                </div>

                <div class="form-group">
                    <label>Email</label>
                    <input type="email" class="form-control" v-model="user.email" required>
                </div>

                <div class="form-group">
                    <label>Job Title</label>
                    <input type="text" class="form-control" v-model="user.job_title" required>
                </div>

                <div class="form-group">
                    <button class="btn btn-danger btn-block">Create</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import axios from "axios";

    export default {
        data() {
            return {
                user: {
                   name: '',
                   email: '',
                   job_title: ''
                }
            }
        },
        methods: {
            handleSubmitForm() {
                let apiURL = 'http://localhost:4000/api/create-student';
                
                //console.log(user.value);

                axios.post(apiURL, this.user).then(() => {
                   this.$router.push('/')
                   this.user = {
                       name: '',
                       email: '',
                       job_title: ''
                    }
                    }).catch(error => {
                      console.log(error)
                });
            }
        }
    }
</script>

<style>

</style>