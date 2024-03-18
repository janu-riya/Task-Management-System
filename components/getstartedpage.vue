<template>
    
    <v-main>
        <v-app-bar app color="#080808">
      <v-app-bar-title class="title-color">Get Started</v-app-bar-title>
      <v-spacer></v-spacer>
      
      <v-btn icon @click="home()">
        <v-icon size="32" class="icon-color">mdi-home</v-icon>
      </v-btn>
    </v-app-bar>
      <v-container  class="image">
       <v-row>
        <v-col cols="14" md="6">
        <div class="blue-bubble">
          <img
            data-aos="zoom-in"
            class="guide2Image"
            data-aos-duration="800"
            data-aos-delay="100"
            src="https://cdni.iconscout.com/illustration/premium/thumb/business-idea-5364786-4491812.png"
            alt="Guide Image"
            :style="{ width: '100%', height: 'auto' }"
          />
        </div>
      </v-col>
      
      <v-col cols="14" md="6">
        <v-row justify="center" align="center">
            
        
            <v-card class="get-started-card" color="black" dark>
              <v-card-title class="text-center">Employee</v-card-title>
              <v-card-text class="text-center">
                Organize your tasks, collaborate with colleagues, know updates.
              </v-card-text>
              <v-card-actions class="justify-center">
                <v-btn color="white" rounded to="/employeesignin" text @click="employeeLogin">Login</v-btn>
                <v-btn color="white" rounded to="/employeesignup" text @click="employeeSignup">Signup</v-btn>
              </v-card-actions>
            </v-card>
        </v-row>
        &ensp;
        <v-row justify="center" align="center">
            <v-card class="get-started-card" color="black" dark>
              <v-card-title class="text-center">Employer</v-card-title>
              <v-card-text class="text-center">
                Assign tasks, track progress, and manage your team efficiently.
              </v-card-text>
              <v-card-actions class="justify-center">
                <v-btn color="white" rounded to="/employersignin" text @click="employerLogin">Login</v-btn>
                <v-btn color="white" rounded to="/employersignup" text @click="employerSignup">Signup</v-btn>
              </v-card-actions>
            </v-card>
        
    
        </v-row>
      </v-col>
       </v-row>
      </v-container>
      <footer class="footer">
      <p>&copy; 2024 Task Management System</p>
    </footer>
    </v-main>
  </template>
  
  <script>
  export default {
    name: 'GetStartedPage',
    
    methods: {

      async home(){
        this.$router.push('/')
      },  
      async employeeLogin() {
        this.$router.push("/employeesignin");
      },
      async employeeSignup() {
        this.$router.push("/employeesignup");
      },
      async employerLogin() {
        this.$router.push("/employersignin");
      },
      },
      async employerSignup() {
        this.$router.push("/employersignup");
      
      }
    }
  
  </script>
  
  <style scoped>
  .title-color {
    color: white !important;
  }
  .get-started-card {
    width: 100%;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 40px;
  box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
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

.guide2Image {
  width: 100%;
  overflow: hidden;
}


@keyframes blueBubble {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(0);
  }
}

.blue-bubble {
  position: relative;
  display: inline-block;
  animation: blueBubble 2s infinite;
}
.image {
  margin-top: 5vh;
  margin-bottom: 5vh;
  text-align: center;
}

  </style>
  