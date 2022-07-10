<template>
  <div id="kt_header" class="header align-items-stretch bg-info">
    <div
      :class="{
        'container-fluid': headerWidthFluid,
        'container-xxl': !headerWidthFluid,
      }"
      class="d-flex align-items-stretch justify-content-between"
    >
      <div
        class="d-flex align-items-center d-lg-none ms-n3 me-1"
        title="Show aside menu"
      >
        <div
          class="btn btn-icon btn-active-light-primary"
          id="kt_aside_mobile_toggle"
        >
          <span class="svg-icon svg-icon-2x mt-1">
            <inline-svg src="media/icons/duotune/abstract/abs015.svg" />
          </span>
        </div>
      </div>

      <div class="d-flex align-items-center flex-grow-1 flex-lg-grow-0">
        <a href="#" class="d-lg-none">
          <img alt="Logo" src="media/logos/logo-2.svg" class="h-30px" />
        </a>
      </div>

      <div
        class="d-flex flex-center justify-content-between flex-lg-grow-1 bg-info"
      >
        <div class="d-flex align-items-stretch" id="kt_header_menu_nav">
          <KTMenu></KTMenu>
        </div>

        <div class="d-flex align-items-stretch flex-shrink-0">
          <KTTopbar></KTTopbar>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import KTTopbar from "@/layout/header/Topbar.vue";
import KTMenu from "@/layout/header/Menu.vue";

import {
  headerWidthFluid,
  headerLeft,
  asideDisplay,
} from "@/core/helpers/config";

export default defineComponent({
  name: "KTHeader",
  props: {
    title: String,
  },
  components: {
    KTTopbar,
    KTMenu,
  },
  setup() {
    return {
      headerWidthFluid,
      headerLeft,
      asideDisplay,
    };
  },
});
</script>

<style scoped>
#kt_header {
  margin-left: -21rem;
}
</style>
