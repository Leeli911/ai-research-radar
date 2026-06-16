# Topic Map - Distribution Shift and Model Reliability

## Purpose

Study how machine learning models fail when training and deployment data differ, and how evaluation can reveal or reduce this failure.

中文定位: 这是最直接连接我的 thesis 的主线, 因为 historical domain shift 本质上就是数据分布随时间变化导致模型可靠性下降。

## Core Questions

- How can we define and measure distribution shift in real applications?
- Which shifts are most harmful to model reliability?
- How can models be evaluated before deployment when the future data distribution is unknown?
- Can monitoring detect performance degradation without full labels?
- How can historical data help predict future model failure?

## Keywords

- distribution shift
- dataset shift
- domain shift
- temporal shift
- out-of-distribution generalization
- model reliability
- model monitoring
- uncertainty estimation
- robustness evaluation

## Datasets and Benchmarks to Watch

- WILDS-style benchmarks
- DomainBed-style benchmarks
- Temporal image datasets
- Medical and demographic datasets with time or site shift
- Real-world monitoring datasets
- Fine-grained visual classification datasets

## Evaluation Metrics

- Accuracy under shift
- Worst-group accuracy
- Calibration error
- Error by time period
- Error by subgroup
- OOD detection AUROC
- Monitoring delay
- False alarm rate

## Open Research Gaps

- Many benchmarks simplify shift into fixed source and target domains.
- Temporal shift is often under-studied compared with synthetic corruptions.
- Monitoring methods often assume labels are available quickly.
- Average accuracy can hide subgroup-specific degradation.
- Model reliability is rarely connected to decision consequences.
- Many drift methods still describe that change happened, but do not localize which subgroup is degrading most.
- Intervention papers often evaluate a single correction under one shift, without testing whether the correction remains stable under later shifts.

## Connection to My Background

My previous thesis on facial age estimation under historical domain shift can become evidence that visual models are sensitive to time, demographic composition, data collection conditions, and historical context.

Possible bridge sentence:

> My previous work studied facial age estimation under historical domain shift, which motivates a broader PhD direction on how machine learning systems can be evaluated and monitored when deployment data changes over time.

## What to Collect Daily

- Papers on temporal shift, OOD generalization, and monitoring
- Benchmarks that include real distribution changes
- Methods that estimate reliability without dense labels
- Evaluation studies showing hidden subgroup errors under shift
- Methods for hierarchical diagnosis that connect subgroup decay to shift mechanisms

## Proposal Angles

- Evaluation protocols for historical or temporal domain shift
- Subgroup-aware model monitoring under changing data
- Data-centric methods for diagnosing shift in visual datasets
- Decision-relevant reliability metrics for deployed ML systems
- Heterogeneous deployment decay analysis instead of average drift reporting

## Week 03 Stable Additions

- Treat distribution shift as a dynamic reliability surface rather than one source-target score: subgroup, time window, representation density, and uncertainty coverage can drift at different rates.
- Add temporal validity metrics to the evaluation vocabulary: subgroup Stability Horizon, Drift Horizon, Temporal Transfer Ratio, and detection lead time.
- Hidden-slice discovery is now part of the distribution-shift map: OOD subsets can reverse model-ranking conclusions even when aggregate OOD metrics look stable.
- For my thesis extension, historical portrait shift should be evaluated by asking which subgroup or hidden slice degrades first, not only whether global MAE changes.

## Week 04 Stable Additions

- Distribution-shift evaluation should first check the comparison baseline: target-population mixture, finite-sample reweighting variance, and shrinkage-corrected subgroup evaluation can change whether an intervention looks helpful or harmful.
- Shift should be modeled hierarchically, not only between named groups: elderly portraits may contain within-group period, source, image-quality, and visual-style shifts that coarse age/gender tables miss.
- Mechanism diagnosis should come before intervention choice: hidden visual concepts, localized harmful clusters, conditional routing, and subgroup mixture mismatch can produce similar worst-group degradation.
- For my thesis extension, balancing and cascaded routing should be evaluated under corrected target mixtures and hidden or hierarchical subgroups before I claim they truly improve elderly reliability.
