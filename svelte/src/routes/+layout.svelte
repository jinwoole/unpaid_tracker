<script>
	import '../app.postcss';
	import { autoModeWatcher } from '@skeletonlabs/skeleton';

</script>

<!-- 그 뭐냐 다크모드 그거 -->
<svelte:head>{@html '<script>(' + autoModeWatcher.toString() + ')();</script>'}</svelte:head>

<slot />
