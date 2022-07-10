<template>
  <div class="card card-flush">
    <div class="card-header flex-column pt-10 pb-10">
      <div
        class="align-items-center d-flex flex-start justify-content-start mb-6"
      >
        <i class="fa-solid fa-user fs-3tx text-primary me-3"></i>
        <h1 class="card-title fs-2 ps-2">Lista de Pacientes</h1>
      </div>

      <div class="form-label text-muted m-0 mb-4">
        Abaixo poderá ver uma lista de com dados de pacientes feita utilizando o
        framework JavaScript Vue
      </div>

      <table class="table table-row-bordered align-middle gy-5 mb-66">
        <thead>
          <tr class="fw-bold fs-6 text-gray-800">
            <th>Nome</th>
            <th>Email</th>
            <th>CPF</th>
            <th class="text-end">Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>ROBERTO DE ALMEIDA PAIVA</td>
            <td>roberto@agenciasdi.com.br</td>
            <td>584.336.390-21</td>
            <td class="text-end">
              <button
                class="btn btn-primary btn-icon btn-hover-rise me-2 show-button"
              >
                <i class="fas fa-eye"></i>
              </button>
              <button
                class="btn btn-warning btn-icon btn-hover-rise edit-button"
              >
                <i class="fas fa-edit"></i>
              </button>
              <button
                class="btn btn-danger btn-icon btn-hover-rise ms-2 show-button"
              >
                <i class="fas fa-trash"></i>
              </button>
            </td>
          </tr>
        </tbody>
      </table>

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
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
