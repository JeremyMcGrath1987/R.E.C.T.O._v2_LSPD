<template>
  <ul class="flex mb-4">
    <li class="mr-6">
      <a
        @click="goto('File')"
        class="hover:text-blue-800 cursor-pointer"
        :class="{
          'border-b-2 border-recto-light': active === 'antecedentes'
        }"
        >Antecedentes</a
      >
    </li>
    <li class="mr-6">
      <a
        @click="goto('Notes')"
        class="hover:text-blue-800 cursor-pointer"
        :class="{ 'border-b-2 border-recto-light': active === 'notas' }"
        >Notas</a
      >
    </li>
    <li class="mr-6">
      <a
        @click="goto('Debts')"
        class="hover:text-blue-800 cursor-pointer"
        :class="{
          'border-b-2 border-recto-light': active === 'deudas'
        }"
        >Deudas</a
      >
    </li>
    <li class="mr-6">
      <a
        @click="goto('Properties')"
        class="hover:text-blue-800 cursor-pointer"
        :class="{
          'border-b-2 border-recto-light': active === 'propiedades'
        }"
        >Propiedades</a
      >
    </li>
    <li class="mr-6">
      <a
        @click="goto('Admin')"
        class="hover:text-blue-800 cursor-pointer"
        :class="{
          'border-b-2 border-recto-light': active === 'admin'
        }"
        >Administración</a
      >
    </li>
    <li class="ml-auto border border-recto-light py-1 px-2">
      <a class="hover:text-blue-800 cursor-pointer" @click="goto('Note')"
        >Añadir nota</a
      >
    </li>
    <li class="ml-1 border border-recto-light py-1 px-2">
      <a class="hover:text-blue-800 cursor-pointer" @click="goto('Debt')"
        >Añadir deuda</a
      >
    </li>
    <li
      class="ml-1 border border-recto-light bg-recto-light text-white py-1 px-2"
    >
      <a class="hover:text-blue-800 cursor-pointer" @click="goto('Report')"
        >Denunciar</a
      >
    </li>
  </ul>
</template>
<script>
export default {
  name: "fileMenu",
  props: {
    active: {
      type: String,
      required: true
    }
  },
  methods: {
    goto: async function(route) {
      if (route !== this.$route.name) {
        await this.$store.dispatch("loadingScreen/ISLOADING", true);
        await this.$router.push({ name: route });
      }
    }
  }
};
</script>
