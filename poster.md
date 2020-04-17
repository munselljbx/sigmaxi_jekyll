---
---

# Poster
## [FULL POSTER IMAGE (Recommended)](.\assets\images\Shapovalov_Munsell_Jeffrey_POSTER-1.jpg)

***

## ABSTRACT
Under the standard model of Big Bang cosmology, the Lambda Cold Dark Matter (𝚲-CDM) model, astronomers have built an understanding of galactic halo structure from dwarf satellites forming fragments and streams. Dwarf satellites represent remnants of the cannibalism that is believed to have formed large galaxies such as the Milky Way. Astronomers initially identified dwarf spheroidal satellites, but observed 1-2 orders of magnitude less than expected. Observations of these satellites caused a second concern as dwarf spheroidal satellites had circular velocities lower than fitting the 𝚲-CDM model. In the last decade, studying these concerns has progressed as astronomers have discovered ultra-faint dwarf satellites, which tend to exhibit low aggregate luminosities and projected densities. Because of these features, astronomers must use RR Lyrae as stellar tracers to identify UFDs. I develop new catalogs of sparse multi-band and multi-epoch data suitable for time domain astronomy from the NGVS. The survey reaches a depth of *g* ≈ 25.9 mag, meaning it reaches farther RR Lyrae in the Virgo Cluster foreground than ever before. I implement random forest classifier-aided candidate selection of RR Lyrae in the foreground of the Virgo Cluster sky area from the generated catalog. The LSST will revolutionize time domain astronomy by imaging the entire sky every night, and could detect almost all RR Lyrae to >350kpc. This project serves as a precursor to future LSST studies by developing an RR Lyrae candidate selection methodology.  Additionally, it aids the research decisions and design for LSST-based studies by providing a new deep field of RR Lyrae to advance background knowledge of distant stellar tracers.

***

## INTRODUCTION
### BACKGROUND
- **Studying outer Milky Way structure requires tracer objects.** The Milky Way is surrounded by a sparse, spherical distribution of stars known as the "stellar halo". It contains the oldest stars in the Galaxy, and is believed to be made up, in part, of the shredded remains of smaller galaxies that were gravitationally captured and subsequently merged into the Milky Way (Deason 2019).

- **RR Lyrae are one of the most effective stellar tracer old stars.** They are quite old (≥ 10Gyr) and are reasonably bright; they vary with well-known period-luminosity relationships that make them useful as standard candles.

- In the last decade, astronomers have discovered **ultra-faint dwarfs**, which tend to exhibit low aggregate luminosities and projected densities. Because of these features, astronomers must use RR Lyrae to identify them, and RR Lyrae may be the only way to study faint galactic satellites (Kunder et al. 2018). RR Lyrae have been found in all ultra-faint dwarfs searched for variability. 

- **A deep astronomical survey** is required to find and analyze distant RR Lyrae in the Milky Way’s stellar halo. The perfect survey for my research is The Next Generation Virgo Cluster Survey (NGVS): a multi-band (*u\*griz* bandpasses) imaging survey using the Canada-France-Hawaii Telescope (CFHT) MegaCam instrument. In part thanks to its step dithering procedure, fields have cadence varying anywhere from hours to years.

### LITERATURE
- The recent move towards using **sparse multi-band, many-epoch surveys** to study RR Lyrae and other variability picked up with studies such as Hernitshek et al. (2016). 

- In the most recent research, **more focused studies have come to the forefront**, with Medina et al. (2018) finding the most distant known RR Lyrae with Dark Energy Camera’s HiTS. 

- **Experts call for more tracers in similar small, deep fields** to make possible general analysis of Milky Way structures rather than local investigation. 

- They note these kinds of studies are vital in the preparation for the coming revolution of the **Large Synoptic Survey Telescope**, which will be able to measure almost all RR Lyrae to ~350 kpc.

### RESEARCH QUESTION
- This study aims to answer: How can RR Lyrae candidates be identified by time domain analysis using random forest classifier-aided selection on a new catalog generated from raw NGVS data?

### HYPOTHESIS
- It is hypothesized that candidate RR Lyrae will be identified through color and brightness as a function of time via variability statistics tuned with random forest classifiers. The brightness of the RR Lyrae is expected to vary significantly, most notably in the *u\** filter and decreasingly so in the *g*, *i*, and *z* filters.

***

## MATERIALS & METHODS
- **Sesar’s previously identified objects**, though largely incomplete, provide a reliable way to examine expected RR Lyrae behavior in the data (Sesar et al. 2013). 

- Candidate selection begins with **cuts from NGVS catalogued magnitudes** (the composite data provided by the NGVS team, not my new catalog), selecting for low-fuzziness objects and selecting in color-color space.

- NGVS was not designed for time domain analysis, so my methodology works from raw data and **creates new catalogs** for time domain astronomy. 

- **Cutout images** are generated around each measurement of each object to be included in the catalog. After reentering the images and performing photometry,  the uncorrected catalog is compiled. 

- The raw data is not suitable for time domain analysis as variability due to atmospheric and instrumental error will obscure the trends of the objects. Therefore, corrections are made using non variable **reference stars**. This results in the **corrected NGVS catalog** used for analysis.

- **Band sigmas** for each object are combined by weighted mean to create a single variability statistic used for selection. The weights of bands are determined by random forest classifier feature importance.

- The random forest classifier is trained to classify based on band sigmas whether an object is an RR Lyrae. Undersampling is used due to the discrepancy in class size between RR Lyrae and Reference star measurements. The feature importances of the model **weigh the band sigma statistic**.

***

