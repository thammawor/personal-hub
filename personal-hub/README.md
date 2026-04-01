# Personal Hub

A modern personal hub built with **Svelte 5** and **SvelteKit**, featuring a beautiful UI to showcase your projects, notes, and social links.

![Svelte](https://img.shields.io/badge/Svelte-5-orange?logo=svelte)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?logo=typescript)
![SvelteKit](https://img.shields.io/badge/SvelteKit-Latest-red?logo=svelte)

## ✨ Features

- 🎨 **Modern Design** - Beautiful gradient background with smooth animations
- 📱 **Responsive** - Works perfectly on mobile, tablet, and desktop
- 🚀 **Projects Section** - Showcase your projects with tags and links
- 📝 **Quick Notes** - Organize notes by category (projects, goals, ideas)
- 🔗 **Social Links** - Easy access to your social media profiles
- ⚡ **Svelte 5 Runes** - Built with the latest Svelte 5 syntax (`$props`, `$state`, etc.)
- 🎯 **TypeScript** - Full TypeScript support for better development experience

## 🏗️ Project Structure

```
personal-hub/
├── src/
│   ├── routes/
│   │   ├── +layout.svelte    # Layout component
│   │   └── +page.svelte      # Main page with all content
│   ├── app.html              # HTML template
│   └── app.d.ts              # TypeScript declarations
├── static/                   # Static assets
├── package.json
├── svelte.config.js
├── tsconfig.json
└── vite.config.ts
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ installed
- npm or pnpm package manager

### Installation

1. Navigate to the project directory:
   ```bash
   cd personal-hub
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm run dev -- --open
   ```

4. Open your browser at `http://localhost:5173`

## 🛠️ Development Commands

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build |
| `npm run check` | Type-check the code |

## 🎨 Customization

### Update Your Information

Edit `src/routes/+page.svelte` to customize:

1. **Profile Info** - Change your name and tagline
2. **Social Links** - Update the `socialLinks` array with your profiles
3. **Projects** - Add/modify projects in the `projects` array
4. **Notes** - Update your quick notes in the `notes` array

### Styling

Modify the `<style>` section in `+page.svelte` to change:
- Color scheme (currently purple-blue gradient)
- Spacing and layout
- Animations and transitions

## 📦 Building for Production

```bash
npm run build
```

The built files will be in the `.svelte-kit/output/` directory.

## 🌟 Features Breakdown

### Profile Section
Displays your avatar, name, and professional tagline in an elegant card.

### Social Links
Interactive buttons linking to your GitHub, Twitter, LinkedIn, Email, and more.

### Projects Grid
Showcase your work with:
- Project title and description
- Technology tags
- Direct links to live projects

### Quick Notes
Organized notes with visual categories:
- 📁 **Project** notes (blue accent)
- 🎯 **Goals** (pink accent)
- 💡 **Ideas** (yellow accent)

## 🤝 Contributing

Feel free to fork this project and customize it for your own use!

## 📄 License

MIT License - feel free to use this for your personal projects!

## 🙏 Acknowledgments

- Built with [Svelte 5](https://svelte.dev/)
- Powered by [SvelteKit](https://kit.svelte.dev/)
- Icons using emoji for simplicity

---

Made with ❤️ using Svelte 5
