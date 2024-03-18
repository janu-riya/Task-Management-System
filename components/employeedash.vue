<template>
    <v-main>
    <v-app-bar app color="#080808">
      <v-app-bar-title class="title-color">Hi,{{ employee.name }}</v-app-bar-title>
      <v-spacer></v-spacer>
      
      <v-btn icon @click="home()">
        <v-icon size="32" class="icon-color">mdi-home</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container>
      <!-- Employee Profile -->
      <v-card>
        <v-card-title>Employee Profile</v-card-title>
        <v-card-text>
          <p>Name: {{ employee.name }}</p>
          <p>Email: {{ employee.email }}</p>
         
        </v-card-text>
      </v-card>
  
      <!-- Actions -->
      <v-card>
        <v-card-title>Actions</v-card-title>
        <v-card-text>
          <v-btn color="black" rounded to="/tasklist" @click="viewTasks">View Tasks</v-btn>
          <v-btn color="black" rounded to="/updatestatus" @click="updateStatus">Update Status</v-btn>
          <v-btn color="black" rounded to="/Viewreports" @click="viewReports">View Reports</v-btn>
        </v-card-text>
      </v-card>
  
      <!-- Notification -->
      <v-card v-if="notification">
        <v-card-title>Notification</v-card-title>
        <v-card-text>
          <p>{{ notification }}</p>
        </v-card-text>
      </v-card>
    </v-container>
    <footer class="footer">
      <p>&copy; 2024 Task Management System</p>
    </footer>
    </v-main>
  </template>
  
  <script>
  export default {
    data() {
      return {
        employee: { // Employee data
          name: 'Robin',
          email: 'robin@example.com',
          
        },
        notification: '' // Notification message for task updates
      };
    },
    methods: {async home(){
           this.$router.push('/')
    },
      viewTasks() {
        // Logic to navigate to task list page
        console.log('Viewing tasks...');
      },
      updateStatus() {
        // Logic to update task status
        console.log('Updating task status...');
      },
      viewReports() {
        // Logic to navigate to reports page
        console.log('Viewing reports...');
      },
      createTaskForEmployee() {
        // Simulating task creation for the employee
        this.notification = 'A new task has been created for you.';
      }
    },
    mounted() {
      // Call the method to simulate task creation for the employee
      this.createTaskForEmployee();
    }
  };
  </script>
  
  <style scoped>
  .v-container {
    margin-top: 20px;
  }
  .footer {
  background-color: #080808;
  color: #fff;
  width: 100%;
  text-align: center;
  padding: 20px 0;
  position: fixed; /* Set the footer to a fixed position */
  bottom: 0; /* Position the footer at the bottom of the viewport */
}

.footer p {
  margin: 0;
}

.icon-color {
  color: white !important;
}
.title-color {
    color: white !important;
  }
  </style>
  