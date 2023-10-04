<section class="hero is-info is-small">
	<div class="hero-body">
		<h1 class="title">
			<a href="/courses/algoritmisch-denken"><slot name="courseName" /></a>
		</h1>
	</div>
</section>

<section class="courseContent content">
	<slot />
</section>

<style type="scss">
	section.courseContent {
		padding: 2rem 2rem 0rem 2rem;
	}
</style>
