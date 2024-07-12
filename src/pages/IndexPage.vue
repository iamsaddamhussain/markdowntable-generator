<template>
  <q-page class="q-pa-sm q-ml-xl">
    <div class="row">
      <q-markup-table separator="vertical" class="col-10">
        <thead>
          <tr>
            <th></th>
            <th class="text-left" v-for="(column, index) in columns" :key="index">{{ column }}</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(number, rowIndex) in numbers" :key="rowIndex">
            <td class="text-left">{{ number.id }}</td>
            <td class="text-left" v-for="(column, colIndex) in columns" :key="colIndex">
              <q-input filled dense v-model="numbers[rowIndex][column]" />
            </td>
          </tr>
        </tbody>
      </q-markup-table>
    </div>
    <div class="row q-mt-md col-10">
      <div class="col-9"></div>
      <div class="col-3 justify-end">
        <q-btn color="purple" no-caps icon="settings_suggest" label="Generate" @click="generateMarkDown" />
      </div>
    </div>

    <div class="row q-mt-md">
      <q-input filled type="textarea" class="col-10" v-model="generatedContent" />
    </div>
  </q-page>
</template>

<script setup>
import { ref } from "vue";

defineOptions({
  name: 'IndexPage'
});

const columns = ref(['A', 'B', 'C', 'D', 'E', 'F'])
const numbers = ref(initialiseNumber(5))
const generatedContent = ref('')

function initialiseNumber(rowCount) {
  return Array.from({ length: rowCount }, (_, index) => {
    const row = { id: index + 1 };
    columns.value.forEach(column => {
      row[column] = ''
    })
    return row
  })
}

function generateMarkDown() {
  generatedContent.value = 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur a interdum dui, eget faucibus massa. Praesent sed lorem eu eros sagittis cursus ac non justo. Suspendisse convallis, purus vel tristique eleifend, urna quam vulputate augue, at consectetur nunc ex sed enim. Nulla facilisi. Donec dapibus, leo id venenatis fringilla, eros turpis consequat est, eu congue justo massa id elit. Nulla non quam id libero tempus bibendum vel vitae odio. Interdum et malesuada fames ac ante ipsum primis in faucibus. Aliquam quis lacus nec sapien eleifend dictum. Vivamus ante lorem, maximus quis dictum sit amet, sodales id turpis. Maecenas consequat risus ut est sollicitudin, id congue eros interdum. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.';
}

</script>
