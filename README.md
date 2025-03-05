# Sepsisclusterstudy
This repository includes scripts used in the sepsis cluster study done by Wickstrøm et. al. The results are presented in this paper: 

The study replicates the CC method that was done by Seymour et al:  
"Seymour CW, Kennedy JN, Wang S, et al. Derivation, Validation, and Potential Treatment Implications of Novel Clinical Phenotypes for Sepsis. JAMA. 2019;321(20):2003–2017. doi:10.1001/jama.2019.5791" (https://jamanetwork.com/journals/jama/fullarticle/2733996) 

The Rmarkdown script will:
- load a dataset with 27 variables similar as in the Seymour data (Alat, alp, bilirubin, chloride, creatinine, crp, glucose, ESR, hemoglobin, GCS, HR, INR, lactate, leucocytes, RR, oxygen saturation, paO2, sodium, systolic blood pressure, thrombocytes, troponin T, urea). The dataset should be transformed for the non-normal variables before loading; logtransform (creatinine, lactate, bilirubin, crp, alp, alat, troponinT, INR, leucocytes, urea, thrombocytes, paO2, glucose) and exp.transformed (saO2).
- Multiple imputation. The dataset are imputed to 100 datasets with "pmm" method.
- Consensus clustering. The imputed datasets will each be run on consensus clustering script which is copied from the original CC-code. Each resulting 100 matrices will be combined to one matrix. This combined matrix will then be used to produce the cluster assignment, a combined matrix plot, CDF plot.
- The 100 imputed datasets will be combined to one dataset- "meansepsisdataset" and the transformed variables will be untransformed.
- A chosen cluster number can be chosen for further characterising the "meansepsisdataset" with median values for the variables in each cluster.


Extra remarks under:
##this is done by 27 variables, almost the same as Seymours 29, but with Alp instead of Asat, and urea instead of bun, and without bicarbonate and bands. This due to differences in our dataset. 
##if your dataset is large, over 2000-3000 patients, it can be timeconsuming and challenging to run this code with 100 imputations. Consider lower number of imputations based on the degree of missingness in your data. 
