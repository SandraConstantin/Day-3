Load the biofam data set that comes with the TraMineR library
library(TraMineR)
data(biofam)

Create a weighted state sequence object named biofam.seq with variables a15 to a30
biofam.lab<-c("parent","left","married","left/married","child","left/child","left/married/child","divorced")
biofam.shortlab<-c("P","L","M","LM","C","LC","LMC","D")
biofam.seq<-seqdef(biofam[,15:30],states=biofam.shortlab,labels=biofam.lab,weights=biofam$wp00tbgs)

Create a full sequence index plot sorted from the end for each class of the cohort variable created in assignment 2
seqIplot(biofam.seq)
seqIplot(biofam.seq,sortv="from.end")

Print the frequencies of the first 20 sequences
seqiplot(biofam.seq,tlim=c(1:10),cex.legend=1.3,border=NA)

Create a sequence frequency plot of the 20 most frequent patterns grouped by values of the cohort variable and save it as a `jpeg' file
seqtab(biofam.seq,tlim=1:20)
seqfplot(biofam.seq,border=NA)
How should I save it in a jpeg file?

Compute the transition rate matrix for the biofam data set
round(seqtrate(biofam.seq),digit=4)

What is the transition rate between states `Left/Married' and `Left/Married/Child'?
0.1994

Display the sequence of transversal state distributions by cohort
seqstatd(biofam.seq)

Within each cohort, at what age is the diversity of the transversal state distribution at its highest?
Could you please explain how to do it during the nex lecture?

Display side by side in a same plot area the mean times spent in each of the states and the sequence of modal states
par(mfrow=c1,3)
seqmtplot(biofam.seq,withlegend = FALSE, border = NA)
seqmsplot(biofam.seq,withlegend = FALSE, border = NA)
seqlegend(biofam.seq,fontsize=1.8)