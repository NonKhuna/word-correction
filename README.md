
# DeepGI-word-correction
A research for solving word error problem using both algorithm and large-language models approach in medical domain. The Norvig approach is an algorithm that loops through the text and corrects it using a language model and an error model. Meanwhile, BART, which is a generative model, is used to train pairs of transcribed and reference texts.

# Dataset
the dataset in this experiment is a pair of transcribed and reference texts exported from the ASR model and the script were obtained by synthesis.

# Approachs

| Approach | Description |
| --- | --- |
| Norvig | Finds the closest correctly spelled word to the given text. The code is customized from the [Norvig](https://pythainlp.github.io/dev-docs/_modules/pythainlp/spell/pn.html#NorvigSpellChecker) algorithm of Pythainlp.. |
| MBart | A sequence-to-sequence denoising auto-encoder pretrained on large-scale monolingual corpora in many languages using the BART objective.|
| MBart + mask_Num | Before feeding the input text to the model, mask and preserve the number in the text. Then, fill the mask with the number in the same order when post-processing the output text.|


# Results

|Evaluate metric|Raw Data|Norvig|MBart|MBart+mask_Num|Description|
| --- | --- | --- | --- | --- | --- |
|word_error_rate|48%|30%|0%|8%|The word is not in "Custom dict"|
|wrong_number_rate|20%|20%|2%|20%|The transcript numbers don't match the reference numbers.|
|exceed_data_rate|8%|8%|2%|3%|The length of the trans text  >  the ref's length.|
|missing_data_rate|7%|7%|1%|0%|The length of the trans text  <  the ref's length.|
|wrong_word_rate|6%|10%|4%|14%|The corrected words in the trans text are not existed in the ref text.
|wer_score|12%|10%|1%|3%|WER score
|accuracy|45%|59%|*96%|78%|Exact match ( the reference text === the transcript text)

The table shows the MBart model achieves the highest score of 96% accuracy and 1% WER score. However, due to a lack of variety of data, generative models like MBart may be overfitting as shown in the results of the wrong number rate. Therefore, The Norvig approach may be better on small datasets.

## Appendix

You can see the presentation slides of the project in this [link](https://www.canva.com/design/DAFedhLsi2M/wcRKCwuB5pw6zm2v8ePrqg/edit?utm_content=DAFedhLsi2M&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton).
