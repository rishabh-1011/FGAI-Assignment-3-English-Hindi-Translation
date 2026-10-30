# English–Hindi Translation Model Comparison

## Overview
This project compares approaches for English-to-Hindi machine translation.

## Dataset
The experiments use the `cfilt/iitb-english-hindi` dataset from Hugging Face.
The original official test split contains 2,507 examples. LLM comparisons reported
here used the first 100 test examples, while the Transformer-from-scratch and
OPUS-MT results used 2,507 examples.

## Approaches
- Transformer encoder-decoder trained from scratch
- mT5-small fine-tuning attempt
- TinyLlama zero-shot prompting and LoRA
- Gemma 2 2B zero-shot prompting and LoRA
- OPUS-MT English-to-Hindi as an additional baseline

## Recorded results

| Model | Approach | Test examples | BLEU | chrF |
|---|---|---:|---:|---:|
| Transformer from scratch | Train from scratch | 2507 | 0.15 | 4.72 |
| mT5-small | Fine-tuning attempt | — | Invalid | Invalid |
| TinyLlama 1.1B | Zero-shot | 100 | 0.63 | 13.25 |
| TinyLlama 1.1B | LoRA | 100 | 0.66 | 12.99 |
| Gemma 2 2B | Zero-shot | 100 | 12.43 | 38.84 |
| Gemma 2 2B | LoRA | 100 | 9.05 | 35.92 |
| OPUS-MT en-hi | Additional baseline | 2507 | 9.88 | 32.33 |

## Findings and limitations
Gemma zero-shot achieved the strongest recorded scores among the LLM experiments.
Gemma LoRA scores declined in this run. The mT5 experiment was unstable and has
no valid evaluation score. OPUS-MT is an additional baseline, not a substitute
for the required approaches.

Results are not directly comparable across experiments with different test-set
sizes. The LLM evaluations used 100 examples, while the Transformer and OPUS-MT
evaluations used 2,507. The recorded metrics are reproduced from the experiment
logs; missing artifacts or invalid metrics are not presented as successful results.

## Reproduction
Open the notebook in Google Colab and follow its cells in order. Access to gated
Hugging Face models may require accepting their model terms and configuring a
token through Colab Secrets. Never commit access tokens or credentials.
