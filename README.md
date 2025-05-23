[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/fqgrep-binder/HEAD?urlpath=%2Flab%2Ftree%2FDemonstrate+Fulcrum+Genomics+fqgrep.ipynb)

# fqgrep-binder
Demonstrating Fulcrum Genomics' fqgrep in MyBinder-served sessions.  
Click 'launch' badge above to get started.

See [Fulcrum Genomics repo for fqgrep here](https://github.com/fulcrumgenomics/fqgrep) for more about the command line utility.

I use Jupyter Notebooks here with some code to demonstrate how easy it is to use and how you can combine `fqgrep` use in with Python coding and Jupyter conveience to more easily analyze data.


## Attribution

***Clarifying Software Attribution: I, Wayne, am not involved with Fulcrum Genomics or `fqgrep` development in any way. I simply set up this repository to demonstrate the use of it in MyBinder-served Jupyter Sessions. See the links above and below for the materials by those who develop and maintain fqgrep.***

--------

## Related utilities

- seqkit grep
	[seqkit grep](https://bioinf.shenwei.me/seqkit/usage/#grep) appears to allow biological-type mismatches (but not deletion/insertion?) and since it is part of a 'Utrafast FASTA/Q kit', I assume it works on both file formats. I have yet to try it. Learned of it from [this Biostar's post](https://www.biostars.org/p/346852/#346875) when I thought to include 'fuzzy' as a search term when I was pondering why no one cared that Fulcrum Genomics' fqgrep seems not to support biological-style mismatches or Indraniel Das' fqgrep is not maintained. (Related: `seqkit locate` in same package also allows mismatches.)

- Indraniel Das' fqgrep

	While older and in some ways less full-featured than Fulcrum Genomics' fqgrep, [Indraniel Das' fqgrep](https://github.com/fomightez/indraniel_fqgrep-binder) does allow mismatches by specifying insertions, deletions, and substitutions. Plus, it allows FASTA formatted files and has some reporting format options that Fulcrum Genomics' fqgrep doesn't have. See more about it and try it in MyBinder-served sessions [here](https://github.com/fomightez/patmatch-binder).

- Patmatch

	[Patmatch](https://github.com/fomightez/patmatch-binder) will run on FASTA files to find matches to patterns. Patmatch supports IUPAC and mismatch insertions, deletions, and substitutions that I haven't seen fqgrep support. (see about 'indraniel/fqgrep' above for more on some of that.)

	And so if you need to allow mismatches with numbers of insertions, deletions, and substitutions, see more about Patmatch [here](https://github.com/fomightez/patmatch-binder).

- grepq

	Rust-based [grepq](https://github.com/Rbfinch/grepq) - I think this may the most recent entry along these lines, and says, "very fast and scales to large FASTQ files" & "IUPAC ambiguity code support"


### Related converting fastq to fasta to be able to use more available tools

Patmatch and many other tools work with fasta format. It is easy to convert.  
This code in a Jupyter notebook will convert fastq format to fasta containing the sequences:

```shell
%%bash
awk '{if(NR%4==1) {printf(">%s\n",substr($0,2));} else if(NR%4==2) print;}' input.fastq > output.fasta
```

Leave off the magic `%%bash` line if you want to run that on the command line `%%bash` Most system have `awk` by default.


--------

## Note about the older fqgrep

Because later I noticed there is another `fqgrep` out there, I'll highlight that **this repo uses as a source Fulcrum Genomics' [fqgrep repo](https://github.com/fulcrumgenomics/fqgrep)**.   
There is an older `fqgrep` that allows insertions, deletions, and substitutions [here](https://github.com/indraniel/fqgrep). It hasn't been updated in more than a decade, as best I can tell, see [here](https://github.com/indraniel/fqgrep/releases/tag/v0.4.4); I'll refer to it as `indraniel/fqgrep` or something to that effect to distinguish it. I have it working in MyBinder-served session [here](https://github.com/fomightez/indraniel_fqgrep-binder), if you'd like to try it. As best I can tell, `indraniel/fqgrep` doesn't offer any special handling for paired ends, like Fulcrum Genomics `fqgrep` does. 
