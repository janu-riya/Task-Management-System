<template>
  <div class="landing-page">
    <div class="landing-content">
      <h1>Task Management System</h1>
      <h2>Manage your tasks accordingly</h2>
      <a href="/getstarted"><button class="get-started-btn" @click="start">Get Started</button></a>
      <a href="/features"><button class="features-btn" @click="showFeatures">Features</button></a>
    </div>
    <footer class="landing-footer">
      <p>&copy; 2024 Task Management System</p>
    </footer>
  </div>
</template>

<script>
export default {
  methods: {
    start() {
      // Implement navigation logic to the main dashboard or login page
    },
    showFeatures() {
      // Implement logic to show features or navigate to features page
    }
  }
};
</script>

<style scoped>
.landing-page {
  background-image: url('https://c0.wallpaperflare.com/preview/134/372/59/abstract-background-copyspace-brainstorm.jpg'); /* Add your task image here */
  background-size: cover;
  background-position: center;
  height: 100vh; /* Set the height to fill the viewport */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative; /* Ensure the footer is positioned relative to the landing-page */
}

.landing-content {
  text-align: center;
  color: #fff;
}

.landing-content h1 {
  font-size: 36px;
  margin-bottom: 20px;
}

.landing-content h2 {
  font-size: 24px;
  margin-bottom: 30px;
}

.get-started-btn,
.features-btn {
  padding: 10px 20px;
  font-size: 18px;
  background-color: #fff; /* Change the color of the button to white */
  color: #080808; /* Change the text color to blue */
  border: none;
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s; /* Add transition for smooth hover effect */
  margin: 10px; /* Add some margin between the buttons */
}

.get-started-btn:hover,
.features-btn:hover {
  background-color: #080808;
  color: #fff;
}

.landing-footer {
  background-color: #080808;
  color: #fff;
  width: 100%;
  text-align: center;
  padding: 20px 0;
  position: fixed; /* Set the footer to a fixed position */
  bottom: 0; /* Position the footer at the bottom of the viewport */
}

.landing-footer p {
  margin: 0;
}
</style>
