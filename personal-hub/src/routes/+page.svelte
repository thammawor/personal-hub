<script lang="ts">
	import '../app.css';

	let name = $state('Personal Hub');
	let tagline = $state('รวมทุกอย่างในที่เดียว');

	interface SocialLink {
		name: string;
		url: string;
		icon: string;
		color: string;
	}

	interface Project {
		title: string;
		description: string;
		tags: string[];
		link: string;
	}

	interface Note {
		category: 'project' | 'goal' | 'idea';
		content: string;
	}

	const socialLinks: SocialLink[] = [
		{ name: 'GitHub', url: 'https://github.com', icon: '🐙', color: '#333' },
		{ name: 'Twitter', url: 'https://twitter.com', icon: '🐦', color: '#1DA1F2' },
		{ name: 'LinkedIn', url: 'https://linkedin.com', icon: '💼', color: '#0A66C2' },
		{ name: 'Email', url: 'mailto:hello@example.com', icon: '📧', color: '#EA4335' }
	];

	const projects: Project[] = [
		{
			title: 'โปรเจคแรก',
			description: 'คำอธิบายโปรเจคที่น่าสนใจของคุณ',
			tags: ['Svelte 5', 'TypeScript', 'SvelteKit'],
			link: '#'
		},
		{
			title: 'เว็บแอปพลิเคชัน',
			description: 'สร้างด้วยเทคโนโลยีล่าสุด',
			tags: ['Svelte', 'Tailwind'],
			link: '#'
		},
		{
			title: 'API Service',
			description: 'บริการ backend ที่รวดเร็วและปลอดภัย',
			tags: ['Node.js', 'Express'],
			link: '#'
		}
	];

	const notes: Note[] = [
		{ category: 'project', content: 'ทำ dashboard สำหรับวิเคราะห์ข้อมูล' },
		{ category: 'goal', content: 'เรียนรู้ Svelte 5 ให้เชี่ยวชาญภายในเดือนนี้' },
		{ category: 'idea', content: 'สร้างแอปจัดการงานส่วนตัวแบบ real-time' },
		{ category: 'project', content: 'อัปเดตพอร์ตโฟลิโอใหม่' },
		{ category: 'goal', content: 'เขียนบล็อกเทคนิคทุกสัปดาห์' }
	];

	function getCategoryIcon(category: string): string {
		switch (category) {
			case 'project': return '📁';
			case 'goal': return '🎯';
			case 'idea': return '💡';
			default: return '📝';
		}
	}

	function getCategoryColor(category: string): string {
		switch (category) {
			case 'project': return '#4CAF50';
			case 'goal': return '#FF9800';
			case 'idea': return '#2196F3';
			default: return '#9E9E9E';
		}
	}
</script>

<svelte:head>
	<title>{name} - Personal Hub</title>
</svelte:head>

