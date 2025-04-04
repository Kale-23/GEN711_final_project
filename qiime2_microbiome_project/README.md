<details> <summary><H2> Quiime2 Pond Microbiome Study </H2></summary>

Using raw data already on Ron, you will losely follow [this](https://amplicon-docs.readthedocs.io/en/latest/tutorials/gut-to-soil.html) tutorial on microbiome analysis using qiime2. You will not be using the data in the tutorial, but you can adapt the commands to fit your data.

Some stuff you will get done:

- cleaning + assessment of raw read inputs
- alignment of 16s regions
- classification of microbes
- phylogenetic tree visualization of microbe relationships
- Diversity metrics of dataset

<details> <summary><i> an example output </i></summary>

![](https://github.com/Kale-23/Qiime2_Microbiome_Analysis/blob/main/plots/alpha-group-sig-obs-feats.png)

Shows an alpha diversity metric on the y axis, and a metadata variable on the x. This specific plot shows the observed features metric vs treatment group.

</details>  <!-- End an example output -->


</details> <!-- End Quiime2 Projects -->

<details> <summary><H2> Project Tutorial </H2></summary>

## Starting Data 

I have borrowed 16s data from another grad student who is studying the microbiome composition of duckweeds. You will recieve 40 fastq files and a metadata file for this project.

This data is in :
- Illumina HiSeq 2500
- paired-end 
- 250 bp sequencing reads

These files include:
- 20 total samples
    - 2 different pond sampling locations
    - 2 "treatments"
        - microbiome sampled directly from duckweed skimmed off the surface of the pond
        - microbiome sampled directly from pond water 
    - 5 replicates of each treatment
- a metadata file to tell qiime which samples are which
- a manifest file to tell qiime where the fastq files are located for importing

## Prepare Your Project Directory + Environment

1. Create a new directory for your project, and navigate into it:
2. Change your permissions so that I can give you your sample
3. Set up your subdirectory structure. Do this early so that you never get confused at what step data is created in!
4. Make a subdirectory for you script. This should be your git repo so that you can update your github every time you update the script. every time you update the script.
5. Either use tmux or nohup to run your script + commands.
    - This makes it so long running commands will not be interrupted if your terminal disconnects or you close your laptop.    
        - [tmux cheatsheet](https://tmuxcheatsheet.com/)
        - [nohup tutorial](https://www.geeksforgeeks.org/nohup-command-in-linux-with-examples/)

6. Activate the `qiime2-amplicon-2024.5` conda environment
    - if you use tmux, the screen you activate it in will stay in the environmnet
    - if not, you need to activate the environment every time you log into RON
    - you can activate the environment within your script using `source activate qiime2-amplicon-2024.5` towards the top

While you follow this tutorial, make sure to remember that all code should be put into a project script file that will be turned in at the end of the project. Commands that are for you such as `ls`, `cd`, `less`, etc do not go in scripts, only the commands that create, remove, or modify files should be in your script. 

## Starting the Tutorial

Your data is already demultiplexed, so you can skip the demultiplexing step in the tutorial

You will start by importing your data into qiime2. Qiime2 uses their own filetypes `.qza` and `.qzv` to store data. `.qza` files are where your data is stored, `.qzv` files are for vizualizations. You are starting with raw fastq files, so you first need to get these files into `qza` format to work with qiime2.

- you will have to use `qiime tools import` to import your data
    - your fastq type is `'SampleData[PairedEndSequencesWithQuality]'` 
    - your metadata file is in the `PairedEndFastqManifestPhred33V2` format
    - if you need further help, the [qiime2 import tutorial](https://amplicon-docs.readthedocs.io/en/latest/how-to-guides/how-to-import.html) is a good resource

- __Make sure to put all this in your script file__

## Quality Control

Sequencing is not a perfect art. Many reads will have poor quality and other bad characteristics. These reads will also still have illumina adapters in their sequence. You need to remove the bad reads, and trim the adapters from the good reads. 

1. Visualize what your data looks like before any trimming or filtering
    - use `qiime demux summarize` to visualize your data
    - this will create a `.qzv` file that you can view in the [qiime2 view website](https://view.qiime2.org/)
    - use this to assess the quality of your data
        - look for regions of low quality in your reads
            - reverse reads tend to have lower quality than forward reads
            - the ends of reads tend to have lower quality than the middle
        - do any regions need to be cut off due to too low a score?
2. Qiime2 offers many ways to filter your reads (DADA2, Deblur, and basic quality-score-based filtering). We will use DADA2.
    - use [this](https://amplicon-docs.readthedocs.io/en/latest/tutorials/gut-to-soil.html#A9FW1su6CQ) tutorial to help you with the DADA2 step
    - make sure to output this step into a new subdirectory. Again, keeping good directory structure will help you keep track of your data
    - the output of this step is more metadata, and your Amplicon Sequence Variants (ASVs), which are all the unique sequences in your data

3. Again, continue through the tutorial 
    - you will need to use `qiime feature-table summarize` to visualize your ASVs
    - you will also need to use `qiime feature-table tabulate-seqs` to visualize the sequences of your ASVs

4. Use the `qiime feature-table filter-seqs` command to filter out any ASVs that are only in a certain number of samples. This will help you reduce the size of your data and make it easier to work with.
    - we only have 20 samples (the full dataset has 264 samples), so it may be a good idea to be conservative with this number.

</details> <!-- End Project Tutorial -->
