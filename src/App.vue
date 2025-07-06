<template>
  <h1>{{ greeting }}</h1>
  <p>Comment allez vous</p>
</template>

<script setup>
const name = 'APDLC ASBL'
const greeting = `Bienvenue à ${name}!`
</script>

<style>
h1{
  color: orangered;
}
</style>
