# glmnetError
data for debugging glmnet() in R
  
the error occurs when running the following code at i == 10:

```R
library(glmnet)

for(i in 1:dim(block_morpho)[1]){
  
  print(i)
  
  temp_morpho <- block_morpho[-i,]
  temp_enviro <- block_enviro[-i,]
  
  print(i)
  
  # initialize the list of models and results if i == 1, otherwise append
  if(i == 1){
    elastic_net_models <- list(glmnet(temp_enviro, temp_morpho, family = "mgaussian", relax = TRUE, gamma = c(0.5)))
    } else {
    elastic_net_models <- list(elastic_net_models, list(glmnet(temp_enviro, temp_morpho, family = "mgaussian", relax = TRUE, gamma = c(0.5))))
  }
}
```

this is the error I recieve:

```
Error in matrix(fit$a0[seq(lmu * nc)], nc, lmu, dimnames = list(classnames,  : 
  length of 'dimnames' [2] not equal to array extent
```
