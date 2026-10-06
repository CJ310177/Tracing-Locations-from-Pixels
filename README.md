# Tracing Locations from Pixels: A Survey of Worldwide Image Geo-localization

**The first dedicated survey of Worldwide Image Geo-localization (WIGL)** — systematically organizing 30 representative methods into four paradigms (classification-based, retrieval-based, generation-based, and retrieval-augmented generation), with datasets, evaluation metrics, and benchmark results.

> **News**
> - **2026.10.01** 🎉 Our survey was **accepted** by *Information Processing and Management* (IPM).
> - **2026.05.26** 📄 Submitted to IPM.

---

## 📖 Introduction

**Worldwide image geo-localization (WIGL)** aims to estimate the geographic coordinates of a photograph from its visual content alone — with **no metadata** on the query image (no EXIF GPS, no user tags) and **no known search area**, so the hypothesis space is the entire Earth's surface. This capability supports practical applications including cybercrime source tracing, disaster response, autonomous navigation, and location-aware analysis of social media content.

This survey presents a comprehensive review of WIGL and makes the following contributions:

- **A unified four-paradigm taxonomy.** We systematically organize current methods into **classification-based**, **retrieval-based**, **generation-based**, and **retrieval-augmented generation (RAG)** approaches — the first survey to analyze all four paradigms with equal depth, elucidating their core design principles, strengths, and limitations.
- **In-depth dataset analysis.** We review training, test, and fine-tuning datasets, and reveal notable geographic coverage biases via spatial distribution analysis.
- **Standardized evaluation.** We consolidate evaluation metrics and compile reported results across six test sets, providing a common basis for performance comparison. RAG approaches currently achieve the highest accuracy on major benchmarks, while generation-based approaches offer a promising alternative for zero-shot location inference.
- **Outlook.** We identify under-explored challenges — such as disambiguating visually similar scenes captured thousands of kilometers apart, unified location encoding, data distribution bias, and interpretable spatial reasoning — to guide future work.

---

## 🧭 Four Paradigms at a Glance

| Paradigm | Core idea | Strength | Limitation |
|---|---|---|---|
| **Classification-based** | Partition the Earth into geographic cells; classify the image into a cell and output its center | End-to-end, no external database at inference | Accuracy bounded by grid granularity |
| **Retrieval-based** | Match the query against a pre-built geotagged image database; return coordinates of the nearest neighbors | Highly flexible, continuously improvable | Costly database construction & maintenance |
| **Generation-based** | Fine-tune LMMs (e.g., LoRA) to generate coordinates directly | Zero-shot potential, rich prior knowledge | Vulnerable to hallucination, weak spatial constraints |
| **RAG** | Retrieve candidate locations first, then let an LMM reason over them to infer coordinates | Balances reliability and flexibility | Depends on retrieval quality and backbone scale |

---

## 🛠 Methods & Code

Representative WIGL methods by paradigm, with links to publicly available official implementations (as compiled in the survey).

### Classification-based Methods

| Method | Year | Venue | Code |
|---|---|---|---|
| PlaNet | 2016 | ECCV'16 | [github.com/google-research/planet](https://github.com/google-research/planet) |
| CPlaNet | 2018 | ECCV'18 | — |
| ISNs | 2018 | ECCV'18 | [github.com/TIBHannover/GeoEstimation](https://github.com/TIBHannover/GeoEstimation) |
| MvMF | 2019 | ECML-PKDD'19 | — |
| G³ | 2022 | EMNLP'22 | [github.com/g-luo/geolocation_via_guidebook_grounding](https://github.com/g-luo/geolocation_via_guidebook_grounding) |
| SemP | 2022 | WACV'22 | [github.com/jtheiner/semantic_geo_partitioning](https://github.com/jtheiner/semantic_geo_partitioning) |
| TransLocator | 2022 | ECCV'22 | [github.com/ShramanPramanick](https://github.com/ShramanPramanick) |
| GeoDecoder | 2023 | CVPR'23 | — |
| PIGEON | 2024 | CVPR'24 | [github.com/LukasHaas/PIGEON](https://github.com/LukasHaas/PIGEON) |

### Retrieval-based Methods

