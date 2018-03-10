# mitags extraction protocol 
        (see: http://onlinelibrary.wiley.com/doi/10.1111/1462-2920.12250/abstract)

# Install and check :
        
        You need to have  1. perl,  2. python and  install 3. hmmer3 executable (v3.0rc2).
        It is key that you use hmmer-3.0rc2 (install instrcutions below). Make sure this version is called always.
        Once you install everything and you've sucessfully run the tests, then you need to add routes to corresponding scripts
        Tested [Linux kyuss 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux]
        Questions: ramiro.logares at gmail.com
        
1. Download : miTAGs_extraction_protocol.zip :     wget https://github.com/ramalok/mitags_extraction_protocol/archive/master.zip
2. unzip master.zip
3. cd mitags_extraction_protocol-master
4. unzip miTAGs_extraction_protocol.zip
5. mv "miTAGs_extraction protocol" miTAGs_extraction_protocol
5. cd miTAGs_extraction_protocol
6.  wget http://downloads.sourceforge.net/project/cdbfasta/cdbfasta.tar.gz
7. tar xvfz cdbfasta.tar.gz
8. cd cdbfasta
9. make
8. cd ..
9. wget http://eddylab.org/software/hmmer3/3.0rc2/hmmer-3.0rc2.tar.gz
10. tar xvzf hmmer-3.0rc2.tar.gz
11. cd hmmer-3.0rc2/
12. ./configure
13. make
14. cd src/
15. pwd
    /YOUR/PATH/TO/mitags_extraction_protocol-master/miTAGs_extraction_protocol/hmmer-3.0rc2/src
16. PATH=/YOUR/PATH/TO/mitags_extraction_protocol-master/miTAGs_extraction_protocol/hmmer-3.0rc2/src:$PATH  # We add hmmer3 to search path
17. cd ../../
18. zcat test.MERGEDPAIRS.fastq.gz | ./fq_all2std.pl fq2fa > test.merged.fna
19. ./cdbfasta/cdbfasta test.merged.fna
20. ./rna_hmm3.py -i test.merged.fna -o test.merged.rRNA -m ssu,lsu -k bac,arc,euk
21. ./parse_rna_hmm3_output.pl test.merged.rRNA
22. ./extract_rrna_seqs.pl test.merged.rRNA.parsed 1 100

### NB: When you want to run this as part of the Uparse pipeline (https://github.com/ramalok/amplicon_processing), you will need to change the perl script " extract_rrna_seqs.pl " in lines 44 & 46 , adding /my/full/path/to/cdbfasta/cdbyank (instead of ./cdbfasta/cdbyank)


## Citing

#### Publication
Logares, R., Sunagawa, S., Salazar, G., Cornejo-Castillo, F.M., Ferrera, I., Sarmento, H., Hingamp, P., Ogata, H., de Vargas, C., Lima-Mendez, G., Raes, J., Poulain, J., Jaillon, J., Wincker, P., Kandels-Lewis, S., Karsenti, E., Bork, P., Acinas, S.G. 2013. Metagenomic 16S rDNA Illumina Tags are a powerful alternative to amplicon sequencing to explore diversity and structure of microbial communities. Environmental Microbiology. 16(9): 2659-2671.

#### Code

Logares, R., S. Sunagawa, G. Salazar, F. M. Cornejo-Castillo, I. Ferrera, H. Sarmento, P. Hingamp, H. Ogata, C. de Vargas, G. Lima-Mendez, J. Raes, J. Poulain, O. Jaillon, P. Wincker, S. Kandels-Lewis, E. Karsenti, P. Bork and S. G. Acinas (2014). MiTags extraction protocol. https://doi.org/10.5281/zenodo.1195523

[![DOI](https://zenodo.org/badge/45834939.svg)](https://zenodo.org/badge/latestdoi/45834939)
