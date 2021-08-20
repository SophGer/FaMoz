# FaMoz
FaMoz (an acronym for "Father/Mother") a software for parentage studies, written in the C language and in TclTk, uses likelihood calculation and simulation to perform parentage studies with codominant and dominant markers (Gerber _et al._ 2000, Gerber _et al._ 2003).

*Gerber S., Streiff R., Bodénès C., Mariette S., Kremer, A., 2000. Comparison of microsatellites and AFLP markers for parentage analysis. Molecular Ecology 9: 1037-1048.

*Gerber S., Chabrier P., Kremer A. 2003. FaMoz: a software for parentage analysis using dominant, codominant and uniparentally inherited markers. Molecular Ecology Notes 3: 479-481.

The software was originally available here: http://www.pierroton.inra.fr/genetics/labo/Software/Famoz/index.html

On Github:

**FaMozTclTk.zip** contains all elements necessary to run the software (see the content of the more recent Famoz.help file below)

**FaMozCCode.zip** contains all the C code that is used (after compilation), by the software.


## **Content of the last file FaMoz.help "Help to use FaMoz.tcl"** ##
June 2003

FaMoz.tcl is a program written in tcltk (see http://tcl.activestate.com/scripting/)
which is a scripting language gluing together C programs in the present case. 
It also uses BLT (see http://www.tcltk.com/blt/) for graphical purposes.

It was written and maintained by:
Sophie Gerber

To be able to run the program, you need a sun/unix/solaris computer or windows98. You need first to install TclTk and BLT on your computer, they are freely distributed and downloadable on Internet, and you will find it easy to make them work. Have a look at the "demos" provided with the programs to get an idea of what they can do.

You will first have to load your data file by clicking on the pink "File" command in the menu.You can load your data file into the screen, save or clear the screen at any time.
The data set are simple text files and have all the same looking. Please use only numbers and check that the sum of your frequencies for codominant markers is precisely 1 (5 digits precision for instance). You can put any comment about your data file at the end of the file.

You will find a series of data files for test in the "data" directory, files are named as follows:
-"pat" refers to paternity analysis, il nothing is specifies, parentage analysis is concerned
-"cod", "dom", "cyt", "miss" refers to codominant, dominant and cytoplasmic markers, and missing data

Here are how the entry files should look like:

NB - Missing data should be coded as -5
     In the likelihood calculations, a missing data is replaced by all possible allele at the locus, and the correponding 
     likelihood is multiplied by the frequency of occurence of this allele. At the end, the likelihood is a weighted average
     over all possible allelic states at the missing data.
NB - for any kind of loci (codominant or cytoplasmic), your alleles should be numbered in a continuous manner, 
     from 1 to number_of_alleles. 
     For instance, if you have 3 alleles, you will have allele 1, 2 and 3 observed, and nothing else.
NB - If alleles are present in offspring but not in parents, a null frequency for this allele at the beginning 
     of the datafile should be avoided (the expected frequency of the offspring having this allele 
     will be zero and as this frequency appears in the denominator of likelihoods, they will be impossible to compute)
     Calculate preferably allele frequencies on the whole set of individuals or alternatively, give
     a very low frequency to alleles only found in offspring.
NB - Please use ONLY NUMBERS, and no letters, in your files


******* For codominant markers and paternity analysis ******* 
________________________________

Number_of_loci
number_of_alleles_locus_n°1 frequency_locus1_allele1 ...[...]...frequency_locus1_last allele
[...]
number_of_alleles_last_locus frequency_last_locus_allele1 ...[...]...frequency_last_locus_last allele

number_of_genotyped_parents number_of_genotyped_offspring

number_of_parent1 genotype_parent1
[...]
number_of_last_parent genotype_last_parent

number_of_kid1_mother number_of_kid1 genotype_kid1
[...]
number_of_last_kid_mother number_of_last_kid genotype_last_kid
___________________________________________

Example:
___________________________________________

2
3 0.3 0.4 0.3
4 0.5 0.2 0.1 0.2
2 3

1 1 2 1 3
2 2 2 1 4

2 1 2 3 1 3
2 2 1 2 3 4 
1 3 1 3 3 3

___________________________________________

In this example, there are 2 nuclear loci, the first locus has 3 alleles, the first allele has a frequency of 0.3 in the parental population. Two parents were genotyped and 3 offspring, offspring n°1 is from mother n°2 and has the 2nd and 3rd alleles at locus one. Be careful that at locus 1, allele numbered 1 in genotypes corresponds to the first frequency at locus one, and so on !


******* For codominant markers and parentage analysis ******* 

___________________________________________

Number_of_loci
number_of_alleles_locus_n°1 frequency_locus1_allele1 ...[...]...frequency_locus1_last allele
[...]
number_of_alleles_last_locus frequency_last_locus_allele1 ...[...]...frequency_last_locus_last allele

number_of_genotyped_parents number_of_genotyped_offspring

number_of_parent1 genotype_parent1
[...]
number_of_last_parent genotype_last_parent

number_of_kid1 genotype_kid1
[...]
number_of_last_kid genotype_last_kid
___________________________________________

Example:
___________________________________________

2
3 0.3 0.4 0.3
4 0.5 0.2 0.1 0.2
2 3

1 1 2 1 3
2 2 2 1 4

1 2 3 1 3
2 1 2 3 4 
3 1 3 3 3

___________________________________________

In this example, there are 2 nuclear loci, the first locus has 3 alleles, the first allele has a frequency of 0.3 in the parental population. Two parents were genotyped and 3 offspring, offspring n°1 has the 2nd and 3rd alleles at locus one.

******* For dominant markers and paternity analysis ******* 

Number_of_loci
frequency_presence_allele_locus1 ...[...]...frequency__presence_allele_last_locus

number_of_genotyped_parents number_of_genotyped_offspring

number_of_parent1 genotype_parent1
[...]
number_of_last_parent genotype_last_parent

number_of_kid1_mother number_of_kid1 genotype_kid1
[...]
number_of_last_kid_mother number_of_last_kid genotype_last_kid

___________________________________________

7 0.8 0.1 0.3 0.9 0.2 0.2 0.2
4 5
1 1 0 0 0 1 0 1
2 0 0 0 1 0 1 0
3 1 1 1 0 0 0 0
4 0 0 1 0 1 0 1

2 1 0 0 0 0 0 0 0
3 2 0 1 0 1 0 1 1
4 3 0 0 0 1 1 1 1
1 4 -5 1 1 0 1 0 0
2 5 -5 0 0 1 0 1 1
___________________________________________

In this example, there are 7 dominant loci, the first locus has a frequency of 0.3 (presence allele) in the parental population, the second, 0.1 and the last 0.2. Four parents were genotyped and 5 offspring, offspring n°1 is from mother n°2, and shows none of the 7 bands. Offspring n°4 and 5 have missing data for locus 1. 


******* For dominant markers and parentage analysis ******* 

Number_of_loci
frequency_presence_allele_locus1 ...[...]...frequency__presence_allele_last_locus

number_of_genotyped_parents number_of_genotyped_offspring

number_of_parent1 genotype_parent1
[...]
number_of_last_parent genotype_last_parent

number_of_kid1 genotype_kid1
[...]
number_of_last_kid genotype_last_kid
___________________________________________

3 0.5 0.001 0.6
4 3
1 1 0 0
2 0 0 0
3 1 1 1
4 0 0 1

1 0 0 1
2 0 1 0 
3 0 0 0 

In this example, there are 3 dominant loci, the first locus has a frequency of 0.5 (presence allele) in the parental population, the second, 0.001 and the last 0.6. Four parents were genotyped and 3 offspring, offspring n°1 and shows only presence of band at locus n°3.

Cytoplasmic markers
________________________

These loci should be put at the end of the data file, that is, they are part of the total number of loci, and there description in term of frequencies is following the one concerning codominant or dominant markers. The genotype of individuals for cytoplasmic markers is also at the end, following genotype for other markers.

Example (dominant nuclear markers):
___________________________________________

4 
0.5 0.001 0.6
4 0.5 0.1 0.1 0.3
4 3
1 1 0 0 1
2 0 0 0 2
3 1 1 1 4
4 0 0 1 3

1 0 0 1 3
2 0 1 0 1
3 0 0 0 2
___________________________________________

In this example, there are 3 nuclear markers and one cytoplasmic marker. This marker has 4 haplotypes, each in frequencies 0.5, 0.1, 0.1 and 0.3. Parent 1 has haplotype n°1 and offspring 1 haplotype n°3 for the cytoplasmic marker.

Codominant, cytoplasmic and dominant markers
________________________

In your file, put first the codominant loci, then the cytoplasmic, and then the dominant one. The genotypes of individuals for codominant, cytoplasmic and dominant markers should follow the order given in the header

Example:
___________________________________________


5
3 0.2 0.3 0.5
4 0.25 0.25 0.25 0.25
5 0.2 0.2 0.2 0.2 0.2
4 0.01 0.19 0.7 0.1

7 0.1 0.1 0.2 0.2 0.1 0.1 0.2

10 0.2 0.5 0.4 0.3 0.15 0.25 0.3 0.4 0.26 0.12


5 6

1 1 2  2 4  5 5  2 4  7  1 1 0 0 1 0 0 0 0 1 
2 2 3  3 3  1 2  2 4  5  0 0 0 0 0 0 0 0 0 0
3 1 1  2 4  1 5  2 4  1  1 1 1 1 1 1 1 1 1 1
4 1 2  2 4  3 4  1 2  2  1 0 1 1 0 0 1 0 1 0
5 2 3  2 2  4 5  1 2  4  0 1 0 1 0 1 0 1 0 1

1 1 1  2 2  3 3  4 4  1  0 1 0 1 1 0 0 1 1 0 
2 2 3  4 4  1 5  3 4  7  1 1 0 1 1 1 0 0 0 0
3 1 2  1 2  1 2  1 2  1  1 0 1 0 1 1 1 0 1 0 
4 2 3  2 3  2 3  2 3  5  1 0 0 1 1 0 1 0 0 1
5 3 3  1 4  1 5  2 4  6  1 1 0 1 1 1 0 0 1 1 
6 1 3  3 4  1 5  1 4  3  0 0 0 1 0 1 0 0 1 0 

In this example, you have 4 codominant loci, with 3, 4 5 and 4 alleles each, then a cytoplasmic marker with 7 different haplotypes, 10 dominant markers. There are 5 parents and 6 offspring, the first parent has the 1/2 genotype at codominant locus 1, haplotype 7 at cytoplasmic marker and phenotype 1 at the first dominant locus.

___________________________________________

WORKING WITH FAMOZ
___________________________________________

The default type of marker is codominant. If you have to define the kind of markers you're working with, press the purple command Marker on the menu bar. Select codominant, dominant or both, if you have cytoplasmic markers, you have to press a second time to tell the program how many of them are present in the data file. Do not forget to declare your number of cytoplasmic markers or it could cause errors in the following. If these markers are maternally inherited, you have to push the button in the cytoplasmic window.
At the end of the "Marker" command, you will be able to decide either to take missing data into account (the software replaces any missing allele by all other alleles at the locus and calculates a mean lod-score for the locus) which can be time consuming, or to simply discard loci with missing data, which is much quicker.
The last option of the "Markers" menu, "Find identical genotypes", looks for individuals for which all loci have identical alleles.

*****  Probabilities *****

You can calculate first EXCLUSION probabilities by using the clear blue Exclusion command.
The formulas of the probabilities for codominant markers are given in  Jamieson & Taylor (1997) and for dominant markers in  Gerber et al (2000). 
You will just need the description of your loci in terms of number of alleles and frequencies, nothing else is needed.

IDENTITY probabilities, expected or observed, can also be computed in the same menu. They represent the probability that two individuals drawn at random from a population will have the same genotype at multiple loci. Formulae for codominant and dominant markers can be found in Waits et al. 2001.


***** Lod scores / delta *****

You will then be able to calculate likelihood ratio according to formulas given in Gerber et al (2000), plus the addition of F, excess of heterozygotes in your parental population. You will have to choose between best father or parents/couple when clicking on the Lod score button.
The introduction of parameter F modify the genotype frequencies and the generation of gametes (more homozygotes than expected at random, using a selfing rate of 2*F/(1+F) in simulated crosses (this corresponds to the theoretical value of selfing in a population at equilibrium)).
To determine a lod score threshold to choose a father, a parent or a parent pair as the true one, you will have to perform some simulation, since likelihood ratio in these cases are not following particular statistical law. The Simulation item will help you to do that.

You'll be able to compute delta score for each potential father/parent or parent pair, that is the difference between the likelihood ratio of the individual (or pair) considered and the highest likelihood ratio observed among potential parent, for the offspring studied.

  **Half- full-sibship likelihood
This option is only available for codominant markers. The file to be used has to be the same format as the one used for parentage analysis.

******* Simulation / Paternity *******

When selecting "Fathers from inside/outside stand: most likely fathers" from the Simulation menu, you will simulate a given number of offspring with father selected at random from your sample set of genotyped parents.
Each simulation consists in two steps:
Firstly:
 - randomly sampling a mother, generating a gamete from the mother,
 - randomly sampling a father, generating a gamete from the father,
 - associating both gametes to generate the offspring,
 - finding out the most likely father of this offspring among the genotyped parents, recording its lod score value and delta value.
Secondly:
 - randomly sampling a mother, generating a gamete from the mother,
 - randomly generating a gamete following the frequencies of the data sample (an allele with a 0.4 frequency will be present in the gamete on 40 gametes over 100 on average),
 - associating both gametes to generate the offspring,
 - finding out the most likely father of this offspring among the genotyped parents, recording its lod score value and delta value.

For each simulation you will be asked to give
 - the number of simulated offspring,
 - the simulation error, that is the number of times a mistake will be done, replacing the allele coming from the genotyped parent by a randomly selected one,
 - the calculation error, that is, the value used in lod score calculation according to formulas given in Gerber et al. 2000,
 - If a non null F (departure from Hardy-Weinberg) is provided, offspring will be generated with an excess of homozygotes.

The software creates 3 files containing the lod-scores of most likely fathers in case of good (gd) or bad decision (bd) for offspring with fathers among genotyped individuals (in) and for fathers simulated according to allele frequencies (out), where a likely father is necessarily a wrong father [father.gd.in, father.bd.in, father.bd.out]. It creates also 3 files in the same situations but recording delta, the difference of the lod-scores of the first and second most likely fathers [deltafather.gd.in, deltafather.bd.in, deltafather.bd.out].



******* Simulation / Parentage *******

The simulation concerning "Parents from inside/outside stand: most likely par&coup", that is most likely parents and couple, follows the same way, but samples both parents among the genotyped parent or both parents according to allele frequencies. For each simulated offspring, the two most likely individual parents and the most likely parent pair are found and their lod score and delta score are recorded. 

The following files storing lod scores are produced at the end of simulations, for both most likely parent ("parent") and parent pairs ("pair"), either issued from simulation with parent from inside ("in") or outside the stand ("out"), resulting in good ("gd") or bad decision ("bd"). "delata" is the lod score difference between the first and the second most likely:
deltaparent.gd.in	deltapair.gd.in		deltaparent.bd.in	deltapair.bd.in		
parent.gd.in		parent.bd.in		pair.gd.in		pair.bd.in		
deltaparent.gd.out	deltapair.gd.out	deltaparent.bd.out	deltapair.bd.out	
parent.gd.out		parent.bd.out		pair.gd.in		pair.bd.in

After these simulation, the two histograms (most likely fathers / single parents / parent pair from inside the stand / outside the stand) can be observed thanks to the Graphics command for each of the three situations following the simulation "fathers lod distribution" after a paternity analysis and both "parents" and "couples lod distribution" after a parentage analysis with either lod score values or delta. You can zoom on any part of the graphic by selecting a zone with the mouse, to measure where the two curves are crossing, for instance. 


******* Simulation / Individuals *******

The "simulating individual" section simulates a given number of individual according to the loci and the allele frequencies in the studied population. For each individual, two gametes are randomly drawn using the frequencies provided by the user. The simulated individual number and its genotype are given. This is a way to add individuals to your data or to simulate an additionnal locus to test for the number of loci effet. Just use your favorite text editor to generate files.

*** Test ***
The green command "Test" allows you to check for each offspring, in your paternity analysis if a father can be find, or in a parentage analysis, if zero, one or a pair of parents can be find according to the test. The program will ask you for the paternity test type (with lod score, delta or both) and then paternity thresholds (lod score and/or delta) or single parent and parent pair thresholds. For parentage analysis, if a parent has a lod score (or a delta) exceeding the single parent threshold, it is considered as a true potential parent, and if a parent pair has a lod score (or delta) greater than the threshold and is made with two true potential parents, it is considered as a true potential parent pair. No father is assigned if there are ex-aequo scores.


*** Simulation of Paternity / Parentage test: decisions and gene flow ***
____________________________________________________________

This section of the test button is a way to simulate a test.

For paternity you will be asked 
- to select a given number of mothers either at random or in a list you will give, 
- to provide the number of offspring to simulate per mother,
- to give the threshold for paternity

For parentage you will be asked 
- to provide the number of offspring to simulate,
- to give the value of F, departure from Hardy-Wainberg equilibrium,
- to give the threshold for single parent,
- to give the threshold for parent pair,

In both cases, after having simulated an offspring:
- either by choosing a mother or by picking a mother at random and by creating a father gamete among the genotyped parents or according to allele frequencies, for paternity simulation,
- by picking both parent randomly according to the method explained above and by generating gametes creating the offspring,
the most likely father / single parent and parent pair are looked for. The test is then performed on these most likely individuals:
- if the lod score of the most likely father exceeds the paternity threshold (and there are no ex-aequo scores), it is considered as the true parent,
- if the lod score of the most likely parent pair exceeds the parent pair thresholdif AND if the lod score of each of the single parent of this parent pair exceeds the single parent threshold, the parent pair is considered as the true parental pair.
- if no parent pair is retained according to the rule described above but if a single parent has a lod score exceeding the single parent threshold, it is considered that the offspring has one parent among the genotyped potential parents.

The decision made after the test is compared to the true situation, and the number of correct assignement is recorded.
The percentages of correct father choice or single parent choice and correct parent pair choice are given.
The number of paternity correctly assigned is given. It is the number of genotyped fathers assigned to offspring and being truly their father. This number is compared to the total number of times genotyped fathers have been assigned to simulated offspring according to the test, as a percentage.
According to the total number of gametes produced during the simulation, the program gives the following gene flow counts:

- cryptic gene flow = beta or type II error, assign a father when the true father is outside
- alpha or type I error, assign no father when the true father is inside
- Apparent gene flow ('gfo', true) when offspring are generated with random parents:
- Apparent gene flow ('gfi', untrue) when offspring are generated with genotyped parents:
- The true gene flow ('tgf') and the gene flow observed in the parentage experiment ('ogf') are connected
	ogf = tgf*gfo + (1-tgf)*gfi = real gene flow + alpha errors
	tgf is calculated thanks to this expression
- Cryptic gene flow ('cgf' or beta) is deduced:  cgf = tgf*(1-gfo) 
- Alpha is deduced:  alpha = (1-tgf)gfi 

*** TwoGener analysis ***
____________________________________________________________
This set of programs is due to Frederic Austerlitz:

The TwoGener analysis (Smouse et al. 2001) can be used on FaMoz paternity analysis data. It requires spatial coordinates of the adults expressed in meters. Missing data are allowed in the genotypes of offspring but not in the genotypes of parents.
To load the program, you must first open your paternity analysis file with "Load entry file" option of the "File" menu 
and then open a coordinates file with the "Load coordinates file" option of the "TwoGener" menu. 
The coordinates file must contain all adult individuals (mothers and fathers) spatial locations in the following format:

number_of_parents

number_of_parent1 x_parent1 y_parent1
[...]
number_of_last_parent x_last_parent y_last_parent

First make the file using the "Make file" option. In the "data" folder of the software two example files are provided 
"genot_twog" for the genotypic file and "coord_twog" for the coordinate file. The file created for TwoGener is called "data_twog".

The density that you have to enter is the total number of adult individuals (genotyped or not) per squared meters in your population.

The TwoGener analysis is then loaded using one of the six possible analyses proposed in the "TwoGener" menu.

All provide the two following quantities:
- Global phi.ft value as computed in Smouse et al. (2001).
- Average distance between the sampled mothers.

Then the analysis will be performed under the chosen dispersal model: 

normal, exponential (Austerlitz and Smouse 2001), exponential power (Dick et al. 2003), Weibull, Geometric or 2Dt (Austerlitz et al. 2004):

1)  Normal model (the numbers correspond to the equations given in Austerlitz and Smouse (2002))
- Global without correction (sigma.g1, eq. 4). The estimates of the dispersal parameter (sigma) of the normal distribution, using the global phi.ft value, without correction for the average distance between mothers, and the corresponding average distance of pollen dispersal (delta).
- Global (sigma.g2 eq. 6). Same estimates but taking this average distance of pollen dispersal into account.
- Fitted #1, 2, 3: the pairwise estimates sigma.p1, sigma.p2 and sigma.p3 obtained respectively with eqs (7) and  (9), and the minimization of the squared error criterion Q(sigma) given in eq. (11). These estimates assume that density is set at its observed value. For the last one, the "error" is the value of Q(sigma) when sigma = sigma.p3. 
- Joint estimate: the joint estimate (d1, sigma.d1) of the adult density (d) and dispersal parameter (sigma) obtained by minimizing Q(sigma) simultaneously for d and sigma.

2) Exponential model:
- Global without correction and global: same as the normal model except that the dispersal parameter gamma of the exponential distribution (Austerlitz and Smouse 2001) is given.
- fitted exponential (fixed density): same as "fitted #3" of the normal model.
- joint estimate exponential: same as "joint estimate" of the exponential model.