| Method | Year | Venue | Code |
|---|---|---|---|
| IM2GPS | 2008 | CVPR'08 | — |
| [L]kNN, σ=4 | 2017 | ICCV'17 | [github.com/lugiavn/revisiting-im2gps](https://github.com/lugiavn/revisiting-im2gps) |
| GeoCLIP | 2023 | NeurIPS'23 | [github.com/VicenteVivan/geo-clip](https://github.com/VicenteVivan/geo-clip) |
| GT-Loc | 2025 | ICCV'25 | [github.com/dshatwell23/gtloc](https://github.com/dshatwell23/gtloc) |
| GeoSURGE | 2026 | CVPR'26 | — |

### Generation-based Methods

| Method | Year | Venue | Code |
|---|---|---|---|
| GeoReasoner | 2024 | ICML'24 | [github.com/lingli1996/GeoReasoner](https://github.com/lingli1996/GeoReasoner) |
| RFM | 2025 | CVPR'25 | [github.com/nicolas-dufour/plonk](https://github.com/nicolas-dufour/plonk) |
| GRE Suite | 2025 | NeurIPS'25 | [github.com/Thorin215/GRE](https://github.com/Thorin215/GRE) |
| GLOBE | 2025 | NeurIPS'25 | [github.com/lingli1996/globe](https://github.com/lingli1996/globe) |
| GaGA | 2025 | arXiv'25 | — |
| GAEA | 2026 | WACV'26 | [github.com/UCF-CRCV/GAEA](https://github.com/UCF-CRCV/GAEA) |
| Geo-R | 2026 | AAAI'26 | [github.com/aialt/geo-r](https://github.com/aialt/geo-r) |
| GeoBayes | 2026 | AAAI'26 | — |
| SpotAgent | 2026 | arXiv'26 | [github.com/Dai0-2/Spotagent](https://github.com/Dai0-2/Spotagent) |

### RAG (Retrieval-Augmented Generation) Methods

| Method | Year | Venue | Code |
|---|---|---|---|
| Img2Loc | 2024 | SIGIR'24 | [github.com/zhangjielu321/Img2Loc](https://github.com/zhangjielu321/Img2Loc) |
| G³ (NeurIPS) | 2024 | NeurIPS'24 | [github.com/Applied-Machine-Learning-Lab/G3](https://github.com/Applied-Machine-Learning-Lab/G3) |
| GeoRanker | 2025 | NeurIPS'25 | [github.com/Applied-Machine-Learning-Lab/GeoRanker](https://github.com/Applied-Machine-Learning-Lab/GeoRanker) |
| GeoToken | 2025 | ICDM'25 | [github.com/NNargesNN/GeoToken](https://github.com/NNargesNN/GeoToken) |
| GEOMR | 2026 | KBS'26 | — |
| **DualGeo** | 2026 | **ICME'26** | [github.com/CJ310177/DualGeo](https://github.com/CJ310177/DualGeo) |
| GeoRouter | 2026 | arXiv'26 | — |

