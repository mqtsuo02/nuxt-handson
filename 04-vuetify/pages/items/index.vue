<template>
  <div>
    <h1>Items</h1>
    <v-data-table
      :headers="headers"
      :items="items"
      hide-actions
    >
      <template slot="items" slot-scope="props">
        <td>{{ props.item.id }}</td>
        <td><router-link :to="'/items/' + props.item.id">{{ props.item.name }}</router-link></td>
        <td>{{ props.item.price }}</td>
      </template>
    </v-data-table>
    <v-btn color="success" @click="route('/items/new')">Add Item</v-btn>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      items: [],
      headers: [
          { text: "id", sortable: false},
          { text: "name", sortable: false},
          { text: "price", sortable: false}
        ],
    };
  },
  asyncData: async function () {
    const response = await axios.get("http://localhost:3001/items")
    return { items: response.data }
  },
  methods: {
    route(url) {
      this.$router.push(url)
    }
  }
};
</script>
