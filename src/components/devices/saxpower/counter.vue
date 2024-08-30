<template>
	<div class="device-saxpower-counter">
		<openwb-base-heading>
			Einstellungen für Saxpower Zähler
			<span class="small">(Modul: {{ $options.name }})</span>
		</openwb-base-heading>
		<openwb-base-alert subtype="info">
			<span class="text-danger">
				Saxpower Zähler geben keine Ströme aus, sodass nur ein
				Lastmanagement anhand der Gesamtleistung, aber nicht
				phasenbasiert möglich ist.
			</span>
		</openwb-base-alert>
	</div>
</template>

<script>
export default {
	name: "DeviceSaxpowerCounter",
	emits: ["update:configuration"],
	props: {
		configuration: { type: Object, required: true },
		deviceId: { default: undefined },
		componentId: { required: true },
	},
	methods: {
		updateConfiguration(event, path = undefined) {
			this.$emit("update:configuration", { value: event, object: path });
		},
	},
};
</script>
