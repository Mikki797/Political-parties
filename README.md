# Political-parties

Цель данного проекта - исследование методами машинного обучения программы политических партий России.

## Датасеты

**parties.zip** - тексты программ 30 партий РФ, взятые с официальных сайтов партий 

**preprocess_parties.zip** - тексты программ партий после предобработки алгоритмом из файла "Проект LDA.ipynb"

**partia_popala_ili_net2.csv** - тексты партий, со столбцом попадания партии в Госдуму

## Проект LDA.ipynb

В файле программы политических партий исследуются методом кластеризации LDA. Сначала программы партий предобрабатываются, после происходит кластеризация на 2 и на 5 кластеров. Выводятся основные слова каждого кластера, степени принадлежности каждой партии определенному кластеру, список партий принадлежащих каждому кластеру, а также оценки перплексии («коэффициент неопределённости») и когерентности. Также строится облако самых популярных слов кластера и строится интерактивный график результатов кластеризации.

## Проект создание датасетов кластеризация классификация.ipynb

В файле создаются датасеты из программ партий, проводится кластеризация иерархическая и k средних, делаются классификация партий по попаданию в Госдуму с использованием knn, Наивный Баес, Деревьев решений, SVM. По результатам видно, что большинство классификаторов совсем не стараются предсказать правильно партии, которые попали в Госдуму. Они по большей части выводят 0. Это следствие несбалансированности классов. Кроме того, это обьясняет то, что на всех классификаторах получилась примерно одинаковая точность - 0.83 - все они предсказывали по большей части лишь нули.

## Проект2.ipynb

В файле делается то же самое, что и в файле "Проект создание датасетов кластеризация классификация.ipynb", но датасет строится с использованием как 1-грамм так и биграмм

## Проект3.ipynb

В файле делается то же, что в файле Проект2, но в качестве метрики для поиска по сетке используется balanced accuracy

Было опробованы методы машинного обучения: knn, Наивный Баес, Деревья решений, SVM для классификации, попала ли в Госдуму партия. Их гиперпараметры подбирались сначала по точности для 1-грамм и биграмм, а затем по сбалансированной точности для биграмм. Они показали точность и балансированную точность, почти не отличающуюся от случайного выбора преобладающего класса 0.

3 из 4 используемых методов машинного обучения работают, если примеры, попадающие в один класс, находятся рядом. Но кластеризация показала, что партии, попадающие в Госдуму, обычно находятся в разных кластерах, и таким образом не находятся рядом, что обьясняет плохую работу методов машинного обучения в этой задаче. Кластеризация показала близость некоторых партий, которые в целом говорят об одном и том же, например КПРФ и Коммунисты России, но те, хоть и говорят в целом об одном, имеют разные результаты по попаданию в Думу.

Таким образом, попадание партии в Госдуму крайне слабо связано с текстом программы партии.

## Проект Пункты.ipynb

В файле из программ партий, попавших в Госдуму, делается датасет из пунктов в программах партий. Для этого проводится сегментация текстов на предложения с выделением пунктов, морфологический анализ и нормализация, создание датасетов из пунктов(count,tf,tf-idf). Пункты кластеризуются с использованием k-means, иерархической, и из них выделяются кластера, представляющие основные сферы, в которых партии, согласно их программам, собираются проводить политику.
