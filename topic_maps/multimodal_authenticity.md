# Topic Map - AIGC Authenticity and Multimodal Trust

## Purpose

Study how to detect, evaluate, and govern AI-generated or manipulated multimodal content, especially images and image-text content.

中文定位: 这条线和你的 CV 背景相关, 也有现实影响力。需要注意不要只追生成模型热点, 要聚焦 authenticity, provenance, evaluation, and trust。

## Core Questions

- How can AI-generated images or multimodal content be detected reliably?
- How do detectors fail under distribution shift, compression, editing, or new generators?
- What datasets and benchmarks are suitable for authenticity evaluation?
- Can provenance signals complement detection models?
- How should authenticity systems be evaluated for real-world use?

## Keywords

- AIGC detection
- AI-generated image detection
- deepfake detection
- multimodal misinformation
- provenance detection
- content authenticity
- watermarking
- synthetic image detection
- robustness under shift

## Datasets and Benchmarks to Watch

- AI-generated image detection datasets
- Deepfake and face manipulation datasets
- Image provenance and watermarking benchmarks
- Multimodal misinformation datasets
- Cross-generator evaluation datasets
- Compression and post-processing robustness benchmarks

## Evaluation Metrics

- Accuracy and F1
- AUROC
- Cross-generator generalization
- Robustness to compression and editing
- False positive rate on real images
- Performance under distribution shift
- Calibration and uncertainty

## Open Research Gaps

- Detectors often overfit to known generators.
- Benchmarks can become obsolete as generation models change.
- False positives on real images can create serious trust problems.
- Provenance metadata may be missing or stripped.
- Multimodal misinformation requires more than image-level detection.

## Connection to My Background

Your facial age estimation work can connect to authenticity research through visual reliability under changing image distributions. A detector trained on one generation period or image style may fail as synthetic image tools change, similar to how age estimation may fail across historical visual domains.

## What to Collect Daily

- New AIGC or synthetic image detection papers
- Cross-generator robustness studies
- Provenance and watermarking research
- Multimodal misinformation benchmarks
- Evaluation papers about detector failure modes

## Proposal Angles

- Distribution shift in AI-generated image detection
- Reliability evaluation for authenticity detectors over time
- Data-centric benchmark design for multimodal trust
- Subgroup and false-positive analysis in AIGC detection

