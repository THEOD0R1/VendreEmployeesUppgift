<script setup>
import EmployeeCards from './components/EmployeeCards.vue'
import VendreEmployeesTitle from './components/VendreEmployeesTitle.vue'
</script>

<template>
  <header>
    <VendreEmployeesTitle />
  </header>
  <main>
    <section class="employeeCardsContainer">
      <Suspense>
        <template #default>
          <EmployeeCards />
        </template>
        <template #fallback>
          <div class="loading"></div>
        </template>
      </Suspense>
    </section>
  </main>
</template>

<style scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
}

.employeeCardsContainer {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.loading {
  position: relative;
  height: 100px;
  width: 100px;
  border-radius: 50%;
  border: solid gray 10px;
  border-left: #5333ed solid 10px;
  animation: loader 1500ms linear infinite;
}
@keyframes loader {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>
