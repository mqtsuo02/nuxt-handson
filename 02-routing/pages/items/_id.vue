<template>
  <div>
    <h1>Items Id</h1>
    <h2>{{id}}</h2>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      id: this.$route.params.id
    };
  }
};
</script>
