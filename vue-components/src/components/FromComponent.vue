<template>
  <form @submit.prevent="submitForm">
    <div class="form-control">
      <label for="emp_name">ชื่อพนักงาน</label>
      <input type="text" v-model.trim="employee.name" />
    </div>

    <div class="form-control">
      <label for="emp_name">เงินเดือน</label>
      <input type="number" v-model="employee.salary" />
    </div>

    <div class="form-control">
      <label for="emp_department">ตำแหน่งงาน</label>
      <select v-model="employee.department">
        <option value="Programmer">Programmer</option>
        <option value="Content Marketing">Content Marketing</option>
        <option value="Accounting">Accounting</option>
        <option value="HR">HR</option>
      </select>
    </div>

    <div class="form-control">
      <h2>เพศ</h2>
      <div>
        <input type="radio" value="ชาย" v-model="employee.gender" />
        <label for="gender">ชาย</label>
      </div>
      <div>
        <input type="radio" value="หญิง" v-model="employee.gender" />
        <label for="gender">หญิง</label>
      </div>
    </div>

    <div class="form-control">
      <h2>ภาษา</h2>
      <div>
        <input type="checkbox" value="ไทย" v-model="employee.language" />
        <label for="language">ไทย</label>
      </div>
      <div>
        <input type="checkbox" value="อังกฤษ" v-model="employee.language" />
        <label for="language">อังกฤษ</label>
      </div>
      <div>
        <input type="checkbox" value="ญี่ปุ่น" v-model="employee.language" />
        <label for="language">ญี่ปุ่น</label>
      </div>
    </div>
    <div>
      <button>บันทึก</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "FormComponent",
  data() {
    return {
      employee: {
        name: "",
        salary: 0,
        department: "",
        gender: "",
        language: [],
      },
    };
  },
  methods: {
    submitForm() {
      const newEmp = {
        name: this.employee.name,
        salary: this.employee.salary,
        department: this.employee.department,
        gender: this.employee.gender,
        language: this.employee.language,
      };
      this.$emit("save", newEmp);
      this.resetForm()
    },
    resetForm() {
      this.employee.name = "";
      this.employee.salary = 0;
      this.employee.department = "";
      this.employee.gender = "";
      this.employee.language = [];
    },
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
  padding: 2rem;
  background: #fff;
}
.form-control {
  margin: 0.5rem 0;
}
label {
  font-weight: bold;
}
input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}
button {
  font: inherit;
  background: rgb(252, 104, 104);
  color: #fff;
  cursor: pointer;
  padding: 0.5rem 1.8rem;
  border-radius: 30px;
  outline: none;
  border: none;
}
input[type="radio"],
input[type="checkbox"] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}
input[type="radio"] + label,
input[type="checkbox"] + label {
  font-weight: normal;
}
h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}
</style>