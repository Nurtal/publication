# TITRE

## Authors

## Abstract
This article presents an algorithm designed to anonymize transcripts of psychiatric consultations, focusing on the integration of generative AI within the realm of natural language processing. The methodology involves the identification and modification of potentially identifiable information using large language models (LLMs) and regular expressions. Performance evaluations revealed that the model [FIX] achieved optimal results in identifying sensitive content, while the model [FIX], combined with the preprompt [FIX], excelled in information replacement. However, the study acknowledges a limitation in its dataset, as it comprises patients from a single center who consulted the same practitioners. Despite this, the application of generative AI for anonymization—while retaining essential information—emerges as a promising avenue for future research. Further investigations are proposed to assess the tool's performance across documents from diverse clinical settings.

## Introduction
In the information age, audio recording of psychiatric consultations represents a critical issue for data collection. These recordings allow for a detailed analysis of interactions between practitioners and patients, but they also raise important ethical concerns regarding the confidentiality of the information exchanged. Given the often sensitive nature of psychiatric consultations, it is essential to develop robust anonymization strategies to enable the reuse of these recordings for research or data-sharing purposes .

Anonymization cannot be limited to simply removing directly identifiable information, such as the patient's name, age, address, or phone number . It is also necessary to capture indirect information that could reveal the patient's identity, such as the names of residence or workplace locations, as well as any mention of other individuals during the consultation . The challenge lies in eliminating these details while preserving as much of the original information as possible from the medical report .

To address this, we developed a tool based on large language models (LLMs) to identify and reformulate potentially identifiable information. The tool takes as input the textual transcription of an audio recording between a practitioner and a patient, and outputs a file where sensitive information is reformulated while retaining similar contextual details. This approach aims to facilitate the anonymization of medical records while minimizing the loss of useful information for analysis .

## Matriel & Methods
### Constitution du jeu de données
Two datasets were created to evaluate the performance of the anonymization tool. The first dataset was generated from sample sentences extracted from transcriptions, which were used as examples for a locally deployed language model (LLama3:70b). This model generated [FIX NB] sentences containing directly or indirectly identifiable information. This dataset is intended to quickly test the tool's capabilities during its development phase.

The second dataset was provided by the psychiatry department and consists of [FIX] complete consultation transcriptions. This dataset is intended to serve as a validation set to assess the tool's performance once its development is completed.

### Construction de l'algorithme
The anonymization tool follows a structured process with several steps. First, the algorithm splits the text document into a list of sentences. Each sentence is then cleaned to resolve potential encoding issues. A preliminary evaluation is conducted using a language model to determine whether the sentence contains potentially identifiable information. If it does, the sentence is extracted and passed through a pre-prompt for a LLM, with instructions to modify the identifying information. The processed sentence is then retrieved.

Directly identifiable information is temporarily stored in a register. This register ensures the overall consistency of the document by applying uniform replacements throughout. For instance, if a name is changed, the new name will be reused consistently wherever the original appears later in the document.

### Implémentation
Different configurations were tested to optimize the anonymization tool. For the first model tasked with identifying sentences containing potentially identifiable information, three approaches were evaluated: a series of regular expressions (regex) to capture proper names (people, cities, countries), a pre-trained BERT model, and several large language models (LLMs). The LLMs tested include LLama3:8b, LLama3:70b, and Mistral, all deployed locally on the computing infrastructure. Lastly, several preprompts, totaling [FIX], were tested to reformulate sentences containing identifiable information.

## Results
### Tableau résultat spot information
| model       | ACC | AUC |   
| regex       |     |     |
| light model |     |     |
| LLM         |     |     |

### Tableau résultat remplacement réussis
| LLM     | preprompt | ACC | AUC |   
| llama   | p1        |     |     |
| llama   | p2        |     |     |
| mistral |           |     |     |

## Conclusion
In this article, we presented an algorithm for anonymizing transcripts of psychiatric consultations, leveraging generative AI in the field of natural language processing. The best performance in identifying identifiable content was achieved with the model [FIX], while the optimal results for replacing this information were obtained using the model [FIX] with the preprompt [FIX].

One limitation of this study is that the dataset used for evaluation consists of patients from the same center who consulted the same practitioners. The use of generative AI for anonymization, while preserving as much useful information as possible, appears to be a promising approach. Future work could explore whether the tool's performance generalizes to documents from different centers, addressing the potential variability in patient data and practitioner styles.

## Biblio - chatgpt
Voigt, P., & Von dem Bussche, A. (2017). The EU General Data Protection Regulation (GDPR).
Doshi-Velez, F., & Kortz, M. (2019). Accountability of AI under the law: The role of explanation. Journal of Law and Technology.
Johnson, A. E. W., et al. (2020). MIMIC-IV (version 1.0).
El Emam, K., et al. (2015). De-identification methods for structured data. Journal of Biomedical Informatics.
Neamatullah, I., et al. (2008). Automated de-identification of free-text medical records. BMC Medical Informatics and Decision Making.
Devlin, J., et al. (2019). BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding. NAACL.
Raffel, C., et al. (2020). Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer. Journal of Machine Learning Research.

## Biblio - verifiée
