<script>
    import { mapWritableState, mapActions } from 'pinia';
    import { useCounterStore } from "../stores/counter"
    
    export default {
        data() {
        return {
            login_email: "",
            login_password: "",
        }
    },
      methods: {
        ...mapActions(useCounterStore, ["getPainting", "logoutHandler", "fetchProducts", 'qrCode', 'loginHandler']),
        loginHandlerComponent(){
            this.loginHandler({
                email: this.login_email,
                password: this.login_password
            })
            // this.$router.push('/')
        },
        changePage(){
            this.$router.push("/register")
        }
      },
    
      computed: {
        ...mapWritableState(useCounterStore, ["paintings", "products", "qrImage", "totalPages", "index", "isLoading"])
      },
      created() {
        this.getPainting()
      }
    }
    
    </script>

<template>

<section class="container-sm">
      <h3 class="text-white mx-5 my-5 justify-content-center"
        style="font-family:monospace;vertical-align: auto;width: auto;text-align: center;">MET Digital is a preview of our
        vast collection in New York. Here you may look at paintings currently being shown at our museum. Enjoy this
        virtual tour!</h3>
      </section>
     
      <div class="d-flex justify-content-center">
        <div class="row">
          <div class="col-md-4">
  
            <section class="container-fluid mt-5 p-3" style="width: 400px;background-color:rgba(200,200,200, 0.3)">
              <h1 class="p-2 bg-secondary text-white text-center" style="border-radius:10px">Login Form</h1>
              <form id="login-form" @submit.prevent="loginHandlerComponent">
                <div class="mb-3">
                  <label for="exampleInputEmail1" class="form-label">Email</label>
                  <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp"
                    placeholder="someone@mail.com" v-model="login_email">
                  <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
                </div>
                <div class="mb-3">
                  <label for="exampleInputPassword1" class="form-label">Password</label>
                  <input type="password" class="form-control" id="exampleInputPassword1" placeholder="*****"
                    v-model="login_password">
                </div>
                <button type="submit" class="btn text-white align-items-center" style="background-color:rgb(12,12,100);font-family:monospace;font-size:20px">Submit</button><br>
                <a @click="changePage" href="#">Don't have an account? Register here</a><br>
                <!-- <br>or sign in with google:<br> -->
              </form>
              <!-- <button id="google-button-login"></button> -->
            </section>
          </div>
          <div class="col container-fluid">
            <img class="my-5 mx-5 img-fluid" src="https://images.metmuseum.org/CRDImages/ep/web-large/DT1567.jpg">
          </div>
        </div>
      </div>


</template>