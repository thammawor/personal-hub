<script lang="ts">
	import type { Snippet } from 'svelte';

	interface SocialLink {
		name: string;
		url: string;
		icon: string;
	}

	interface Project {
		title: string;
		description: string;
		link?: string;
		tags: string[];
	}

	interface Note {
		id: number;
		content: string;
		category: 'project' | 'goal' | 'idea';
	}

	let { children }: { children: Snippet } = $props();

	const socialLinks: SocialLink[] = [
		{ name: 'GitHub', url: 'https://github.com/yourusername', icon: '🐙' },
		{ name: 'Twitter', url: 'https://twitter.com/yourusername', icon: '🐦' },
		{ name: 'LinkedIn', url: 'https://linkedin.com/in/yourusername', icon: '💼' },
		{ name: 'Email', url: 'mailto:your@email.com', icon: '📧' }
	];

	const projects: Project[] = [
		{
			title: 'Project Alpha',
			description: 'A modern web application built with SvelteKit',
			link: '#',
			tags: ['Svelte', 'TypeScript', 'Node.js']
		},
		{
			title: 'Project Beta',
			description: 'Mobile-first responsive design system',
			link: '#',
			tags: ['CSS', 'Design System', 'Accessibility']
		}
	];

	const notes: Note[] = [
		{ id: 1, content: 'Learn Svelte 5 runes syntax', category: 'goal' },
		{ id: 2, content: 'Build a personal portfolio site', category: 'project' },
		{ id: 3, content: 'Create a component library', category: 'idea' }
	];
</script>

<svelte:head>
	<title>Personal Hub</title>
	<meta name="description" content="My personal hub for projects, notes, and links" />
</svelte:head>

<div class="container">
	<header class="header">
		<div class="profile-section">
			<div class="avatar">👤</div>
			<h1>Your Name</h1>
			<p class="tagline">Developer | Creator | Learner</p>
		</div>
	</header>

	<nav class="social-links">
		{#each socialLinks as link}
			<a href={link.url} target="_blank" rel="noopener noreferrer" class="social-link">
				<span class="icon">{link.icon}</span>
				<span>{link.name}</span>
			</a>
		{/each}
	</nav>

	<main>
		<section class="projects-section">
			<h2>🚀 Projects</h2>
			<div class="projects-grid">
				{#each projects as project}
					<article class="project-card">
						<h3>{project.title}</h3>
						<p>{project.description}</p>
						<div class="tags">
							{#each project.tags as tag}
								<span class="tag">{tag}</span>
							{/each}
						</div>
						{#if project.link}
							<a href={project.link} class="project-link">View Project →</a>
						{/if}
					</article>
				{/each}
			</div>
		</section>

		<section class="notes-section">
			<h2>📝 Quick Notes</h2>
			<div class="notes-grid">
				{#each notes as note}
					<div class="note-card {note.category}">
						<span class="note-category">
							{note.category === 'project' && '📁'}
							{note.category === 'goal' && '🎯'}
							{note.category === 'idea' && '💡'}
						</span>
						<p>{note.content}</p>
					</div>
				{/each}
			</div>
		</section>
	</main>

	<footer class="footer">
		<p>Built with Svelte 5 + SvelteKit • {new Date().getFullYear()}</p>
	</footer>
</div>

{@render children()}

<style>
	:global(*) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	:global(body) {
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
		background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
		min-height: 100vh;
		color: #333;
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 2rem;
	}

	.header {
		text-align: center;
		margin-bottom: 3rem;
	}

	.profile-section {
		background: rgba(255, 255, 255, 0.95);
		border-radius: 20px;
		padding: 3rem;
		box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
	}

	.avatar {
		font-size: 5rem;
		margin-bottom: 1rem;
	}

	h1 {
		font-size: 2.5rem;
		color: #667eea;
		margin-bottom: 0.5rem;
	}

	.tagline {
		color: #666;
		font-size: 1.2rem;
	}

	.social-links {
		display: flex;
		justify-content: center;
		gap: 1rem;
		flex-wrap: wrap;
		margin-bottom: 3rem;
	}

	.social-link {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		background: rgba(255, 255, 255, 0.9);
		padding: 0.8rem 1.5rem;
		border-radius: 50px;
		text-decoration: none;
		color: #333;
		font-weight: 500;
		transition: all 0.3s ease;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
	}

	.social-link:hover {
		transform: translateY(-3px);
		box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
		background: white;
	}

	main {
		display: grid;
		grid-template-columns: 1fr;
		gap: 3rem;
	}

	@media (min-width: 768px) {
		main {
			grid-template-columns: 1fr 1fr;
		}
	}

	section h2 {
		color: white;
		font-size: 1.8rem;
		margin-bottom: 1.5rem;
		text-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
	}

	.projects-grid,
	.notes-grid {
		display: grid;
		gap: 1.5rem;
	}

	.project-card {
		background: rgba(255, 255, 255, 0.95);
		border-radius: 15px;
		padding: 1.5rem;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
		transition: transform 0.3s ease;
	}

	.project-card:hover {
		transform: translateY(-5px);
	}

	.project-card h3 {
		color: #667eea;
		margin-bottom: 0.5rem;
		font-size: 1.3rem;
	}

	.project-card p {
		color: #666;
		margin-bottom: 1rem;
		line-height: 1.6;
	}

	.tags {
		display: flex;
		gap: 0.5rem;
		flex-wrap: wrap;
		margin-bottom: 1rem;
	}

	.tag {
		background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
		color: white;
		padding: 0.3rem 0.8rem;
		border-radius: 20px;
		font-size: 0.85rem;
		font-weight: 500;
	}

	.project-link {
		display: inline-block;
		color: #667eea;
		text-decoration: none;
		font-weight: 600;
		transition: color 0.3s ease;
	}

	.project-link:hover {
		color: #764ba2;
	}

	.note-card {
		background: rgba(255, 255, 255, 0.95);
		border-radius: 15px;
		padding: 1.5rem;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
		transition: transform 0.3s ease;
		border-left: 4px solid #667eea;
	}

	.note-card:hover {
		transform: translateX(5px);
	}

	.note-card.project {
		border-left-color: #667eea;
	}

	.note-card.goal {
		border-left-color: #f093fb;
	}

	.note-card.idea {
		border-left-color: #fbc531;
	}

	.note-category {
		font-size: 1.2rem;
		margin-right: 0.5rem;
	}

	.note-card p {
		display: inline;
		color: #333;
		line-height: 1.6;
	}

	.footer {
		text-align: center;
		margin-top: 4rem;
		padding-top: 2rem;
		border-top: 1px solid rgba(255, 255, 255, 0.3);
	}

	.footer p {
		color: rgba(255, 255, 255, 0.9);
		font-size: 0.9rem;
	}

	@media (max-width: 640px) {
		.container {
			padding: 1rem;
		}

		h1 {
			font-size: 2rem;
		}

		.profile-section {
			padding: 2rem 1.5rem;
		}

		.social-links {
			flex-direction: column;
			align-items: stretch;
		}

		.social-link {
			justify-content: center;
		}
	}
</style>
