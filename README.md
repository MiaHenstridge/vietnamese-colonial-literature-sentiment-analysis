# The Quantitative Soul: Computational Sentiment Analysis of Vietnamese Colonial Literature

A computational analysis of emotional landscapes in six seminal Vietnamese novels from the French colonial period (1930–1945), using NRC emotion lexicons and Markov Chain modeling to quantify how literary schools and social class shaped narrative affect.

📄 [Full report (PDF)](final_report.pdf)

## Overview

Traditional literary criticism categorizes pre-1945 Vietnamese authors into distinct schools (Romanticism, Critical Realism, Satire), but the emotional structures of their works have remained qualitative. This project quantifies those structures by treating each novel as a sequence of emotional states and asking: does the "emotional mobility" of a narrative depend on the social class of its protagonist?

## Corpus

| Novel | Author | Protagonist class | Literary school |
|-------|--------|-------------------|-----------------|
| Tắt đèn | Ngô Tất Tố | Oppressed peasantry | Documentary Realism |
| Bước đường cùng | Nguyễn Công Hoan | Oppressed peasantry | Confrontational Realism |
| Sống mòn | Nam Cao | Impoverished intelligentsia | Psychological Realism |
| Ngày mới | Thạch Lam | Impoverished intelligentsia | Poetic Realism |
| Đoạn tuyệt | Nhất Linh | Urban petty bourgeoisie | Reformist Romanticism |
| Số đỏ | Vũ Trọng Phụng | Urban underclass | Grotesque Realism / Satire |

## Methods

1. **Vietnamese NLP preprocessing** — word segmentation and NER via `underthesea`, custom negation handling, stopword removal
2. **Lexicon-based sentiment analysis** — emotion scoring using VnEmoLex (Vietnamese NRC Emotion Lexicon) across 8 emotions + 2 polarities
3. **Chapter-level trajectory analysis** — normalized sentiment density and polarity arcs over narrative time
4. **Statistical testing** — Kruskal-Wallis H-test + pairwise Mann-Whitney U-tests with Bonferroni correction for cross-novel emotion comparisons
5. **Markov Chain modeling** — first-order emotional transition matrices capturing narrative rhythm and predictability

## Key Findings

- Narratives of the oppressed peasantry are dominated by fear and anger with "stagnant" transition matrices — emotional loops mirroring material entrapment.
- Urban and reformist narratives exhibit a more "liquid" emotional economy with higher trust and joy, and more volatile transitions.
- Sadness is a statistically universal constant across the entire corpus (p = .051), but the capacity for emotional transition depends on the protagonist's social class.

## Project Structure

```
00_clean_up_emotion_lexicon_dataset.ipynb    # Preprocess VnEmoLex into JSON format
01_data_cleaning.ipynb                       # Vietnamese text segmentation, NER, normalization
02_sentiment_analysis_and_topic_modeling.ipynb  # Sentiment scoring, statistical tests, Markov Chains
data/                                        # Source texts and processed lexicon
fig/                                         # Generated figures
```

## Technologies

Python: underthesea, NLTK, SciPy, pandas, NumPy, matplotlib