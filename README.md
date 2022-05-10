# SFCSyntheticDataGenerator
## A synthetic data generation system for myalgic encephalomyelitis / chronic fatigue syndrome questionnaires


There is an increasing demand for artificial intelligence healthcare models. Large health datasets are needed to build these predictive models to help other investigators to find new treatments or to deliver individualized healthcare interventions. However, it is not easy to share health data and gather large datasets, since there are issues concerning patient privacy to be accounted for and restricted law protects from sharing any personal data between investigators. 

Our objective is to create an open-source generator of high-fidelity synthetic data for investigation and educational use, and free of legal, privacy and security restrictions. As a proof-of-concept, we will apply it to chronic fatigue syndrome (CFS) questionnaire generation. 

We used six questionnaires from 2522 CFS diagnosed patients. each test has between 8 to 90 questions with 3-5 ordered options. These have fed forward Network algorithms to create a synthetic data generator. SF-36 questionnaire is considered commonly used for patients with CFS symptomatology and is required as input data. 

Real data of all of six questionnaires are required to train and build the models. It is processed in different steps. Each of them is made up of an input array and a target array. In each step, the previous result is added to the input matrix, obtaining synthetic data from each cascade test. The order of the tests in the steps is defined by the result of the graph analysis. This analysis is performed based on the subscales of the tests to optimize the results based on the relationship we obtain. The models achieve 0.69 - 0.81 rank accuracy to predict HAD, SCL 90 R, FIS8, FIS40 and PSQI questionnaires. The t-student has used as validated metric to test how are similar artificial data to real. The rank results were 0.18-0.85 as p-value.

Synthetic patients can be efficiently generated using models of CFS questionnaires to produce risk-free realistic synthetic health care records at any scale. Synthetic patients can be simulated with models of ME/CFS questionnaires data and corresponding standards of care to produce risk-free realistic synthetic health care records at scale.

## How to use

There is the code you must use to generate synthetic data generator.
You can use your SF-36 questionnaire dataset and predict HAD, SCL90R, FI8, FIS40 and PSQI validated and free to use and share.
I will share a synthetic SF-36 validated in next future.
You need the models h5 files, I could not share for space limits. You have to ask me permission to access.
The link I store the models is: https://drive.google.com/drive/folders/1dgBAP7qYim5MrS-iBoSFDf8LY58AK7mY?usp=sharing
Please, contact me to ask me permission.

### Limitations
All the patients come from the specialized chronic fatigue unit of the Vall D'Hebrón University Hospital in Barcelona. Being able to count on more data from patients from other units with similar protocols could enrich this work. Shared synthetic data may not represent reality for some non-Caucasian populations. More studies are required to find out differences in CFS patients to validate this work.

Synthetic patients can be simulated with models of ME/CFS questionnaires data and corresponding standards of care to produce risk-free realistic synthetic health care records at scale. We offer an open-source generator of high-fidelity synthetic data for investigation and educational use, and free of legal, privacy, security and intellectual property restrictions. 

