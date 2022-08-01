<template>
  <div class="w-lg-500px bg-white rounded shadow-sm p-10 p-lg-15 mx-auto">
    <Form
      class="form w-100"
      id="kt_login_signin_form"
      @submit="onSubmitLogin"
      :validation-schema="login"
    >
      <div class="text-center mb-10">
        <h1 class="text-dark mb-3">Entre Com Sua Conta</h1>

        <div class="text-gray-400 fw-bold fs-4">
          Novo Aqui? Utilize o email: admin@demo.com e a senha: demo
        </div>
      </div>

      <div class="fv-row mb-10">
        <label class="form-label fs-6 fw-bolder text-dark">Email</label>

        <Field
          class="form-control form-control-lg form-control-solid"
          type="text"
          name="email"
          autocomplete="off"
        />
      </div>

      <div class="fv-row mb-10">
        <div class="d-flex flex-stack mb-2">
          <label class="form-label fw-bolder text-dark fs-6 mb-0">Senha</label>
        </div>

        <Field
          class="form-control form-control-lg form-control-solid"
          type="password"
          name="password"
          autocomplete="off"
        />
      </div>

      <div class="text-center">
        <button
          type="submit"
          ref="submitButton"
          id="kt_sign_in_submit"
          class="btn btn-lg btn-primary btn-hover-rise w-100"
        >
          <span class="indicator-label"> Continue </span>

          <span class="indicator-progress">
            Aguarde...
            <span
              class="spinner-border spinner-border-sm align-middle ms-2"
            ></span>
          </span>
        </button>
      </div>
    </Form>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { ErrorMessage, Field, Form } from "vee-validate";
import { Actions } from "@/store/enums/StoreEnums";
import { useStore } from "vuex";
import { useRouter } from "vue-router";
import Swal from "sweetalert2/dist/sweetalert2.min.js";
import * as Yup from "yup";

export default defineComponent({
  name: "sign-in",
  components: {
    Field,
    Form,
  },
  setup() {
    const store = useStore();
    const router = useRouter();

    const submitButton = ref<HTMLButtonElement | null>(null);

    //Create form validation object
    const login = Yup.object().shape({
      email: Yup.string().email().required().label("Email"),
      password: Yup.string().min(4).required().label("Password"),
    });

    //Form submit function
    const onSubmitLogin = async (values) => {
      // Clear existing errors
      store.dispatch(Actions.LOGOUT);

      if (submitButton.value) {
        // eslint-disable-next-line
        submitButton.value!.disabled = true;
        // Activate indicator
        submitButton.value.setAttribute("data-kt-indicator", "on");
      }

      // Send login request
      await store.dispatch(Actions.LOGIN, values);
      const [errorName] = Object.keys(store.getters.getErrors);
      const error = store.getters.getErrors[errorName];

      if (!error) {
        Swal.fire({
          text: "Login Bem Sucedido!",
          icon: "success",
          buttonsStyling: false,
          confirmButtonText: "Prosseguir",
          customClass: {
            confirmButton: "btn fw-bold btn-light-primary",
          },
        }).then(function () {
          // Go to page after successfully login
          router.push({ name: "dashboard" });
        });
      } else {
        Swal.fire({
          text: "Dados Incorretos",
          icon: "error",
          buttonsStyling: false,
          confirmButtonText: "Tentar Novamente",
          customClass: {
            confirmButton: "btn fw-bold btn-light-danger",
          },
        });
      }

      //Deactivate indicator
      submitButton.value?.removeAttribute("data-kt-indicator");
      // eslint-disable-next-line
      submitButton.value!.disabled = false;
    };

    return {
      onSubmitLogin,
      login,
      submitButton,
    };
  },
});
</script>
