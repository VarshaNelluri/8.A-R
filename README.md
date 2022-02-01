# 8.A-R
# Goodness of fit for ND  
x<-c(1,3,5,7,9)
y<-c(3,5,7,9,11)
f<-c(1,4,6,4,1)
xi<-(x+y)/2
fx<-f*xi
fxx<-f*xi*xi
sumfx<-sum(f*xi)
print(sumfx)
sumfxx<-sum(f*xi*xi)
sumf<-sum(f)
print(sumf)
m<-sumfx/sumf
print(m)
sd<-(sumfxx/sumf)-(m*m)
sd<-sqrt(sd)
print(sd)
u<-pnorm(y,m,sd)
l<-pnorm(x,m,sd)
pr<-u-l
u<-round(u,digits=5)
l<-round(l,digits=5)
pr<-round(pr,digits=5)
fee<-(pr*sumf)
fe<-round(fee,digits=0)
mydata<- data.frame(x,y,xi,f,fx,fxx,u,l,pr,fee,fe)
print(mydata)
sums<-list(NA,NA,NA,sum(f),sum(f*xi),sum(f*xi*xi),NA,NA,NA,NA,sum(fe))
mydata<-rbind(mydata,sums)
print(mydata,row.names=FALSE)
result<-chisq.test(f,p=pr,rescale.p=TRUE)
print(result)
OUTPUT:
 # Goodness of fit for ND  
> x<-c(1,3,5,7,9)
> y<-c(3,5,7,9,11)
> f<-c(1,4,6,4,1)
> xi<-(x+y)/2
> fx<-f*xi
> fxx<-f*xi*xi
> sumfx<-sum(f*xi)
> print(sumfx)
[1] 96
> sumfxx<-sum(f*xi*xi)
> sumf<-sum(f)
> print(sumf)
[1] 16
> m<-sumfx/sumf
> print(m)
[1] 6
> sd<-(sumfxx/sumf)-(m*m)
> sd<-sqrt(sd)
> print(sd)
[1] 2
> u<-pnorm(y,m,sd)
> l<-pnorm(x,m,sd)
> pr<-u-l
> u<-round(u,digits=5)
> l<-round(l,digits=5)
> pr<-round(pr,digits=5)
> fee<-(pr*sumf)
> fe<-round(fee,digits=0)
> mydata<- data.frame(x,y,xi,f,fx,fxx,u,l,pr,fee,fe)
> print(mydata)
  x  y xi f fx fxx       u       l      pr     fee fe
1 1  3  2 1  2   4 0.06681 0.00621 0.06060 0.96960  1
2 3  5  4 4 16  64 0.30854 0.06681 0.24173 3.86768  4
3 5  7  6 6 36 216 0.69146 0.30854 0.38292 6.12672  6
4 7  9  8 4 32 256 0.93319 0.69146 0.24173 3.86768  4
5 9 11 10 1 10 100 0.99379 0.93319 0.06060 0.96960  1
> sums<-list(NA,NA,NA,sum(f),sum(f*xi),sum(f*xi*xi),NA,NA,NA,NA,sum(fe))
> mydata<-rbind(mydata,sums)
> print(mydata,row.names=FALSE)
  x  y xi  f fx fxx       u       l      pr     fee fe
  1  3  2  1  2   4 0.06681 0.00621 0.06060 0.96960  1
  3  5  4  4 16  64 0.30854 0.06681 0.24173 3.86768  4
  5  7  6  6 36 216 0.69146 0.30854 0.38292 6.12672  6
  7  9  8  4 32 256 0.93319 0.69146 0.24173 3.86768  4
  9 11 10  1 10 100 0.99379 0.93319 0.06060 0.96960  1
 NA NA NA 16 96 640      NA      NA      NA      NA 16
> result<-chisq.test(f,p=pr,rescale.p=TRUE)
Warning message:
In chisq.test(f, p = pr, rescale.p = TRUE) :
  Chi-squared approximation may be incorrect
> print(result)

	Chi-squared test for given probabilities

data:  f
X-squared = 0.010944, df = 4, p-value = 1
