/* eslint-disable */
<template>
  <SubmitForm @newPerson="insertPerson" />
  <DemoGrid :data="gridData" :columns="gridColumns" />
</template>

<script setup>
import SubmitForm from './components/SubmitForm.vue'
import DemoGrid from './components/GridView.vue'
import { ref } from 'vue'

function insertPerson(lastName, firstName, birthDate) {
  gridData.value.push({ Nume: lastName, Prenume: firstName, 'Data Nasterii': birthDate })
}
const gridColumns = ['Nume', 'Prenume', 'Data Nasterii']
const gridData = ref([])
</script>


