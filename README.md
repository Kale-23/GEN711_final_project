# gen_projects
project information for gen711/811 final projects 

General Information About the Project

1. You will have a final github repo that contains all your information and code within. You can find an example [here](https://github.com/jthmiller/gen711-811-example)
2. You will complete a final presentation on your findings, what you did to get them, and what tools you used. you can find an example [here](https://github.com/Kale-23/Qiime2_Microbiome_Analysis/blob/main/presentation/gen711_final_presentation.pdf)
3. We are expecting you to put in effort outside of just lab time. Bioinformatics work, especially computation time for each step, takes much longer than 2 hours once a week. Please make sure to meet with your groups a couple times a week and try to complete a couple steps in your pipeline before each lab time.
4. Lab times will now mostly be time to work on your projects. We will be at lab to help guide you through each step, introduce tools and methods for you to use in your project, and explain what you are doing.

<details> <summary><H2> Quiime2 Projects </H2></summary>

<details> <summary><H3> Human microbiome Study </H3></summary>
  
Data taken from [this](https://microbiomejournal.biomedcentral.com/articles/10.1186/s40168-016-0225-7) Human microbiome study is used to perform a bioinformatic pathway analysis based on [this](https://docs.qiime2.org/2022.2/tutorials/fmt/) tutorial by qiime2. 

Some stuff you will get done:

- cleaning + assessment of raw read inputs
- alignment of 16s regions
- classification of microbes
- phylogenetic tree visualization of microbe relationships
- Diversity metrics of dataset

<details> <summary><i> initial data downloads </i></summary>

[sample metadata](https://data.qiime2.org/2022.2/tutorials/fmt/sample_metadata.tsv)  

<br>

[foward reads](https://data.qiime2.org/2022.2/tutorials/fmt/fmt-tutorial-demux-1-10p.qza)  

<br>

[reverse reads](https://data.qiime2.org/2022.2/tutorials/fmt/fmt-tutorial-demux-2-10p.qza)
  
</details> <!-- end initial data downloads -->

<details> <summary><i> an example output </i></summary>

![](https://github.com/Kale-23/Qiime2_Microbiome_Analysis/blob/main/plots/alpha-group-sig-obs-feats.png)

Shows an alpha diversity metric on the y axis, and a metadata variable on the x. This specific plot shows the observed features metric vs treatment group.

</details>  <!-- End an example output -->

</details> <!-- End Human microbiome Study -->

</details> <!-- End Quiime2 Projects -->

<details> <summary><H2> Bacterial Genome Assembly </H2></summary>

Using raw data already on Ron, you will losely follow [this](https://github.com/Joseph7e/MDIBL-T3-WGS-Tutorial) tutorial on creating a genome that would be ready to upload to a database such as NCBI

Some stuff you will get done:

- cleaning + assessment of raw read inputs
- Genome assembly
- Genome assessment + quality checking
- Organism identification
- Genome filtering
- Visualization of Genome

<details> <summary><H3>  an example of a final genome visualization! </H2></summary>
  
![](https://github.com/Joseph7e/MDIBL-T3-WGS-Tutorial/blob/master/img/genome-visual.png)
  
</details> <!-- End final visualizations -->

</details> <!-- End Bacterial Genome Assembly -->

