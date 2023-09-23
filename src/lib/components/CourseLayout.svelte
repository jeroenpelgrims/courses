<section class="hero is-info is-small">
	<div class="hero-body">
		<h1 class="title"><slot name="courseName" /></h1>
	</div>
</section>

<section class="courseContent content">
	<slot />
</section>

<style type="scss">
	section.courseContent {
		padding: 1rem;
	}
</style>
