# Face Autoencoder

## Dataset  
Для реализации проекта был использован данные "Labeled Faces in the Wild" http://vis-www.cs.umass.edu/lfw/

## Задачи 
- Обучить encoder извлекать из картинок хорошее латентное представление для дальнейшей генерации лиц людей из случаных векторов.
- Изменить атрибуты картинки (добавить улыбку грустному человеку, добавить очки и т.д.)

## Описание
Обе реализации (1024.ipynb, 1024_BCE.ipynb) имеют размерность вектора латентного представления 1024, что позволяет приблизительно в 50 раз сжать изображение.

Основными различиями в реализации являются функция потерь(1024.ipynb-MSE, 1024_BCE.ipynb-BCE), а также в выходном слое Encoder и Decoder(1024.ipynb-ReLu, 1024_BCE.ipynb-Sigmoid).

Для реализации задачи №2 необходимо взять два небольших набора изображений отличающихся на интересующий нас атрибут, получить их усредненные латентные представления, вычесть друг из друга(это и будет представление атрибута), а затем добавить этот вектор к интересующему нас изображению.

## Результат
- Реализация 1024.ipynb показывает хорошие результаты в задаче №2(изменить атрибуты картинки), но совсем плохие в задаче №2(плохо генерируются лица людей из случайнх векторов). Предположительно это связано с тем, что генерируемый вектор имеет координаты [0, 1], в то время как Encoder из-за функции активации Relu не гарантирует нам таких координат.
- Реализация 1024_BCE.ipynb показывает значительно лучшие результаты в задаче №1 (Sigmoid гарантирует координаты значения координат вектора в интервале [0, 1]), а также неплохие результаты в задаче №2.

### Результаты задачи №1
6 сгенерированных лиц из случайных векторов:
![Результаты задачи №1](https://github.com/artitre/FaceAutoencoder/blob/master/Image/Test_1.PNG)

### Результаты задачи №2
Первое изображение - исходное изображение.

Второе изображение - изображение на выходе autoencoder-a.

Третье изображение - результат. 

![Результаты задачи №2](https://github.com/artitre/FaceAutoencoder/blob/master/Image/Test_2.PNG)
