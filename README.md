# Visualisation-probability-ggplot2

# Create Probability Function
par(bg = '#191661', fg = '#ffffff', col.main = '#ffffff', col.lab = '#ffffff', col.axis = '#ffffff')
muCalculation <- function(lambda, powers) {1 - ((1 - lambda)^powers)}
probability_at_lambda <- sapply(c(0.02, 0.04, 0.06), muCalculation, seq(0, 100, 10))
probability_at_lambdadf=data.frame(probability_at_lambda)
col_headings <- c("probability1","probability2","probability3")
names(probability_at_lambdadf) <- col_headings
probability_at_lambdadf
attach(probability_at_lambdadf)

#Plot Probability Functions with ggplot2
plot(probability_at_lambdadf$probability1,type="o",col="#b1aef4", xlab="N", ylab="Probability", xlim=c(0, 10), ylim=c(0.0, 1.0), pch=19)
lines(probability_at_lambdadf$probability2,type="o",col="red", xlab="N", ylab="Probability2", xlim=c(0, 10), ylim=c(0.0, 1.0), pch=19)
lines(probability_at_lambdadf$probability3,type="o",col="green", xlab="N", ylab="Probability3", xlim=c(0, 10), ylim=c(0.0, 1.0), pch=19)
title(main="Probability Chart")
grid(nx = NULL, ny = NULL, col = "lightgray", lty = "dotted",
     lwd = par("lwd"), equilogs = TRUE)
legend("bottomright", probability[2], c("probability_at_lambda_1","probability_at_lambda_2", "probability_at_lambda_3"), cex=0.6, col=c("#b1aef4","red","green"), pch=21:22, lty=1:2)
