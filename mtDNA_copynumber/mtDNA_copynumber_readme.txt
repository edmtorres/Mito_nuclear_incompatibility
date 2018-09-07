### analyses to do with mtDNA copy number ####

2 folders:

- Calculating_copyn: Code to estimate mtDNA copy number from 1,000 Genomes Project sequence alignments

	#### calculating mtDNA copy number from low-coverage sequence alignments ####

	Description of files and folders:

		Files:

			1. extract_copy_no.sh: Unix shell script accesses the alignment file online, generates an *.idxstats file, and calculates mtDNA copy number from the *.idxstats file.
				arguments: 
					${1} = id of individual (e.g. NA18486)
					${2} = full name of .bam alignment file  - provided in *.bams.txt files (see below)

			2. cal_mtdna_copy.R: R script uses .idxstats file and read length provided by user
				arguments:
					${1} = name of *.idxstats file
					${2} = read length - this is calculated by extract_copy_no.sh file

			3. phase3.*.mapped.bams.txt: list of individual IDs (first column) and names of *.bam files (second column) - used to run extract_copy_no.sh in batch. 
			* = {CEU,YRI,Americans}

		Folders:

			1. Admixed_Americans: contains *.idxstats files and *.mtdna_no for each individual, which contain the number of reads aligning to each chromosome and mtDNA copy numbers calculated from them, respectively. This folder only contains these files for "admixed" Americans (see paper)

			2. CEU and YRI folder: contains *.idxstats and *.mtdna_no files for CEU and YRI individuals

	#### calculating mtDNA copy number from low- and high-coverage sequence alignments ####

		Files:

			1. extract_copy_no.sh: Unix shell script accesses the alignment file online, generates an *.idxstats file, and calculates mtDNA copy number from the *.idxstats file.
				arguments: 
					${1} = id of individual (e.g. NA18486)
					${2} = full name of .bam alignment file  - provided in *.bams.txt files (see below)
					${3} = coverage type (either low or high). If alignment is low, the argument is just "alignment". If alignment is high, the argument is "high_coverage_alignment"

			2. cal_mtdna_copy.R: R script uses .idxstats file and read length provided by user
				arguments:
					${1} = name of *.idxstats file
					${2} = read length - this is calculated by extract_copy_no.sh file

			3. *_cov_bam.txt: list of IDs and their corresponding bam files. 
				* = {low, high}

		Folders:

			1. "high_coverage_alignment" and "alignment": folders containing *.idxstats and *.mtdna files calculated from high coverage and low coverage alignments, respectively.


- Association_bw_ancestry_and_copyn: Code to run association between mtDNA copy number and mito-nuclear discordance

	Files:

		1. ancestry_mtcopyn_association.R: script which carries out all the relevant association tests between mitonuclear discordance and mtDNA copy number, and outputs all the plots generated in the paper.

		2. cal_med_copyn_06012018.R: script calculated median mtDNA copy number across all chromosomes for each individual

		3. mtdna_copyn_allsamples_06012018.txt: output of cal_med_copyn_06012018.R script. Contains median mtDNA copy number for each individual

		4. lowcov_mtdna_copyn_distribution_6012018.pdf: plot showing distribution of mtDNA copy number annotated by tissue type

		5. mitonuclear_copyn_distribution_06012018.pdf: Fig. 3 of the main text


