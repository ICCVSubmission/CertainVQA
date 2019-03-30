# CertainVQA

The Repository contains additional details and analysis for our Anonymous Submission.

### Certainty maps obtained after doing Monte Carlo Simulations. 

#### "e" in the images stands for entropy.


<table>
    <tr>
        <td>
            <table>
                <tr>
                    <td colspan="2">
                        <i>Q</i>: <b> <font size="0.5"> What is the man holding? </font> </b>
                    </td>
                </tr>
                <tr>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55288603-7b1bbc00-53d7-11e9-9459-19da90311150.png" align="center"></td>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55269813-87abf180-52bd-11e9-87c9-35aac68c0713.gif" align="center"></td>
                </tr>
            </table>
        </td>
        <td>
            <table>
                <tr>
                    <td colspan="2">
                        <i>Q</i>: <b> <font size="0.5"> Which room is this? </font> </b>
                    </td>
                </tr>
                <tr>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55288640-101eb500-53d8-11e9-8b48-fb0093ea3321.png" align="center"></td>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55269810-7d89f300-52bd-11e9-88f1-ed9dc7da8a29.gif" align="center"></td>
                </tr>
            </table>
        </td>
    </tr>
</table>

<table>
    <tr>
        <td>
            <table>
                <tr>
                    <td colspan="2">
                        <i>Q</i>: <b> <font size="0.5"> What is behind the TV? </font> </b>
                    </td>
                </tr>
                <tr>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55288609-9a1a4e00-53d7-11e9-9961-a63de48f3b78.png" align="center"></td>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55269793-62b77e80-52bd-11e9-8bb3-776bd8633484.gif" align="center"></td>
                </tr>
            </table>
        </td>
            <td>
                <table>
                    <tr>
                        <td colspan="2">
                            <i>Q</i>: <b> <font size="0.5"> What is the girl eating? </font> </b>
                        </td>
                    </tr>
                    <tr>
                        <td><img src="https://user-images.githubusercontent.com/48848404/55288646-2b89c000-53d8-11e9-8d7b-2e558307438b.png" align="center"></td>
                        <td><img src="https://user-images.githubusercontent.com/48848404/55269787-4fa4ae80-52bd-11e9-80ff-5863722072bb.gif" align="center"></td>
                    </tr>
                </table>
            </td>
    </tr>
</table>

<table>
    <tr>
        <td>
            <table>
                <tr>
                    <td colspan="2">
                        <i>Q</i>: <b> <font size="0.5"> What fruit is in the bowl? </font> </b>
                    </td>
                </tr>
                <tr>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55288588-50c9fe80-53d7-11e9-9441-a57e7ffc85fc.png" align="center"></td>
                    <td><img src="https://user-images.githubusercontent.com/48848404/55269778-38fe5780-52bd-11e9-9534-5fa6e0306dad.gif" align="center"></td>
                </tr>
            </table>
        </td>
            <td>
                <table>
                    <tr>
                        <td colspan="2">
                            <i>Q</i>: <b> <font size="0.5"> Which animals are they? </font> </b>
                        </td>
                    </tr>
                    <tr>
                        <td><img src="https://user-images.githubusercontent.com/48848404/55288656-4bb97f00-53d8-11e9-997b-1f11dd333b36.png" align="center"></td>
                        <td><img src="https://user-images.githubusercontent.com/48848404/55269771-2ab03b80-52bd-11e9-91a8-55b25c0de68e.gif" align="center"></td>
                    </tr>
                </table>
            </td>
    </tr>
</table>

### Dataset Details
##### VQA-V1
It contains human annotated  question-answer pairs  based  on  images  on  MS-COCO dataset's images.
 
| Field | Train | Val | Test |
|:---:|:---:|:---:|:---:|
Q-A pairs | 2,48,349 | 1,21,512 | 2,44,302 |

##### VQA-V2
It has almost twice the number of question-answer pairs as **VQA-V1** and also claims to remove some biases.
 
| Field | Train | Val | Test |
|:---:|:---:|:---:|:---:|
Q-A pairs | 4,43,757 | 2,14,354 | 4,47,793 |

##### VQA-HAT
Dataset containing human annotated attention maps. (Based on **VQA-V1**)

 
| Field | Train (out of 2,48,349) | Val (out of 1,21,512) |
|:---:|:---:|:---:|
Q-A pairs | 58,475 | 1,374 |

##### VQA-X
Human annotated visual explanation maps. (Based on **VQA-V2**)

 
| Field | Train | Val | Test |
|:---:|:---:|:---:|:---:|
Q-A pairs | 29,459 | 1,459 | 1,968 |

### Evaluation methods
##### Accuracy
VQA dataset has 3 type of answers: _yes/no_, _number_ and
_other_. The evaluation is carried out using two test splits, i.e
test-dev and test-standard. The question in corresponding
test split are of two types: Open-Ended and
Multiple-choice. Our model generates a single word answer on the open ended task. For
each question there are 10 candidate answer provided with
their respective confidence level. This answer
can then be evaluated using accuracy metric defined as follows:

<img src="https://user-images.githubusercontent.com/48848404/55290640-5a615f80-53f3-11e9-802b-5ffc401e7d33.png">

Where a<sub>i</sub> the predicted answer and t is the annotated answer
in the target answer set T<sup>i</sup> of the i<sup>th</sup> example and I[.]
is the indicator function. The predicted answer a<sub>i</sub> is correct if at least 3 annotators agree on the predicted answer. If the
predicted answer is not correct then the accuracy score depends
on the number of annotators that agree on the answer.



##### Rank Correlation
The algorithm is as follows:

```yaml
procedure: (Initialization)
    PH: Probability distribution of Human Attention Map
    PM: Probability distribution of our model
Rank:
    Compute Rank of PH : RH
    Compute Rank of PM : RM
Rank Difference :
  Compute difference in rank between RH & RM : Rank_Diff  
  Compute square of rank difference Rank_Diff: S_Rank_Diff
Rank Correlation:
  Compute Dimension of PM: N
  Compute Rank Correlation using : Formula given below for R_Cor

```

<img src="https://user-images.githubusercontent.com/48848404/55291917-fc884400-5401-11e9-87a6-37e3ab642b64.png">


