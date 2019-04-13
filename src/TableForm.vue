<template>
  <form class="mt-4">
    <div class="row">
      <div class="col">
        <input type="text" class="form-control" placeholder="Year" v-model="data.year">
      </div>
      <div class="col">
        <input type="text" class="form-control" placeholder="Make" v-model="data.make">
      </div>
      <div class="col">
        <input type="text" class="form-control" placeholder="Model" v-model="data.model">
      </div>
      <div class="col">
        <input type="text" class="form-control" placeholder="Colour" v-model="data.colour">
      </div>
      <div class="col">
        <button type="button" class="btn btn-primary mx-2" @click="create">Create</button>
        <!-- TODO: Implement reset form functionality -->
        <button type="button" class="btn btn-danger mx-2" @click="reset">Reset</button>
      </div>
    </div>
  </form>
</template>
<script>
export default {
  props: ["data"],
  methods: {
    create() {
      this.$emit("createItem", this.data);
    },
    reset() {
      this.$emit("resetForm", this.data);
    }
  }
};
</script>