# Autophagy-related circRNA evaluation reveals hsa_circ_0001747 as a potential favorable prognostic factor for biochemical
recurrence in patients with prostate cancer


### Correlation calculation
The result
R code

'''
pvalueFilter=0.05
corFilter=0.30
outTab=data.frame()
for(i in row.names(exp)){
  if(sd(exp[i,])>0.5){
    for(j in row.names(ARGgene)){
      x=as.numeric(exp[i,])
      y=as.numeric(ARGgene[j,])
      corT=cor.test(x,y)
      cor=corT$estimate
      pvalue=corT$p.value
      if((abs(cor)>corFilter) & (pvalue<pvalueFilter)){
        outTab=rbind(outTab,cbind(ARGgene=j,exp=i,cor,pvalue))
      }
    }
  }
}
'''
