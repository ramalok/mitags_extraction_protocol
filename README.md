## mitags extraction scripts 
        (see: http://onlinelibrary.wiley.com/doi/10.1111/1462-2920.12250/abstract)

# Install and check :

    you need to have 1. perl, 2. python and 3. hmmer3 executable
    tar xvfz test.tgz
    cd test
    wget http://downloads.sourceforge.net/project/cdbfasta/cdbfasta.tar.gz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fcdbfasta%2Ffiles%2F%3Fsource%3Dnavbar
    tar xvfz cdbfasta.tar.gz
    cd cdbfasta
    make
    cd ..
    zcat test.MERGEDPAIRS.fastq.gz | ./fq_all2std.pl fq2fa > test.merged.fna
    ./cdbfasta/cdbfasta test.merged.fna
    ./rna_hmm3.py -i test.merged.fna -o test.merged.rRNA -m ssu,lsu -k bac,arc,euk
    ./parse_rna_hmm3_output.pl test.merged.rRNA
    ./extract_rrna_seqs.pl test.merged.rRNA.parsed 1 100
