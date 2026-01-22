# 📚 EPUB Reader - Advanced Web EPUB Reader

A modern, fully self-contained single-file HTML EPUB reader with native browser translation support and responsive interface.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## ✨ Key Features

### 🌐 Browser Translation-Friendly
**Unique feature**: Unlike most web-based EPUB readers, this application is designed to be **fully translatable** using built-in browser translation systems (Google Translate, Microsoft Translator, etc.). EPUB content is rendered in a way that allows browsers to access and translate the text, both in paginated mode and in the bookmarks sidebar.

### 📖 Complete Reading Features
- **3-level interactive table of contents** with hierarchical expand/collapse
- **Multiple viewing modes**: paginated, continuous scroll, dual page
- **5 reading themes**: Normal, Sepia, Gray, Dark Gray, Dark
- **Advanced typography control**: font size (50%-200%) and line height (1, 1.2, 1.4, 1.6, 1.8)
- **Smooth navigation** via buttons or bookmarks

### 🎨 Modern Interface
- **Responsive design** optimized for desktop, tablet, and smartphone
- **Colorful toolbar** with Bootstrap Icons
- **Compact header** with modern gradient
- **Logical control groups** for ease of use
- **Immediate visual feedback** on all actions

### 🚀 Technology
- **Single self-contained file**: all code in one HTML file
- **Zero installation**: open and use
- **Works offline** after first load
- **Stable CDN dependencies** with guaranteed fixed versions

## 📋 Detailed Features

### Typography Controls
| Function | Description | Range/Values |
|----------|-------------|--------------|
| **Font Size +5/-5** | Fast increment/decrement | 50% - 200% |
| **Font Size +1/-1** | Fine size control | 50% - 200% |
| **Reset Font** | Restore default size | 100% |
| **Line Height** | Spacing between lines | 1, 1.2, 1.4, 1.6, 1.8 |

### Display Modes
- **Paginated Mode** (default): Page-by-page view with prev/next buttons
- **Scroll Mode**: Continuous vertical scrolling of chapter
- **Dual Page Mode**: Side-by-side two-page view (paginated only)

### Color Themes
1. **Normal**: White background, black text (default)
2. **Sepia**: Beige background (#f4ecd8), black text - ideal for extended reading
3. **Gray**: Light gray background (#e5e7eb), black text - reduces eye strain
4. **Dark**: Black background (#1a1a1a), light gray text - night reading

### Navigation
- **Table of Contents (TOC)**: Sidebar with 3-level hierarchical index
- **Prev/Next Buttons**: Sequential navigation (in paginated mode)
- **Bookmark Clicks**: Jump directly to chapters/sections
- **Toggle Sidebar**: Show/hide TOC to maximize reading space

## 🛠️ Technologies Used

### Core Libraries
- **[epub.js](https://github.com/futurepress/epub.js/) v0.3.93**: EPUB rendering engine
- **[JSZip](https://stuk.github.io/jszip/) v3.10.1**: EPUB archive handling
- **[Bootstrap Icons](https://icons.getbootstrap.com/) v1.11.3**: Icon library

### CDN
All libraries are served from **jsDelivr** with fixed versions to guarantee permanent availability:
```
https://cdn.jsdelivr.net/npm/jszip@3.10.1/dist/jszip.min.js
https://cdn.jsdelivr.net/npm/epubjs@0.3.93/dist/epub.min.js
https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css
```

## 🚀 How to Use

### Installation
1. **Download** the HTML file
2. **Open** the file with any modern browser (Chrome, Safari, Edge)
3. No installation or configuration required!

### Basic Usage
1. Click **"Choose file"** to select an EPUB file from your device
2. The EPUB will load automatically with the index in the sidebar
3. Use the **toolbar controls** to customize your reading experience
4. Click on **bookmarks** to navigate between chapters

### Content Translation
**Special feature**: To translate EPUB content:

#### Desktop (Chrome/Edge):
1. Right-click on text → "Translate to..."
2. Or use the translation icon in the address bar

#### Mobile (Chrome):
1. Browser menu (⋮) → "Translate..."
2. Select target language

**Note**: **Paginated mode** provides better translation results than scroll mode on some mobile browsers.

## 📱 Compatibility

### Supported Browsers
- ✅ Chrome/Edge 90+
- ✅ Safari 14+
- ✅ Opera 76+

### Devices
- ✅ Desktop (Windows, macOS, Linux)
- ✅ Tablet (iPad, Android tablets)
- ✅ Smartphone (iOS, Android)

### Responsive Design
The interface automatically adapts to:
- **Desktop**: Full layout with all controls visible
- **Tablet**: Proportional sidebar, optimized controls
- **Smartphone**: Compact layout, multi-row header if needed

## ⚙️ Advanced Configuration

### Default Settings
The following settings can be modified directly in the JavaScript code:

```javascript
let fontSize = 100;        // Initial font size (%)
let lineHeight = 1.2;      // Initial line height
let scrollMode = false;    // Scroll mode (false = paginated)
let dualPageMode = false;  // Dual page (false = single)
let sidebarVisible = true; // Sidebar visible on startup
let currentTheme = 'normal'; // Initial theme
```

## 🔒 Privacy and Security

- ✅ **No tracking**: The app doesn't collect data
- ✅ **No servers**: Everything works locally in the browser
- ✅ **Your files stay private**: EPUBs are not uploaded to external servers
- ✅ **Open source**: Fully inspectable code

## 🐛 Known Issues and Limitations

### Translation on Mobile
- On some mobile browsers (especially in scroll mode), automatic translation may only translate portions of text due to browser limitations in translating content within dynamic iframes
- **Solution**: Use **paginated mode** for more complete translations on mobile

### EPUB Compatibility
- Supports EPUB 2 and EPUB 3
- Some DRM-protected EPUBs are not supported
- EPUBs with complex JavaScript may not work correctly

## 🗺️ Future Roadmap

Possible future features:
- [ ] Save reading position in localStorage
- [ ] Annotations and highlights
- [ ] Full-text search
- [ ] Export notes
- [ ] Dictionary integration
- [ ] Support for additional formats (PDF, MOBI)
- [ ] Speed reading mode
- [ ] Optional cloud synchronization

## 📄 License

This project is released under the **MIT License**. See the `LICENSE` file for details.

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📧 Contact

For bugs, suggestions, or questions, open an [issue](../../issues) on GitHub.

## 🙏 Acknowledgments

- [epub.js](https://github.com/futurepress/epub.js/) - For the excellent EPUB rendering library
- [JSZip](https://stuk.github.io/jszip/) - For archive handling
- [Bootstrap Icons](https://icons.getbootstrap.com/) - For the beautiful icons
- [jsDelivr](https://www.jsdelivr.com/) - For reliable CDN hosting

---

**Made with ❤️ for digital reading lovers**
