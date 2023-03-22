<template>
  <form @submit.prevent="handlSubmit">
    <label>Email</label>
    <input type="email" required v-model="email" />
    <label>Password</label>
    <input type="password" required v-model="password" />
    <div v-if="passworError" class="error">
       {{ passworError }}
    </div>
    <label>Role</label>
    <select v-model="role">
      <option value="developer">Developer</option>
      <option value="designer">Web Designer</option>
    </select>
    <label>Skills</label>
    <input type="text" v-model="tempSkills" @keyup="AddSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
        <span @click="deleteItem(skill)"> {{ skill }}</span>
    </div>
    <div class="terms">

    <input type="checkbox" required v-model="terms" />
    <label>Accept Terms and Conditions </label>
    </div>
    <div class="submit">
        <button>Create An Account</button>
    </div>
  </form>
  <p>{{ email }}</p>
  <p>{{ password }}</p>
  <p>{{ role }}</p>
  <p>{{ terms }}</p>
</template>

<script>
export default {
  props: [],
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      terms: false,
      tempSkills: "",
      skills: [],
      passworError:''
    };
  },
  methods: {
    AddSkill(e) {
      if (e.key === "," && this.tempSkills) {
        if(!this.skills.includes(this.tempSkills)){
            this.skills.push(this.tempSkills);
        }
        
        this.tempSkills = "";
      }
    },
    deleteItem(skill){
this.skills=this.skills.filter((item)=>{
    return skill!=item
})
    },
    handlSubmit(){
       this.passworError=this.passworError>5?"":"Passowrd must be atleast 6 char long"
    }
  },
};
</script>

<style>
form {
  max-width: 520px;
  margin: 30px auto;
  background-color: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.8em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  color: #e555;
  border-bottom: 1px solid #ddd;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  color: #e555;
  border-bottom: 1px solid #ddd;
}

input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0;
  position: relative;
  margin-top: 2px;
}
.pill{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 10px 6px;
    border-radius: 20px;
    letter-spacing: 1px;
    background: #eee;
    color:#777;
    font-weight: bold;
    cursor: pointer;
    font-size: 14px;
}
button{
background: rgb(65, 65, 242);
padding: 10px 20px;
margin-top: 20px;
border-radius: 20px;
color: #ddd;
border: none;
}
.submit{
    text-align: center;
}
.error{
color:#ff0062;
margin-top: 10px;
font-size: 0.8em;
font-weight: bold;
}
</style>
