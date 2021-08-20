# [HackBio internship 2021](https://thehackbio.com/): Genomics-One-B

![hackbio image](https://media-exp1.licdn.com/dms/image/C561BAQHKcVQGbcedOA/company-background_10000/0/1598491473588?e=2159024400&v=beta&t=rxECjvQ_YSc28Dn0n9YOtDoFFmvXjatRiqc__C2mpU0)
![](https://files.slack.com/files-pri/T025KDN24L8-F02BXHY1JMP/1629208803397.jpg)

[HackBio](https://thehackbio.com/) is a virtually regimented research internship that is practice oriented and focused on equipping African scientists with advanced bioinformatics and computational biology skills. By the end of internship, successful interns should have:
- Honed their skills in a specific bioinformatics method
- Have at least a peer-reviewed article to show for the internship experience

# PROJECT WORKFLOW & DESIGN
![hackbio ads](https://github.com/HackBio-Genomics-One-B/Genomics-One-B/blob/main/PROJECT%20DESIGN%20(GENOMICS%201B).png?raw=true)

## Step-by-Step 

### Task distribution:

|STEP|TASK|COLLABORATORS' SLACK USERNAME |
|----|--------------|--------------------|
|1|Importing data (From Galaxy Library) |@Solomon @Temmykeji|
|2|Checking data quality using FastQC|@Solomon @Temmykeji|
|3|Mapping reads to a reference using BWA-MEM|@Rajeshcha44 @Nitigya-M|
|4|**Post-processing mapped reads** _*Merge datasets using SAMFiles_ _*Remove duplicates using MarkDuplicates_  _*Left aligning indels using BAM left align_ _*Filtering reads_|@abdnahid_ @Mike @Karteek|     
|5|Calling non-diploid variants using FreeBayes|@Priyacomp @MANGAIYARKARASI @pragna_lakshmi|
|6|Filtering variants using VCFfilte|@Naomi @Galaxy @Aarathi04|
|7|Visualization using IGV|@Gautami @Shreyashi @ZubairAlam|
|8|Compare frequencies|@omimiIII @Temmykeji @pragna_lakshmi @Gautami|



# Calling variants in non-diploid systems
#### _By: AvatarAnton Nekrutenko AvatarAlex Ostrovsky_

## Questions
How does frequency of mitochondrial polymorphisms change from mother to child?

## Objectives
Using Galaxy’s main site we will see how to call variants in bacteria, viruses, and organelles.

## Requirements
1. Introduction to Galaxy Analyses
2. Sequence analysis
      - Quality Control
      - Mapping

## Introduction
A handful of life ranging from prokaryotes, down to viruses and a few extension operate on non-diploid mechanism.
In this tutorial Team Genomics_One_B will be recreating the above project which involves working on four datasets, gotten from human genomic DNA sequencing. The aim of this is to identify heteroplasmies variant within the mitochondria DNA using Galaxy packages.

In this tutorial, we will cover:

## STEP 1: IMPORTING DATASET

      •Download datasets from resource page
      •Click upload data on Galaxy web page
      •Galaxy will prompt to ask if it is from the local files or web (it depends on where you saved the dataset)
      •After uploading, click start. Once import is completed, the dataset highlight turns green as seen on the picture below.
      
![gd](https://user-images.githubusercontent.com/77963733/130158462-53243352-6693-4370-b0aa-2223834cb571.jpg)
    
      
## STEP 2: QUALITY CHECK OF DATASET

It is important to check the quality of the data to be used before proceeding with the analysis. This is done to determine if there is a problem with the data setOn Galaxy, by the left hand side, click FASTA/FastqThen click FastQC Read Quality Check and execute. It will run a check on the data.

![gc](https://user-images.githubusercontent.com/77963733/130158592-ceedd90b-8761-4289-8284-504bf35ae368.jpg)


![gd](https://user-images.githubusercontent.com/77963733/130158596-09ad1ed9-390e-44a3-a3c5-64cb2e0d0100.png)


## STEP 3: MAPPING THE READS USING BWA MEM 

Human genome, ‘hg38’ was used as the reference genome.Using the Paired end sequencing, the datasets has to be uploaded by selecting multiple datasets as follows:

      First set of reads: both dataset 1 (raw_child-ds-1.fq & raw_mother-ds-1.fq )
      Second set of reads: both datasets 2 (raw_child-ds-2.fq & raw_mother-ds-2.fq )
      Set read groups information to “Set read groups (SAM/BAM specification) and Execute
      
## STEP 4: POST-PROCESSING MAPPED READ

      Step 4.1: Merging BAM datasetsSelect Picard from the left side of the Galaxy page.
      Click Merge SAM Files tool, Then import dataset obtained from Step 3 into the dataset collection.
      Input parameters as seen in the image below. Then executeStep 3
     
     
   ![41](https://user-images.githubusercontent.com/77963733/130158840-9923d314-6841-44cd-a4cb-33d738e1a208.png)


      Step 4.2: Removing duplicates using MarkDuplicates
      Select Picard on the left side panel. 
      Click on MarkDuplicates In the SAM/BAM or dataset collection box. 
      Upload merged SAMFiles Input parameters as seen below and Execute
    
![42](https://user-images.githubusercontent.com/77963733/130158847-44d2da3e-d50e-46f8-a2ae-c8f7a2d676cc.png)

      Step 4.3: Left-aligning indels using BamLeftAlign 
      ToolLeft aligning of indels is important for obtaining accurate variant calls 
      (The BAM dataset generated by MarkDuplicates will be used to run this step)
      Click on Variant analysis and select BamLeftAlign
      Input MarkDuplicate dataset and 
      Use reference genome: hg38(Input parameters as seen in picture below)Execute
      
![43](https://user-images.githubusercontent.com/77963733/130158853-bc589b3e-3841-44cc-b5fa-4951f483459e.png)
      
      Step 4.4: Filtering reads Select filter under BamToolsUsing MarkDuplicates dataset. 
      Input parameters as seen in picture below.
      Then execute (NB: Would you like to set rules should be NO)
      
![44](https://user-images.githubusercontent.com/77963733/130158864-3000b582-0429-48cb-9655-f5b4b1ec683a.png)
      
## STEP 5: CALLING NON-DIPLOID VARIANTS USING FREEBAYES

You can navigate to the tool (FreeBayes) using the search button in GalaxySelect the reference genome mode of run and the BAM file input as followsSet the parameters for the following options using uploaded pictures as reference:Population model optionsAllelic scope optionsInput filter options

![51](https://user-images.githubusercontent.com/77963733/130159354-9c941c1e-52a2-4345-8245-6fbb3c776318.jpg)


![52](https://user-images.githubusercontent.com/77963733/130159365-17e62592-2693-4b66-9c2f-f79d406e9ec3.jpg)


![53](https://user-images.githubusercontent.com/77963733/130159377-fa30dab0-0547-4e3d-8047-40ababc86442.jpg)


![54](https://user-images.githubusercontent.com/77963733/130159384-10e83cd7-b90d-4c36-82e3-205fe3999671.jpg)




## STEP 6: FILTERING VARIANTS USING VCF

FilterNavigate to tool (VCFfilter) using the search button option on Galaxy webUsing the dataset obtained from step 5 Input parameters as seen in the image below and execute

![61](https://user-images.githubusercontent.com/77963733/130159393-bf828636-a389-4580-a54e-3f8e20702da6.jpg)


![62](https://user-images.githubusercontent.com/77963733/130159398-e5ae3a89-0118-4fa6-ac52-5135899eaf76.jpg)

## STEP 7: VISUALIZATION USING IGV
````bash
Click on processed VCF datasets, it will expand to show link. 
Click on “display at vcf.iobio” at the bottom
Use the reference genome, Human hg38 for comparison
VCF datasets will be index to display them
Repeat process for IGV by clicking on "Display with IGV"
````

![2 _visualization_options-1](https://user-images.githubusercontent.com/77963733/130158091-b579883b-5903-4b12-9cc6-8dfaa8b67383.jpg)

## STEP 8: COMPARING FREQUENCIES


## 📌Team 🚀 Contribution

Individual committment to a group effort- that is what makes a team work, a company work, a society work, a civilization work - **Vince Lombardi**. Any contributions you make are **greatly appreciated** 👏👍

**Contributors:**



- `Temmykeji` 
- Graphic design of workflow, Dataset and FastQC

      


- `Solomon` 
- Dataset, FastQC and Github Markdown


 

- `Rajeshcha44` 
- Mapping of read using BWA-MEM
      
      
 


- `Nitigya-M` 
- Mapping of read using BWA-MEM






- `Abdnahid_` 
- Post Processing mapped read (This contains four steps)

      
      
  

- `Mike` 
- Post Processing mapped read (This contains four steps)



  

- `Karteek` 
- Post Processing mapped read (This contains four steps)
      


      
 

- `Priyacomp` 
- Variant calling of dataset
      
      
  
        
- `MANGAIYARKARASI` 
- Variant calling of dataset

      
  

- `Pragna_lakshmi` 
- Variant calling of dataset using FreeBayes and Comparing of frequencies using VCFtoTab-delimited
        
        
 
- `Naomi` 
- Mapping of read using BWA-MEM


  

- `Galaxy` 
- Filtering of variant call dataset using FreeBayes


  

- `Aarathi04` 
- Filtering of variant call dataset using VCFfilter

       
     
      
           
- `Gautami`**(Team Leader)**
- Visualization using IGV and VCF.IOBIO; and Comparing of frequencies using VCFtoTab-delimited



 
- `ZubairAlam` 
- Visualization using IGV and VCF.IOBIO


  

- `Shreyashi` 
- Visualization using IGV and VCF.IOBIO



- `omimill` 
- Comparing of frequencies using VCFtoTab-delimited and Github Markdown
        
        
        
        
