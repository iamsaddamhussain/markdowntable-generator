<template>
  <q-page class="q-pa-sm q-ml-xl">
    <div class="row">
      <q-markup-table separator="vertical">
        <thead>
          <tr>
            <th class="text-left">A</th>
            <th class="text-right">B</th>
            <th class="text-right">C</th>
            <th class="text-right">D</th>
            <th class="text-right">E</th>
            <th class="text-right">F</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td class="text-left">1</td>
            <td class="text-right">34</td>
            <td class="text-right">6</td>
            <td class="text-right">24</td>
            <td class="text-right">4</td>
            <td class="text-right">87</td>
          </tr>
          <tr>
            <td class="text-left">2</td>
            <td class="text-right">237</td>
            <td class="text-right">9</td>
            <td class="text-right">37</td>
            <td class="text-right">4.3</td>
            <td class="text-right">129</td>
          </tr>
          <tr>
            <td class="text-left">3</td>
            <td class="text-right">262</td>
            <td class="text-right">16</td>
            <td class="text-right">23</td>
            <td class="text-right">6</td>
            <td class="text-right">337</td>
          </tr>
          <tr>
            <td class="text-left">4</td>
            <td class="text-right">305</td>
            <td class="text-right">3.7</td>
            <td class="text-right">67</td>
            <td class="text-right">4.3</td>
            <td class="text-right">413</td>
          </tr>
          <tr>
            <td class="text-left">5</td>
            <td class="text-right">356</td>
            <td class="text-right">16</td>
            <td class="text-right">49</td>
            <td class="text-right">3.9</td>
            <td class="text-right">327</td>
          </tr>
        </tbody>
      </q-markup-table>
    </div>
    <div class="row q-mt-md">
      <q-btn color="purple" label="Generate" />
    </div>

    <div class="row q-mt-md">
      <div class="code-editor">
        <div class="line-numbers">
          <pre>{{ lineNumbers }}</pre>
        </div>
        <textarea v-model="codeSnippet" @input="updateLineNumbers" class="code-input" rows="10"></textarea>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from "vue";

defineOptions({
  name: 'IndexPage'
});

const codeSnippet = ref('')
const lineNumbers = ref('1\n')

function updateLineNumbers() {
  const lines = codeSnippet.value.split('\n').length;
  lineNumbers.value = Array.from({ length: lines }, (_, i) => i + 1).join('\n') + '\n';
}
</script>

<style scoped>
.code-editor {
  display: flex;
  border: 1px solid #ccc;
  border-radius: 4px;
  overflow: hidden;
}

.line-numbers {
  background-color: #f0f0f0;
  padding: 8px;
  text-align: right;
  color: #666;
  user-select: none;
}

.code-input {
  flex-grow: 1;
  border: none;
  padding: 8px;
  resize: none;
  outline: none;
  font-family: monospace;
}
</style>
