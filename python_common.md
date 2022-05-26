# Daily python
## usual python pakages

## input and output
### base
### numpy
### pandas

- get the duplicate rows
```
cellranger_outs_genes_1 = cellranger_outs_genes.drop_duplicates(subset=[1])
cellranger_outs_genes_2 = cellranger_outs_genes.drop_duplicates(subset=[1],keep=False)
cellranger_outs_genes_3 = pd.concat([cellranger_outs_genes_1, cellranger_outs_genes_2]).drop_duplicates(subset=[1],keep=False)
```
### scipy
## sparse matrix

`x * y no longer performs matrix multiplication, but element-wise multiplication (just like with NumPy arrays). To make code work with both arrays and matrices, use x @ y for matrix multiplication.`
https://docs.scipy.org/doc/scipy/reference/sparse.html

## Function based 
### multiprocessing
```
import math
import datetime
import multiprocessing as mp
def train_on_parameter(name, param):
    result = 0
    for num in param:
        result += math.sqrt(num * math.tanh(num) / math.log2(num) / math.log10(num))
    return {name: result}


if __name__ == '__main__':

    start_t = datetime.datetime.now()

    num_cores = int(mp.cpu_count())
    print("本地计算机有: " + str(num_cores) + " 核心")
    pool = mp.Pool(num_cores)
    param_dict = {'task1': list(range(10, 30000000)),
                  'task2': list(range(30000000, 60000000)),
                  'task3': list(range(60000000, 90000000)),
                  'task4': list(range(90000000, 120000000)),
                  'task5': list(range(120000000, 150000000)),
                  'task6': list(range(150000000, 180000000)),
                  'task7': list(range(180000000, 210000000)),
                  'task8': list(range(210000000, 240000000))}
    results = [pool.apply_async(train_on_parameter, args=(name, param)) for name, param in param_dict.items()]
    results = [p.get() for p in results]

    end_t = datetime.datetime.now()
    elapsed_sec = (end_t - start_t).total_seconds()
    print("多进程计算 共消耗: " + "{:.2f}".format(elapsed_sec) + " 秒")

```

### nan value
https://blog.csdn.net/maymay_/article/details/107034221
1. numpy.nan是一个numpy.float64的非空对象，所以不能直接用bool表达式去判断，故一切依赖于布尔表达式的判断方式都不行，比如if语句。
2. 对于pandas中空值的判断，我们只能通过pandas或者numpy的函数和is表达式去判断，不能用python的内置函数any或all判断。


**可以判断pandas中单个空值对象的方式：**
1、利用pd.isnull(),pd.isna();

2、利用np.isnan();

3、利用is表达式；

4、利用in表达式。

**不可以用来判断pandas单个空值对象的方式：**
1、不可直接用==表达式判断；

2、不可直接用bool表达式判断；

3、不可直接用if语句判断。

**对于同时多个空值对象的判断和处理：**
1、可以用Series对象和DataFrame对象的any()或all()方法；

2、可以用numpy的any()或all()方法；

3、不可以直接用python的内置函数any()和all()方法；

4、可以用Series或DataFrame对象的dropna()方法剔除空值；

5、可以用Series或DataFrame对象的fillna()方法填充空值。



# python in bio


# visualization
