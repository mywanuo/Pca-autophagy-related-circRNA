# Autophagy-related circRNA evaluation reveals hsa_circ_0001747 as a potential favorable prognostic factor for biochemical recurrence in patients with prostate cancer

Paper under review

### Correlation  calculation 
The result:
[Correlation result of autophagy-related circRNA in prostate cancer.txt](https://github.com/mywanuo/Pca-autophagy-related-circRNA/blob/main/Correlation%20result%20of%20autophagy-related%20circRNA%20in%20prostate%20cancer.txt)

R code

```
pvalueFilter=0.05 
# P-value Filter
corFilter=0.30 
# Correlation filter
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
dim(outTab)
```

