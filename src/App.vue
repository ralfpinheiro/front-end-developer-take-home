<template>
    <div id="app" class="container">
        <div class="row">
            <div class="col-12 my-5 p-0">
                <h1>Fleet Assets</h1>
            </div>
            <!-- TODO: Separate into a new component -->
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
                    <tr v-for="(vehicle, index) in vehicles" :key="index">
                        <td> {{ vehicle.year }} </td>
                        <td> {{ vehicle.make }} </td>
                        <td> {{ vehicle.model }} </td>
                        <td> {{ vehicle.colour }} </td>
                        <td>
                            <!-- TODO: Implement deleting the specified vehicle -->
                            <button type="button" class="btn btn-sm btn-outline-danger mx-2">Delete</button>
                        </td>
                    </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- TODO: Separate into a new component-->
        <form class="mt-4">
            <div class="row">
                <div class="col">
                    <input type="text" class="form-control" placeholder="Year" v-model="form.year">
                </div>
                <div class="col">
                    <input type="text" class="form-control" placeholder="Make" v-model="form.make">
                </div>
                <div class="col">
                    <input type="text" class="form-control" placeholder="Model" v-model="form.model">
                </div>
                <div class="col">
                    <input type="text" class="form-control" placeholder="Colour" v-model="form.colour">
                </div>
                <div class="col">
                    <button type="button" class="btn btn-primary mx-2" @click="create">Create</button>
                    <!-- TODO: Implement reset form functionality -->
                    <button type="button" class="btn btn-danger mx-2">Reset</button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'app',

        data() {
            return {
                vehicles: {
                    1: {
                        year: '2018',
                        make: 'Ford',
                        model: 'Econoline',
                        colour: 'White',
                    },

                    2: {
                        year: '2017',
                        make: 'Mercedes',
                        model: 'Sprinter',
                        colour: 'Black',
                    }
                },

                form: {
                    year: '',
                    make: '',
                    model: '',
                    colour: '',
                }
            }
        },

        methods: {
            create() {
                // TODO: Dynamically increment the Index based on the number of vehicles
                const index = 3;

                const formFields = { ...this.form }

                this.$set(this.vehicles, index, formFields);

                // TODO: Reset the form
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }
</style>
