<script lang="ts">
	import ToggleButtonGroup from './common/toggleButton-v2/ToggleButtonGroup.svelte'
	import ToggleButton from './common/toggleButton-v2/ToggleButton.svelte'
	import { Building } from 'lucide-svelte'
	interface Props {
		selected?: 'hub' | 'workspace'
	}

	// FlowPurple personal build: Hub imports hidden, workspace-only pickers.
	let { selected = $bindable('workspace') }: Props = $props()
</script>

<div class="max-w-min">
	<ToggleButtonGroup bind:selected>
		{#snippet children({ item })}
			<ToggleButton value="workspace" icon={Building} label="Workspace" {item} />
		{/snippet}
	</ToggleButtonGroup>
</div>
