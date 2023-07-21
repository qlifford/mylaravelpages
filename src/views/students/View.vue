<template>
    <div class="card">
        <div class="card-header">
                <h4>Students</h4>
                <RouterLink to="/students/create" class="btn btn-primary float-end mb-2">Add Student</RouterLink>
            <div class="card-body">
                <table class="table table-bordered">
                    <thead>
                        <tr class="fw-bold">
                            <th>#</th>
                            <th>Name</th>
                            <th>Course</th>
                            <th>Email</th>
                            <th>Phone</th>
                            <th>Created_at</th>
                            <th colspan="2" class="text-center">Action</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(student, index) in this.students" :key="index">
                            <td>{{ student.id }}</td>
                            <td>{{ student.name }}</td>
                            <td>{{ student.course }}</td>
                            <td>{{ student.email }}</td>
                            <td>{{ student.phone }}</td>
                            <td>{{ student.created_at }}</td>
                            <td class="m-4">
                                <RouterLink to="/students/create" class="btn btn-success btn-sm">Edit</RouterLink>
                                <button type="button" class="btn btn-danger float-end btn-sm btn-sm">Delete</button>
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
        name: 'students',
        data() {
            return {
                students: []
            }
        },
        mounted() {
            this.getStudents();
        },
        methods: {
            getStudents() {
                axios.get('http://127.0.0.1:8000/api/students').then(res => {
                    this.students = res.data.student
                    console.log(this.students)
                });
            }
            
        },
    }
    </script>