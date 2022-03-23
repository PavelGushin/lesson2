<template>
  <div id="app">
    <div class="d-flex">
      <table-component
        :userData="tblData"
        class="me-5 ms-5"
        v-on:move="onMove"
      />
      <table-component
        :userData="tblData2"
        class="me-5 ms-5"
        v-on:move="onMove"
      />
    </div>
  </div>
</template>

<script>
import tableComponent from "./components/tableComponent.vue";
import jsonData from "./tblData.json";

export default {
  name: "App",
  components: {
    tableComponent,
  },
  data() {
    return {
      tblData: jsonData,
      tblData2: [
        {
          id: 3,
          login: "Alex",
        },
        {
          id: 4,
          login: "Joe",
        },
      ],
    };
  },
  methods: {
    onMove: function (data) {
      console.log(data);
      let result = this.tblData.filter(function (item) {
        return item.id !== data.id;
      });
      if (result.length === this.tblData.length) {
        this.tblData.push(data);

        result = this.tblData2.filter(function (item) {
          return item.id !== data.id;
        });

        this.tblData2 = result;
      } else {
        this.tblData2.push(data);
        this.tblData = result;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
