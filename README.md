# hijab_nonhijab
классификация изображений: в женщины хиджабе / нет

Необходимо распознать наличие женщины в хиджабе на картинке.
Датасет в свободном доступе расположен по ссылке github: https://github.com/najcardboyz/naja-dataset/

## Требования

Для запуска предсказаний модели необходимо:

- Проект hijab_nonhijab_project, состоящий из:

    ~ Запускаемого файла с расширением .ipynb, main.ipynb
    содержащим предварительную обработку данных и непосредственно код построения модели на базе предобученной.
    ~ Вспомогательного пакета custom_import_from_directory, содержащего _init_.py, 
    благодаря которому достигается возможность использовать все указанные в датасетах директории, 
    избегая некоторые методы tensorflow, не позволяющие работать с данными при отсутсвии конкретной структуры директорий.
    ~ Файл с необходимыми библиотеками requirements.txt.
 

## Решение

Для наших получения необходимого результата был использован метод трансферного обучения на основе предобученной модели MobileNet V2 из руководства tensorflow.org: https://www.tensorflow.org/tutorials/images/transfer_learning

Однако некоторые методы предобработки данных, такие как image_dataset_from_directory, не предусматривают различные возможные структуры директорий. 
Поэтому они были заменены кодом, который собирает все изображения по директориям, присваивая им метки класса, и уже затем собирает zip данные в датасет, который затем разделяет на тестовый и тренировочный наборы.

Используем классическую метрику accuracy. 
Она самая простая и удобная для задач классификации и позволяет узнать долю правильных ответов алгоритма.


