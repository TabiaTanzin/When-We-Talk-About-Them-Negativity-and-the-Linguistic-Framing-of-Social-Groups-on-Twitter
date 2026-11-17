# When We Talk About Them: Negativity and the Linguistic Framing of Social Groups on Twitter

**Research code and analysis materials for a longitudinal study of social-group discourse on Twitter (X), 2012–2022.**

This project examines how eight social identities—**Muslims, Liberals, Conservatives, Immigrants, Jews, LGBTQ+ individuals, Black Americans, and Refugees**—are discussed on Twitter (X). We study changes in group-reference prevalence, affective language, word use, semantic associations, and discussion topics. The goal is to describe how the linguistic framing of social groups differs across identities and over time.

## Research questions

1. **Temporal patterns:** How do the prevalence and evaluative framing of social-group references change over time?
2. **Affective framing:** How do lexical happiness and multidimensional linguistic characteristics differ across identities and evolve over time?
3. **Lexical and semantic associations:** Which words and semantic associations distinguish discourse about different groups?
4. **Thematic context:** Which themes characterize group-referencing discourse, and how are they associated with lexical happiness?

## Data collection and annotation

We retrieve candidate tweets and retweets from the **DataMountain** Twitter archive using predefined group-related keywords and expressions. A two-stage pipeline then identifies relevant social-group references:

1. **Heuristic filtering** retrieves candidate posts containing group-related terms.
2. **LLM quality assurance and annotation** filters for relevant group references and assigns a target-group label and an evaluative comment-type label (*Discriminatory*, *Supportive*, or *Neutral*).

The study uses **Llama-3.1-8B-Instant** for full-corpus annotation, selected after evaluation against a consensus-labeled sample of **200 tweets** annotated by two humans (inter-annotator Cohen's κ = **0.74**). On this evaluation set, the selected model achieved weighted F1 scores of **0.62** for target-group identification and **0.77** for comment-type classification.

### Annotation workflow

![Two-stage annotation pipeline showing keyword-based heuristic filtering followed by LLM quality-assurance filtering of candidate social-group tweets.](LLM_Labeled_Data/annotation_pipleline.pdf)

*Figure: Illustrative examples of Phase 1 heuristic retrieval and Phase 2 LLM-based filtering. The figure illustrates the annotation process; it does not represent the full analysis workflow. [View the original PDF](LLM_Labeled_Data/annotation_pipleline.pdf).*

## Methods

| Analysis | Purpose |
| --- | --- |
| **Temporal modeling** | Model monthly group-reference prevalence, accounting for sampled Twitter volume and seasonality. |
| **Hedonometrics (labMT)** | Quantify frequency-weighted lexical happiness and its changes over time. |
| **Ousiometrics** | Analyze Goodness, Aggression, Structure, Power, and Danger in group-referencing language. |
| **Word shifts** | Identify individual words contributing to happiness differences relative to general Twitter discourse. |
| **Allotaxonometry** | Compare ranked word-frequency distributions using rank-turbulence divergence (RTD), independently of sentiment. |
| **Semantic projections** | Explore associations between group-related terms and Power, Danger, and Goodness axes. |
| **Thematic clustering** | Identify 25 recurring lexical themes and examine their relationships with social identity and lexical happiness. |

For comparisons with general Twitter vocabulary, the analysis uses a **separate 10% random sample of general tweets** as a reference corpus. This is distinct from the keyword-retrieved group-referencing dataset.

## Main findings

- **Changing attention:** Normalized group-reference prevalence follows nonlinear trajectories. In the primary model, all eight groups show significant increases between June 2015 and June 2019; seven show declines between June 2019 and June 2022.
- **Negatively valenced vocabulary:** All eight group-referencing corpora have lower lexical happiness than the general Twitter reference corpus. Word shifts identify contributions from words associated with conflict, discrimination, violence, and group-specific contexts.
- **Linguistic diversity:** Allotaxonometry reveals distinct word-frequency patterns across political, religious, racial, and migration-related discourse; the degree of lexical divergence from general Twitter differs across groups.
- **Multidimensional framing:** Liberal- and Conservative-referencing discourse differs significantly in four of five measured ousiometric dimensions (Goodness, Aggression, Structure, and Power). The mean difference in Danger is not statistically significant.
- **Semantic associations:** Baseline semantic projections illustrate contrasting associations with Power, Danger, and Goodness. These exploratory positions should not be treated as stable group rankings because they vary with embedding and anchor specifications.
- **Thematic differentiation:** Topic distributions differ strongly across identities (**Cramér's V = 0.599**). Topic-related differences in lexical happiness remain significant after accounting for group and calendar year.
- **Temporal affect:** Muslim- and Jewish-referencing discourse show statistically significant increases in lexical happiness in 2020–2022 relative to 2016–2019.

**Interpretation:** A low lexical-happiness score indicates a greater prevalence of negatively rated words, **not necessarily hostility toward the referenced group**. Negative wording can also occur in reporting adverse events, criticizing prejudice, or expressing support through counter-speech.

## Repository contents and reproducibility

The `LLM_Labeled_Data/` directory contains the research data and analysis materials included in this release. Individual analysis scripts, notebooks, and outputs can be used to explore the corresponding methods and findings. The `figures/` directory contains the annotation-workflow image displayed above and its original PDF.

Some source data, large intermediate CSV files, and pretrained embeddings may **not** be included in the GitHub release because of file-size restrictions or redistribution considerations. As a result, not every analysis may be reproducible from the repository alone without its external inputs. Refer to the associated manuscript and code for analysis-specific parameters and dependencies.

## Data use and research ethics

This repository supports computational social science research. Tweet text, usernames, and other potentially identifying information should be handled in accordance with applicable platform terms, dataset permissions, and institutional requirements. Do not interpret the linguistic scores as intrinsic characteristics of any social group or direct measures of individual beliefs.

## Citation

If you use this work, please cite the associated paper:

*When We Talk About Them: Negativity and the Linguistic Framing of Social Groups on Twitter.*

Full bibliographic details will be added when available.
