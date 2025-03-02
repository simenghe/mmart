<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>
<div class="flex items-center justify-between bg-indigo-900 p-4 text-center">
	<h1 class="text-2xl font-bold text-white">
		<a href="/" class="hover:text-indigo-200"><span> MMart </span></a>
	</h1>
	<div class="flex gap-4">
		<a href="/login" class="text-white hover:text-indigo-200">Login</a>
		<a href="/signup" class="text-white hover:text-indigo-200">Sign Up</a>
	</div>
</div>
{@render children()}