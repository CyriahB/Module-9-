# Module-9-
Visualization in R

 #For this assignment, I decided to use the "SmokeBan" dataset from the Vincent Arel Bundock dataset list. The first visualization I created was a scatterplot between the employee and the amount of years smoked. 
 
 #To start this process, subset "afam" was created to represent the African American population of smokers:
> afam <- subset(SmokeBan,smoker=="yes" &  afam=="yes",select=c(gender,ban,age))

#Next, the column "years_smoked" was added the subset:
> afam$years_smoked<-sample(1:25, size = 187, replace = T)

#Here is where the scatterplot between age and years_smoked is created. Gender is used as a factor:
ScatterPlot <- ggplot(afam, aes(x = age, y = years_smoked, color = factor(gender)))+ 
+   geom_point(size=3)
> ScatterPlot


#The second visualization created was a box plot between the age and gender of employees that smoked.
#again, another subset was created: 
> smkn_emp <- subset(SmokeBan,smoker=="yes" &  afam=="yes",select=c(gender,age))

#Box plot comparing the age and gender for smoking employees:
> plot=ggplot(data=smkn_emp, mapping=aes(x=gender, y=age))+geom_boxplot()
> plot


#The third visualization was a histogram for age and non-smoking employees.
#A subset for nonsmoking employees was created:
> non_smokers <- subset(SmokeBan,smoker=="no" ,select=c(age))

#The creation of the histogram:
hist(non_smokers$age, col = 'purple', main = "Non-Smokers' Age Histogram", xlab = "Age")



