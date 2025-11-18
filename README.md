# Blue Noise Stippling: Transforming Photographs into Art

<div align="center">

**Convert photographs into aesthetically pleasing dot patterns using advanced blue noise algorithms**

🌐 **[View Live Website](https://ibro06.github.io/stippleChallenge/)**

[![Quarto](https://img.shields.io/badge/Built%20with-Quarto-9cf)](https://quarto.org/)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![R](https://img.shields.io/badge/R-4.0+-blue.svg)](https://www.r-project.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## 📖 Overview

Blue noise stippling transforms photographs into elegant patterns of dots (stipples) while preserving visual information. This project implements a modified **void-and-cluster algorithm** that combines importance sampling with blue noise distribution properties.

**Key Features:**
- ✅ Visual accuracy through intelligent importance mapping
- ✅ Even dot distribution using blue noise properties
- ✅ Progressive GIF animations
- ✅ Dual language support (Python & R)

---

## 🚀 Quick Start

### Installation

**Python:**
```bash
pip install numpy pillow matplotlib
```

**R:**
```r
install.packages(c("imager", "magick"))
```

### Usage

1. Place your image in the project directory
2. Update the image path in `index.qmd` (line 49 for Python, line 102 for R)
3. Render: `quarto render index.qmd`
4. View results in `index.html`

---

## 📚 How It Works

The algorithm uses a modified void-and-cluster approach:

1. **Importance Mapping**: Identifies visually important regions (dark areas get more dots)
2. **Energy Field**: Lower energy = higher probability of dot placement
3. **Toroidal Gaussian Repulsion**: Ensures even spacing with blue noise properties
4. **Iterative Selection**: Points selected to minimize energy while maintaining distribution

### Key Parameters

| Parameter | Description | Default |
|-----------|-------------|---------|
| `percentage` | Fraction of pixels to convert to dots | 0.08 |
| `sigma` | Gaussian kernel width (dot spacing) | 0.9 |
| `content_bias` | Weight of importance vs. spatial distribution | 0.9 |
| `extreme_downweight` | Reduction of dots in extreme tones | 0.5 |

---

## 🔧 Customization

### Adjust Importance Mapping
```python
importance_map = compute_importance(
    img_resized,
    extreme_downweight=0.5,      # Reduce dots in extreme tones
    extreme_threshold_low=0.2,    # Dark tone threshold
    extreme_threshold_high=0.8,   # Light tone threshold
    mid_tone_boost=0.4           # Mid-tone enhancement
)
```

### Adjust Stippling Parameters
```python
stipple_pattern, samples = void_and_cluster(
    img_resized,
    percentage=0.08,           # 8% of pixels become dots
    sigma=0.9,                 # Repulsion kernel size
    content_bias=0.9          # Content vs. spatial balance
)
```

---

## 📖 References

- **Bart Wronski**: [Progressive Image Stippling and Greedy Blue Noise Importance Sampling](https://bartwronski.com/2022/08/31/progressive-image-stippling-and-greedy-blue-noise-importance-sampling/)
- **Robert Ulichney**: "Void-and-cluster method for dither array generation" (1993)

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

<div align="center">

**Transform your photographs into art with blue noise stippling**

Made with ❤️ using Quarto, Python, and R

</div>
