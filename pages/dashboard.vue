<template>
  <div class="container-fluid p-0">
    <v-card color="grey lighten-4" flat height="50px" tile>
      <v-toolbar dense>
        <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->

        <v-toolbar-title>
          <section>
            <v-img class="overlay-img" src="getchangelogo.png"> </v-img>
          </section>
        </v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-circle</v-icon>
        </v-btn>
        <span>Hi, Joshua</span>
        <v-btn icon>
          <v-icon>mdi-arrow-down</v-icon>
        </v-btn>
      </v-toolbar>
    </v-card>

    <div class="row">
      <div class="col-xs-2">
        <div class="sidebar">
          <a
            v-bind:class="{ active: isActive1 }"
            @click="activate1()"
            href="#home"
            ><v-img src="iconted.png"> </v-img
          ></a>
          <a
            v-bind:class="{ active: isActive2 }"
            @click="activate2()"
            href="#newss"
            ><v-img src="icon2.png"> </v-img
          ></a>
          <a
            class="outer-a"
            v-bind:class="{ active: isActive3 }"
            @click="activate3()"
            href="#contact"
            ><v-img src="icon3.png"> </v-img
          ></a>
        </div>
      </div>

      <div class="col-sm main-display">
        <div class="row">
          <div class="col">
            <div
              class="head-section"
              style="display: flex; justify-content: space-between"
            >
              <p class="head-sec-emp">Employees</p>
              <p>
                <button
                  v-b-modal.modal-1
                  @click="showModal"
                  ref="btnShow"
                  type="button"
                  style="color: white"
                  class="btn btn-lg btn-success btn-inner"
                >
                  Add New
                </button>

                <b-modal id="modal-1" :ok-disabled="true" hide-footer>
                  <div class="d-block head-sec-emp">Add New Employee</div>
                  <br />
                  <br />
                  <form ref="form" @submit.stop.prevent="handleSubmit">
                    <b-form-group label="Firstname" label-for="firstname-input">
                      <b-form-input
                        id="firstname-input"
                        v-model="formData.firstname"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group label="Lastname" label-for="lastname-input">
                      <b-form-input
                        id="lastname-input"
                        v-model="formData.lastname"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group label="Email" label-for="email-input">
                      <b-form-input
                        id="email-input"
                        v-model="formData.email"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group label="Phone" label-for="phone-input">
                      <b-form-input
                        id="phone-input"
                        v-model="formData.phone"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group label="Password" label-for="password-input">
                      <b-form-input
                        id="password-input"
                        v-model="formData.password"
                        required
                      ></b-form-input>
                    </b-form-group>
                  </form>
                  <div class="row">
                    <div class="col">
                      <b-button
                        @click="submit"
                        class="btn btn-lg btn-success btn-inner"
                        style="color: #ffffff"
                        >Submit</b-button
                      >
                      <b-button
                        @click="toggleModal"
                        class="btn btn-lg btn-info btn-inner"
                        style="color: #ffffff"
                        >Close</b-button
                      >
                    </div>
                  </div>
                </b-modal>

                <b-modal id="modal-2" :ok-disabled="true" hide-footer>
                  <div class="d-block head-sec-emp">Update Employee</div>
                  <br />
                  <br />
                  <form ref="form" @submit.stop.prevent="handleSubmited">
                    <b-form-group label="Firstname" label-for="firstname-input">
                      <b-form-input
                        id="firstname-input"
                        v-model="formData.firstname"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group label="Lastname" label-for="lastname-input">
                      <b-form-input
                        id="lastname-input"
                        v-model="formData.lastname"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group label="Email" label-for="email-input">
                      <b-form-input
                        id="email-input"
                        v-model="formData.email"
                        required
                      ></b-form-input>
                    </b-form-group>

                    <b-form-group label="Phone" label-for="phone-input">
                      <b-form-input
                        id="phone-input"
                        v-model="formData.phone"
                        required
                      ></b-form-input>
                    </b-form-group>
                  </form>
                  <div class="row">
                    <div class="col">
                      <b-button
                        @click="updateEmployee"
                        class="btn btn-lg btn-success btn-inner"
                        style="color: #ffffff"
                        >Update Employee</b-button
                      >
                      <b-button
                        @click="toggleModal"
                        class="btn btn-lg btn-info btn-inner"
                        style="color: #ffffff"
                        >Close</b-button
                      >
                    </div>
                  </div>
                </b-modal>
              </p>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col">
            <div class="card" style="background: #ffffff; border-radius: 5px">
              <div
                class="card-body"
                style="display: flex; justify-content: space-between"
              >
                <p class="comp-name">Josh Bakery Ventures.</p>
                <p class="comp-address">62, Bode Thomas, Surulere, Lagos</p>
              </div>
            </div>
          </div>
        </div>

        <br /><br />

        <div class="row">
          <div class="col">
            <div style="display: flex; justify-content: space-between">
              <span style="display: flex">
                <p style="margin-right: 10px">
                  <b-form-select
                    v-model="selected"
                    :options="selctoptions"
                  ></b-form-select>
                </p>
                <p style="margin-right: 10px">
                  <button
                    type="button"
                    style="color: white"
                    class="btn btn-md btn-success btn-inner"
                  >
                    change
                  </button>
                </p>
                <p>
                  <b-form-input
                    v-model="filter"
                    type="search"
                    id="filterInput"
                    placeholder="Type to Search"
                  >
                  </b-form-input>
                </p>
              </span>

              <span>
                <b-pagination
                  v-model="currentPage"
                  :total-rows="rows"
                  :per-page="perPage"
                  aria-controls="my-table"
                ></b-pagination>
              </span>
            </div>
          </div>
        </div>

        <b-row>
          <b-col>
            <b-table
              striped
              none
              hover
              outlined
              :items="employess"
              :fields="fields"
              :filter="filter"
              :current-page="currentPage"
              :per-page="perPage"
            >
              <template v-slot:cell(actions)="data">
                <b-button variant="light" @click="deleteItem(data.item.id)"
                  ><v-icon @click="deleteItem(data.item.id)">mdi-delete</v-icon>
                </b-button>
                <b-button
                  v-b-modal.modal-2
                  variant="light"
                  @click="fetchUpdateItem(data.item.id)"
                  ><v-icon @click="fetchUpdateItem(data.item.id)"
                    >mdi-pen</v-icon
                  >
                </b-button>
              </template>
            </b-table>
          </b-col>
        </b-row>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      formData: {
        firstname: "",
        lastname: "",
        email: "",
        phone: "",
        password: "",
        role: "ADMIN",
      },
      selected: "",
      idForUpdate: null,
      selctoptions: [{ value: 1, text: "ADMIN" }],
      employess: [],
      isActive1: true,
      isActive2: false,
      isActive3: false,
      hasError: false,

      filter: "",
      perPage: 5,
      currentPage: 1,
      fields: [
        "id",
        "firstname",
        "lastname",
        "email",
        "phone",
        "role",
        "actions",
      ],
    };
  },

  methods: {
    activate1() {
      this.isActive1 = !this.isActive1;
      this.isActive2 = false;
      this.isActive3 = false;
    },
    activate2() {
      this.isActive1 = false;
      this.isActive2 = !this.isActive2;
      this.isActive3 = false;
    },
    activate3() {
      this.isActive3 = !this.isActive3;
      this.isActive1 = false;
      this.isActive2 = false;
    },

    deleteItem(id) {
      this.$axios
        .$delete(`employee/${id}`)
        .then((res) => {
          this.employess = res.data;
          console.log(res.data);
          this.$router.go();
        })
        .catch((err) => {
          console.log(err);
        });
    },

    fetchUpdateItem(id) {
      let employee = JSON.parse(JSON.stringify(this.employess));
      let data = this;
      // console.log(employee);
      for (let i = 0; i < employee.length; i++) {
        if (employee[i].id == id) {
          data = employee[i];
        }
      }

      this.formData.firstname = data.firstname;
      this.formData.lastname = data.lastname;
      this.formData.email = data.email;
      this.formData.phone = data.phone;
      this.idForUpdate = id;
    },

    updateEmployee() {
      this.$axios
        .$put(`employee/${this.idForUpdate}`, this.formData)
        .then((res) => {
          this.employess = res.data;
          console.log(res.data);
          this.$router.go();
        })
        .catch((err) => {
          console.log(err);
        });
    },

    showModal() {
      this.$root.$emit("bv::show::modal", "modal-1", "#btnShow");
    },
    submit() {
      this.$root.$emit("bv::hide::modal", "modal-1", "#btnShow");
      this.$axios
        .$post(`employee`, this.formData)
        .then((res) => {
          this.employess = res.data;
          console.log(res.data);
          this.$router.go();
        })
        .catch((err) => {
          console.log(err);
        });
    },
    toggleModal() {
      this.$root.$emit("bv::toggle::modal", "modal-1", "#btnToggle");
    },
  },

  computed: {
    rows() {
      return this.employess.length;
    },
  },
  mounted() {
    this.$axios
      .$get("employee")
      .then((res) => {
        this.employess = res.data;
        console.log(res.data);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style scoped>
.container-fluid {
  width: 100vw;
  min-height: 100vh;
  background-color: #e5e5e5;
}

.sidebar {
  margin-right: 120px;
  padding-left: 20px;
  min-height: 100vh;
  background-color: #ffffff;
}

/* The side navigation menu */
.sidebar {
  margin: 0;
  padding: 0;
  width: 100px;
  background-color: #ffffff;
  position: fixed;
  height: 100%;
  overflow: auto;
}

.icon-bg {
  background-color: #ffffff;
  display: block;
}

.main-display {
  margin-top: 50px;
  padding-left: 150px;
  padding-right: 100px;
}

/* Sidebar links */
.sidebar a {
  width: 100px;
  display: block;
  color: black;
  padding: 33px;
  text-decoration: none;
}

/* Active/current link */
.sidebar a.active {
  background-color: #ffffff;
  border-left: 19px solid #2bda53;
  color: #2bda53;
}

/* Links on mouse-over */
.sidebar a:hover:not(.active) {
  background-color: #555;
  color: white;
}

/* Page content. The value of the margin-left property should match the value of the sidebar's width property */
div.content {
  margin-left: 200px;
  padding: 1px 16px;
  height: 1000px;
}

.comp-name {
  font-family: Roboto;
  font-style: normal;
  font-weight: 500;
  font-size: 36px;
  line-height: 15px;
  /* or 42% */

  display: flex;
  align-items: center;
  letter-spacing: -0.9px;

  color: #013c61;
}

.comp-address {
  font-family: Roboto;
  font-style: normal;
  font-weight: normal;
  font-size: 22px;
  line-height: 15px;
  /* or 68% */

  display: flex;
  align-items: center;
  text-align: right;
  letter-spacing: -0.55px;
}

.head-sec-emp {
  font-family: Roboto;
  font-style: normal;
  font-weight: 500;
  font-size: 26px;
  line-height: 15px;
  /* or 58% */

  display: flex;
  align-items: center;
  letter-spacing: -0.65px;

  color: #013c61;
}
/* On screens that are less than 700px wide, make the sidebar into a topbar */
@media screen and (max-width: 700px) {
  .sidebar {
    width: 100%;
    height: auto;
    position: relative;
  }
  div.content {
    margin-left: 0;
  }
}

/* On screens that are less than 400px, display the bar vertically, instead of horizontally */
@media screen and (max-width: 500px) {
  .sidebar a {
    text-align: center;
    float: none;
  }

  .main-display {
    margin-top: 10px;
    padding-left: 10px;
  }
}
</style>
