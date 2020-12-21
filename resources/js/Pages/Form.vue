<template>
  <app-layout>
    <div class="flex items-center h-screen w-full bg-teal-lighter">
      <div class="w-full bg-white rounded shadow-lg p-8 m-4">
        <h1 class="block w-full text-center text-grey-darkest text-xl mb-6">
          Añadir Producto
        </h1>
        <form @submit.prevent="submit" class="mb-6">
          <div class="flex flex-col mb-4">
            <label
              class="mb-2 uppercase font-bold text-lg text-grey-darkest"
              for="name"
              >Nombre:</label
            >
            <input
              id="name"
              v-model="form.name"
              class="border py-2 px-3 text-grey-darkest"
            />
            <div v-if="errors.name" class="bg-red-200">El Nombre es Requerido</div>
          </div>
          <div class="flex flex-col mb-4">
            <label
              class="mb-2 uppercase font-bold text-lg text-grey-darkest"
              for="price"
              >Precio:</label
            >
            <input
              id="price"
              v-model="form.price"
              class="border py-2 px-3 text-grey-darkest"
            />
            <div v-if="errors.price" class="bg-red-200">El Precio es Requerido</div>
          </div>
          <button
            type="submit"
            class="block bg-blue-500 hover:bg-blue-800 text-white uppercase text-lg mx-auto p-4 rounded"
          >
            Añadir
          </button>
        </form>
      </div>
    </div>
  </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
export default {
  components: {
    AppLayout,
  },
  props: {
    errors: Object,
  },
  data() {
    return {
      form: {
        name: null,
        price: null,
      },
    };
  },
  methods: {
    submit() {
      this.$inertia.post(route('products.store'), this.form);
    },
  },
};
</script>