<template>
  <div class="container-fluid p-0">
    <div class="row no-gutters">
      <div class="left-side-landing col-xs-12 col-sm-6 col-md-6">
        <!-- <section class="overlay-section">
          <p>No Hazzles</p>
          <p>
            Lorem ipsum dolor sit amet, consectetur <br />adipiscing elit, sed
            do eiusmod.
          </p>
        </section>
        <section  class="overlay-image">
          <v-img class="overlay-img" src="sliderdot.png"></v-img>
        </section> -->
      </div>

      <div class="col-xs-12 col-sm-6 col-md-6">
        <div class="row inner-div-right">
          <div class="col d-flex justify-content-center">
            <section class="head-text">
              <p class="signup-header">Create your free account</p>
              <p class="signup-subtext">
                Already registered?
                <span class="subtext-in">
                  <nuxt-link
                    to="/dashboard"
                    style="color: #2bda53; text-decoration: none"
                    >Sign in</nuxt-link
                  ></span
                >
              </p>
            </section>
          </div>
        </div>

        <div class="row">
          <div class="col d-flex justify-content-center">
            <div class="card">
              <div class="card-body">
                <v-form v-model="valid" ref="form">
                  <!-- <v-container> -->
                  <v-row>
                    <v-col cols="12" sm="12" md="6">
                      <v-text-field
                        append-icon="mdi-account"
                        v-model="firstname"
                        :rules="nameRules"
                        label="First name"
                        required
                      ></v-text-field>
                    </v-col>

                    <v-col cols="12" sm="12" md="6">
                      <v-text-field
                        append-icon="mdi-account"
                        v-model="lastname"
                        :rules="nameRules"
                        label="Last name"
                        required
                      ></v-text-field>
                    </v-col>

                    <v-col cols="12" sm="12" md="12">
                      <v-text-field
                        append-icon="mdi-email"
                        v-model="email"
                        :rules="emailRules"
                        label="E-mail"
                        required
                      ></v-text-field>
                    </v-col>

                    <v-col cols="12" sm="12" md="12">
                      <v-text-field
                        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                        :rules="[rules.required, rules.emailMatch]"
                        :type="show1 ? 'text' : 'password'"
                        name="input-10-2"
                        label="Password"
                        hint="At least 8 characters"
                        v-model="userPassword"
                        error
                        @click:append="show1 = !show1"
                        required
                      ></v-text-field>
                    </v-col>

                    <section class="btn-submit d-flex justify-content-right">
                      <button
                        type="button"
                        class="btn btn-lg btn-success btn-inner"
                      >
                        <nuxt-link
                          to="/dashboard"
                          style="color: #ffffff; text-decoration: none"
                          >Continue
                        </nuxt-link>
                      </button>
                    </section>
                  </v-row>
                  <!-- </v-container> -->
                </v-form>
              </div>
            </div>
          </div>
        </div>
        <div class="row bottom-section">
          <div class="col-xs-12 col-sm-6 d-flex justify-content-center">
            <p class="footer-test">
              By siging up, you agree to our
              <span class="subtext-in">Terms</span> and
              <span class="subtext-in">Privacy Policy</span>
            </p>
          </div>
          <div class="col-xs-12 col-sm-6 d-flex justify-content-center">
            <p class="footer-copyright">
              © 2019 Tinylabs. All rights reserved.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      valid: true,
      show1: false,
      password: "Password",
      rules: {
        required: (value) => !!value || "required",
        min: (v) => v.length >= 8 || "Min 8 characters",
      },
      valid: false,
      userPassword: "",
      firstname: "",
      lastname: "",
      nameRules: [(v) => !!v || "required"],
      email: "",
      emailRules: [
        (v) => !!v || "required",
        (v) => /.+@.+/.test(v) || "E-mail must be valid",
      ],
    };
  },

  methods: {
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },
  },
};
</script>
<style scoped>
.container-fluid {
  background-color: #e5e5e5;
}
.left-side-landing {
  height: 100vh;
  background-image: url("/Model.png");
  background-repeat: no-repeat;
  background-size: cover;
}
.inner-div-right {
  margin-top: 50px;
  text-align: center;
}
.signup-header {
  font-family: Roboto;
  font-style: normal;
  font-weight: 500;
  font-size: 34px;
  letter-spacing: 0.4px;
  color: #013c61;
}

.signup-subtext {
  font-family: Roboto;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  letter-spacing: -0.102857px;
  color: #013c61;
  text-align: left;
}

.subtext-in {
  color: #2bda53;
}

.inner-div-card {
  margin-top: 50px;
  text-align: center;
}

.card {
  margin-left: 120px;
  margin-right: 120px;
  padding-bottom: 20px;
  background: #ffffff;
  box-shadow: 0px 20px 50px #eaeee9;
  border-radius: 5px;
}
.btn-inner {
  text-align: center;
  color: #ffffff;
  background-color: #2bda53;
  width: 50%;
}

.btn-submit {
  display: flex;
  justify-content: right;
  width: 100%;
}

.footer-test {
  font-family: Roboto;
  font-style: normal;
  font-weight: normal;
  font-size: 13px;
  line-height: 18px;
  /* identical to box height, or 138% */

  letter-spacing: -0.08px;

  color: #6a7e8a;
}

.footer-copyright {
  font-family: Roboto;
  font-style: normal;
  font-weight: normal;
  font-size: 13px;
  line-height: 18px;
  /* identical to box height, or 138% */

  text-align: right;
  letter-spacing: -0.08px;

  color: #6a7e8a;
}

.bottom-section {
  padding-top: 80px;
  padding-left: 30px;
  padding-right: 30px;
}
.overlay-img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 8%;
}

.overlay-section {
}

@media only screen and (max-width: 894px) {
  .card {
    margin-left: 10px;
    margin-right: 10px;
    padding-bottom: 20px;
    background: #ffffff;
    box-shadow: 0px 20px 50px #eaeee9;
    border-radius: 5px;
  }
}

@media only screen and (max-width: 600px) {
  .left-side-landing {
    display: none;
  }

  .card {
    margin-left: 10px;
    margin-right: 10px;
    padding-bottom: 20px;
    background: #ffffff;
    box-shadow: 0px 20px 50px #eaeee9;
    border-radius: 5px;
  }
}
</style>
