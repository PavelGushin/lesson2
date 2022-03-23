<template>
  <table class="table table-dark">
    <thead>
      <tr>
        <th scope="col">id</th>
        <th scope="col">Имя пользователя</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="item in userData"
        :key="item.id"
        class="pointer"
        v-on:click="send(item)"
      >
        <th>{{ item.id }}</th>
        <th>{{ item.login }}</th>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "tableComponent",
  props: ["userData"],
  methods: {
    send: function (item) {
      this.$emit("move", item);
    },
  },
};
</script>


<style scoped>
.pointer {
  cursor: pointer;
}
</style>

