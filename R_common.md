# R in daily
## library management

## input and output


### Rdata v.s. rds
.rds和.Rdata （也称为.rda ）文件都可用于以R本机格式存储R对象。与非本机存储方法（例如write.table相比，保存此方法有多个优点：
1)将数据恢复到R更快
2)它保持在数据中编码的R特定信息（例如，属性，变量类型等）

- rds function:
```
saveRDS()
readRDS()

saveRDS(object = iris, file = "my_data_frame.rds")
iris2 <- readRDS(file = "my_data_frame.rds") # can try to rename it when you load again

```
 Notes: for sigle R object
 
 
- Rdata function:
```
save()
load()

save(iris, file = "myIrisAndCarsData.Rdata")
load("myIrisAndCarsData.Rdata") # just get the same name as previous

save(iris, cars, file = "myIrisAndCarsData.Rdata")
load("myIrisAndCarsData.Rdata")
```
Notes: for single or multiple objects


## 


# R in bio
