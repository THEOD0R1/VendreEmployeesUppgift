<script setup>
import { ref } from 'vue'
import { getApi } from '../api/getApi'
import SelectPaginering from './SelectPaginering.vue'

const vendreEmployeesData = async (pageNo = 1) => {
  return await getApi(`https://reqres.in/api/users?page=${pageNo}`)
}
const vendreEmployees = ref(await vendreEmployeesData())

const switchPage = async (page) => {
  vendreEmployees.value = await vendreEmployeesData(page)
}
</script>

<template>
  <section class="employeeCardsContainer">
    <section
      v-for="(employee, i) in vendreEmployees.data"
      :key="i"
      :employee="employee"
      class="employeeCard"
    >
      <article class="employeeCard_imgContainer">
        <img
          class="employeeCard_img"
          :src="employee.avatar"
          :alt="employee.first_name + ' ' + employee.last_name"
        />
      </article>
      <article class="employeeCard_info">
        <div class="employeeCard_info-name">
          <h2>{{ employee.first_name + ' ' + employee.last_name }}</h2>
        </div>
        <div class="employeeCard_info-email">
          <a :href="'mailto:' + employee.email"> {{ employee.email }}</a>
        </div>
      </article>
    </section>
  </section>
  <SelectPaginering :switchPage="switchPage" :vendreEmployees="vendreEmployees" />
</template>

<style scoped>
.employeeCardsContainer {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  margin-left: 5%;
  margin-right: 5%;
}

.employeeCard {
  display: flex;
  justify-content: center;
  width: 100%;
  margin-top: 20px;
  margin-bottom: 20px;
}

.employeeCard_imgContainer {
  display: flex;
  justify-content: center;
  align-items: center;
}
.employeeCard_img {
  object-fit: cover;
  border-radius: 50%;
  height: 130px;
  width: 130px;
}
.employeeCard_info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: start;
  max-width: 80%;
}

@media (min-width: 1024px) {
  .employeeCard {
    align-items: center;
    max-width: 45%;
    margin-top: 20px;
    margin-bottom: 20px;
  }
}
</style>
