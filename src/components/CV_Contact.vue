<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
</script>

<template>
  <div>
    <slot name="email"></slot>
  </div>
  <div>
    <slot name="localisation"></slot>
  </div>
  <div>
    <slot name="phonenumber"></slot>
  </div>
  <div>
    <slot name="mobility"></slot>
  </div>

</template>