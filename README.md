ЦЕЛЬ РАБОТЫ

Решение задачи обнаружения плагиата на примере шедевров мировой культуры.

Проблема обнаружения плагиата делится на 2 подзадачи: 
1) Если заранее неизвестно, на какую работу или автора сделан данный ремейк, то было бы хорошо, если бы модель могла по картике угадать, на какого автора сделан этот ремейк. 
Для решения этой задачи мы будем использовать модель трансформера CLIP 
Будем адаптировать модель для решения своей задачи, дообучив модель репродукциями картин для примера 10 самых известных автров, на работы которых чаще всего производят разного вида плагиат. 
2) Второй важной задачей является определение похожести изображений. 
Для решения этой задачи была написана функция, на вход принимающая 2 изображения и, используя препроцессинг и автоэнкодер модели CLIP, 
рассчитывала метрику cosine_similarity из torch.nn.functional, основанную на косинусном расстоянии.
Чем больше полученное значение, тем более релевантными / визуально похожими являются два изображения.

Итого мы хотим получить удобоваримое качество подсказки, на какого автора мы перед собой видим плагиат, пока из 10 классов.
 И хотим понять, на сколько эти картинки похожи исходя из метрики косинусного расстояния.