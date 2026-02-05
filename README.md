# A Color Preserving Tone Mapping Framework in the Intrinsic Domain

[![Conference](https://img.shields.io/badge/Conference-LIM_2025-blue)](https://iopscience.iop.org/article/10.1088/1742-6596/3128/1/012008)


**Authors:** S. Melcarne¹, P. Cyriac², J.L. Dugelay¹, A. Artusi³, F. Banterle⁴

¹ *Eurecom Research Center, Sophia Antipolis, France* ² *Huawei Nice Research Center, Mougins, France* ³ *DeepCamera MRG, RISE Ltd, Nicosia, Cyprus* ⁴ *Visual Computing Lab, ISTI-CNR, Pisa, Italy*

<p align="center">
  <img src="figures/teaser_lasvegas.jpg" alt="Proposed framework" width="100%">
</p>

---

## Publication
This paper has been accepted for publication at the **6th London Imaging Meeting (LIM 2025)** and appears in the **IOP Journal of Physics: Conference Series**.

---

## Abstract
Tone mapping is an essential step in an acquisition or a rendering pipeline to map high dynamic range (HDR) content to a reference display range. The simplest tone mapping approach is to apply a function to the luminance channel of an HDR image and then to propagate the change to the red, green, and blue channels. However, this often causes color distortions since luminance and chrominance channels are interdependent. We propose a novel tone mapping approach that preliminarily decomposes the image into intrinsic components (Reflectance and Shading) and leverages them to perform the actual operation. This strategy effectively mitigates color distortions, eliminating the need for post-processing color correction required by many state-of-the-art methods, and it also assists tone mapping operators (TMOs), improving the overall image quality.

## The Framework

<p align="center">
  <img src="figures/intrinsic_pipeline_LIM.png" alt="Proposed framework" width="100%">
</p>


Our method formulates tone mapping in the **intrinsic domain**. Instead of processing the luminance channel directly, we decompose the image into:
1.  **Reflectance ($R$):** Invariant to illumination changes (spectral properties/colors).
2.  **Shading ($S$):** Accounts for illumination effects and high dynamic range.

The pipeline consists of the following steps:
1.  **Encoding:** Input HDR is encoded using **NORGAMMA** (Normalization + Gamma correction) to preserve details.
2.  **Decomposition:** An Intrinsic Image Decomposition (IID) network separates the image into $R$ and $S$.
3.  **Tone Mapping:** The TMO is applied **only to the Shading component** ($S$), leaving the Reflectance ($R$) untouched to preserve original colors.
4.  **Recombination & Refinement:** The components are recombined, and a brightness refinement step normalizes the output.


## Repository Structure
* `paper/`: Contains the camera-ready version of the paper.
* `supplementary_material/`: Additional qualitative comparisons and details on the psychophysical experiment.

## Citation

If you find this work useful for your research, please cite our paper:

```bibtex
@inproceedings{melcarne2025color,
  title={A Color Preserving Tone Mapping Framework in the Intrinsic Domain},
  author={Melcarne, S. and Cyriac, P. and Dugelay, J.L. and Artusi, A. and Banterle, F.},
  booktitle={London Imaging Meeting (LIM)},
  series={Journal of Physics: Conference Series},
  year={2025},
  publisher={IOP Publishing}
}
