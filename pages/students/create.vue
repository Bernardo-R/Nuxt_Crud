<template>
    <div class="container mt-5">
      <div class="card">
        <div class="card-header d-flex justify-content-between p-3">
          <h4>Add Student</h4>
          <NuxtLink to="/" class="btn btn-danger float-end">Back</NuxtLink>
        </div>
        <div class="card-body">
          <div v-if="isLoading">
            <Loading :title="isLoadingTitle" />
          </div>
          <form @submit.prevent="saveStudent">
            <div class="mb-3">
              <label for="name">Name</label>
              <input
                type="text"
                id="name"
                v-model="student.name"
                class="form-control"
                required
              />
            </div>
            <div class="mb-3">
              <label for="course">Course</label>
              <input
                type="text"
                id="course"
                v-model="student.course"
                class="form-control"
                required
              />
            </div>
            <div class="mb-3">
              <label for="phone">Phone</label>
              <input
                type="tel"
                id="phone"
                v-model="student.phone"
                class="form-control"
                pattern="[0-9]{10}"
                title="Please enter a valid 10-digit phone number"
                required
              />
            </div>
            <div class="mb-3">
              <label for="email">Email</label>
              <input
                type="email"
                id="email"
                v-model="student.email"
                class="form-control"
                required
              />
            </div>
            <div class="mb-3">
              <button type="submit" class="btn btn-primary">Save</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </template>

<script>
import axios from 'axios'

//********************************************************************************** */
// Create a new Date object
const currentDate = new Date();

// Get the individual components (month, day, year)
const month = String(currentDate.getMonth() + 1).padStart(2, '0'); // Adding 1 because months are zero-based
const day = String(currentDate.getDate()).padStart(2, '0');
const year = currentDate.getFullYear();

// Construct the formatted date string
const formattedDate = `${month}/${day}/${year}`;

//*********************************************************************************** */

export default {
    name: 'student-create',
    data() {
        return {
            student: {
                name: '',
                course: '',
                phone: '',
                email: '',
                createdAt: ''
            },
            isLoading: false,
            isLoadingTitle: 'Loading'
        }
    },
    methods: {
        saveStudent() {
            this.isLoading = true;
            this.isLoadingTitle ='Saving'

            this.student.createdAt = formattedDate;
            

            axios.post('https://643d8ccb6c30feced81531da.mockapi.io/cars', this.student).then(res => {
    
                this.student.name = ''
                this.student.course = ''
                this.student.phone = ''
                this.student.email = ''
        
                this.isLoading = false;
                this.isLoadingTitle ='Loading'
            })
            .catch((error) => {
                if (error.response && error.response.status === 422){
                    //console.log(error.response);
                    const errors = error.response['errors'];
                    Object.keys(this.student).forEach(keyError => {
                        if(errors[keyError]){
                            this.$refs[keyError].applyFocus();
                            }
                            });
                            }else{
                                alert("An Error Occured");
                                }
                    
            })
        }
    }
    }

</script>

<style scoped>

</style>