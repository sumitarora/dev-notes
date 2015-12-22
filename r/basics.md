matrix(1:6, nrow = 2)
1 3 5
2 4 6

matrix(1:6, ncol = 3)
1 3 5
2 4 6

matrix(1:6, ncol = 3,  byrow = True)
1 2 3
4 5 6


matrix(1:2, nrow = 2, ncol = 3)
1 3 2
2 1 3

cbind(1:3, 1:3)
1 1
2 2
3 3

rbind(1:3, 1:3)
1 2 3
1 2 3


rbind(m, 7:9)
cbind(m, 7:9)

rownames(m) <- c('a', 'b', 'c')
colnames(m) <- c('a', 'b', 'c')

dimname = list(c('a', 'b'), c('1', '2', '3'))

can contain same name matrices only

rownames(scores) <- c("row1","row2","row3","row4")
colname(scores) <- c("c1","c2","c3","c4","c5","c6","total")

m[1, 3]
m[3,]
m[,3]

m[2, c(2,3)]
