<template>
  <Card>
    <template v-slot:card-header>
      <h1>{{ name }}</h1>
    </template>
    <template v-slot:card-content>
      <p>เพศ: {{gender}}</p>
      <p>Salary: {{ salary }} บาท ,ตำแหน่งงาน {{ department }}</p>
      <p>ภาษา: {{language}}</p>
    </template>
  </Card>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "Person",
  components: {
    Card,
  },
  props: {
    name: {
      type: String,
      requred: true,
    },
    salary: {
      type: Number,
      default: 15000,
    },
    department: {
      type: String,
      requred: true,
    },
    gender:{
      type:String
    },
    language:{
      type:Array
    }
  },
};
</script>

<style scoped>
button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background: #ff0077;
  color: #fff;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.5s linear;
}
</style>