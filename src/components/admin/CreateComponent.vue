<template>
  <div class="row justify-content-center">
    <div class="col-md-6">
      <h3 class="text-center">Registrar Administrador</h3>




      <form @submit.prevent="handleSubmitForm">
        <div class="form-group">
          <label>Nombre</label>
          <input type="text" class="form-control" v-model="student.name"
            required
          />
        </div>

        <div class="form-group">
          <label>Email</label>
          <input
            type="email" class="form-control"
            v-model="student.email"
            required
          />
        </div>

        <div class="form-group">
          <label>Telefono</label>
          <input
            type="text"
            class="form-control"
            v-model="student.phone"
            required
          />
        </div>

        <br/>

        <div class="form-group">
          <button class="btn btn-info btn-block">Crear</button>
        </div>
      </form>
    </div>
  </div>










</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      student: {
        name: "",
        email: "",
        phone: "",
      },
    };
  },
  methods: {
    handleSubmitForm() {
      let apiURL = "http://localhost:4000/api/create-student";

      axios
        .post(apiURL, this.student)
        .then(() => {
          this.$router.push("/view");
          this.student = {
            name: "",
            email: "",
            phone: "",
          };
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
