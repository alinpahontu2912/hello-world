<template>
  <div id="data" class="container well center">
    <form class="dataForm" @submit.prevent="addPerson">
      <div class="form-group">
        <label for="firstNameInput">Prenume:</label>
        <input v-model="firstName" class="form-control" id="firstNameInput" placeholder="Introdu prenume">
      </div>
      <div class="form-group">
        <label for="lastNameInput">Nume:</label>
        <input v-model="lastName" class="form-control" id="lastNameInput" placeholder="Introdu nume">
      </div>
      <div class="form-group">
        <label for="datepicker">Data nasterii:</label>
        <input type="date" v-model="birthDate" class="form-control" id="datepicker">
      </div>
      <div class="d-flex justify-content-center">
        <button type="submit" class="btn btn-primary btn-large">Submit</button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const lastName = ref('')
const firstName = ref('')
const birthDate = ref('')
// eslint-disable-next-line
const emit = defineEmits(['newPerson'])



function addPerson() {
  if (firstName.value !== '' && lastName.value !== '' && birthDate.value !== '') {
    emit('newPerson', firstName.value, lastName.value, birthDate.value)
    firstName.value = ''
    lastName.value = ''
    birthDate.value = ''
  }
  else {
    alert('Introdu toate datele!')
  }
}
</script>


<style>
#data .dataForm {

  width: "85vw";
  padding: 3em;

}
</style>