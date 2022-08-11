<template>
  <div class="header bg-indigo-400 text-2xl text-white font-bold text-center p-4">
    <h1><i class="fa-solid fa-virus text-red-900 mx-2"></i>{{ appName }}<i class="fa-solid fa-virus text-red-900 mx-2"></i></h1>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: ['appName']
}
</script>
