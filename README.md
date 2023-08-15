# Resolving Hungarian Anaphora with ChatGPT

## The Experiment (First Round)

This is an experiment in which we investigated how ChatGPT performs in resolving ambiguous pronominal anaphoras in Hungarian sentences.

For our experiments, the test data of the [HAPP](https://github.com/nytud/HAPP) collection was used, which contains a total of 564 sentences and questions.
ChatGPT was used through the [Python API](https://platform.openai.com/docs/guides/chat) provided by OpenAI.
To use the chat function, we used the most advanced GPT model at the time, `gpt-3.5-turbo`.
The experiment was completed in March 2023.
After formatting the output, the received answers were compared to the answers in the schema collection.

Four experiments were performed as it can be seen in the following example (for the sake of clarity it is an [original English example](https://www.hlt.utdallas.edu/~vince/data/emnlp12/) by Rahman and Ng (2012)):

sentence: The car beat the bike because it was faster.
* first experiment: What was faster?
* second experiment: What was faster? Please answer in one or two words!
* third experiment: What was faster? The car or the bike?
* fourth experiment: What was faster? The car or the bike? Please explain your answer!

The answers of ChatGPT have been manually sorted into the following categories:

* correct answer
* incorrect answer
* it did not know the answer
* avoided answering by giving some general comments

The number of answers classified into the four categories were totalled, then we examined how the number of answers falling into each category developed in the four experiments. We interpreted the results using the experience we gained in the fourth experiment.

### Categorizing the Answers

Table [winograd_chatgpt.csv](winograd_chatgpt.csv) consists of the following columns:
* A: the sentence
* B: the question
* C: answer options
* D: the correct answer
* E: result of the first experiment
* F: evaluation of the first experiment
* G: result of the second experiment
* H: evaluation of the second experiment
* I: result of the third experiment
* J: evaluation of the third experiment
* K: result of the fourth experiment
* L: evaluation of the fourth experiment
* M: the number of correct answers to the given scheme
* N: the number of the cases where it did not know the answer to the given scheme
* O: the number of incorrect answers to the given scheme
* P: the number of the cases it avoided answering to the given scheme
* Q: the second experiment corrected than the first one
* R: the third experiment corrected than the first one
* S: the fourth experiment was worse than the third one
* T: the fourth experiment corrected than the third one
* U: the third and fourth experiments were consistently correct

Keep in mind that the table contains my own subjective judgments.

### Results

The results can be seen for each experiment in the table [winograd_chatgpt.csv](winograd_chatgpt.csv) in rows 572-575.

|             | first experiment | second experiment | third experiment | fourth experiment |
|------------:|-----------------:|------------------:|-----------------:|------------------:|
|     correct |           66.37% |            70.62% |           79.29% |            74.69% |
| didn't know |           11.86% |             2.48% |            3.89% |             4.42% |
|   incorrect |           15.75% |            24.01% |           13.45% |            16.64% |
|     general |            5.84% |             2.65% |            3.19% |             4.07% |

Row 577-578 contains the sums of columns M-U. M:577-578 counts the cases when ChatGPT gave correct answer in at least two experiments.

## Evaluating Consistency (Second Round)

We repeated the test with a few sentences from the first round.
The second round was carried out in August 2023.
The same API and modell were used as in the first round.

For the second round we selected those sentences for which zero, one or two correct answers were obtained during the four experiments in the first round.
We asked ChatGPT ten times each question and saw how consistent the answers were.
We created 1650 questions from the 165 schemes.
The questions were asked together with the two answer options (as in the third experiment of the first round).
The results are shown in table [winograd_chatgpt_cons.csv](winograd_chatgpt_cons.csv).

In this round, we set up three categories to classify the answers (the letters in the table are shown in brackets):
* correct answer (j)
* incorrect answer (r)
* didn't answer / didn't know (n)

### Results

It is considered a fully consistent response if we received answers to the same category in all ten times.
It is considered a mostly consistent response if at least eight answers to the given question fall into the same category.

|             | fully consistent | mostly consistent |
|------------:|-----------------:|------------------:|
|     correct |           22.42% |            35.76% |
|   incorrect |           14.55% |            27.27% |
| didn't know |            4.24% |             7.88% |
|       TOTAL |           41.21% |            70.91% |


# References
If you use my results, please refer to:

Noémi Vadász (2023): Resolving Hungarian Anaphora with ChatGPT. TSD 2023 (In press).

```bibtex
@InProceedings{vadasz2023,
  author       = "Noémi Vadász",
  title        = "Resolving Hungarian Anaphora with ChatGPT",
  year         = "2023",
  note         = "In press",
}
```

If you use the [HAPP](https://github.com/nytud/HAPP) collection, please refer to:

```bibtex
@article{vadaszligeti2022actawinograd,
      author = "Noémi Vadász and Noémi Ligeti-Nagy",
      title = "Winograd schemata and other datasets for anaphora resolution in Hungarian",
      journal = "Acta Linguistica Academica",
      year = "2022",
      publisher = "Akadémiai Kiadó",
      address = "Budapest, Hungary",
      volume = "69",
      number = "4"
}
```
and to:

```bibtex
@InProceedings{rahman_ng,
  author = {Altaf Rahman and Vincent Ng},
  title = {{Resolving Complex Cases of Definite Pronouns: The Winograd Schema Challenge}},
  booktitle = {Proceedings of the 2012 Joint Conference on Empirical Methods in Natural Language Processing and Computational Natural Language Learning},
  pages = {777--789}, 
  year = 2012
}
```

# License
The resource is available under CC-BY-SA 4.0 license.
