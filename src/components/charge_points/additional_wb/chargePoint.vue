<template>
  <div class="charge-point-additional-wb">
    <openwb-base-text-input
      title="IP oder Hostname"
      subtype="host"
      required
      :model-value="chargePoint.configuration.ip_address"
      @update:model-value="updateConfiguration($event, 'configuration.ip_address')"
    />
    <openwb-base-text-input
      title="Token"
      required
      :model-value="chargePoint.configuration.token"
      @update:model-value="updateConfiguration($event, 'configuration.token')"
    />
  </div>
</template>

<script>
import ChargePointConfigMixin from "../ChargePointConfigMixin.vue";

export default {
  name: "ChargePointAdditionalWB",
  mixins: [ChargePointConfigMixin],
};
</script>
