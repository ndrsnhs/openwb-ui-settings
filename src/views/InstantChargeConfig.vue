<template>
  <div class="instantChargeConfig">
    <form name="instantChargeConfigForm">
      <openwb-base-card title="Phasenumschaltung">
        <div v-if="$store.state.mqtt['openWB/general/extern'] === true">
          <openwb-base-alert subtype="info">
            Diese Einstellungen sind nicht verfügbar, solange sich diese openWB im Steuerungsmodus "secondary" befindet.
          </openwb-base-alert>
        </div>
        <div v-else>
          <openwb-base-button-group-input
            title="Anzahl Phasen"
            :buttons="[
              { buttonValue: 1, text: '1' },
              { buttonValue: 3, text: 'Maximum' },
            ]"
            :model-value="$store.state.mqtt['openWB/general/chargemode_config/instant_charging/phases_to_use']"
            @update:model-value="updateState('openWB/general/chargemode_config/instant_charging/phases_to_use', $event)"
          >
            <template #help>
              Hier kann eingestellt werden, ob Ladevorgänge im Modus "Sofortladen" mit nur einer Phase oder dem
              möglichen Maximum in Abhängigkeit der "Ladepunkt"- und "Fahrzeug"-Einstellungen durchgeführt werden.
              Voraussetzung ist die verbaute Umschaltmöglichkeit zwischen 1- und 3-phasig (s.g. 1p3p).
            </template>
          </openwb-base-button-group-input>
        </div>
      </openwb-base-card>
      <openwb-base-submit-buttons
        form-name="instantChargeConfigForm"
        @save="$emit('save')"
        @reset="$emit('reset')"
        @defaults="$emit('defaults')"
      />
    </form>
  </div>
</template>

<script>
import ComponentState from "../components/mixins/ComponentState.vue";

export default {
  name: "OpenwbInstantChargeConfigView",
  mixins: [ComponentState],
  emits: ["save", "reset", "defaults"],
  data() {
    return {
      mqttTopicsToSubscribe: [
        "openWB/general/extern",
        "openWB/general/chargemode_config/instant_charging/phases_to_use",
      ],
    };
  },
};
</script>
