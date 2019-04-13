<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-12 my-5 p-0">
        <h1>Fleet Assets</h1>
      </div>
      <!-- TODO: Separate into a new component -->
      <vehicles-table :data="vehicles" @removeItem="remove($event)"></vehicles-table>
    </div>
    <!-- TODO: Separate into a new component-->
    <table-form :data="form" @createItem="create($event)" @resetForm="reset($event)"></table-form>
  </div>
</template>

<script>
import VehiclesTable from "./VehiclesTable";
import TableForm from "./TableForm";

export default {
  name: "app",
  components: {
    VehiclesTable,
    TableForm
  },
  data() {
    return {
      vehicles: {
        1: {
          year: "2018",
          make: "Ford",
          model: "Econoline",
          colour: "White"
        },

        2: {
          year: "2017",
          make: "Mercedes",
          model: "Sprinter",
          colour: "Black"
        }
      },

      form: {
        year: "",
        make: "",
        model: "",
        colour: ""
      }
    };
  },

  methods: {
    create() {
      // TODO: Dynamically increment the Index based on the number of vehicles
      const index = Object.keys(this.vehicles).length + 1;

      const formFields = { ...this.form };

      if (
        formFields.year == "" ||
        formFields.make == "" ||
        formFields.model == "" ||
        formFields.colour == ""
      ) {
        alert("Please fill in all fields!");
        return;
      }

      this.$set(this.vehicles, index, formFields);

      this.reset();

      // TODO: Reset the form
    },
    reset() {
      this.form.year = "";
      this.form.make = "";
      this.form.model = "";
      this.form.colour = "";
    },
    remove(event) {
      this.$delete(this.vehicles, event);
    }
  }
};
</script>

<style>
body {
  background-color: #f9f9f9;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
