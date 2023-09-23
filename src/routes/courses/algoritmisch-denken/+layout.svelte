<script>
	import CourseLayout from '$lib/components/CourseLayout.svelte';
</script>

<CourseLayout>
	<svelte:fragment slot="courseName">Algoritmisch denken</svelte:fragment>
	<slot />
</CourseLayout>