## RESULTS
### COLOR-COLOR SPACE  
- Gaussian density plots show the C-C distribution of known Sesar RR Lyrae. Initial selections are made at 0.25<*u*-*g*<1.05, -0.1<*g*-*i*<0.65, and -0.3<*i*-*z*<0.25. In the case of *u*-*g* vs *g*-*i*. (Figure 4), 47.90% of the 2-D probability distribution falls in this area, and 90.74% of Sesar RR Lyrae.

### RANDOM FOREST WEIGHTS AND BAND SIGMA
- The random forest classifier trained to differentiate RR Lyrae from non-RR Lyrae does so with 98.07% accuracy. However, this also determines class accuracies of 98.5% and 77.5% for reference objects and known RR Lyrae, respectively. This shows that the machined learned classification is not sufficient to resolve RR Lyrae itself, as expected. The use of the random forest is instead, as earlier explained, to determine feature importances.  

- From most important to least, I expect *u\**, *g*, *i*, then *z* to predict RR Lyrae variability, as RR Lyrae vary more towards the blue side of the light spectrum. Consistently, the random forest method determines weights of ~0.65, 0.14, 0.12, and 0.09, for the *u\**, *g*, *i*, and *z* bands, respectively.

- This relationship between the bands is also demonstrated through plots comparing sigmas of different bands. Figure 6, illustrating *i* sigma vs. *g* sigma, displays a disproportionate concentration of RR Lyrae below one-to-one, demonstrating again the greater variability of RR Lyrae in *g* than in *i*. The same pattern is evident for the other bands pairs when plotted.

### BAND SIGMA CLASSIFICATION
- When the weights determined by the random forest classifier are used to take a weighted mean of the sigmas of each band for all objects, candidates can be selected. 

- The cutoff based on one standard deviation above the median of the weighted sigma binned by cataloged *g* magnitude is 0.1 mag. 

- This cutoff results in an RR Lyrae completeness of 98.15% and a reference object completeness of 6.79%. This means the second-stage candidate selection reduces computation for RR Lyrae confirmation by 93.17%, while only throwing out 1.85% of RR Lyrae.

***

## DISCUSSION
### IMPLICATIONS OF RESULTS
**Significance:**
- My research answers the call for deeper RR Lyrae data and **new deep fields**, and the development of methodologies for future LSST work.

- The NGVS is the most modern survey of the Virgo Cluster sky region and reaches *g* ≈ 25.9 mag, containing new potential accessible through my new catalog and methodology (Ferrarese et al. 2012). 

**Accomplishments:**
- **I develop a catalog** of NGVS Data suitable for time domain analysis.

- The time domain analysis portion of my methodology provides **computationally efficient candidate selection that is broadly applicable**. Cutout queries, downloads, image checks and corrections, and photometry were performed on UCSC servers. Now that the new catalog is complete, I or other researchers can apply my time domain analysis procedure to the NGVS at little computational expense. 

### FUTURE WORK
- This project selects candidate RR Lyrae, setting up future validation. Validation requires mass computing power and is, based on expert work, not feasible on personal computer-scale computing.

- I asked an independent expert to apply it to his dataset, and it immediately led to discovering five new RR Lyrae. Light curve fitting was used to confirm the candidate objects. I suggest light curve fitting be performed on all candidates for validation as a follow up to this project, and the expert mentioned is currently working on that project. 

- My variability selection methods do not rely on a unique property of RR Lyrae. These methods can therefore be applied to other variable objects such as QSOs. I recommend QSOs especially as Hernitshek et al. (2016) have proved feasible.

- This study serves as a precursor to the Large Synoptic Survey Telescope (LSST). The LSST will image the entire night sky every few days starting in 2022. One of the specific goals of LSST is to study variable stars such as RR Lyrae. 

***

## REFERENCES
- Belokurov, V., Deason, A. J., Koposove, S. E., et al. 2018, Monthly Notices of the Royal Astronomy Society. doi:10.1093/mnras/sty61.5
- Dambis, A. K., Berdnikov, L. N., Kniazev, A. Y., et al. 2013, Monthly Notices of the Royal Astronomical Society. doi:10.1093/mnras/stt1514
- Deason, A. J., Belokurov, V., Sandars, J. L. 2019, Monthly Notices of the Royal Astronomical Society. doi:10.1093/mnras/stz2793
- Fadeyev, Y. A., 2019, Astronomy letters. doi:10.1134/S1063773719060021
- Ferrarese, L., Côté, P., Cuillandre, J., et al. 2012, The Astrophysical Journal Supplement. doi:10.1088/0067-0049/200/1/4
- Hendel, D., Scrowcroft, V., Johnston, K. V., et al. 2018, Monthly Notices of the Royal Astronomy Society. doi:10.1093/mnras/sty1455
- Hernitschek, N., Schlafly, E. F., Sesar, B., et al. 2016, The Astrophysical Journal. doi:10.1088/0004-6256/146/2/21
- Ivezić, Ž., Vivas, A. K., Lupton, R. H., et al. 2005, The Astronomical Journal. doi:10.1086/427392
- Kunder, A., Valenti, E., Dall’Ora, M., et al. 2018, Space Science Reviews. doi:10.1007/s11214-018-0519-0
- Medina, G. E., Muñoz, R. R., Vivas, A. K., et al. 2018, The Astrophysical Journal. doi:10.3847/1538-4357/aaad02
- Sesar, B., Ivezić, Ž., Scott, S. J., et al. 2013, The Astronomical Journal. doi:10.1088/0004-6256/146/2/21
- Sesar, B., Hernitscheck, N., Sandra, M., et al. 2017, The Astronomical Journal. doi:10.3847/1538-3881/aa661b
- Stringer, K. M., Long, J. P., Macri, L. M., et al. 2019, The Astronomical Journal. doi:10.3847/1538-3881/ab1f46
- Szabados, L. 2019, Contributions of the Astronomical Observatory Skalnaté. arxiv:1902.06620
