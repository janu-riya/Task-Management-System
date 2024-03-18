<template>
    <v-main>
    <v-app-bar app color="#080808">
      <v-app-bar-title class="title-color">Hi,{{ employer.name }}</v-app-bar-title>
      <v-spacer></v-spacer>
      
      <v-btn icon @click="home()">
        <v-icon size="32" class="icon-color">mdi-home</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container>
      <!-- Employer Profile -->
      <v-card>
        <v-card-title>Profile</v-card-title>
        <v-card-text>
          <p>Name: {{ employer.name }}</p>
          <p>Email: {{ employer.email }}</p>
          
        </v-card-text>
      </v-card>
  
      <!-- Actions -->
      <v-card>
        <v-card-title>Actions</v-card-title>
        <v-card-text>
          <v-btn color="black" rounded to="/taskcreate" @click="createTask">Create Task</v-btn>
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
        employer: { // Employer data
          name: 'John Doe',
          email: 'john@example.com',
          
        },
        notification: '' // Notification message for status update
      };
    },
    methods: {async home(){
           this.$router.push('/')
       },
      createTask() {
        // Logic to navigate to task creation page
        console.log('Creating task...');
      },
      viewReports() {
        // Logic to navigate to reports page
        console.log('Viewing reports...');
      }
    },
    mounted() {
      // Simulating notification from employee status update
      this.notification = 'Employee X has updated the project status.';
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
  