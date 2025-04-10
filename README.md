[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/fqgrep-binder/HEAD?urlpath=%2Fdoc%2Ftree%2FDemonstrate+Fulcrum+Genomics+fqgrep.ipynb)

# fqgrep-binder
Demonstrating Fulcrum Genomics' fqgrep in MyBinder-served sessions.  
Click 'launch' badge above to get started.

See [Fulcrum Genomics repo for fqgrep here](https://github.com/fulcrumgenomics/fqgrep) for more about the command line utility.

I use Jupyter Notebooks here with some code to demonstrate how easy it is to use and how you can combine `fqgrep` use in with Python coding and Jupyter conveience to more easily analyze data.


## Attribution

***Clarifying Software Attribution: I, Wayne, am not involved with Fulcrum Genomics or `fqgrep` development in any way. I simply set up this repository to demonstrate the use of it in MyBinder-served Jupyter Sessions. See the links above and below for the materials by those who develop and maintain fqgrep.***

--------

## Related utility

[Patmatch](https://github.com/fomightez/patmatch-binder) will run on fasta to find matches to patterns. Patmatch supports IUPAC and mismatch insertions, deletions, and substitutions that I haven't seen fqgrep support. (see about 'indraniel/fqgrep' below for more on that.)

And so if you need to allow mismatches with numbers of insertions, deletions, and substitutions, see more about Patmatch [here](https://github.com/fomightez/patmatch-binder).


### Related converting fastq to fasta to be able to use more available tools

Patmatch and many other tools work with fasta format. It is easy to convert.  
This code in a Jupyter notebook will convert fastq format to fasta containing the sequences:

```shell
%%bash
awk '{if(NR%4==1) {printf(">%s\n",substr($0,2));} else if(NR%4==2) print;}' input.fastq > output.fasta
```

Leave off the magic `%%bash` line if you want to run that on the command line `%%bash` Most system have `awk` by default.


--------

## Not about the older fqgrep

Because later I noticed there is another fqgrep, I'll point out **this repo specifically uses as soure Fulcrum Genomics' [fqgrep repo](https://github.com/fulcrumgenomics/fqgrep)**.   
(There is an older `fqgrep` that allows insertions, deletions, and substitutions [here](https://github.com/indraniel/fqgrep). It hasn't been updated since 2016, as best I can tell, see [here](https://github.com/indraniel/fqgrep/releases/tag/v0.4.4); I'll refer to it as `indraniel/fqgrep` ot something to that effect to distinguish it. As best I can tell, `indraniel/fqgrep` doesn't offer any special handling for paired ends, like Fulcrum Genomics `fqgrep` does.)
