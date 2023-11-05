<template>
    <div>
        <div class="card">
            <div class="card-header">
                <h4>Student List</h4>
                <NuxtLink to="/students/create" class="btn btn-primary float-end">Add Student</NuxtLink>
            </div>
        </div>
        <div class="card-body">

            <div v-if="isLoading">
                <Loading title="Loading..." />
            </div>
            <div v-else>
                <table class="table table-bordered table-striped">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Name</th>
                            <th>Course</th>
                            <th>Email</th>
                            <th>Phone Number</th>
                            <th>Created At</th>
                            <th>Action</th>
    
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(student, index) in students" :key="index">
                            <td>{{ student.id }}</td>
                            <td>{{ student.name }}</td>
                            <td>{{ student.course }}</td>
                            <td>{{ student.email }}</td>
                            <td>{{ student.phone }}</td>
                            <td>{{ student.createdAt }}</td>
                            <td><NuxtLink to="/" class="btn btn-success btn-sm mx-2">Edit</NuxtLink>
                                <button type="button" class="btn btn-danger btn-sm mx2">Delete</button>
                            </td>
                                               
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "student",

        data() {
            return {
                students: [],
                isLoading: true

            }
        },
 
        mounted() {
            this.getStudents();

        },
        methods:{
            getStudents() {
                axios.get('https://643d8ccb6c30feced81531da.mockapi.io/cars').then(res => {
                    this.students = res.data
                    this.isLoading = false
                })
            }
        }
    } 
    
</script>

<style lang="scss" scoped>

</style>