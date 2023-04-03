<template>
  <div class="mainPage">
      <h1>Hello {{ students.name }}</h1> <!--Interpolation-->
      <a :href="github" target="blank" rel="nooperner noreferrer"><h2>Github</h2></a>
      <a v-bind:href="twitter" target="blank"><h2>Twitter</h2></a>
      <br>
      <p>student information:</p>
        <label class="label" for="id">id: </label>
        <label class="input" id="id">{{ students.id }}</label><br>

        <label class="label" for="name">name: </label>
        <input type="input" v-model="students.name"><br/>

        <label class="label" for="id">surname: </label>
        <input type="input" v-model="students.surname"/><br>

        <label class="label" for="age">age: </label>
        <input type="input" v-model="students.age"/><br>

        <label class="label" for="age">carreer: </label>
        <input type="input" v-model="students.carreer"/><br>

        <label class="label">Eyes color</label>
        <label class="radio" for="color-black">
          <input type="radio" value="Black" v-model="students.eyesColor">
          Black
        </label>
        <label class="radio" for="color-blue">
          <input type="radio" value="Blue" v-model="students.eyesColor">
          Blue
        </label>
        <label class="radio" for="color-brown">
          <input type="radio" value="Brown" v-model="students.eyesColor">
          Brown
        </label><br/>
        <div class="colored-line" :style="{ 'background-color': students.eyesColor }"></div><br>

        <label for="grade">Grade:  
        <div class="select is-primary">
          <select id="grade" v-model="students.grade" @keyup.esc="clearGrade">
            <option disabled value>Select one grade</option>
            <option>1st Grade</option>
            <option>2nd Grade</option>
            <option>3rd Grade</option>
            <option>4th Grade</option>
          </select>
        </div>
        </label><br>

        <label class="checkbox" for="active">active</label>
        <input type="checkbox" id="active" v-model="students.active"/><br><br>

      <button v-on:click="saveStudent()">Save student</button>
      <button @:click="clearStudent()">Delete Student</button>  <!-- Event binding shortcut @-->
      <div>
        <p><pre>{{ message }}</pre></p>
      </div>
  </div>
</template>

<script>

export default {
  name: "HelloWorld",
  data() {
    return {
      github: "https://github.com/Jorge85015?tab=repositories",
      twitter: "https://twitter.com/home",
      students: {
        id: 1,
        name: "Jorge",
        surname: "Quinonez",
        age: 19,
        carreer: "Software Engineer",
        nationality: "Guatemala",
        eyesColor: "",
        grade: "",
        active: true,
      },
      message: 'Student information:',
    }
  },
  methods: {
    clearStudent() {
      this.message = '';
    },
    saveStudent() {
      // This only updates when you click the save button
      this.message = JSON.stringify(this.students, null, '\n ');
    },
  },
}
</script>

<style>
p {
  font-weight: bold;
}

.colored-line {
  width: 160px;
  height: 8px;
  border: 1px #dbdbdb solid;
  margin: 8px 0;
}
</style>




      //   {
      //     id: 2,
      //     name: "Qory",
      //     surname: "Centeno",
      //     age: 21,
      //     carreer: "Psicology",
      //     nationality: "Peru",
      //     eyesColor: "",
      //     grade: "",
      //     active: true,
      //   },
      //   {
      //     id: 3,
      //     name: "Tomi",
      //     surname: "Marcelo",
      //     age: 19,
      //     carreer: "Arquitecture",
      //     nationality: "Spain",
      //     eyesColor: "",
      //     grade: "",
      //     active: false,
      //   }