<template>
    <v-main>
      <v-app-bar app color="#080808">
        <v-app-bar-title class="title-color">Hi</v-app-bar-title>
        <v-spacer></v-spacer>
        
        <v-btn icon @click="home()">
          <v-icon size="32" class="icon-color">mdi-home</v-icon>
        </v-btn>
      </v-app-bar>
  
      
      <v-container >
        <p>Here is listed all the features that I made in this application for your reference.Because without backend integration it sounds not looks good for visit all the page.</p>
        &ensp;  &ensp;  &ensp;  &ensp;  &ensp;
        <v-row>
          <v-col cols="12" md="4">
            <div class="feature" @click="navigateToListing">
              <h2>Task Listing</h2>
              <p>View all tasks in one place</p>
            </div>
          </v-col>
          <v-col cols="12" md="4">
            <div class="feature" @click="navigateToCreation">
              <h2>Task Creation</h2>
              <p>Create new tasks and assign them</p>
            </div>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" md="4">
            <div class="feature" @click="navigateToEmployeeDashboard">
              <h2>Employee Dashboard</h2>
              <p>View the Dashboard of employee here</p>
            </div>
          </v-col>
          <v-col cols="12" md="4">
            <div class="feature" @click="navigateToEmployerDashboard">
              <h2>Employer Dashboard</h2>
              <p>View the Dashboard of employee here</p>
            </div>
          </v-col>
        </v-row>
      </v-container>
      
      
      <footer class="footer">
        <v-container fluid>
          <v-row>
            <v-col cols="12">
              <p>&copy; 2024 Task Management System</p>
            </v-col>
          </v-row>
        </v-container>
      </footer>
    </v-main>
  </template>
  
  <script>
  export default {
    methods: {
      home() {
        // Handle home button click
        this.$router.push('/');
      },
      navigateToListing() {
        this.$router.push('/tasklist');
      },
      navigateToCreation() {
        this.$router.push('/taskcreate');
      },
      navigateToEmployeeDashboard() {
        this.$router.push('/employeedashboard');
      },
      navigateToEmployerDashboard() {
        this.$router.push('/employerdashboard');
      }
    }
  }
  </script>
  
  <style scoped>
  .app-container {
    max-width: 1200px;
    margin: 0 auto;
  }
  
  .features {
    display: flex;
    justify-content: space-around;
    margin-top: 50px;
  }
  
  .feature {
    text-align: center;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .footer {
    background-color: #080808;
    color: #fff;
    text-align: center;
    padding: 20px 0;
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
  