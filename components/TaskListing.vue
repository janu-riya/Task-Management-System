<template>
    <v-app>
        <v-app-bar app color="#080808">
      <v-toolbar-title class="title-color">Task Management System</v-toolbar-title>
    </v-app-bar>
    <v-container>
        <v-card>
    <div class="task-list">
      <v-card-title color="#080808">Task List</v-card-title>
      <v-card-text>
      <v-row>
              <v-col cols="6">
                <v-select v-model="selectedStatus" :items="statusOptions" label="Filter by Status" outlined></v-select>
              </v-col>
              <v-col cols="6">
                <v-select v-model="selectedPriority" :items="priorityOptions" label="Filter by Priority" outlined></v-select>
              </v-col>
            </v-row>
        </v-card-text>

        <v-list>
            <v-list-item v-for="task in filteredTasks" :key="task.id">
              <v-list-item-content>
                <v-list-item-title>{{ task.name }}</v-list-item-title>
                <v-list-item-subtitle>{{ task.description }}</v-list-item-subtitle>
                <v-list-item-subtitle>Due Date: {{ task.dueDate }}</v-list-item-subtitle>
                <v-list-item-subtitle>Status: {{ task.status }}</v-list-item-subtitle>
                <v-list-item-subtitle>Priority: {{ task.priority }}</v-list-item-subtitle>
              </v-list-item-content>
              <v-list-item-action class="actions">
          <button  @click="showTaskDetails(task)">View</button>
          <button  @click="showEditForm(task)">Edit</button>
          <button  @click="deleteTask(task)">Delete</button>
              </v-list-item-action>
            </v-list-item>
          </v-list>
     
      
      <!-- Task Details Modal -->
      <div v-if="selectedTask" class="modal">
        <div class="modal-content">
          <span class="close" @click="selectedTask = null">&times;</span>
          <h2>{{ selectedTask.name }}</h2>
          <p><strong>Description:</strong> {{ selectedTask.description }}</p>
          <p><strong>Due Date:</strong> {{ selectedTask.dueDate }}</p>
          <p><strong>Priority:</strong> {{ selectedTask.priority }}</p>
          <p><strong>Status:</strong> {{ selectedTask.status }}</p>
        </div>
      </div>
      
      <!-- Edit Task Form -->
      <div v-if="editMode" class="modal">
        <div class="modal-content">
          <span class="close" @click="editMode = false">&times;</span>
          <h2>Edit Task</h2>
          <!-- Include your edit form here -->
          <!-- For simplicity, you can just display input fields with existing task data -->
          <input type="text" v-model="editedTask.name" />
          <!-- Include other fields as needed -->
          <button @click="updateTask">Save</button>
        </div>
      </div>
    </div>
</v-card>
</v-container>
<footer class="footer">
      <p>&copy; 2024 Task Management System</p>
    </footer>
    </v-app>
  </template>
  
  <script>
  export default {
    async mounted(){
      this.$vuetify.theme.dark=false;
  },
    data() {
      return {
        selectedStatus: '',
        selectedPriority: '',
        statusOptions: ['All', 'Pending', 'Completed'],
        priorityOptions: ['All', 'Low', 'Medium', 'High'],
        tasks: [
          { id: 1, name: 'Task 1', description: 'Description of Task 1', dueDate: '2024-03-17', priority: 'High', status: 'Pending' },
          { id: 2, name: 'Task 2', description: 'Description of Task 2', dueDate: '2024-03-18', priority: 'Medium', status: 'Completed' }
        ],
        selectedTask: null,
        editMode: false,
        editedTask: {}
      };
    },
    computed: {
    filteredTasks() {
      let filteredTasks = this.tasks;
      if (this.selectedStatus && this.selectedStatus !== 'All') {
        filteredTasks = filteredTasks.filter(task => task.status === this.selectedStatus);
      }
      if (this.selectedPriority && this.selectedPriority !== 'All') {
        filteredTasks = filteredTasks.filter(task => task.priority === this.selectedPriority);
      }
      return filteredTasks;
    }
  },
    methods: {
      showTaskDetails(task) {
        this.selectedTask = task;
      },
      showEditForm(task) {
        this.editedTask = { ...task }; // Copy task object for editing
        this.editMode = true;
      },
      updateTask() {
        // Update task logic goes here
        console.log('Task updated:', this.editedTask);
        this.editMode = false;
      },
      deleteTask(task) {
        // Find index of task to delete
        const index = this.tasks.findIndex(t => t.id === task.id);
        if (index !== -1) {
          // Remove task from tasks array
          this.tasks.splice(index, 1);
          console.log('Task deleted:', task);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .task-list {
    max-width: 800px;
    margin: 0 auto;
  }
  
  .task {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    margin-bottom: 10px;
  }
  
  .actions {
    margin-top: 10px;
  }

  
  button {
    margin-right: 5px;
    cursor: pointer;
  }
  
  /* Modal Styles */
  .modal {
    display: block;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: #fff;
  }
  
  .modal-content {
    background-color: #fff;
    margin: 20% auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 50%;
  }
  
  .close {
    color: #aaa;
    float: right;
    font-size: 28px;
    font-weight: bold;
    cursor: pointer;
  }
  
  .close:hover,
  .close:focus {
    color: black;
    text-decoration: none;
    cursor: pointer;
  }
  .title-color {
  color: #f9f5f5 !important;
}

.footer {
  background-color: #090909;
  color: white;
  text-align: center;
}
  </style>