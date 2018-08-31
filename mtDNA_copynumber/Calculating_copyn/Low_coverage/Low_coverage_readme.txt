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

		3. phase3.*.mapped.bams.txt: list of individual IDs (first column) and names of *.bam files (second column) - used to run extract_copy_no.sh in batch. * = {CEU,YRI}

	Folders:

		1. Admixed_Americans: contains *.idxstats files and *.mtdna_no for each individual, which contain the number of reads aligning to each chromosome and mtDNA copy numbers calculated from them, respectively. This folder only contains these files for "admixed" Americans (see paper)

		2. CEU and YRI folder: contains *.idxstats and *.mtdna_no files for CEU and YRI individuals