<div class="container">
	<!-- Profile Section -->
	<section class="profile-section">
		<div class="avatar">👤</div>
		<h1>{name}</h1>
		<p class="tagline">{tagline}</p>
		
		<!-- Social Links -->
		<div class="social-links">
			{#each socialLinks as link}
				<a 
					href={link.url} 
					class="social-link"
					style="border-color: {link.color}"
					target="_blank"
					rel="noopener noreferrer"
				>
					<span class="icon">{link.icon}</span>
					<span class="name">{link.name}</span>
				</a>
			{/each}
		</div>
	</section>

	<!-- Projects Section -->
	<section class="projects-section">
		<h2>🚀 โปรเจคของฉัน</h2>
		<div class="projects-grid">
			{#each projects as project}
				<div class="project-card">
					<h3>{project.title}</h3>
					<p>{project.description}</p>
					<div class="tags">
						{#each project.tags as tag}
							<span class="tag">{tag}</span>
						{/each}
					</div>
					<a href={project.link} class="project-link">ดูโปรเจค →</a>
				</div>
			{/each}
		</div>
	</section>

	<!-- Quick Notes Section -->
	<section class="notes-section">
		<h2>📝 Quick Notes</h2>
		<div class="notes-grid">
			{#each notes as note}
				<div 
					class="note-card" 
					style="border-left-color: {getCategoryColor(note.category)}"
				>
					<div class="note-header">
						<span class="note-icon">{getCategoryIcon(note.category)}</span>
						<span class="note-category" style="color: {getCategoryColor(note.category)}">
							{note.category.toUpperCase()}
						</span>
					</div>
					<p>{note.content}</p>
				</div>
			{/each}
		</div>
	</section>

	<footer>
		<p>สร้างด้วย ❤️ โดยใช้ Svelte 5 + SvelteKit</p>
	</footer>
</div>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
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

	/* Profile Section */
	.profile-section {
		text-align: center;
		padding: 3rem 0;
		color: white;
	}

	.avatar {
		font-size: 5rem;
		margin-bottom: 1rem;
		animation: bounce 2s infinite;
	}

	@keyframes bounce {
		0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
		40% { transform: translateY(-20px); }
		60% { transform: translateY(-10px); }
	}

	h1 {
		font-size: 3rem;
		margin: 0.5rem 0;
		font-weight: 700;
	}

	.tagline {
		font-size: 1.2rem;
		opacity: 0.9;
		margin-bottom: 2rem;
	}

	.social-links {
		display: flex;
		justify-content: center;
		gap: 1rem;
		flex-wrap: wrap;
	}

	.social-link {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		padding: 0.8rem 1.5rem;
		background: white;
		border-radius: 50px;
		text-decoration: none;
		color: #333;
		font-weight: 600;
		border: 3px solid transparent;
		transition: all 0.3s ease;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
	}

	.social-link:hover {
		transform: translateY(-3px);
		box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
	}

	.icon {
		font-size: 1.3rem;
	}

	/* Projects Section */
	.projects-section {
		margin: 3rem 0;
	}

	h2 {
		color: white;
		font-size: 2rem;
		margin-bottom: 2rem;
		text-align: center;
	}

	.projects-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
		gap: 1.5rem;
	}

	.project-card {
		background: white;
		padding: 2rem;
		border-radius: 15px;
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
		transition: all 0.3s ease;
	}

	.project-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
	}

	.project-card h3 {
		color: #667eea;
		margin: 0 0 1rem 0;
		font-size: 1.5rem;
	}

	.project-card p {
		color: #666;
		line-height: 1.6;
		margin-bottom: 1.5rem;
	}

	.tags {
		display: flex;
		gap: 0.5rem;
		flex-wrap: wrap;
		margin-bottom: 1.5rem;
	}

	.tag {
		background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
		color: white;
		padding: 0.3rem 0.8rem;
		border-radius: 20px;
		font-size: 0.85rem;
		font-weight: 600;
	}

	.project-link {
		color: #667eea;
		text-decoration: none;
		font-weight: 600;
		transition: color 0.3s ease;
	}

	.project-link:hover {
		color: #764ba2;
	}

	/* Notes Section */
	.notes-section {
		margin: 3rem 0;
	}

	.notes-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: 1rem;
	}

	.note-card {
		background: white;
		padding: 1.5rem;
		border-radius: 10px;
		border-left: 4px solid;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
		transition: all 0.3s ease;
	}

	.note-card:hover {
		transform: translateX(5px);
		box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
	}

	.note-header {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		margin-bottom: 0.8rem;
	}

	.note-icon {
		font-size: 1.2rem;
	}

	.note-category {
		font-size: 0.75rem;
		font-weight: 700;
		letter-spacing: 0.5px;
	}

	.note-card p {
		color: #555;
		line-height: 1.5;
		margin: 0;
	}

	/* Footer */
	footer {
		text-align: center;
		padding: 3rem 0;
		color: white;
		opacity: 0.8;
	}

	/* Responsive */
	@media (max-width: 768px) {
		.container {
			padding: 1rem;
		}

		h1 {
			font-size: 2rem;
		}

		.avatar {
			font-size: 3.5rem;
		}

		.social-links {
			flex-direction: column;
			align-items: center;
		}

		.social-link {
			width: 100%;
			max-width: 280px;
			justify-content: center;
		}

		.projects-grid,
		.notes-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
