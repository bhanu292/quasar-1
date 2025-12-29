<template>
  <q-page class="q-pa-md">

    <!--Name-->
    <h1>My Name :{{ name }}</h1>

    <!-- Toggle Button-->
    <q-btn 
           label="Toggle Message"
           color="secondary"
           class="q-mb-md"
           @click="toggleMessage"/>

    <!--Toggle Text-->       
    <p v-if="showMessage">
      Welcome to Quasar Module
    </p>

    <hr/>

    <!--Student Section-->
    <h5>Student List</h5>

    <!--Input-->
    <q-input
      v-model="newStudent"
      label="Enter Student Name"
      filled
      class="q-mb-md"/>

      <!--Buttons-->
      <q-btn
       label="Add Student"
       :color="addColor"
       class="q-mr-sm"
       @click="addStudent"/>

       <q-btn
        label="Remove Last Student"
        color="negative"
        @click="removeStudent"/>

    <!--List-->
    
    <ul class="q-mt-md">
      <li v-for="(student, index) in students" :key="index">
        {{ student }}
      </li>
    </ul>

    <!--Computed Property-->
    <p>Total Students: {{ totalStudents }}</p>

  </q-page>
  </template>

  <script>

 export default {
  name: 'IndexPage',

  data () {
    return {
      name: 'Bharat',
      showMessage: false,

      newStudent: '',
      students: ['Ram','Shyam','Amit','Rohit'],
      addColor: 'primary'
    }
  },

  computed: {
    totalStudents () {
      return this.students.length
    }
  },

  methods: {
    toggleMessage () {
      this.showMessage = !this.showMessage
    },
    addStudent () {
      if (this.newStudent !== '') {
        this.students.push(this.newStudent)
        this.newStudent=''
        this.addColor = 'positive'
      }
    },

    removeStudent () {
      if(this.students.length > 0) {
        this.students.pop()
        this.addColor = 'warning'
      }
    }
  }
 }
  </script>
