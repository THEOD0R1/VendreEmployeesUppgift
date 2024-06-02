<script setup>
defineProps({
  switchPage: {
    type: Function
  },
  vendreEmployees: {}
})
</script>

<template>
  <section class="paginering_contaner">
    <article class="paginering_page" :key="page" v-for="page in vendreEmployees.total_pages">
      <button
        class="select_pag_btn"
        :class="{ page_selected: vendreEmployees.page === page }"
        @click="switchPage(page)"
      >
        {{ page }}
      </button>
    </article>
  </section>
</template>

<style scoped>
.paginering_contaner {
  display: flex;
  margin: 30px;
}
.paginering_page {
  margin: 5%;
}

.page_selected {
  text-decoration: underline;
}
</style>
