<template>
  <div class="math-tuition">
    <h2>Math Tuition Details</h2>
    <p>Course: Algebra Basics</p>
    <p>Teacher: Mr. Saksham Nagpal</p>
    <p>Class Schedule: Mondays and Wednesdays, 5:00 PM - 7:00 PM</p>

    <h2>Course Information</h2>
    <p v-html="courseDescription"></p>

    <h2>Student List</h2>
    <ul>
      <li v-for="student in students" :key="student.id">{{ student.name }}</li>
    </ul>

    <h2>Enroll in the Course</h2>
    <label for="studentName">Your Name:</label>
    <input type="text" v-model="studentName" />

    <button @click="enroll">Enroll Now</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const courseDescription = '<p>Learn the basics of algebra in this comprehensive course. Improve your math skills and ace your exams!</p>';
const studentName = ref('');
const students = ref([
  { id: 1, name: 'Krish' },
  { id: 2, name: 'Dhruv' },
  { id: 3, name: 'Shivansh' },
]);

const enroll = () => {
  if (studentName.value) {
    students.value.push({ id: students.value.length + 1, name: studentName.value });
    studentName.value = '';
  }
};
</script>

<style>
.math-tuition {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: beige;
  border: 1px solid blue;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h2 {
  color: skyblue;
  margin-top: 10px;
}

p {
  margin: 5px 0;
}

button {
  background-color: red;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
}

button:hover {
  background-color: blue;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 5px 0;
}

label {
  display: block;
  margin-top: 10px;
  font-weight: bold;
}

input[type="text"] {
  width: 100%;
  padding: 5px;
  margin: 5px 0;
  border: 1px solid silver;
  border-radius: 3px;
}
</style>
