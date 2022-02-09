<template>
  <div class="container-fluid p-0">
    <div class="row no-gutters">
      <div class="left-side-landing col-sm-6"></div>

      <div class="col-sm-6">
        <div class="row inner-div-right">
          <div class="col d-flex justify-content-center">
            <section class="head-text">
              <p class="signup-header">Create your free account</p>
              <p class="signup-subtext">
                Already registered? <span class="subtext-in">Sign in</span>
              </p>
            </section>
          </div>
        </div>

        <div class="row">
          <div class="col d-flex justify-content-center">
            <div class="card">
              <div class="card-body">
                <v-form v-model="valid"  ref="form">
                  <!-- <v-container> -->
                    <v-row>
                      <v-col cols="12" md="6">
                        <v-text-field
                          append-icon="mdi-account"
                          v-model="firstname"
                          :rules="nameRules"
                          label="First name"
                          required
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" md="6">
                        <v-text-field
                          append-icon="mdi-account"
                          v-model="lastname"
                          :rules="nameRules"
                          label="Last name"
                          required
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" md="12">
                        <v-text-field
                          append-icon="mdi-email"
                          v-model="email"
                          :rules="emailRules"
                          label="E-mail"
                          required
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" md="12">
                        <v-text-field
                          :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                          :rules="[rules.required, rules.emailMatch]"
                          :type="show1 ? 'text' : 'password'"
                          name="input-10-2"
                          label="Password"
                          hint="At least 8 characters"
                          value="Pa"
                          error
                          @click:append="show1 = !show1"
                          required
                        ></v-text-field>
                      </v-col>

                      <section class="btn-submit d-flex justify-content-right">
                        <button type="button" class="btn btn-success btn-inner">Success</button>
                      </section>
                    </v-row>
                  <!-- </v-container> -->
                </v-form>
              </div>
            </div>
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
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
      },
      valid: false,
      firstname: "",
      lastname: "",
      nameRules: [(v) => !!v || "Name is required"],
      email: "",
      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+/.test(v) || "E-mail must be valid",
      ],
    };
  },

   methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
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
  background: #ffffff;
  box-shadow: 0px 20px 50px #eaeee9;
  border-radius: 5px;
}
.btn-inner {
  text-align: right;
}
</style>
