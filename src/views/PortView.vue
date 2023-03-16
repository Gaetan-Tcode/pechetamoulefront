<template>

  <main>
    <template v-if="dataApi">

<!--      <h1 class="text-3xl font-bold">-->
<!--        Titre : {{ dataApi["name"] }}-->
<!--      </h1>-->
<!--      <h2>Matin</h2>-->
<!--      <p>Coef : {{ dataApi["tides"][0]["coefficient"]}}</p>-->
<!--      <p>Hauteur max : {{ dataApi["tides"][0]["highHeight"]}} Heure : {{ dataApi["tides"][0]["highHour"]}}</p>-->
<!--      <p>Hauteur min : {{ dataApi["tides"][0]["lowHeight"]}} Heure : {{ dataApi["tides"][0]["lowHour"]}}</p>-->
<!--      <h2>Après-midi</h2>-->
<!--      <p>Coef : {{ dataApi["tides"][1]["coefficient"]}}</p>-->
<!--      <p>Hauteur max : {{ dataApi["tides"][1]["highHeight"]}} Heure : {{ dataApi["tides"][1]["highHour"]}}</p>-->
<!--      <p>Hauteur min : {{ dataApi["tides"][1]["lowHeight"]}} Heure : {{ dataApi["tides"][1]["lowHour"]}}</p>-->



      <div class="flex justify-between">
        <h1>{{ dataApi["name"] }}</h1>
        <h1 class="ml-auto">Aujoud'hui</h1>
      </div>

      <div class="flex-1  p-6">
        <div class="flex flex-col gap-2">
          <table class="w-full sm:w-1/2 m-auto">
            <caption class="text-xl font-semibold bg-blue-600 text-white py-2 px-4 border-white ">Matin</caption>
            <thead class="hidden sm:table-header-group">
            <tr class="border-white">
              <th class="px-4 py-2 bg-blue-600 text-white border-white">Coeff.</th>
              <th class="px-4 py-2 border-white bg-blue-300">Hauteur Max</th>
              <th class="px-4 py-2 border-white bg-blue-300">Hauteur Min</th>
            </tr>
            </thead>
            <tbody class="table-row-group">
            <tr class="border-white">
              <td class="border px-4 py-2 border-white bg-blue-300" rowspan="2">{{ dataApi["tides"][0]["coefficient"]}}</td>
              <td class="border px-4 py-2 border-white bg-blue-300">{{ dataApi["tides"][0]["highHeight"]}}</td>
              <td class="border px-4 py-2 border-white bg-blue-300">{{ dataApi["tides"][0]["lowHeight"]}}</td>
            </tr>
            <tr class="border-white">
              <td class="border px-4 py-2 border-white bg-blue-300">{{ dataApi["tides"][0]["highHour"]}}</td>
              <td class="border px-4 py-2 border-white bg-blue-300"> {{ dataApi["tides"][0]["lowHour"]}}</td>
            </tr>
            </tbody>
          </table>
          <table class="w-full sm:w-1/2 m-auto">
            <caption class="text-xl font-semibold bg-blue-600 text-white py-2 px-4 border-white ">Après-midi</caption>
            <thead class="hidden sm:table-header-group">
            <tr class="border-white">
              <th class="px-4 py-2 bg-blue-600 text-white border-white">Coeff.</th>
              <th class="px-4 py-2 border-white bg-blue-300">Hauteur Max</th>
              <th class="px-4 py-2 border-white bg-blue-300">Hauteur Min</th>
            </tr>
            </thead>
            <tbody class="table-row-group">
            <tr class="border-white">
              <td class="border px-4 py-2 border-white bg-blue-300" rowspan="2">{{ dataApi["tides"][1]["coefficient"]}}</td>
              <td class="border px-4 py-2 border-white bg-blue-300">{{ dataApi["tides"][1]["highHeight"]}}</td>
              <td class="border px-4 py-2 border-white bg-blue-300">{{ dataApi["tides"][1]["lowHeight"]}}</td>
            </tr>
            <tr class="border-white">
              <td class="border px-4 py-2 border-white bg-blue-300">{{ dataApi["tides"][1]["highHour"]}}</td>
              <td class="border px-4 py-2 border-white bg-blue-300"> {{ dataApi["tides"][1]["lowHour"]}}</td>
            </tr>
            </tbody>
          </table>
        </div>
      </div>
    </template>
  </main>

</template>


<script setup>
import {onMounted, ref} from "vue";
import {useRoute} from 'vue-router';
const route = useRoute();
const dataApi = ref();

onMounted(async () => {

      const response = await fetch(`http://192.168.50.113:8000/api/harbors/${route.params.id}`);
      if (response.ok) {
        const data = await response.json();
        dataApi.value = data;
      }
    }
);




</script>