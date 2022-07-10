<template>
  <KTLoader v-if="loaderEnabled" :logo="loaderLogo" />

  <div class="page d-flex flex-row flex-column-fluid">
    <div id="kt_wrapper" class="d-flex flex-column flex-row-fluid wrapper ps-0">
      <KTHeader :title="pageTitle" />

      <div
        id="kt_content"
        class="content d-flex flex-column flex-column-fluid pt-0 mt-n3"
      >
        <div class="post d-flex flex-column-fluid">
          <div
            id="kt_content_container"
            :class="{
              'container-fluid': contentWidthFluid,
              'container-xxl': !contentWidthFluid,
            }"
          >
            <router-view />
          </div>
        </div>
      </div>
      <KTFooter />
    </div>
  </div>
  <KTScrollTop />
  <KTDrawerMessenger />
  <KTUserMenu />
  <KTCreateApp />

  <KTDemosDrawer />
  <KTHelpDrawer />
</template>

<script lang="ts">
import { defineComponent, computed, onMounted, watch, nextTick } from "vue";
import { useStore } from "vuex";
import { useRoute, useRouter } from "vue-router";
import KTHeader from "@/layout/header/Header.vue";
import KTFooter from "@/layout/footer/Footer.vue";
import HtmlClass from "@/core/services/LayoutService";
import KTScrollTop from "@/layout/extras/ScrollTop.vue";
import KTUserMenu from "@/layout/header/partials/ActivityDrawer.vue";
import KTLoader from "@/components/Loader.vue";
import KTCreateApp from "@/components/modals/wizards/CreateAppModal.vue";
import KTDemosDrawer from "@/layout/extras/DemosDrawer.vue";
import KTHelpDrawer from "@/layout/extras/HelpDrawer.vue";
import KTDrawerMessenger from "@/layout/extras/MessengerDrawer.vue";
import { Actions } from "@/store/enums/StoreEnums";
import { MenuComponent } from "@/assets/ts/components";
import { removeModalBackdrop } from "@/core/helpers/dom";
import { reinitializeComponents } from "@/core/plugins/keenthemes";
import {
  toolbarDisplay,
  loaderEnabled,
  contentWidthFluid,
  loaderLogo,
  asideEnabled,
  subheaderDisplay,
  themeLightLogo,
  themeDarkLogo,
} from "@/core/helpers/config";

export default defineComponent({
  name: "Layout",
  components: {
    KTHeader,
    KTFooter,
    KTScrollTop,
    KTCreateApp,
    KTUserMenu,
    KTDemosDrawer,
    KTHelpDrawer,
    KTDrawerMessenger,
    KTLoader,
  },
  setup() {
    const store = useStore();
    const route = useRoute();
    const router = useRouter();

    // show page loading
    store.dispatch(Actions.ADD_BODY_CLASSNAME, "page-loading");

    // initialize html element classes
    HtmlClass.init();

    const pageTitle = computed(() => {
      return store.getters.pageTitle;
    });

    const breadcrumbs = computed(() => {
      return store.getters.pageBreadcrumbPath;
    });

    onMounted(() => {
      //check if current user is authenticated
      if (!store.getters.isUserAuthenticated) {
        router.push({ name: "sign-in" });
      }

      nextTick(() => {
        reinitializeComponents();
      });

      // Simulate the delay page loading
      setTimeout(() => {
        // Remove page loader after some time
        store.dispatch(Actions.REMOVE_BODY_CLASSNAME, "page-loading");
      }, 500);
    });

    watch(
      () => route.path,
      () => {
        MenuComponent.hideDropdowns(undefined);

        // check if current user is authenticated
        if (!store.getters.isUserAuthenticated) {
          router.push({ name: "sign-in" });
        }

        nextTick(() => {
          reinitializeComponents();
        });
        removeModalBackdrop();
      }
    );

    return {
      toolbarDisplay,
      loaderEnabled,
      contentWidthFluid,
      loaderLogo,
      asideEnabled,
      subheaderDisplay,
      pageTitle,
      breadcrumbs,
      themeLightLogo,
      themeDarkLogo,
    };
  },
});
</script>
