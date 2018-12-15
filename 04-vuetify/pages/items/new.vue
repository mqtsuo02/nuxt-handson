<template>
  <div>
    <h1>Items New</h1>
    <v-form>
      <v-text-field
        v-model="name"
        label="name"
        required
      ></v-text-field>
      <v-text-field
        v-model="price"
        label="price"
        required
      ></v-text-field>
      <v-text-field
        v-model="description"
        label="description"
        required
      ></v-text-field>
    </v-form>
    <v-btn color="success" @click="add({name, price, description})">Add</v-btn>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      name: "",
      price: null,
      description: ""
    };
  },
  methods: {
    add(item) {
      console.log(item)
    }
  }
};
</script>