3) Exponential power, Weibull, Geometric or 2Dt models:
This performs the pairwise estimates explained in Dick et al. (2003) and in Austerlitz et al. (2004) under these models (see eq. 1), again minimizing the squared error criterion. 
- fitted xxx (fixed density): The dispersal parameters, i.e. the scale parameter (a) and the shape parameter (b), are estimated while the density is fixed at its measured value.
- fitted xxx (fixed b): The parameter b is set at the previously obtained value and density (d) and scale parameter (a).
- joint xxx: all three parameters (d, a and b) are jointly estimated. This analysis requires a lot of data and has not worked properly in most of the cases that we have tried yet (see Austerlitz et al., 2004).

Where xxx will be respectively exponential power, Weibull, Geometric or 2Dt.

BE CAREFULL: the analyses can be long. You have to leave the software running, till the "TwoGener in progress" window has disappeared. The results are then displayed in the main window.



__________________________________________

REFERENCES
___________________________________________
Austerlitz F., Smouse P.E. 2001 Two-generation analysis of pollen flow across a landscape. II. Relation between Fft, pollen dispersal and inter-females distance. Genetics 157: 851-857.

Austerlitz F., Smouse P.E. 2002 Two-generation analysis of pollen flow across a landscape. IV. Estimating the dispersal parameter. Genetics 161: 355-363.

