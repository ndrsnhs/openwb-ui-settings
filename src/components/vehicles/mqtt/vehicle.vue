<template>
  <div class="vehicle-soc-mqtt">
    <openwb-base-alert subtype="info">
      Die Daten werden immer dann aktualisiert, wenn das Topic veröffentlicht wird. Die Abfrageintervalle werden nicht
      berücksichtigt, da das Intervall vom sendenden Client festgelegt wird.
      <ul>
        <li>
          <openwb-base-copy-to-clipboard
            class="text-info"
            tooltip="Topic kopieren"
          >
            openWB/set/mqtt/vehicle/{{ vehicleId }}/get/soc
          </openwb-base-copy-to-clipboard>
          <br />
          Fahrzeug-SoC mit Nachkommastellen (Float) oder Ganzzahl<br />
          Beispiel: <span class="text-info">89.5</span>
        </li>
        <li>
          <openwb-base-copy-to-clipboard
            class="text-info"
            tooltip="Topic kopieren"
          >
            openWB/set/mqtt/vehicle/{{ vehicleId }}/get/soc_timestamp
          </openwb-base-copy-to-clipboard>
          <br />
          Zeitstempel des SoCs in s als Unix-Zeitstempel<br />
          Diese Info ist optional. Wird kein Wert für das Topic veröffentlicht, wird bei der Abfrage automatisch der
          aktuelle Zeitstempel gesetzt.<br />
          Beispiel: <span class="text-info">1748339524</span>
        </li>
        <li>
          <openwb-base-copy-to-clipboard
            class="text-info"
            tooltip="Topic kopieren"
          >
            openWB/set/mqtt/vehicle/{{ vehicleId }}/get/range
          </openwb-base-copy-to-clipboard>
          <br />
          Reichweite des Fahrzeugs in km mit Nachkommastellen (Float) oder Ganzzahl<br />
          Diese Info ist optional.<br />
          Beispiel: <span class="text-info">356.5</span>
        </li>
      </ul>
    </openwb-base-alert>
  </div>
</template>

<script>
import VehicleConfigMixin from "../VehicleConfigMixin.vue";

export default {
  name: "VehicleSocMqtt",
  mixins: [VehicleConfigMixin],
};
</script>
