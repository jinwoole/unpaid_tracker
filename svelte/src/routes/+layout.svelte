<script>
	import '../app.postcss';
	import { onMount } from 'svelte';
	import { autoModeWatcher } from '@skeletonlabs/skeleton';

	onMount(() => {										
		autoModeWatcher();
	})
</script>

<!-- 그 뭐냐 다크모드 그거 -->
<slot />
