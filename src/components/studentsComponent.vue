<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Major</th>
          <th scope="col">Grade</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="student in students" :key="student.id">
          <th scope="row">{{ student.id }}</th>
          <td>{{ student.name }}</td>
          <td>{{ student.major }}</td>
          <td>{{ student.grade }}</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <th colspan="3" class="text-center"># of students = {{ students.length }}</th>
        </tr>
      </tfoot>
    </table>

    <div class="modal" :class="{ 'd-block': showModal }">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Add Student</h5>
            <button type="button" class="btn-close" @click="closeModal"></button>
          </div>
          <div class="modal-body">

            <form @submit.prevent="addStudent">
              <div class="mb-3">
                <label for="name" class="form-label">Name</label>
                <input type="text" id="name" v-model="newStudent.name" class="form-control" required>
              </div>
              <div class="mb-3">
                <label for="major" class="form-label">Major</label>
                <input type="text" id="major" v-model="newStudent.major" class="form-control" required>
              </div>
              <div class="mb-3">
                <label for="grade" class="form-label">Grade</label>
                <input type="number" id="grade" v-model="newStudent.grade" class="form-control" required>
              </div>
              <button type="submit" class="btn btn-dark">Add</button>
            </form>
          </div>
        </div>
      </div>
    </div>

    <!-- Button to open modal dialog -->
    <button class="btn btn-dark" @click="openModal">Add Student</button>
  </div>
</template>

<script>
import students from '../students.js';

export default {
  data() {
    return {
      students: students,
      showModal: false,
      newStudent: {
        name: '',
        major: '',
        grade: ''
      }
    };
  },
  methods: {
    openModal() {
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
      this.resetForm();
    },
    addStudent() {
      const newId = this.students.length + 1;
      const student = {
        id: newId,
        name: this.newStudent.name,
        major: this.newStudent.major,
        grade: this.newStudent.grade
      };
      this.students.push(student);
      this.closeModal();
    },
    resetForm() {
      this.newStudent.name = '';
      this.newStudent.major = '';
      this.newStudent.grade = '';
    }
  }
};
</script>

<style>
/* Add your existing styles here */
</style>