> **Notes** (from the survey):
> - *G³* (EMNLP'22) performs localization through classification but leverages location-discriminative text from the GeoGuessr community, laying a practical foundation for subsequent generation-based methods.
> - *RFM* does not use an LMM; it is categorized as generation-based because its mathematical formulation provides a solid foundation for LMM-based generation approaches to mitigate hallucination.
> - *GeoSURGE* operates over geographic cells instead of real coordinate samples; its retrieved geographic-cell rankings can provide reference candidates for downstream RAG applications.
> - "—" indicates that no public official implementation was available at the time of writing.

---

## 📚 Datasets & Download Links

### Training Datasets

| Dataset | Year | Description | Download |
|---|---|---|---|
| IM2GPS | 2008 | The first large-scale geo-localization dataset (~6.47M valid images from Flickr); not publicly released | [Project page](https://graphics.cs.cmu.edu/projects/im2gps/) |
| MP-16 | 2016 | Selected from YFCC100M; the standard dataset of the MediaEval 2016 Places task; a mainstream WIGL training choice | [TIB service](https://service.tib.eu/ldmservice/vdataset/luh-extended-mp-16-dataset) |
| MP16 Pro | 2024 | Extended MP-16 (~4.23M images) with multi-level geographic text descriptions at eight hierarchical levels | [Hugging Face](https://huggingface.co/datasets/Jia-py/MP16-Pro/tree/main) |
| OSV5M | 2024 | Street-view dataset from Mapillary covering 225 countries/regions; ~4.89M training + ~0.21M test images | [Hugging Face](https://huggingface.co/datasets/osv5m/osv5m) |

### Test Datasets (Benchmarks)

| Dataset | Year | Description | Download |
|---|---|---|---|
| IM2GPS Test | 2008 | 237 high-purity samples from IM2GPS; a core early benchmark | [Download (zip)](https://graphics.cs.cmu.edu/projects/im2gps/gps_query_imgs.zip) |
| IM2GPS3k | 2017 | 2,997 images from IM2GPS with region/city/scene annotations; one of the most widely used test sets | [Download (MediaFire)](http://www.mediafire.com/file/7ht7sn78q27o9we/im2gps3ktest.zip) |
| YFCC4k | 2017 | 4,536 images from YFCC100M; diverse scene types demanding generalization | [Download (MediaFire)](http://www.mediafire.com/file/3og8y3o6c9de3ye/yfcc4k.zip) |
| YFCC26k | 2018 | 25,600 geo-tagged images from YFCC100M; large-scale validation | [Kaggle](https://www.kaggle.com/datasets/lbgan2000/img2gps-yfcc4k/data) |
| GWS15k | 2023 | 14,955 street-view images over 193 countries, sampled proportional to country land area to counter distribution bias | [github.com/wp4032/gws15k](https://github.com/wp4032/gws15k) |
| OSV5M-test | 2024 | Test split of OSV5M (street-view; see above) | [Hugging Face](https://huggingface.co/datasets/osv5m/osv5m) |

### Fine-tuning Datasets (for LMM-based methods)

| Dataset | Year | Description | Download |
|---|---|---|---|
| GRE30K | 2025 | 30K samples in two subsets: GRE30K-CoT (20K chain-of-thought reasoning triplets) and GRE30K-Judge (10K reasoning-judgment samples for RL) | [github.com/Thorin215/GRE](https://github.com/Thorin215/GRE) |
| MP16-Reason | 2025 | ~45K samples (33K train / 12K test) built to train GLOBE's geographic reasoning ability, with deliberate geographic generalization splits | [Hugging Face](https://huggingface.co/datasets/globe-project/MP16-Reason/tree/main) |

---

## 📏 Evaluation Metrics

- **Distance threshold metrics** (de facto standard): accuracy within 1 km (street), 25 km (city), 200 km (region), 750 km (country), and 2500 km (continent), computed with the Haversine distance.
- **Gamified scoring (GeoScore)**: a 0–5000 exponential-decay score inspired by GeoGuessr; intuitive for science communication.
- **Administrative region metrics**: match predicted coordinates to hierarchical geopolitical units (continent → country → province → city) via reverse geocoding.

---

## 🔮 Open Challenges & Future Directions

1. **Resolving semantic-spatial mismatch** — disambiguating visually similar scenes captured at distant locations.
2. **Unified location encoding** — reconciling discrete cells, continuous coordinates, and textual place descriptions.
3. **Overcoming data distribution bias** — Flickr-sourced benchmarks are heavily skewed toward North America and Europe.
4. **Interpretable spatial reasoning** — making LMM coordinate predictions trustworthy and verifiable.
5. **Ethical, privacy, and dual-use considerations** — responsible deployment of geo-localization technology.

---

## 📝 Citation

If you find this survey useful, please cite:

```bibtex
@article{cui2026tracing,
  title   = {Tracing Locations from Pixels: A Survey of Worldwide Image Geo-localization},
  author  = {Cui, Junchao},  % TODO: complete the author list
  journal = {Information Processing and Management},
  year    = {2026},
  note    = {Accepted}
}
```

---

## 🔗 Links

- Author homepage: [cj310177.github.io](https://cj310177.github.io/)
- DualGeo (ICME 2026): [github.com/CJ310177/DualGeo](https://github.com/CJ310177/DualGeo)
