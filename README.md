# hse23_hw1

### 1. Анализ QC чтений

![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_base_seq_content.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_base_seq_content2.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_seq_gc_content.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_seq_gc_content2.png)

Первое, что можем заметить, что содержание парных оснований не одинаковое: на первом графике содержание цитозина около 10%, а гуанина примерно в два раза больше; содержание тимина и аденина тоже отличается. В молекуле ДНК процент должен быть одинаковым.

Помимо этого, можем видеть, что на графике GC content теоретическое распределение нормальное, а в реальном есть два пика.

### 2. Выравнивание BS-seq ридов

| Образец | Число ридов на 11347700-11367700 | Число ридов на 40185800-40195800 | Процент дуплицирований |
|:----------:|:----:|:---:|:------:|
| SRR5836473 | 1090 | 464 | 81.69% |
| SRR5836475 | 1456 | 630 | 90.92% |
| SRR3824222 | 2328 | 1062 | 97.08% |


### 3. Коллинг метилирования

##### SRR3824222

![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/SRR3824222_mbiasplot.png)

##### SRR5836473

![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/SRR5836473_mbiasplot.png)

##### SRR5836475
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/SRR5836475_mbiasplot.png)

Для каждого образца представлено два графика, потому что это paired-end reads. Каждый график представляет пропорцию метилирования для каждой позиции рида. Мы можем видеть смещение метилирования на втором риде к началу у каждого образца. На первом риде процент практически постоянен.

### 4. Гистограмма распределение метилирования цитозинов

```python
import pandas as pd

df_8_cell = pd.read_csv("s_8_cell.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)
df_icm = pd.read_csv("s_icm.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)
df_epiblast = pd.read_csv("s_epiblast.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)
df_8_cell.head()

import matplotlib.pyplot as plt

plt.hist(df_8_cell[3], bins=100, density=True, stacked=True) #bins = 100(=максимальному проценту), чтобы высота столбика отображала вероятность
plt.xlabel("% метилирования")
plt.ylabel("Частота")
plt.title("8 cell")

plt.hist(df_icm[3], bins=100, density=True, stacked=True)
plt.xlabel("% метилирования")
plt.ylabel("Частота")
plt.title("ICM")

plt.hist(df_epiblast[3], bins=100, density=True, stacked=True)
plt.xlabel("% метилирования")
plt.ylabel("Частота")
plt.title("Epiblast")
```

![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/8cell.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/icm.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/epiblast.png)

Наиболее часто метилирование произошло на образце Epiblast (почти 100% в половине случаев). Наоборот, на образце ICM в 60% случаев метиляция была на уровне 0%. На образце 8cell ситуация несколько другая, хоть метиляция чаще была на уровне 0% (частота примерно 0.45), случалась и полная метиляция (частота примерно 0.25). Для всех трёх графиков можно сделать вывод, что метиляция чаще всего либо не происходит совсем, либо находится на уровне 100%.

### 5. Визуализация уровня метилирования и покрытия

##### Метилирование

![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/methylation.png)

##### Покрытие

![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/coverage.png)
