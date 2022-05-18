import AppLayout from '@/Layouts/AppLayout.vue';
<template>
  <app-layout>
    <template  #header>
      <h1
        class="
          text-center
          text-2x1
          font-bold
          leading-7
          uppercase
          text-gray-300
          sm:text-3x1
          sm:truncate
          py-4
          bg-gradient
          from-indigo-500
          to-indigo-800
        "
      >
        Mostrar los productos
      </h1>
    </template>

    <div class="py-12">
      <div class="max-w-7x1 max-auto sm px-6 lg:px-8">
        <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
          <inertia-link
            :href="route('productos.create')"
            class="
              flex-shrink-0
              bg-blue-500
              text-white text-base
              font-semibold
              py-2
              px-4
              rounded-lg
              shadow-md
              hover:bg-blue-700
              focus:outline-none focus:ring-offset-blue-200
            "
            type="button"
          >
            Nuevo
          </inertia-link>

          <table
            class="
              rounded-t-lg
              mt-5
              min-w-full
              mx-auto
              bg-gray-800
              text-gray-100
            "
          >
            <thead>
              <th
                scope="col"
                class="
                  px-6
                  py-3
                  text-left text-xs
                  font-bold
                  text-gray-100
                  uppercase
                  tracking-wide
                "
              >
                Descripción
              </th>
              <th
                scope="col"
                class="
                  px-6
                  py-3
                  text-left text-xs
                  font-bold
                  text-gray-100
                  uppercase
                  tracking-wide
                "
              >
                Precio
              </th>
              <th
                scope="col"
                class="
                  px-6
                  py-3
                  text-center text-xs
                  font-bold
                  text-gray-100
                  uppercase
                  tracking-wide
                "
              >
                Acciones
              </th>
            </thead>
            <tbody class="bg-gray-700 border-b border-gray-600 text-gray-200">
              <tr v-for="producto in productos" :key="producto.id">
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="flex items-center">
                    <div class="ml-4">
                      <div class="text-sm font-medium">
                        {{ producto.descripcion }}
                      </div>
                    </div>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="text-sm"><span>$ </span>{{ producto.precio }}</div>
                </td>
                <td class="flex m-2">
                  <inertia-link :href="route('productos.edit', producto.id)" class="flex-shrink-0 bg-purple-600 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2 focus:ring-offset-purple-200" type="button">
                      Editar
                  </inertia-link>
                  <inertia-link :href="route('productos.destroy', producto.id)" class="flex-shrink-0 bg-pink-600 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-pink-700 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:ring-offset-2 focus:ring-offset-pink-200" type="button">
                      Eliminar
                  </inertia-link>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
import { Inertia } from "@inertiajs/inertia";
import { Link } from '@inertiajs/inertia-vue3';
export default {
  props: {
    productos: Array,
  },
  components: {
    AppLayout,
  },
};
</script>