# road-signs-detection
Road signs detection project for DL in practice course

<div align="left"><img src="https://s5.gifyu.com/images/SRDNW.gif" width="500" /></div>

# Обоснование подбора метрик
В задачах сегментации обычно используются такие метрики оценки, как пересечение с объединением (IoU), коэффициент Dice и точность пикселей. Intersection over Union (IoU) измеряет перекрытие между предсказанной маской сегментации и истинной маской. Он вычисляется как отношение пересечения двух масок к объединению двух масок.
Коэффициент Dice — это метрика, аналогичная IoU, но она более чувствительна к небольшим различиям между предсказанной и истинной масками. Он вычисляется как удвоенное пересечение предсказанной и истинной масок, деленное на сумму количества пикселей в каждой маске. Коэффициент Dice часто предпочтительнее, чем IoU, поскольку он более чувствителен к небольшим вариациям и может лучше отражать общую производительность модели сегментации. Кроме того, он может быть полезен в ситуациях, когда предсказанная маска имеет малое количество пикселей, связанных со значениями в истинной маске. Однако IoU также часто используется, поскольку его интерпретация может быть более интуитивной.

При обучении модели YOLO были выбраны метрики IoU и Mean Average Precision (mAP) с акцентом на кривых точности и полноты. Этот выбор был обусловлен необходимостью комплексной оценки, учитывающей компромисс между точностью и полнотой в различных классах объектов. Путем изучения кривой точности-полноты оценивалась производительность модели при различных порогах уверенности, что позволяло получить тщательное представление о ее способности обнаруживать и правильно классифицировать объекты.

# Выбор гиперпараметров для YOLO
В ходе подбора параметров для обучения, был выбран следующий вариант:
- изображения подавались на вход в разрешении 640 пикселей
- размер батча был установлен равным 16
- количество эпох равное 20

Остальные параметры самой модели, такие как размер сетки, количество и координаты якорей определялись самой моделью в процессе обучения, исходя из тренировочного датасета.

# Возможность масштабирования работы
На данный момент модель способна обрабатывать видео со скоростью примерно в 30 кадров в секунду. Это позволяет рассмотреть варианты масштабирования модели для работы с несколькими камерами. Стоит учесть, что мы все еще не уверены в тонкостях распараллеливания этих процессов, но в теории, модель может быть адаптирована для обработки видеопотоков с 2-3 камер.

Выбор YOLO в качестве основной архитектуры дает нам определенные преимущества, включая ее относительную легкость в вычислительном плане. Это позволяет нам обдумать возможности масштабирования без излишних оптимистических оценок, ориентируясь на текущие ресурсы и требования учебной задачи.


