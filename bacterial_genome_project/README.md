<details> <summary><H2> Bacterial Genome Assembly </H2></summary>

Using raw data already on Ron, you will losely follow [this](https://github.com/Joseph7e/MDIBL-T3-WGS-Tutorial) tutorial on bacterial genome assembly and annotation. 

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

<details> <summary><H2> Project Tutorial </H2></summary>

For each program that we run in this tutorial, a link to the manual is provided. It is a good idea to skim through to get a good idea of what what options are available, and the purpose of the program. Most commands will use the general options in this tutorial, but depending on your data you may need to adjust some options. Don't forget other ways we talked about finding information on commands (ie `-h`, `--help`, etc).

While you follow this tutorial, make sure to remember that all code should be put into a project script file that will be turned in at the end of the project. Commands that are for you such as `ls`, `cd`, `less`, etc do not go in scripts, only the commands that create, remove, or modify files should be in your script. 

## Starting Data
These samples were sequenced using:
- Illumina HiSeq 2500, paired-end, 250 bp sequencing reads

You will recieve:
- 4 raw fastq files
    - 2 `sample1_R1.fastq.gz` (forward reads denoted by "R1")
    - 2 `sample2_R2.fastq.gz` (reverse reads denoted by "R2")
        - the full name explanation is `SampleName_Barcode_LaneNumber_Direction_001.fastq.gz`
- you will have to run both mystery samples through the whole pipeline.
    - a for loop, multiple for loops, wildcards, and/or variables will be very useful in your script to avoid repeating the same commands for each sample.

## Prepare Your Project Directory + Environment

1. Create a new directory for your project, and navigate into it:
2. Change your permissions so that I can give you your sample
3. Set up your subdirectory structure. Do this early so that you never get confused at what step data is created in!
4. Make a subdirectory for you script. This should be your git repo so that you can update your github every time you update the script. every time you update the script.
5. Either use tmux or nohup to run your script + commands.
    - This makes it so long running commands will not be interrupted if your terminal disconnects or you close your laptop.    
        - [tmux cheatsheet](https://tmuxcheatsheet.com/)
        - [nohup tutorial](https://www.geeksforgeeks.org/nohup-command-in-linux-with-examples/)

6. Activate the `genomics` conda environment
    - if you use tmux, the screen you activate it in will stay in the environmnet
    - if not, you need to activate the environment every time you log into RON
    - you can activate the environment within your script using `source activate genomics` towards the top
## Basic Read Assessment 
These files are gzipped to reduce the large file size of genomic data. Many of the commands we have learned have a version that works with zipped/ compressed file types. `zcat`, `zgrep`, and `zless` all work.

1. take a look at your files using `less -S`. Make sure the files look like fastq files
2. check the number of reads in your files. 
    - Always start by counting the number of reads in each sample. This is done to quickly assess whether we have enough data to assemble a meaningful genome. Usually these file contains millions of reads. Forward and Reverse reads have the same number of entries so you only need to count one.
3. check total bp of your samples
    - (total reads) x (read length of 250) x ( 2 for paired-end) = total base pairs

4. roughly estimate genome coverage of bacterial genome
    - (total base pairs) / (estimated bacterial genome size of ~7Mbp)

```bash
# repeat for each mystery sample
zgrep -c '^@' sample_forward_read
echo "read_count * 250 * 2" | bc
echo "total_bp / 7000000" | bc
```

Coverage Generally greater than 10x is considered good for an assembly to take place. If you don't get this number, normally you would have to go back out and collect more data, or scrap the project.

## Quality Control of Reads
[Fastqc](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/) is the standard for read assessment. It gives you stats for each read file. This gives you assurance that your data is good enough to continue with the assembly.

1. Use `FastQC` to assess the quality of your reads. This will generate a report in HTML format that you can open in a web browser.
    - Make sure to run FastQC on both forward and reverse reads.
    - Just as a reminder, make a directory for the output of `fastqc`. If you look at `--help`, you can see that there is a `-o` flag to denote where you want the output to go
2. Download the resulting `html` files to your local device to view2. Download the resulting `html` files to your local device to view

## Adapter and Quality Trimming

[Trimmomatic](http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/TrimmomaticManual_V0.32.pdf) is the standard tool, but [this figure](https://www.researchgate.net/figure/Comparison-of-various-tools-for-trimming-adapters_tbl1_228099841) shows many other tools that cut adaptors and/or trim low-quality bases.

You may have noticed from the fastqc output the some of your reads have poor qualities towards the end of the sequence, this is especially true for the reverse reads and is common for Illumina data. You may also notice that the fastqc report 'failed' for adapter content. The Trimmomtic program will be used to trim these low quality bases and to remove the adapters.

(Joe)[https://github.com/Joseph7e] created a wrapper script called `trim_scriptV2.sh` which makes this program much easier to use. It is available on the server by calling its name. For this wrapper script the input is the raw forward and reverse reads and the output will be new trimmed fastq files. We will use these trimmed reads for our genome assembly. When you are more comfortable using BASH you can call Trimmomatic directly by using the manual or by copying the code from the provided script.

1. take a look at the script at what is inside the script
    - you should notice that although the trimmomatic part is a bit confusing, you should understand how this script helps take in both foward and reverse reads, and designates output names

```bash
which trim_scriptV2.sh
less "path to trim_scriptV2.sh"
```
2. Run the script on your reads.
3. Move trimmed reads to new directory
4. Repeat Quality Control Steps on these newly trimmed reads
    - You should notice a difference, especially in the quality scores and adapter content if these were lacking before.

## Genome Assembly


</details> <!-- End Project Tutorial -->
