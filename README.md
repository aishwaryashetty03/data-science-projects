# bigmart project
train=read.csv("D://Individual projects//BigMart//Train.csv")
test=read.csv("D://Individual projects//BigMart//Test.csv")
dim(train)
dim(test)
test['Item_Outlet_Sales']=0
data=rbind(train,test)
dim(data)

summary(data)

plot(data$Item_Outlet_Sales,type='l')

library(moments)
skewness(data$Item_Outlet_Sales)
kurtosis(data$Item_Outlet_Sales)

View(data)

library(ggplot2)
qplot(factor(data$Outlet_Size),data$Item_Outlet_Sales,data=data,geom="boxplot")


data[data==""]<-NA
#data$Outlet_Size[data$Outlet_Size==""]<-NA
#summary(data$Outlet_Size)

data$Item_Weight[is.na(data$Item_Weight)]<-mean(data$Item_Weight,na.rm=T)
View(data)
summary(data$Item_Fat_Content)
data$Item_Fat_Content[data$Item_Fat_Content=='LF']<-'Low Fat'
data$Item_Fat_Content<-droplevels(data$Item_Fat_Content,'LF')
data$Item_Fat_Content[data$Item_Fat_Content=='low fat']<-'Low Fat'
data$Item_Fat_Content[data$Item_Fat_Content=='reg']<-'Regular'

View(data)


