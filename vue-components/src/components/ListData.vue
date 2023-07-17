<template>
  <div>
    <ul>
      <Person
        v-for="(item,index) in employees"
        :key="index"
        :name="item.name"
        :salary="item.salary"
        :department="item.department"
        :gender="item.gender"
        :language="item.language"
      />
    </ul>
  </div>
</template>

<script>
import Person from "./Person.vue";

export default {
  name: "ListData",
  components: {
    Person,
  },
  props: ["employees"],
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 1rem 0;
  padding: 0;
}
</style>