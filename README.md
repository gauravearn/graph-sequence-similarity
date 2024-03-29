# graph-sequence-similarity
a site specific function to estimate the site similarity across the graphs to make it faster, i implemented a linear approach so that it will compare the iterable as a list and then stores it in the another iterable. You can nest these functions as callables under the class. Since graphs are nested as the linear in the grammar of the graphics, so it specifically reads the fasta as a linear fasta file and not multi line fasta. 
```
usage
def alignmentChecker(alignmentfile = None):
  # Universitat Potsdam
  # Author Gaurav Sablok
  # date: 2024-3-1
    """"
    a site specific function to estimate the site similarity across the graphs
    to make it faster, i implemented a linear approach so that it will compare 
    the iterable as a list and then stores it in the another iterable. You can
    nest these functions as callables under the class. 
    """
    if alignmentfile is not None:
        readalignment = open(alignmentfile)
        fastaidlist = []
        fastasequences = []
        for i in readalignment.readlines():
            if i.startswith(">"):
                fastaidlist.append(i.strip().replace(">", ""))
            else:
                fastasequences.append(i.strip())
        resolveids = [j for i in fastaidlist for j in i]
        resolvesequences = [j for i in fastasequences for j in i]
    return list(zip(fastaidlist,fastasequences))
def computeSimilarity(alignmentfile = None):
    alignmentiterable = alignmentChecker(alignmentfile)
    storingseq = list(map(lambda num: list(num[1]), alignmentiterable))
    # [storingseq[i][j] for i in range(len(storingseq)-1) for j in storingseq[i] if storingseq[i][j] not in storingseq[i+1][j]] 
    alignemnt_similarity = [storingseq[i] for i in range(len(storingseq)-1) \
                                                 if storingseq[i] not in storingseq[i+1]]
    return alignemnt_similarity
```

Gaurav Sablok \
Academic Staff Member \
Bioinformatics \
Institute for Biochemistry and Biology \
University of Potsdam \
Potsdam,Germany
