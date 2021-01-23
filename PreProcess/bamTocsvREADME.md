We made use of a java program (bamTOCSV.exe.jar) to extract signal track- csvs for training our various downstream models. The program takes into input a <base-file> which helps it build the traininig file (christened em.csv) and the <test-file> which represents the target region of which we will create the signal track csv. They are accompanied by their respecctive index files (of .bai  format). 

The program extracts 10% of the basefile to determince the statistics of the 4 distributions. Then,  1000 regions from the base file are further extracted where there is a relatively high read overlap. These are used to generate the  em.csv file used as a train file across the models. 

With the signal distributions from the base file, we proceed to create signal tracks for <test-file>. These are returned in chunks of 1M Basepairs (w.r.t to the input <genome-description-file> and stored in relevant files titled split-<idx>.csv.

bash
```
java -jar bamToCSV.exe.jar -b <base-file>.bam -i <base-file-index>.bam.bai -g <genome-desccription-file>.genome --testbam <test-file>.bam --testindex <test-file-index>.bam.bai --window 1000000
```

