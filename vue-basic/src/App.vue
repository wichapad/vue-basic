<template>
  <section>
    <img :src="picture" :width="size" :height="size" alt="" ref="imageUrl" />
    <br />

    <h1>ผู้สมัคร : {{ getFullName}}</h1>

    <h2>อายุ : {{ age }} ปี</h2>
    <h1>Salary: {{salary}} บาท</h1>
    <h1>ตำแหน่งงาน: {{getDepartment}}</h1>

    <button @click="addSaraly(5000)">increase salary</button>
    <button @click="decreaseSaraly(5000)">decrease salary</button>
    <button @click="toggleVisible">{{ isVisible ? "Hide" : "Show" }}</button>
    <div v-show="isVisible">
      <p><span v-html="address"></span></p>
      <a :href="social" target="_blank">Youtube</a>
      <p v-if="hobby.length === 0">Not Hobby</p>
      <div v-else>
        <p>Hobby:</p>
        <ul>
          <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
        </ul>
      </div>
      <ul>
        <li v-for="(item, key) in general" :key="key">{{ item }}</li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "Wichapad",
      lastName: "Muenjumrad",

      age: 27,
      address: "<i>Bankok</i>",
      picture:
        "https://images.unsplash.com/photo-1661956602944-249bcd04b63f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
      size: 150,
      social: "https://www.youtube.com/watch?v=9j537584dI0",
      hobby: [
        "game",
        "Learn program",
        "listen music",
        "See Movies",
        "Reading",
        "Basketball",
      ],
      general: { gender: "male", weight: 70, height: 171, status: false },
      isVisible: false,
      salary:50000
    };
  },
  methods: {
    toggleVisible() {
      this.isVisible = !this.isVisible;
    },
    addSaraly(value){
      this.salary+=value
    },
    decreaseSaraly(value){
      this.salary-=value
    }
    
  },
  computed: { //
    getFullName() {
      return `${this.firstName + " " + this.lastName}`;
    },
    getIncome(){
      return this.salary * 12
    },
    getDepartment(){
      return this.salary >= 35000 ? "Project Manager" : "Programmer"
    }
  },

  watch:{
    salary(value){
      if (value > 50000) {
        alert("เงินเดือนไม่ควรเกิน 50000 บาท")
        setTimeout(()=>{
          this.salary = 20000
        },200)
      }
    }
  }
};
</script>

<style>
</style>
