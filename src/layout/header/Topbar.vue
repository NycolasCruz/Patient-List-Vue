<template>
  <div class="d-flex align-items-stretch flex-shrink-0">
    <div
      class="d-flex align-items-center ms-1 ms-lg-3"
      id="kt_header_user_menu_toggle"
    >
      <div
        class="cursor-pointer symbol symbol-30px symbol-md-40px"
        data-kt-menu-trigger="click"
        data-kt-menu-attach="parent"
        data-kt-menu-placement="bottom-end"
        data-kt-menu-flip="bottom"
      >
        <img src="media/avatars/blank.png" alt="metronic" />
      </div>
      <KTUserMenu></KTUserMenu>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import KTUserMenu from "@/layout/header/partials/UserMenu.vue";

export default defineComponent({
  name: "topbar",
  components: {
    KTUserMenu,
  },
});
</script>
