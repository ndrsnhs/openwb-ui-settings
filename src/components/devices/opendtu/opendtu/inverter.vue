<template>
  <!-- Einstellungen sind vorbelegt und sollen nicht im UI angezeigt werden -->
  <div class="device-opendtu-inverter"></div>
</template>

<script>
import ComponentConfigMixin from "../../ComponentConfigMixin.vue";

export default {
  name: "DeviceOpenDTUInverter",
  mixins: [ComponentConfigMixin],
};
</script>
