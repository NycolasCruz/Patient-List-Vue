<template>
  <div class="card card-flush">
    <div class="card-header flex-column pt-10 pb-10">
      <div
        class="align-items-center d-flex flex-start justify-content-start mb-6"
      >
        <i class="fa-solid fa-user fs-3tx text-primary me-3"></i>
        <h1 class="card-title fs-2 ps-2">Lista de Pacientes</h1>
      </div>
      <Table />
      <Pagination />
    </div>
  </div>
</template>

<script>
import Table from "@/components/created/table/Table";
import Pagination from "@/components/created/pagination/Pagination";

export default {
  name: "Dashboard",
  components: {
    Table,
    Pagination,
  },
};
</script>
