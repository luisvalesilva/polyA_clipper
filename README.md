# polyA_clipper

Simple application to clip off poly(A) tails from reads in FASTQ files.

Given a FASTQ file (originally one generated by PAT-seq; Poly(A)-Test
RNA-sequencing), **`polyA_clipper`** performs the following steps:
 
1. Load input fastq file one line at a time;
2. After loading each group of 4 lines:
    * If the read ends in "AAAAA":
        * Clip all "A"s from the end of the sequence
        * Update seq length in lines 0 and 2
        * Clip corresponding quality score characters
 3. Append 4 lines to output file.
 
Currently **`polyA_clipper`** does **not**:

* Find runs of “A”s extending into the adaptor sequence
* Allow any errors in the sequence
* Consider read base quality


## How to run

To run **`polyA_clipper`** your `example.fastq`:
 
1. Clone the repo and go inside
```shell
git clone https://github.com/luisvalesilva/polyA_clipper.git
cd polyA_clipper/
```

2. Run **`polyA_clipper`**

```shell
python polyA_clipper.py -f /path/to/example.fastq
```

Print help string:
```shell
python polyA_clipper.py

# Or
python polyA_clipper.py -h
```
## License

This project is licensed under the terms of the MIT license. See [LICENSE](LICENSE) file for details.
