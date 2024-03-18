<template>
    <v-main>
      <v-app-bar app color="#080808">
        <v-app-bar-title class="title-color">View Reports</v-app-bar-title>
        <v-spacer></v-spacer>
        <v-btn icon @click="goToHome()">
          <v-icon size="32" class="icon-color">mdi-home</v-icon>
        </v-btn>
      </v-app-bar>
  
      <div class="report-list">
        <h2>Recent Reports</h2>
        <v-list>
          <v-list-item v-for="report in reports" :key="report.id">
            <v-list-item-content>
              <v-list-item-title>{{ report.title }}</v-list-item-title>
              <v-list-item-subtitle>{{ report.date }}</v-list-item-subtitle>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn @click="viewReport(report)" outlined color="primary">View</v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-list>
      </div>
  
      <v-footer app class="footer">
        <span class="white--text">&copy; 2024 Task Management System</span>
      </v-footer>
    </v-main>
  </template>
  
  <script>
  export default {
    data() {
      return {
        reports: [
          { id: 1, title: 'Report 1', date: '2024-03-20' },
          { id: 2, title: 'Report 2', date: '2024-03-21' },
          { id: 3, title: 'Report 3', date: '2024-03-22' },
          { id: 4, title: 'Report 4', date: '2024-03-23' }
        ]
      };
    },
    methods: {
      goToHome() {
        this.$router.push('/');
      },
      viewReport(report) {
        // Logic to view report details
        console.log('Viewing report:', report);
      }
    }
  };
  </script>
  
  <style scoped>
  .report-list {
    max-width: 800px;
    margin: 0 auto;
  }
  
  .title-color {
    color: white !important;
  }
  
  .icon-color {
    color: white !important;
  }
  
  .footer {
    background-color: #080808;
    color: white;
    text-align: center;
  }
  </style>
  