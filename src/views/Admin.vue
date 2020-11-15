<template>
  <div class="note flex flex-col flex-no-wrap">
    <top-bar />
    <div class="file-details-content flex flex-row">
      <div class="flex flex-wrap p-4">
        <file-image />
      </div>
      <div class="file-content p-4 flex flex-col w-full">
        <file-menu active="admin" />
        <toggle
          v-on:changeStatus="$store.dispatch('TOGGLESTATUS', 'peligroso')"
          :active="peligroso"
          >Peligroso</toggle
        >
        <toggle
          v-on:changeStatus="$store.dispatch('TOGGLESTATUS', 'byc')"
          :active="byc"
          >Búsqueda y captura</toggle
        >
        <toggle
          v-on:changeStatus="$store.dispatch('TOGGLESTATUS', 'lspd')"
          :active="lspd"
          >LSPD</toggle
        >
      </div>
    </div>
  </div>
</template>
<script>
import topBar from "../components/topbar";
import fileMenu from "../components/fileMenu";
import fileImage from "../components/fileImage";
import toggle from "../components/toggle";
import { mapGetters } from "vuex";
export default {
  name: "Admin",
  components: { topBar, fileMenu, fileImage, toggle },
  async mounted() {
    await this.$store.dispatch("loadingScreen/ISLOADING", false);
  },
  computed: {
    ...mapGetters(["peligroso", "byc", "lspd"])
  }
};
</script>
