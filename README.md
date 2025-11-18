# Blue Noise Stippling: Transforming Photographs into Art

<div align="center">

**Convert photographs into aesthetically pleasing dot patterns using advanced blue noise algorithms**

[![Quarto](https://img.shields.io/badge/Built%20with-Quarto-9cf)](https://quarto.org/)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![R](https://img.shields.io/badge/R-4.0+-blue.svg)](https://www.r-project.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## 📖 Overview

Blue noise stippling is a sophisticated technique that transforms photographs into elegant patterns of dots (stipples) while preserving the visual information of the original image. This project implements a modified **void-and-cluster algorithm** that combines importance sampling with blue noise distribution properties to create stippling patterns that are both visually accurate and spatially well-distributed.

### What Makes This Special?

- **Visual Accuracy**: Preserves important image details through intelligent importance mapping
- **Spatial Distribution**: Ensures even dot distribution using blue noise properties
- **Progressive Animation**: Watch the stippling pattern develop frame by frame
- **Dual Language Support**: Implementations available in both Python and R
- **Professional Quality**: Production-ready code with comprehensive documentation

---

## 🎨 What is Blue Noise Stippling?

Blue noise stippling converts continuous-tone images into discrete dot patterns. Unlike random dot placement, blue noise stippling ensures that:

1. **Dots are evenly distributed** - No clustering or large empty regions
2. **Visual information is preserved** - Dark areas get more dots, light areas get fewer
3. **Aesthetically pleasing** - The pattern looks natural and artistic

The term "blue noise" refers to the frequency spectrum of the dot pattern, which has more high-frequency components (like blue light) and fewer low-frequency components, resulting in a visually pleasing, evenly distributed pattern.

---

## ✨ Features

### Core Algorithm
- **Modified Void-and-Cluster Algorithm**: Advanced point selection with energy minimization
- **Toroidal Gaussian Kernel**: Periodic repulsion ensures consistent blue noise properties
- **Importance Mapping**: Intelligent weighting of image regions based on visual importance
- **Smooth Tone Downweighting**: Selectively reduces dots in extreme dark/light regions

### Output Capabilities
- **High-Quality Stippled Images**: Professional-grade dot patterns
- **Progressive GIF Animations**: Watch the pattern develop incrementally
- **Flexible Parameters**: Fine-tune dot density, distribution, and appearance
- **Multiple Format Support**: Works with JPEG, PNG, and other common image formats

### Technical Features
- **Dual Implementation**: Python and R versions available
- **Efficient Processing**: Optimized algorithms for reasonable processing times
- **Reproducible Results**: Seed-based randomization for consistent outputs
- **Comprehensive Documentation**: Detailed explanations and examples

---

## 🚀 Quick Start

### Prerequisites

**Python Requirements:**
- Python 3.8 or higher
- NumPy
- Pillow (PIL)
- Matplotlib

**R Requirements:**
- R 4.0 or higher
- `imager` package
- `magick` package (for GIF creation)

### Installation

#### Python Setup

```bash
pip install numpy pillow matplotlib
```

#### R Setup

```r
install.packages(c("imager", "magick"))
```

### Basic Usage

1. **Place your image** in the project directory
2. **Update the image path** in `index.qmd` (line 49 for Python, line 102 for R)
3. **Render the document**:

```bash
quarto render index.qmd
```

4. **View the results** in `index.html`

---

## 📚 Algorithm Details

### The Modified Void-and-Cluster Algorithm

Our implementation uses a sophisticated approach that balances visual accuracy with spatial distribution:

#### 1. Importance Mapping
The algorithm first creates an importance map that identifies visually important regions:
- **Brightness Inversion**: Dark areas receive higher importance (more dots)
- **Extreme Tone Downweighting**: Very dark and very light regions are selectively downweighted
- **Mid-Tone Boost**: Mid-tone regions receive enhanced importance for better detail preservation

#### 2. Energy Field Initialization
An energy field is created where:
- Lower energy = higher probability of dot placement
- Energy is inversely related to importance (important regions have lower energy)

#### 3. Toroidal Gaussian Repulsion
A periodic (toroidal) Gaussian kernel ensures:
- Consistent repulsion behavior regardless of point location
- Blue noise properties through proper spacing
- No edge artifacts due to periodic boundary conditions

#### 4. Iterative Point Selection
Points are selected iteratively:
- First point is chosen near the center in a low-energy region
- Subsequent points minimize energy while maintaining spatial distribution
- Each selected point adds a Gaussian "splat" to prevent nearby selections
- Exploration noise decreases over time for better convergence

### Key Parameters

| Parameter | Description | Default | Effect |
|-----------|-------------|---------|--------|
| `percentage` | Fraction of pixels to convert to dots | 0.08 | Higher = more dots, more detail |
| `sigma` | Gaussian kernel width | 0.9 | Controls dot spacing |
| `content_bias` | Weight of importance vs. spatial distribution | 0.9 | Higher = more content-aware |
| `extreme_downweight` | Reduction of dots in extreme tones | 0.5 | Higher = fewer dots in very dark/light areas |
| `mid_tone_boost` | Enhancement of mid-tone importance | 0.4 | Higher = more dots in mid-tones |

---

## 🖼️ Example Output

The algorithm produces:

1. **Original Image**: Your input photograph
2. **Importance Map**: Visualization of where dots will be concentrated
3. **Stippled Image**: Final dot pattern preserving visual information
4. **Progressive Animation**: GIF showing the pattern developing over time

### Visual Comparison

The stippling process transforms continuous-tone images into discrete dot patterns while maintaining:
- Facial features and expressions
- Textural details
- Overall composition and lighting
- Artistic aesthetic appeal

---

## 📁 Project Structure

```
stippleChallenge/
├── index.qmd              # Main Quarto document
├── index.html             # Rendered HTML output
├── README.md              # This file
├── LICENSE                # License information
├── *.jpeg                 # Input images
├── progressive_stippling.gif  # Output animation
└── index_files/           # Generated assets
    ├── figure-html/       # HTML figure outputs
    └── figure-pdf/        # PDF figure outputs
```

---

## 🔧 Advanced Usage

### Customizing Importance Mapping

The `compute_importance` function allows fine-tuning of dot distribution:

```python
importance_map = compute_importance(
    img_resized,
    extreme_downweight=0.5,      # Reduce dots in extreme tones
    extreme_threshold_low=0.2,   # Dark tone threshold
    extreme_threshold_high=0.8,  # Light tone threshold
    extreme_sigma=0.1,           # Transition smoothness
    mid_tone_boost=0.4,          # Mid-tone enhancement
    mid_tone_sigma=0.2           # Mid-tone width
)
```

### Adjusting Stippling Parameters

```python
stipple_pattern, samples = void_and_cluster(
    img_resized,
    percentage=0.08,           # 8% of pixels become dots
    sigma=0.9,                 # Repulsion kernel size
    content_bias=0.9,          # Content vs. spatial balance
    importance_img=importance_map,
    noise_scale_factor=0.1     # Exploration noise
)
```

### Creating Progressive Animations

The progressive stippling animation shows how the pattern develops:
- Frames are captured at regular intervals (every 100 points by default)
- Each frame shows the cumulative dot pattern
- The final GIF demonstrates the algorithm's iterative nature

---

## 🎓 Understanding the Results

### What to Look For

**Good Stippling:**
- ✅ Even dot distribution (no large empty areas)
- ✅ Preserved facial features and details
- ✅ Smooth gradients in tone
- ✅ No obvious clustering or patterns

**Areas for Improvement:**
- Adjust `percentage` if detail is lost or image is too cluttered
- Modify `extreme_downweight` if extreme tones need more/less dots
- Tune `content_bias` to balance content vs. spatial distribution
- Change `sigma` to adjust dot spacing

### Tone Analysis

The algorithm includes tone analysis tools that:
- Divide the image into a grid of sections
- Compute average brightness in each section
- Identify regions with specific tone characteristics
- Help understand dot distribution patterns

---

## 📖 References

This implementation is based on the work of:

- **Bart Wronski**: [Progressive Image Stippling and Greedy Blue Noise Importance Sampling](https://bartwronski.com/2022/08/31/progressive-image-stippling-and-greedy-blue-noise-importance-sampling/)

The void-and-cluster algorithm was originally described by:
- **Robert Ulichney**: "Void-and-cluster method for dither array generation" (1993)

---

## 🤝 Contributing

This is an educational project demonstrating blue noise stippling techniques. Contributions, suggestions, and improvements are welcome!

### Areas for Enhancement
- Performance optimization for large images
- Additional importance mapping strategies
- Color stippling support
- Interactive parameter tuning interface

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Bart Wronski** for the excellent blog post and algorithm description
- **Quarto** team for the powerful document rendering system
- The open-source community for the excellent libraries used in this project

---

## 📧 Contact & Support

For questions, issues, or suggestions:
- Open an issue on the repository
- Review the documentation in `index.qmd`
- Check the rendered HTML output for detailed explanations

---

<div align="center">

**Transform your photographs into art with blue noise stippling**

Made with ❤️ using Quarto, Python, and R

</div>

