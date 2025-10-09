# Nav-data

A modern, elegant website for flight simulation resources and navigation data.

## Features

- 🎨 Beautiful, minimalist design inspired by aviation aesthetics
- 🌓 Dark/Light theme toggle with persistent storage
- ✈️ Dedicated sections for resources, aircraft, and about information
- 📱 Fully responsive design
- 🎭 Smooth animations and transitions
- 🚀 Built with Vue 3 and Vite for optimal performance

## Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn

### Installation

1. Install dependencies:
```bash
npm install
```

2. Start the development server:
```bash
npm run dev
```

3. Build for production:
```bash
npm run build
```

4. Preview production build:
```bash
npm run preview
```

## Customization

### Adding Your Aircraft Image

Replace the placeholder image by adding your aircraft image to the `public` folder:

```
public/
  └── aircraft-hero.jpg
```

The recommended image size is at least 1920x1080px for best quality on all screens.

### Modifying Content

Edit the following sections in `src/App.vue`:

- **Resources**: Update the `resources` array with your navigation data links
- **Aircraft**: Modify the `aircraftList` array with your featured aircraft
- **Hero Section**: Change the title, subtitle, and description
- **About Section**: Update the about text

### Color Scheme

The color scheme can be customized in `src/style.css`:

```css
:root {
  --accent-color: 59, 130, 246; /* Blue accent */
  --accent-secondary: 180, 152, 107; /* Gold accent */
}
```

## Project Structure

```
nav-data/
├── public/
│   └── aircraft-hero.jpg (add your image here)
├── src/
│   ├── components/
│   │   ├── IconPlane.vue
│   │   ├── IconNavData.vue
│   │   ├── IconChart.vue
│   │   └── IconTower.vue
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

## Technologies Used

- **Vue 3** - Progressive JavaScript framework
- **Vite** - Next-generation frontend tooling
- **CSS3** - Modern styling with animations

## License

MIT License - feel free to use this project for your own flight simulation website!

## Credits

Design inspiration from modern aviation and minimalist web design principles.
