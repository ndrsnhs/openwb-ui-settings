<template>
	<div class="device-mqtt">
		<openwb-base-heading>
			Einstellungen für MQTT
			<span class="small">(Modul: {{ $options.name }})</span>
		</openwb-base-heading>
		<openwb-base-alert subtype="info">
			Das MQTT Modul stellt keine aktive Verbindung her, sondern erwartet,
			dass die Daten an die angegebenen Topics im Broker gesendet werden.
			Da die Daten direkt an den Broker gesendet werden, erfolgt keine
			Verrechnung bei Hybrid-Systemen und auch keine Berechnung fehlender
			Werte, z.B. von Phasen-Leistung aus Spannung und Strömen. Beim
			Logging und im Lastmanagement, z.B. bei verschachtelten Zählern,
			werden die MQTT-Zähler wie gewohnt berücksichtigt.<br />
			Alle Daten sind als gültiges JSON zu senden! Zahlen mit
			Nachkommastellen (Float) müssen einen Punkt als Dezimaltrenner
			verwenden (internationales Format).
		</openwb-base-alert>
	</div>
</template>

<script>
export default {
	name: "DeviceMqtt",
	emits: ["update:configuration"],
	props: {
		configuration: { type: Object, required: true },
		deviceId: { default: undefined },
	},
	methods: {
		updateConfiguration(event, path = undefined) {
			this.$emit("update:configuration", { value: event, object: path });
		},
	},
};
</script>
