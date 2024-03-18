<template>
  <v-main>
    <v-app-bar app color="#080808">
      <v-app-bar-title class="title-color">Features</v-app-bar-title>
      <v-spacer></v-spacer>
      
      <v-btn icon @click="home()">
        <v-icon size="32" class="icon-color">mdi-home</v-icon>
      </v-btn>
    </v-app-bar>
    <footer class="footer">
      <p>&copy; 2024 Task Management System</p>
    </footer>
  </v-main>
</template>
<script>
export default {
    name: 'sampleLayout'
  }
</script>
  
<style scoped>
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