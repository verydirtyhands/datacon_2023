# Резистентность к антибиотикам и терапия металлическими наночастицами

## Описание задачи

Резистентность к антибиотикам — серьезная проблема современной медицины. Заболевания, которые вызваны резистентными бактериями, с трудом поддаются лечению, а иногда и вовсе не лечатся. Для борьбы с такими бактериями биологи и медики постоянно ищут новые подходы, и один из вариантов — терапия металлическими наночастицами. Металлические наночастицы могут как воздействовать на бактерии самостоятельно (повреждая мембраны бактерий и генерируя радикальные частицы), так и усиливать эффект антибиотиков.

Задание состоит в построении предсказательной модели регрессии для прогнозирования ZOI - зоны игибирования роста бактерий - для комплексов лекарство-наночастицы.

## Инструменты:

`Python==3.9.16`
`Pandas==1.5.3`
`sklearn==1.2.2`
`seaborn==0.12.2`
`matplotlib==3.6.3`
`rdkit==2023.3.2`
`keras==2.12`
`numpy==1.23.5`
`Shap==0.42.0`
`CatBoost==1.2`
`ydata-profiling==4.1.2`

## Описание данных:

### место хранения:

- data.csv — основной набор данных (оценивает эффект наночастиц серебра (Ag) на бактерии)
- bacterial_descriptors.csv — дополнительная информация о бактериях
- drug_descriptors.csv — дополнительная информация о лекарстве

### описание признаков:

#### data.csv
Для всех образцов в датасете использовались наночастицы серебра Ag
- Bacteria - бактериальная клетка-мишень
- NP_Synthesis - тип синтеза наночастиц
- drug - название лекарства
- drug class - класс лекарства
- Drug dose - доза препарата
- NP_concentration - концентрация НЧ
- NP_size - размер НЧ
- shape - форма НЧ
- method - метод определения антимикробной активности
- ZOI_drug, ZOI_NP, ZOI_drug_NP - зона ингибирования препарата, НЧ и их комбинации
- Fold increase in antibacterial activity (%) - кратное увеличение антибактериальной активности (%)
- MDR - множественная лекарственная устойчивость резистентен ли обычный препарат к целевому патогену

#### bacterial_descriptors.csv
- Tax_id - id бактерии в базе данных NCBI
- Bacteria - название бактерии
- kingdom - царство бактерии
- subkingdom - подцарство бактерии
- clade - характеристика бактерии с точки зрения родственных взаимоотношений между таксономическими группами
- phylum - филум бактерии
- class - класс бактерии
- order - порядок бактерии
- family - семейство бактерии
- genus - род бактерии
- species - вид бактерии
- gram - результат реакции окрашивания по Грамму для бактерии
- min_Incub_period, avg_Incub_period, max_Incub_period h - характеристики инкубационного периода бактерии
- growth_temp, C - температура роста бактерии
- biosafety_level - уровень опасности бактерии
- isolated_from - источник

#### drug_descriptors.csv
- drug - название лекарства
- chemID - id лекарства в базе данных CHEMBL
- prefered_name - название лекарства
- smiles - химическая формула лекарства

## Краткое описание проведённой работы:
<i> 
Проанализированы данные: технические характеристики ,цены и время регистрации автомобилей. Построены модели на основе Catboost ,TweedieRegressor ,Keras для определения стоимости автомобиля с пробегом.Также все модели кроме TweedieRegressor были интерпретированы при помощи shap </i>

## Выводы
<i>На данный момент модель на основе градиентного бустинга показалась оптимальной: предсказания происходят очень быстро, а время обучения остается адекватным при самой высокой точности. Модель на основе линейной регрессии оказалась самой быстрой, но при этом с самой большой ошибкой. Модель на основе многослойной нейронной сети прямого распространения не обладает необходимой скоростью и имеет точность ниже Catboost (потенциально точность предсказаний можно было бы улучшить, однако из-за времени обучения эксперименты были прекращены).

Таким образом, для компании "Не бит, не крашен" мы можем смело рекомендовать использование модели CatBoostRegressor. Эта модель обладает оптимальной скоростью обучения и качеством предсказаний</i>

## Рекомендации
<i>Предлагается создать базу данных с информацией о автомобилях, чтобы более эффективно обнаруживать и обрабатывать выбросы. Также данное действие поможет осуществлять более компетентный инженеринг признаков.
</i>

 ---
 
#### Если проект не открывается или вы хотите посмотреть со всеми интерактивными ячейками(ydata-profiling), его можно открыть по ссылке: <a href='https://nbviewer.org/github/verydirtyhands/the_cost_of_cars/blob/main/p10f.ipynb'>Модель для определение стоимости автомобилей
</a>

