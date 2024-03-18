<template>
    <v-main>
    <v-app-bar app color="#080808">
      <v-app-bar-title class="title-color">Hi</v-app-bar-title>
      <v-spacer></v-spacer>
      
      <v-btn icon @click="home()">
        <v-icon size="32" class="icon-color">mdi-home</v-icon>
      </v-btn>
    </v-app-bar>
    <div class="task-form">
      <h2>Create New Task</h2>
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="taskName">Task Name</label>
          <input type="text" id="taskName" v-model="taskName" required />
        </div>
        <div class="form-group">
          <label for="description">Description</label>
          <textarea id="description" v-model="description" required></textarea>
        </div>
        <div class="form-group">
          <label for="plannedDuration">Planned Duration (hours)</label>
          <input type="number" id="plannedDuration" v-model.number="plannedDuration" required />
        </div>
        <div class="form-group">
          <label for="plannedTimeRange">Planned Time Range</label>
          <input type="text" id="plannedTimeRange" v-model="plannedTimeRange" />
        </div>
        <div class="form-group">
          <label for="priority">Priority</label>
          <select id="priority" v-model="priority" required>
            <option value="">Select Priority</option>
            <option value="low">Low</option>
            <option value="medium">Medium</option>
            <option value="high">High</option>
          </select>
        </div>
        <div class="form-group">
          <label for="dueDate">Due Date</label>
          <input type="date" id="dueDate" v-model="dueDate" />
        </div>
        <button class="create-btn" type="submit">Create Task</button>
      </form>
        
    </div>
    <footer class="footer">
      <p>&copy; 2024 Task Management System</p>
    </footer>
    </v-main>
  </template>
  
  <script>
  export default {
    data() {
      return {
        taskName: '',
        description: '',
        plannedDuration: '',
        plannedTimeRange: '',
        priority: '',
        dueDate: ''
      };
    },
    methods: {
        async home(){
           this.$router.push('/')
       },
      submitForm() {
        if (this.validateForm()) {
          // Logic to submit form data
          console.log('Form submitted successfully!');
        } else {
          console.log('Form validation failed!');
        }
      },
      validateForm() {
        if (!this.taskName || !this.description || !this.plannedDuration || !this.priority) {
          return false;
        }
        return true;
      }
    }
  };
  </script>
  
  <style scoped>
  .task-form {
    max-width: 400px;
    margin: 0 auto;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
  }
  
  input[type="text"],
  input[type="number"],
  select,
  textarea {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  .create-btn {
  padding: 10px 20px;
  font-size: 18px;
  background-color: #817d7d; /* Change the color of the button to white */
  color: #080808; /* Change the text color to blue */
  border: none;
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s; /* Add transition for smooth hover effect */
  margin: 10px; /* Add some margin between the buttons */
}
  .create-btn:hover {
  background-color: #080808;
  color: #fff;
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
  