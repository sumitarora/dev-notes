m.
 <- matrix(sample(1:15, 12), nrow = 3)
m[1,3] = 1st row 3rd colmn
m[1,] 1st rom
m[,2] 2nd column
m[4] column wise
m[2, c(2,3)]

result is vector
colSums
rowSums

matrix / 1.12 all math functions

# Print the first observations of mtcars
head(mtcars)

# Print the last observations of mtcars
tail(mtcars)

# Print the dimensions of mtcars
dim(mtcars)

mfrow with par

par(mfrow = c(2,2))
par(mfcol = c(2,2))

par(mfcol = c(1,1)) to reset
layout(1) to reset

old <- par()
par(old_par)

lm_sales <- lm(x$y, a$b)
abline(coef(lm_sales), lwd = 2)
point
segments
lines
text

ranks <- order(x$y)

plot(x$y, a$b)

plot(
    movies$votes,
    movies$runtime,
    main = 'Votes versus Runtime',
    xlab = 'Number of votes [-]',
    ylab = 'Runtime [s]',
    sub = 'No clear correlation'
)

hist(
    movies$runtime,
    breaks = 20,
    main = 'Distribution of Runtime',
    xlab = 'Runtime [-]',
    col = 'cyan',
    border = 'red',
    xlim = c(90, 220)
)

plot(movies$votes, movies$runtime,
     main = "Votes versus Runtime",
     xlab = "Number of votes [-]",
     ylab = "Runtime [s]",
     sub = "No clear correlation",
     col = '#dd2d2d',
     col.main = 604
     pch = 9
    )

create plots with code
reporducable
replocation and modification
graphics package
ggplot2, ggvis, lattice

plot
- generic
- different inputs - different plots
- vectors linear models kernel etc.

plot(x$y)
plot(x$y, a$b)
plot(log(x$y), log(a$b))

hist
- histogram
- visual distribution
- bin all values

hist(x$y, breaks = 10)
barplot
boxplot
pairs


xlab - x label
ylab - y label
main - title
type - o/l
col - color

par
par(col = 'blue') // session wise
par()$blue

col.main - title color
ces.axis - tick font size
lty - line types  1 to 6
pch - pont symbot 1 to 35

---------------------------------------------------
song <- list('asda', 13, 23)
names(song) <- c('a','asd','asdas')

str(song)

song <- list(a='asdsa', b=10, c=12)
store list insides also

song[[1]]
single [] return list
double [] gives correct value

song[c(1, 3)] will not work with double if index is more
select 3rd elemet from 1st row

song[[c(1, 3)]] will not work with double

subset by name
subset by logicals only for rows

# shining_list is already defined in the workspace

# Add both the year and director to shining_list: shining_list_ext
shining_list_ext <- c(shining_list, year = 1980, director = "Stanley Kubrick")
shining_list_ext <- c(shining_list, list(year = 1980, director = "Stanley Kubrick"))  # also works

# Have a look at the structure of shining_list_ext
str(shining_list_ext)

song$duration

song$add <- /...
song[['sent']] <-


---------------------------------------------------

class(TRUE)
TRUE / FALSE - logical
NA - logical

numeric - 2, 2.5
mathemetical operatins
integers 2L

is.numeric()
is.integer()

character string
double
complex
raw

as.numeric(TRUE)

as.character("4")
as.integer("4.5") = 4
as.integer("4.sa5") = NA
--------------------------------------------------------------------------------

values <- c(1, 2, 3)
names <- c('a', 'b', 'c')

names(values) <- names

vals <- c(a = 10, b= 11, c = 12)
vals <- c("a" = 10, "b"= 11, "c" = 12)
str(vals)

length(vals) = 3

can hold value of same type
atomic vectors <> lists

class(c) = vector
is.vector(c)

--------------------------------------------------------------------------------

computations are element wise
math operations elementwise
sum()

--------------------------------------------------------------------------------
vals <- c(a = 10, b= 11, c = 12)
vals[1]
vals[-1]
vals['b']
vals[c(1,2)]
vals[-c(1,2)]
vals[c('a','b')]
vals[c(F,T,F)]

- does not work with names

# Mid-week poker results: poker_midweek
poker_midweek <- poker_vector[c(2,3,4)]

# End-of-week roulette results: roulette_endweek
roulette_endweek <- roulette_vector[c(4,5)]






gender <- c('M', 'F', 'O')
gender_factor <- factor(gender)

gender_factor <- factor(gender, levels = c('M', 'F', 'O'))

lebels(gender_factor) <- c('M', 'F', 'O'))

gender_factor <- factor(gender, levels <- c, labels <- )

nominal eg. gender
ordinal eg. size of shoe

we can creare ordered factor using ordered = TRUE


char values -? integer
str(gender_factor)

auto infers



# Defintion of survey_vector and survey_factor
survey_vector <- c("R", "L", "L", "R", "R")
survey_factor <- factor(survey_vector, levels = c("R", "L"), labels = c("Right", "Left"))

# Summarize survey_vector
summary(survey_vector)

# Summarize survey_factor
summary(survey_factor)


# Create speed_vector
speed_vector <- c("OK", "Slow", "Slow", "OK", "Fast")

# Convert speed_vector to ordered speed_factor
speed_factor <- factor(speed_vector, ordered = TRUE, levels = c('Slow', 'OK', 'Fast')


# Print speed_factor
speed_factor

# Summarize speed_factor
summary(speed_factor)


# Definition of speed_vector and speed_factor
speed_vector <- c("Fast", "Slow", "Slow", "Fast", "Ultra-fast")
factor_speed_vector <- factor(speed_vector, ordered = TRUE, levels = c("Slow", "Fast", "Ultra-fast"))

# Compare DA2 with DA5: compare_them
compare_them <- factor_speed_vector[2] > factor_speed_vector[5]

# Print compare_them: Is DA2 faster than DA5?
compare_them


fly_class_factor <- factor(fly_class, ordered = TRUE, levels = c('economy', 'business', 'first'))

fly_class_factor <- factor(fly_class, ordered = TRUE, levels = c('eco', 'bus', 'fir'), labels = c('economy', 'business', 'first'))
