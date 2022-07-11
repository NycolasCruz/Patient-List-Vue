<template>
  <div class="d-flex justify-content-between align-items-center mt-1">
    <span class="text-muted"> Mostrando 10 de 106 registros </span>
    <ul class="pagination">
      <li class="page-item" style="cursor: default">
        <button class="page-link">
          <i class="previous"></i>
        </button>
      </li>
      <li class="page-item active"><a class="page-link">1</a></li>
      <li class="page-item"><a class="page-link">2</a></li>
      <li class="page-item"><a class="page-link">3</a></li>
      <li class="page-item"><a class="page-link">4</a></li>
      <li class="page-item"><a class="page-link">5</a></li>
      <li class="page-item" style="cursor: default">
        <button class="page-link">
          <i class="next"></i>
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Pagination",
};
</script>

<style></style>
