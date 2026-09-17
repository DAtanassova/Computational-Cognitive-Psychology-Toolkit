# Computational-Cognitive-Psychology-Toolkit

This repository contains experimental tasks and computational models developed and adapted to investigate learning and decision-making in adult and developmental cohorts (including infants and young children).

**Contents Overview**

1. **Children-Social-Nonsocial-Reversal-Learning-Task**
This folder contains executable script for a probabilistic reversal-learning task designed for children aged 4 years and above. The task takes approximately 8 minutes to complete and is designed to run in Python using PsychoPy 2022 for best compatibility.

**Paradigm Description**
On each trial, children see an animal enclosure with an animal in the centre (fixation) for 600±150 ms. Two food options then appear on either side of the animal. Children have 5 seconds to choose which food to offer to the animal. The food options are selected to be appropriate for the animal (e.g., fish and apples for a bear). Children choose the left food option by pressing A or the right food option by pressing C. If no response is made within 5 seconds, the screen displays “Too slow!” accompanied by a sound. If a response is made, an outcome is presented for 950 ms. After the outcome, an empty animal enclosure is presented for 700 ± 150 ms, after which the next trial begins.

**Social condition**
In the social condition, the outcome is presented as the face of a junior zookeeper (another child) on a display board. Correct choices result in a smiling expression, whereas incorrect choices result in a frowning expression. The perceptual ambiguity of the facial expression is experimentally manipulated using the variable Perc_Unc, with higher values indicating greater ambiguity.

**Non-social condition**
In the non-social condition, the same display board is presented with a symbolic outcome instead of a face: a check mark indicates a correct choice and an X mark indicates an incorrect choice. The perceptual ambiguity of these symbols is also experimentally manipulated.

**Task Structure**
The task comprises 80 trials, with 40 trials per condition (40 social and 40 non-social). Two animals are currently used, one for each condition: rhino and bear.
The task consists of an initial stable acquisition block, followed by multiple reversal blocks. During reversals, the food option associated with the higher probability of reward changes, requiring children to update their expectations and adapt their choices.
The order of the social and non-social conditions is pseudo-randomised based on participant number. 
- Even participant numbers: social condition first. 
- Odd participant numbers: non-social condition first

**Practice**
When practice mode is enabled in the pop-up menu, the task begins with a short 7-trial practice run, during which social and non-social outcomes are mixed. A different face stimulus is used during practice to avoid exposing children to one of the experimental face stimuli before the main task.

**Instructions**
Given the young age of the participants, instructions are not presented within the task. Instead, we recommend providing instructions before the task begins by showing the child the different possible outcomes and familiarising them with the buttons they will use to respond.

**Image Attribution**
The faces used in the task are retrieved from the Radboud Faces Database (RaFD): https://rafd.nl/.
Other images were Designed by Magnific and are used with the required attribution: www.magnific.com.

**Compatability with EEG**
The task is designed to be used with EEG: the EEG component can be enabled in the pop-up menu, in which
case the task runs as a simple behavioural paradigm. 

**How to start the task**
Download the entire folder "Children-Social-Nonsocial-Reversal-Learning-Task". To run the task, open the "SPARK_Zoo_Task.py" in PsychoPy (or another Python shell). 
When you start the task, you will be prompted to enter a participant number, as well as select the session settings.
Indicate if the session is a practice (in which case, a shorter sequence will be run), and whether there is an EEG system connected.
When prompted, press SPACE to begin the task. You can pause the task at any moment by pressing **SPACE**. 
To quit the task at any moment, press **Escape**.

2. **Infant-Reversal-Learning-Task**
This folder contains a developmentally appropriate probabilistic task allows for an investigation of how infants (aged 8–12 months, though it works well with older children too) learn and adapt in volatile conditions. The task is a short passive viewing paradigm where a reward (animation) appears reliably on one side until it  switches. By tracking infants' anticipatory looks (where they expect the reward to appear next), we can measure how quickly and how well they detect and adapt  to these hidden changes.

The task takes ~4 minutes, making it suitable for infant attention spans, and  is fully compatible with EEG and eye-tracking setups.
See the README_runTask for instructions on running it.


3. **Computational-Modelling-for-Developmental-Research-Tutorial**
This repository provides everything you need to study how infants learn in a  changing, uncertain world including example data from the Infant-Reversal-Learning-Task and a step-by-steo tutorial on how to apply a computational model to such data and extract the hidden computational processes driving their behavior.

**The computational modelling**
While behavioral data can provide insights on how infants adapt (e.g. average
accuracy, win-stay, lose-shift rates), we use the Hierarchical Gaussian Filter 
(HGF) to extract an estimate of how they learn in changing conditions. The HGF 
(model available here: https://github.com/translationalneuromodeling/tapas/) is
considered the best mathematical approximation of how humans learn under
uncertainty and in volatile (changing) conditions.

The model allows for an estimate of how predictions or beliefs (i.e. about the 
side where a target would appear) are generated, and how fast these beliefs
update in response to new information. It also quantifies various latent 
parameters representing individual differences in this process (i.e. how 
sensitive or reactive someone is to change). These hidden quantities cannot be
observed directly but the model creates an estimate based on observed behaviour
(in this case: the anticipatory looking behaviour).

4. **Computational-Modelling-for-Developmental-Research-Tutorial**
This folder contains a selection of models, developed based on existing models from the HGF tapas toolbox (https://github.com/translationalneuromodeling/tapas) that can be applied to behavioural choice data.

**Models**
- **ehgf_ar1_binary_mab**
An implementation of the ehgf_ar1_binary model from the HGF tapas toolbox, adapted for multi-armed bandit (MAB) configurations. This model was used in Atanassova, D.V., Oosterman, J.M., Diaconescu, A.O. et al. Exploring when to exploit: the cognitive underpinnings of foraging-type decisions in relation to psychopathy. Transl Psychiatry 15, 31 (2025). https://doi.org/10.1038/s41398-025-03245-2

- **softmax_binary_wld**
An adaptation of the softmax_wld model from the HGF tapas toolbox for binary outcomes. This implements a Win-Loss Distortion (WLD) model for modeling decision-making in binary-outcome environments.

- **softmax_binary_mu3**
An adaptation of the softmax_mu3 model from the HGF tapas toolbox for binary outcomes. Binary decisions are modelled based on the trial-wise mu3 (meta-volatility)
estimates as decision temperature. 

- **tapas_ehgf_ar1_binary_pu**
An adaptation of the ehgf_binary_pu model that includes an autoregressive (AR1) process. It allows you to model binary decision-making in a paradigm where the outcomes are uncertain (have a degree of ambiguity).

Additional models and adaptations will be added as they are developed and used across projects.





