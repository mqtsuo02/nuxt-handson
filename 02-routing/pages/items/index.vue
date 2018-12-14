<template>
  <div>
    <h1>Items</h1>
    <table border="1">
      <thead>
        <tr>
          <th>id</th>
          <th>name</th>
          <th>price</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>{{item.id}}</td>
          <td>
            <router-link :to="'/items/' + item.id">{{item.name}}</router-link>
          </td>
          <td>{{item.price}}</td>
        </tr>
      </tbody>
    </table>
    <button>
      <router-link to="/items/new">Add Item</router-link>
    </button>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      items: [
        {
          id: 1,
          name: "apple",
          price: 120
        },
        {
          id: 2,
          name: "banana",
          price: 80
        }
      ]
    };
  }
};
</script>
