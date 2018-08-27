<template>
    <li>
        {{ pokemon_species.name }} color {{ name }}
    </li>
</template>

<script>
export default {
  props: {
    color: Object
  }
};
</script>

<style>

</style>
