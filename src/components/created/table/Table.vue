<template>
  <table class="table table-row-bordered align-middle gy-5 mb-6">
    <thead>
      <tr class="fw-bold fs-6 text-gray-800">
        <th class="text-center">#</th>
        <th>Nome</th>
        <th>Email</th>
        <th>CPF</th>
        <th class="text-end">Ações</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(data, index) in dataList" :key="index">
        <td class="text-center">{{ index + 1 }}</td>
        <td>{{ data.name }}</td>
        <td>{{ data.email }}</td>
        <td>{{ data.cpf }}</td>
        <td class="text-end">
          <button
            class="btn btn-primary btn-icon btn-hover-rise me-2 show-button"
          >
            <i class="fas fa-eye"></i>
          </button>
          <button class="btn btn-warning btn-icon btn-hover-rise edit-button">
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
</template>

<script>
export default {
  name: "Table",
  setup() {
    const dataList = [
      {
        name: "ROBERTO DE ALMEIDA PAIVA",
        email: "roberto@agenciasdi.com.br",
        cpf: "584.336.390-21",
      },
      {
        name: "LUCAS RODRIGUES DA SILVA",
        email: "lucas@hotmail.com",
        cpf: "876.876.876-76",
      },
      {
        name: "JOAO PAULO DE SOUZA",
        email: "paulo@gmail.com",
        cpf: "448.933.540-00",
      },
      {
        name: "ALESSANDRA DE SOUSA MELO",
        email: "ale.melo@gmail.com",
        cpf: "876.876.876-76",
      },
      {
        name: "MOREIRA DUTRA DA SILVA",
        email: "dutra@hotmail.com",
        cpf: "563.678.141-76",
      },
      {
        name: "ROBERTO DE ALMEIDA PAIVA",
        email: "roberto@agenciasdi.com.br",
        cpf: "584.336.390-21",
      },
      {
        name: "LUCAS RODRIGUES DA SILVA",
        email: "lucas@hotmail.com",
        cpf: "876.876.876-76",
      },
      {
        name: "JOAO PAULO DE SOUZA",
        email: "paulo@gmail.com",
        cpf: "448.933.540-00",
      },
      {
        name: "ALESSANDRA DE SOUSA MELO",
        email: "ale.melo@gmail.com",
        cpf: "876.876.876-76",
      },
      {
        name: "MOREIRA DUTRA DA SILVA",
        email: "dutra@hotmail.com",
        cpf: "563.678.141-76",
      },
    ];

    return { dataList };
  },
};
</script>

<style></style>
