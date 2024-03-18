<template>
  <v-main>
    <v-app-bar app color="#080808">
      <v-app-bar-title class="title-color">Hi</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click="home()">
        <v-icon size="32" class="icon-color">mdi-home</v-icon>
      </v-btn>
    </v-app-bar>
  
    <v-container class="signup">
      <v-row align="center">
        <v-col cols="12" md="6">
          <div class="blue-bubble">
            <img
              data-aos="zoom-in"
              class="guide2Image"
              data-aos-duration="800"
              data-aos-delay="100"
              src="https://img.freepik.com/free-vector/access-control-system-abstract-concept-vector-illustration-security-system-authorize-entry-login-credentials-electronic-access-password-passphrase-pin-verification-abstract-metaphor_335657-5746.jpg?w=360"
              alt="Guide Image"
              :style="{ width: '100%', height: 'auto' }"
            />
          </div>
        </v-col>
        <v-col cols="14" md="6">
          <v-card elevation="12" class="signup-card">
            <v-form>
              <h1 class="text-center">Create your account</h1>
              <v-alert
                border="top"
                color="red lighten-1"
                dismissible
                v-if="fail"
              >
                Invalid Email ID or Password
              </v-alert>

              <div v-if="error" class="custom-info">
                <v-icon class="alert-icon">mdi-alert-circle</v-icon>
                <span class="alert-text">Signup Failed</span>
              </div>

              <v-container class="text-center"></v-container>

              <br />

              <v-row>
                <v-col cols="12">
                  <v-text-field
                    outlined
                    :textarea="true"
                    class="text-field-in-box"
                    v-model="signupdata.name"
                    prepend-icon="mdi-account"
                    :rules="[rules.required]"
                    label="Name"
                  ></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-text-field
                    outlined
                    :textarea="true"
                    class="text-field-in-box"
                    v-model="signupdata.email"
                    prepend-icon="mdi-email"
                    :rules="[rules.email, rules.required]"
                    label="Email"
                  ></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-text-field
                    outlined
                    :textarea="true"
                    class="text-field-in-box"
                    v-model="signupdata.password"
                    prepend-icon="mdi-lock"
                    type="password"
                    :rules="[rules.required]"
                    label="Password"
                  ></v-text-field>
                </v-col>
              </v-row>

              <br />

              <v-row justify="center">
                <v-col cols="12">
                  <v-btn
                    text
                    color="blue lighten-1"
                    @click="signup()"
                  >
                    Sign Up
                  </v-btn>
                </v-col>
              </v-row>
            </v-form>
          </v-card>
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
  name: 'EmployeeSignup',
  data() {
    return {
      signupdata: {
        name: '',
        email: '',
        password: ''
      },
      confirmPassword: '',
      error: false,
      fail: false,
      rules: {
        required: v => !!v || 'Required',
        email: v => /.+@.+\..+/.test(v) || 'Email must be valid',
        
      }
    };
  },
  methods: {
    async signup(){
            let url = ""
            await this.$axios.post(url,this.user).then(res => {
                if (res.data == true){
                    this.success = true
                    this.$router.push('/employeesignin')
                }
                else{
                    this.fail = true
                }
            });
      },
    home() {
      this.$router.push('/');
    }
  }
};
</script>

<style scoped>
.signup {
  margin-top: 5vh;
  margin-bottom: 5vh;
  text-align: center;
}

.signup-card {
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 40px;
  box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
}

.text-field-in-box {
  width: 100%;
}

.guide2Image {
  width: 100%;
  overflow: hidden;
}

.img-resize {
  max-width: 600%;
  max-height: 600px;
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

.custom-info {
  display: flex;
  align-items: center;
  background-color: transparent;
  color: red;
}

.custom-info .alert-icon {
  margin-right: 5px;
  color: red;
}

.custom-info .alert-text {
  font-size: 16px;
}

.footer {
  background-color: #080808;
  color: #fff;
  width: 100%;
  text-align: center;
  padding: 20px 0;
  position: fixed;
  bottom: 0;
}
</style>