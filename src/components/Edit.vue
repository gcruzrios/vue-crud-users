<template>
  <div class="row justify-content-center">
        <div class="col-md-6">
            <h3 class="text-center">Update User</h3>
            <form @submit.prevent="handleUpdateForm">
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
                    <button class="btn btn-danger btn-block">Update</button>
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
            user: { }
        }
    },
    created() {
        let apiURL = `https://www.testjsonapi.com/user/${this.$route.params.id}`;

        axios.get(apiURL).then((res) => {
            this.user = res.data;
            console.log(this.user);
        })
    },
    methods: {
        handleUpdateForm() {
            let apiURL = `http://localhost:4000/api/update-student/${this.$route.params.id}`;

            axios.post(apiURL, this.user).then((res) => {
                console.log(res)
                this.$router.push('/')
            }).catch(error => {
                console.log(error)
            });
        }
    }
}
</script>

<style>

</style>