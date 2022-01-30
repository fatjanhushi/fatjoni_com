<script context="module">
	export async function load({ fetch }) {
		const url = 'https://jsonplaceholder.typicode.com/posts'
		const res = await fetch(url)
		const articles = await res.json()

		if (res.ok) {
			return {
				props: {
					articles
				}
			}
		}
		return {
			status: res.status,
			error: new Error('Could not fetch from network.')
		}
	}
</script>

<script>
	export let articles
</script>

<div>
	{#each articles as article}
		<p>{article.title}</p>
	{/each}
</div>
