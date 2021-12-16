# ClinicalNotes_EntityExtraction
Approaches to extract clinically relevant entities from Clinical Notes

Files shared - 
1. Aditya_Medical_Entity_Extraction_V6.ipynb
2. Aditya_Medical_Entity_Extraction_V6.py


Jupyter notebook version has visual outputs stored along with the code. 

Approach is broken down into 6 steps - 
1. Entity extraction using packages, pre-defined or custom built libraries
2. De-identification using models for Negations, PMH etc.
3. Tagging the entities extracted from step 2 to UMLS CUIs/concepts
4. Disambiguation of entities to CUIs relationship
5. Using CUI information or raw text to get the sparse or embedded vectors 
6. Using the vectors in our 4 use cases at the end

Due to infrastructural constraints the code has been executed in batches and the following abberations have been considered - 
1. Entity extraction has been done using only SciSpacy packages at this point. Other predefined library that I am keen on using is Metamap (https://lhncbc.nlm.nih.gov/ii/tools/MetaMap.html) but I needs a dedicated server space & docker environment to be installed which was difficult to get to. Additionally, custom libraries as well are hard to put up on the limited space using a public cloud. So I have considered SciSpacy packages at this point to get entities like diseases, drugs and their dosages and other bio-medical entities. 
2. De-identification using models for Negations, PMH also isn't covered due to lack of labeled data for model training. Although I wanted to show the use case by giving an example of NegSpacy model which does a decent job on Negations, I wasn't able to install those due to package issues.
3. Tagging the entities to UMLS CUIs/concepts - recommended method is using the metamap way but I have tried to show that in the second part of my code. Alternatively I've used the UMLSEntityLinker package from SciSpacy to do the job.
4. As one entity gets linked to multiple CUIs I am trying to dis-ambiguate by a naive approach of picking the one with the highest probability, the code is running and looks like it will take a time before it gets executed completely. I will update my code once I have the updates from this part.
5. Was never able to make it to any of the use cases through the code as it needs part 4 to get completed.


Updates:
#16/12 - Disambiguation by picking up the cui with max probability has completed execution on google colab. Next steps are to create maxtrix view for this approach. Other two ways of doing the vectors - through doc2vec and using output from first approach to feed into auto encoders for dimensionality reduction is pending. The three ways can be tested out for the 4 use cases. Specific to use cases additional data needed would be - ICD10 data, disease severity and criticality data, claims data, CPT data
