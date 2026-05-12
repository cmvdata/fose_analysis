# Peru's Electricity Subsidy Reaches the Wrong Households

**The FOSE covers 76% of Peruvian homes, but half of beneficiaries are not energy-poor — and the causal impact on energy burden is statistically zero.**

Peru's *Fondo de Compensación Social Eléctrica* (FOSE) is the country's main electricity subsidy. It applies to any household consuming up to 140 kWh/month. The political assumption is that low consumption signals vulnerability. This project tests whether that assumption holds.

## Headline result

Using ERCUE 2025 microdata (14,815 households):

| What | Value |
|---|---|
| FOSE coverage | **76.1%** |
| Inclusion error (non-poor receiving subsidy) | **47.5%** |
| Exclusion error (poor not receiving subsidy) | 10.4% |
| Causal impact on energy burden (CEM, ±20 kWh) | **ATT = −2.37 pp, p = 0.330** |
| IPW robustness check | ATT = −2.09 pp, p = 0.376 |

The subsidy reaches almost everyone — but **nearly half** of beneficiaries are not actually energy-poor, and there's no statistically detectable effect on the targeted outcome. The 140 kWh threshold is the wrong instrument.

## Why this is non-obvious

- High coverage looks good in headlines. The inclusion error is what hides the policy failure.
- Low consumption is **not** a clean proxy for energy poverty in Peru: many low-consumption households are small but middle-class urban units, while energy-poor rural households often have erratic consumption above the threshold.
- The result is robust: CEM, IPW, multiple bandwidths (±10 to ±40 kWh), and a counterfactual simulation all agree.

## How it works

- **Coarsened Exact Matching** around the 140 kWh threshold as main identification strategy.
- **Inverse Probability Weighting** as robustness check.
- **Regression Discontinuity discarded**: bunching at the threshold (households deliberately staying under 140 kWh) violates the continuity assumption.
- **Counterfactual simulation**: what would energy burden be without the FOSE? +3.2 pp for eligible households.
- **Bandwidth sensitivity** confirms ATT stability across windows.

## Stack

Python · pandas · scikit-learn · matplotlib · Jupyter

## Run it

```bash
pip install pandas numpy matplotlib seaborn scikit-learn pyarrow openpyxl
jupyter notebook notebooks/Calculo_CEM.ipynb       # main analysis
jupyter notebook notebooks/Contexto_FOSE.ipynb     # descriptive context
```

Notebooks were developed in Google Colab; comment out `from google.colab import files` lines if running locally.

## More

- **Full report (PDF)**: [`docs/paper_fose.pdf`](docs/paper_fose.pdf)
- **Data**: ERCUE 2019/2023/2025 microdata (MINEM/OSINERGMIN). Not redistributed.

---

*Máster Universitario en Economía, Regulación y Competencia en los Servicios Públicos — Universitat de Barcelona, 2026.*
