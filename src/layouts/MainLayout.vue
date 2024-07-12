<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="bg-purple text-white">

        <q-btn flat round dense icon="assignment_ind" />
        <q-toolbar-title>
          Markdown Table Generator
        </q-toolbar-title>
        <q-btn flat round dense icon="apps" class="q-mr-xs" />
        <q-btn flat round dense icon="more_vert" />

        <div>Markdown Table Generator v1.0.0</div>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
defineOptions({
  name: 'MainLayout'
})
</script>
