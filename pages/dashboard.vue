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
        <b-row>
          <b-col md="2">
            <b-form-select v-model="selected" :options="selctoptions"></b-form-select>
          </b-col>
          <b-col md="1">
            <button type="button" style="color:white" class="btn btn-md btn-success btn-inner">
              change
            </button>
          </b-col>
          <b-col md="2">
            <b-form-input
              v-model="filter"
              type="search"
              id="filterInput"
              placeholder="Type to Search"
            ></b-form-input>
          </b-col>

          <b-col>
            <section
              class=""
              style="
                margin-left:350px
              "
            >
              <b-pagination
                v-model="currentPage"
                :total-rows="rows"
                :per-page="perPage"
                aria-controls="my-table"
              ></b-pagination>
            </section>
          </b-col>
        </b-row>
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
                  ><v-icon @click="deleteItem(data.item.id)"
                    >mdi-delete</v-icon
                  ></b-button
                >
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
      selctoptions:[{value:1, text: 'ADMIN'}],
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
