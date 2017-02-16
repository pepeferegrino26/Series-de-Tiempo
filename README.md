# Series-de-Tiempo
rm(list = ls()) #listado de objetos con los que estamos trabajando 
library(foreign)
library(readxl)
petroleo<- read_excel("/Users/pepeferegrino/Documents/seriesdata/15feb17/petroleo.xlsx")
petroleo.ts<-ts(petroleo)
plot(petroleo.ts,xlab="ejex",ylab="ejey", main="Precios del petroleo", col=3)
?decompose
petroleo.ts=ts(petroleo,frequency = 5)

petroleo.descon<- decompose(petroleo.ts,"additive")
#GRaficas
plot(as.ts(petroleo.descon$seasonal))
plot(as.ts(petroleo.descon$trend))
plot(as.ts(petroleo.descon$random))
plot(petroleo.descon)
##Otra manera de graficar 
?windows
#windows()
#window(petroleo.ts)
#par(mfrow=c(3,1))
#plot(as.ts(petroleo.descon$seasonal))
#plot(as.ts(petroleo.descon$trend))
#plot(as.ts(petroleo.descon$random))
#plot(diff(petroleo.descon))

##########OTRO EJEMPLO!!!!!!!!!!!

gdpmexico<-read_excel("/Users/pepeferegrino/Documents/seriesdata/15feb17/gdpmexico.xlsx")
gdpmexico.ts<-ts(gdpmexico)
plot(gdpmexico.ts,xlab="ejex",ylab="ejey", main="GDP MEXICO",col=3)
gdpmexico.ts=ts(gdpmexico, frequency=5)
gdpmexico.descom<-decompose(gdpmexico.ts,"additive")
plot(as.ts(gdpmexico.descom$seasonal))
plot(as.ts(gdpmexico.descom$trend))
plot(as.ts(gdpmexico.descom$random))
plot(gdpmexico.descom)

#########OTRO EJEMPLO!!!!!!!!!
ruralmex<- read_excel("/Users/pepeferegrino/Documents/seriesdata/15feb17/ruralmexico.xlsx")
