# A project that uses NLP Python libraries like SpaCy to perform Named Entity Recognition

## Introduction

This project is based on the NLP Named Entity Recognition concept where we can extract entities from a text (sentence or paragraph). We use generated fake sentences which contain credit card number, CVV and expiry date which are regarded as sensitive information and try to predict these entities based on a commonly-used NLP library called SpaCy.

## Tools/Technology used

•	Python SpaCy library (https://spacy.io/) – used for NER
•	MongoDB – to store the model’s prediction outcomes.

## Steps followed in the code
•	Import necessary libraries into the code- SpaCy, Displacy (visualization tool for NER) and os.
•	Download the pre-trained NLP model from SpaCy, such as en_core_web_lg or en_core_web_sm. (command- !python -m spacy download en_core_web_lg)
•	Create training data with sufficient number of text samples.
•	Example: provide the text and then indicate the start and end position of each entity (refer below) in the text. cardnumber entity here starts at 27 and ends at 46th position.
("Your transaction with card 6789 7890 8901 0123, expiring 08/30 and CVV 987, is complete.", {'entities':[(27, 46, 'cardnumber'), (57, 62, 'expirydate'), (71, 74, 'cvv')]})
•	Use spacy.load() function to use the en_core_web_lg we downloaded initially.
•	Convert the text into a Docbin object, as required by SpaCy.
•	Save the Docbin object into a folder in local PC as "./train.spacy".
•	Model training (can be done either in Command Prompt or Jupyter)- 
  
  o	  !python -m spacy init fill-config ./base_config.cfg ./config.cfg is used to create a configuration file with initial values specified for hyperparameters of the NLP model (can be adjusted to improve model performance).
  ![image](https://github.com/arjunsai07/CreditCardEntityRecognition/assets/14110439/3f857d57-1159-4559-8a67-5cdac3d7cca7)
  
  
  o	  !python -m spacy train /content/config.cfg --output ./output --paths.train ./train.spacy --paths.dev ./train.spacy --gpu-id 0 is used to train the model using the provided configuration file.

