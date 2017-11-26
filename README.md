# Задание к занятию «Рекомендации на основе схожести»
## Подготовка данных:
```
/home/asigachev/mrec/sbin/mrec_prepare --dataset ml-100k/u.data --outdir datasplits --binarize
```

## Модель Popularity
### Обучение
```
/home/asigachev/mrec/sbin/mrec_train --model=popularity -n4 --input_format tsv --train "datasplits/u.data.train.*" --outdir models_pop
```
### Рекомендации
```
/home/asigachev/mrec/sbin/mrec_predict --input_format tsv --test_input_format tsv --train "datasplits/u.data.train.*" --modeldir models_pop --outdir recs_pop
```
### Результат:
```
ItemPop
mrr            0.6139 +/- 0.0040
prec@5         0.3829 +/- 0.0025
prec@10        0.3551 +/- 0.0012
prec@15        0.3257 +/- 0.0014
prec@20        0.3030 +/- 0.0016
```

## Модель kNN
### Обучение
```
/home/asigachev/mrec/sbin/mrec_train --model=knn -n4 --input_format tsv --train "datasplits/u.data.train.*" --outdir models_pop
```
### Рекомендации
```
/home/asigachev/mrec/sbin/mrec_predict --input_format tsv --test_input_format tsv --train "datasplits/u.data.train.*" --modeldir models_pop --outdir recs_knn
```
### Результат:
```
CosineKNNRecommender(k=100)
mrr            0.7397 +/- 0.0037
prec@5         0.5451 +/- 0.0024
prec@10        0.5012 +/- 0.0024
prec@15        0.4687 +/- 0.0018
prec@20        0.4432 +/- 0.0016
```

