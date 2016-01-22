## mitags extraction scripts 
        (see: http://onlinelibrary.wiley.com/doi/10.1111/1462-2920.12250/abstract)

# Install and check :

###    you need to have 1. perl, 2. python and 3. hmmer3 executable
1. Download : miTAGs_extraction_protocol.zip : https://github.com/ramalok/mitags_extraction_protocol/blob/master/miTAGs_extraction_protocol.zip
2. Unzip all
3. cd to folder containing files
4.  wget http://downloads.sourceforge.net/project/cdbfasta/cdbfasta.tar.gz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fcdbfasta%2Ffiles%2F%3Fsource%3Dnavbar
5. tar xvfz cdbfasta.tar.gz
6. cd cdbfasta
7. make
8. cd ..
9. zcat test.MERGEDPAIRS.fastq.gz | ./fq_all2std.pl fq2fa > test.merged.fna
10. ./cdbfasta/cdbfasta test.merged.fna
11. ./rna_hmm3.py -i test.merged.fna -o test.merged.rRNA -m ssu,lsu -k bac,arc,euk
12. ./parse_rna_hmm3_output.pl test.merged.rRNA
13. ./extract_rrna_seqs.pl test.merged.rRNA.parsed 1 100