Austerlitz, F., Dick, C.W., Dutech, C., Klein, E.K., Oddou-Muratorio, S., Smouse, P.E., Sork, V.L. 2004 Using genetic markers to estimate the pollen dispersal curve. Molecular Ecology 13: 937-954.

Dick C.W., Etchelecu G., Austerlitz F. 2003 Pollen dispersal of tropical trees (Dinizia excelsa: Fabaceae) by native insects and African honeybees in pristine and fragmented Amazonian rainforest. Molecular Ecology 12: 753-764.

Gerber S., Streiff R., Bodenes C., Mariette S., Kremer, A. 2000 Comparison of microsatellites and AFLP markers for parentage analysis. Molecular Ecology 9: 1037-1048.

Gerber S., Chabrier P., Kremer A. 2003. FaMoz: a software for parentage analysis using dominant, codominant and uniparentally inherited markers. Molecular Ecology Notes 3: 479-481.

Jamieson A., Taylor S.S. 1997 Comparisons of three probability formulae for parentage exclusion. Animal Genetics 28: 397-400.

Smouse PE, Dyer RJ, Westfall RD, Sork VL (2001) Two-generation analysis of pollen flow across a landscape. I. Male gamete heterogeneity among females. Evolution, 55, 260-271.

Waits,L.P., Luikart,G. Taberlet,P. 2001 Estimating the probability of identity among genotypes in natural populations: cautions and guidelines Mol Ecol 10(1): 249-256

__________________________________________

ACKNOWLEDMENT
__________________________________________

We would like to thank for their very usefull help at different step of the evolution of FaMoz:

Georges Koepfler
Francois Lefevre
Frederic Austerlitz
Nikolaos Koutsias and Aikaterini Dounavi
Olivier Hardy
Cecile Bacles
Concetta Burgarella 

