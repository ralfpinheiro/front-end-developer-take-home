<template>
  <div class="col-12 p-0">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Year</th>
          <th scope="col">Make</th>
          <th scope="col">Model</th>
          <th scope="col">Colour</th>
          <th scope="col">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(vehicle, index) in data" :key="index">
          <td>{{ vehicle.year }}</td>
          <td>{{ vehicle.make }}</td>
          <td>{{ vehicle.model }}</td>
          <td>{{ vehicle.colour }}</td>
          <td>
            <!-- TODO: Implement deleting the specified vehicle -->
            <button
              type="button"
              class="btn btn-sm btn-outline-danger mx-2"
              @click="remove(index)"
            >Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  props: ["data"],
  methods: {
    remove(index) {
      this.$emit("removeItem", index);
    }
  }
};
</script>
