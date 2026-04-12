# Research Poster Checklist

## Title Banner
- [ ] Project title (large, readable from 10 feet)
- [ ] Your name and institution
- [ ] Any logos (university, lab, funding body)

## Introduction (~10% of space)
- [ ] Why zoonotic spillover is hard to predict
- [ ] Gap in existing models (most don't combine genomic + behavioral data)
- [ ] One-sentence statement of what your project does differently

## Methods (~30% of space)
- [ ] Brief description of the dataset (NCBI viral sequences, 3.25M rows)
- [ ] Phylogenetic risk scoring via NCBIPhyloEstimator (TimeTree divergence times)
- [ ] Stochastic SIR/SEIR model with Monte Carlo simulation
- [ ] How genomic features and host data feed into the model
- [ ] Note on Gathering Intensity algorithm (frame as "in development")

## Results (~35% of space)
- [ ] Geographic risk heatmap (centerpiece visual)
- [ ] Top high-risk host species by phylogenetic risk score
- [ ] Example model output (spillover probability distribution)
- [ ] Any key statistics worth calling out (e.g. host species analyzed, regions covered)

## Discussion (~15% of space)
- [ ] What the results suggest about spillover hotspots
- [ ] Limitations (missing data in Genotype/Tissue columns, Gathering Intensity incomplete)
- [ ] How this model improves on existing approaches

## Next Steps (~5% of space)
- [ ] Completing the Gathering Intensity algorithm
- [ ] Launching the interactive dashboard
- [ ] Validating against known historical spillover events

## Footer
- [ ] References (abbreviated)
- [ ] Acknowledgments / funding sources
- [ ] Your contact email
- [ ] QR code linking to your GitHub or paper
