# My MR Collections

> This is my personal space to store and share brilliant MRI tutorials and source codes.
> Huge thanks to all contributors! 🥳

## 📚 Tutorials

### 1. \[Stanford] RAD 229: Brilliant Class on MRI Signal & Sequence Design

> Stanford University course (Dr. Daniel Ennis & Dr. Brian Hargreaves). Covers everything from the fundamentals of MRI signal formation to advanced sequence design. Includes open-access videos, slides, and code.

* Links: \[[Home Page](https://web.stanford.edu/class/rad229/index.html)] \[[YouTube Videos](https://www.youtube.com/channel/UCJgAoFeFMKQ-f1XVPrFBslQ)] \[[Slides](https://web.stanford.edu/class/rad229/Notes.html)] \[[GitHub Repo](https://github.com/mribri999/MRSignalsSeqs)] \[[My Updated Version](https://github.com/ZihanNing/MRSignalsSeqs/tree/ZN_testing)]
* Highlights: MR signal simulation (Bloch/EPG) and excellent coverage of commonly used sequences and their characteristics.

### 2. Interactive Book: Principles of MRI

> A fantastic interactive book with demos and source code to explain MRI physics. Perfect for those who prefer reading over watching lectures.

* Links: \[[Home Page](https://larsonlab.github.io/MRI-education-resources/Introduction.html)] \[[Suggestions from README](https://github.com/larsonlab/MRI-education-resources)]

### 3. Questions & Answers in MRI

> Probably the most famous MRI Q\&A site. A true “dictionary” of MRI knowledge.

* Links: \[[Home Page](https://www.mriquestions.com/index.html)]

### 4. \[UCSF] BI 201: Principles of MRI

> UCSF’s BI 201 lectures (Dr. Peder Larson) — comprehensive and beginner-friendly, with some introductory reconstruction tutorials.

* Links: \[[YouTube Playlist](https://www.youtube.com/playlist?list=PLjBt5Iq93BT9eXMsgevVTXKVv4BgVLB1X)] \[[Larson Lab GitHub](https://github.com/LarsonLab)]

### 5. Video Series: *Introducing MRI*

> Short, topic-focused videos from Albert Einstein College of Medicine. Each video answers a single question.

* Links: \[[YouTube Playlist](https://www.youtube.com/playlist?list=PLPcImQzEnTpz-5TzxyyoYSbiAa9xdd89l)]

### 6. Two Classic E-Books on NMR & MRI

> Dr. Joseph P. Hornak’s well-known e-books — must-reads for understanding the basics of NMR and MRI.

* Links: \[[Basics of NMR](https://www.cis.rit.edu/htbooks/nmr/)] \[[Basics of MRI](https://www.cis.rit.edu/htbooks/mri/)]

---

## 🛠️ My Favourite / Most-Used Toolboxes & Software

### 1. ITK-SNAP

> Free, open-source software for segmenting 3D and 4D biomedical images. **I use it daily for quick image reviews (NIfTI format).**

* Links: \[[Home Page](https://www.itksnap.org/pmwiki/pmwiki.php)]

### 2. elastix

> Open-source toolbox for rigid and non-rigid image registration. **I rely on it heavily for brain and kidney image registrations in my projects.**

* Links: \[[Home Page](https://elastix.dev)] \[[User Manual](https://elastix.dev/download.php)] \[[Model Zoo](https://lkeb.ml/modelzoo/)]

### 3. SPM12

> Toolbox for modelling and testing hypotheses about functional imaging data.
> **I use it for brain segmentation, registration, and as a backend for NIfTI I/O in many of my custom tools — a must-have for MATLAB users.**

* Links: \[[Home Page](https://www.fil.ion.ucl.ac.uk/spm/)]

### 4. 3D Slicer

> Free, open platform for medical image visualization, processing, segmentation, registration, and statistics. **Great for manual workflows — the community constantly contributes new tools.**

* Links: \[[Home Page](https://www.slicer.org)]

---

## 💻 Open-Source Code & Software

### 1. Stanford SLR RF Pulse Design Code

> MATLAB routines by John Pauly for RF pulse design using the Shinnar-Le Roux algorithm.

* Links: \[[Home Page](https://rsl.stanford.edu/research/software.html)] \[[Manual](https://rsl.stanford.edu/download/pauly/rftools-manual.pdf)]

---

## 🌐 Collections

### 1. Dr. Mark Chiew’s Home Page

> A model example of a research homepage — includes open-sourced code, teaching slides, and reconstruction tools.

* Links: \[[Home Page](https://mchiew.github.io/index.html)] \[[Code by Publication](https://mchiew.github.io/Research.html)] \[[Teaching Slides](https://mchiew.github.io/Teaching.html)] \[[MR Recon MATLAB Code](https://mchiew.github.io/Tools.html)]
* Recommended Repos:

    * **[recon-tools-matlab](https://github.com/mchiew/recon-tools-matlab)** — ADMM, CG, dictionary learning, denoising, and more (MATLAB).

### 2. MR-Hub: ISMRM Open-Source Tool Collection

> Maintained by the **ISMRM Reproducibility Research Study Group** — features validated, community-approved MR software.

* Links: \[[Home Page](https://ismrm.github.io/mrhub/)]
* Highlights I’ve Used:

    * **[MRtrix3](https://www.mrtrix.org)** — diffusion MRI tools (used for Gibbs ringing removal).
    * **[BART](http://mrirecon.github.io/bart/)** — reconstruction toolbox (used for ESPIRiT coil sensitivity estimation).
    * **[Gadgetron](http://gadgetron.github.io)** + **[ISMRMRD](https://ismrmrd.github.io/apidocs/1.5.0/)** — inline recon platform and data format (used in many of my recon pipelines). \[[My Practical Inline Recon Framework](https://github.com/ZihanNing/Practical_Inline_Recon_Framework-public.git)]
    * **[KomaMRI](https://github.com/JuliaHealth/KomaMRI.jl)** — flexible signal simulation and k-space trajectory plotting.
    * **[gpuNUFFT](https://github.com/andyschwarzl/gpuNUFFT)** — GPU-accelerated NUFFT solver, MATLAB-friendly (used for sodium imaging recon).

### 3. NYU Collection: Open-Source Data & Code

> MRI datasets, reconstruction code, RF simulation tools, and image analysis software from NYU CAI2R.

* Links: \[[Home Page](https://cai2r.net/resources/#reconstruction-code)]
* Highlights:

    * **[fastMRI](https://cai2r.net/resources/fastmri-dataset/)** — large raw k-space dataset for ML research.
    * **[AGILE](https://cai2r.net/resources/agile-gpu-image-reconstruction-library/)** — GPU-accelerated linear/non-linear recon.
    * **[MPPCA](https://cai2r.net/resources/denoising-using-marchenko-pastur-principal-component-analysis/)** — diffusion denoising method.
    * **[gpuNUFFT](https://cai2r.net/resources/gpunufft-an-open-source-gpu-library-for-3d-gridding-with-direct-matlab-interface/)** — fast non-Cartesian NUFFT.
    * **[GRASP / RACER-GRASP / XD-GRASP](https://cai2r.net/resources/)** — popular respiratory motion correction techniques.
    * **[k-t sparse sense](https://cai2r.net/resources/k-t-sparse-sense-matlab-code/)** — dynamic MRI reconstruction code.
    * **[L+S Recon](https://cai2r.net/resources/ls-reconstruction-matlab-code/)** — low-rank + sparse dynamic reconstruction (MATLAB).

### 4. Michigan Image Reconstruction Toolbox (MIRT)

> MATLAB collection for image reconstruction and RF pulse design, developed by Jeff Fessler.

* Links: \[[Home Page](https://web.eecs.umich.edu/~fessler/code/index.html)] \[[Download](http://web.eecs.umich.edu/~fessler/irt/fessler.tgz)] \[[GitHub](https://github.com/JeffFessler/mirt)]
* Highlights:

    * **[Image Reconstruction Toolbox](https://web.eecs.umich.edu/~fessler/code/mri.htm)** — GPU-enabled NUFFT, SENSE (Cartesian & non-Cartesian), field map estimation, compressed sensing.
    * **RF Pulse Design** — spectral-spatial pulses and phase-precompensated slice selection.

### 5. ISMRM Links of Interest

> A comprehensive collection of MR communities, journals, websites, tutorials, and software.

* Links: \[[Home Page](https://www.ismrm.org/resources/mr-sites/)]
