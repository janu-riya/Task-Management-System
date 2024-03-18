<template>
    <v-main>
    <v-app-bar app color="#080808">
      <v-app-bar-title class="title-color">Update Status</v-app-bar-title>
      <v-spacer></v-spacer>
      
    </v-app-bar>
    <v-container>
      <v-card>
        <v-card-title>Update Task Status</v-card-title>
        <v-card-text>
          <v-form @submit.prevent="updateTaskStatus">
            <v-select v-model="selectedTask" :items="tasks" label="Select Task" outlined></v-select>
            <v-select v-model="selectedStatus" :items="statusOptions" label="Select Status" outlined></v-select>
            <v-btn type="submit" color="black">Update Status</v-btn>
          </v-form>
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
        tasks: [
          { id: 1, name: 'Task 1', status: 'Pending' },
          { id: 2, name: 'Task 2', status: 'Completed' },
          // Add more tasks as needed
        ],
        statusOptions: ['Pending', 'In Progress', 'Completed'],
        selectedTask: null,
        selectedStatus: ''
      };
    },
    methods: {
      async home(){
           this.$router.push('/')
       },
      updateTaskStatus() {
        if (this.selectedTask && this.selectedStatus) {
          // Update task status logic goes here
          console.log(`Task "${this.selectedTask.name}" status updated to "${this.selectedStatus}".`);
        } else {
          console.log('Please select a task and status.');
        }
      }
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

.title-color {
    color: white !important;
  }
  </style>
  