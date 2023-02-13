# hse23_hw1

### 1. Анализ QC чтений

![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_base_seq_content.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_base_seq_content2.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_seq_gc_content.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/per_seq_gc_content2.png)

Первое, что можем заметить, что содержание парных оснований не одинаковое: на первом графике содержание цитозина около 10%, а гуанина примерно в два раза больше; содержание тимина и аденина тоже отличается. В молекуле ДНК процент должен быть одинаковым.

Помимо этого, можем видеть, что на графике GC content теоретическое распределение нормальное, а в реальном есть два пика.

| Образец | Число ридов на 11347700-11367700 | Число ридов на 40185800-40195800 | Процент дуплицирований |
|:----------:|:----:|:---:|:------:|
| SRR5836473 | 1090 | 464 | 81.69% |
| SRR5836475 | 1456 | 630 | 90.92% |
| SRR3824222 | 2328 | 1062 | 97.08% |


![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/SRR3824222_mbiasplot.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/SRR5836473_mbiasplot.png)
![](https://github.com/KirillMatirko/hse23_hw1/blob/main/pics/SRR5836475_mbiasplot.png)
