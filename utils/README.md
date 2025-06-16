# Download PDF Utility

A reusable utility for converting DOM elements to PDF using html2canvas and jsPDF.

## Features

- Convert any DOM element to PDF
- Configurable options for filename, scale, orientation, etc.
- Promise-based API with error handling
- Backward compatibility with existing code
- Support for both class-based and static usage

## Dependencies

Make sure to include these scripts before using the utility:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<script src="./utils/downloadPdf.js"></script>
```

## Basic Usage

### Quick Download (Static Method)
```javascript
// Download with default settings
await DownloadPdfUtil.download();

// Download with custom filename
await DownloadPdfUtil.download({
  filename: 'my-document.pdf'
});
```

### Class-based Usage
```javascript
// Create instance with default options
const pdfUtil = new DownloadPdfUtil({
  selector: '.my-content',
  filename: 'custom-document.pdf'
});

// Download PDF
await pdfUtil.downloadPdf();

// Override options for specific download
await pdfUtil.downloadPdf({
  filename: 'different-name.pdf',
  scale: 3
});
```

### Backward Compatibility
```javascript
// For existing code, this still works:
await downloadPdf({
  filename: 'document.pdf',
  selector: '.terminal-window'
});
```

## Configuration Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `selector` | string | `'.terminal-window'` | CSS selector for the element to convert |
| `filename` | string | `'document.pdf'` | Name of the downloaded PDF file |
| `scale` | number | `2` | Scale factor for image quality |
| `useCORS` | boolean | `true` | Enable CORS for external images |
| `orientation` | string | `'portrait'` | PDF orientation ('portrait' or 'landscape') |
| `unit` | string | `'px'` | Unit for PDF dimensions |
| `delay` | number | `100` | Delay in ms before capturing (for rendering) |

## Real-world Examples

### CV Download
```javascript
const cvUtil = new DownloadPdfUtil({
  selector: '.terminal-window',
  filename: 'daza-cv-2025.pdf',
  scale: 2
});

await cvUtil.downloadPdf();
```

### One-pager Download
```javascript
await DownloadPdfUtil.download({
  selector: '.terminal-window',
  filename: 'daza-one-pager-2025.pdf'
});
```

### Custom Content with High Quality
```javascript
await downloadPdf({
  selector: '.report-content',
  filename: 'quarterly-report.pdf',
  scale: 3,
  orientation: 'landscape',
  delay: 500
});
```

## Error Handling

```javascript
try {
  await DownloadPdfUtil.download({
    selector: '.non-existent-element'
  });
} catch (error) {
  console.error('PDF generation failed:', error.message);
  // Handle error (show user message, fallback, etc.)
}
```

## Integration with Existing Code

To replace existing `downloadPdf` functions in your HTML files:

1. Include the utility script
2. Replace your existing function with:

```javascript
async function downloadPdf() {
  await DownloadPdfUtil.download({
    selector: '.terminal-window',
    filename: 'your-specific-filename.pdf'
  });
}
```

Or use the global convenience function:
```javascript
async function downloadPdf() {
  await window.downloadPdf({
    filename: 'your-specific-filename.pdf'
  });
}
```

## Browser Support

- Modern browsers with Promise support
- Requires html2canvas and jsPDF libraries
- Works with ES5+ environments