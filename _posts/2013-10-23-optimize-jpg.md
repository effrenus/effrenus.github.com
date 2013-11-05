---
layout: post
title: Оптимизация графических файлов (JPEG) на основе PSNR
tags: ["jpeg", "optimization", "web", "psnr", "bash"]
page_type: "post"
---
В одном из видео докладчик предложил идею, как автоматически сжимать jpeg файлы с возможностью программно оценивать результат. Для этого в качестве метрики предложил [PSNR](http://ru.wikipedia.org/wiki/%CF%E8%EA%EE%E2%EE%E5_%EE%F2%ED%EE%F8%E5%ED%E8%E5_%F1%E8%E3%ED%E0%EB%E0_%EA_%F8%F3%EC%F3) (Peak-Signal-to-Noise-Ratio).

В результате я написал небольшой bash скрипт. Он ищет в текущей директории все jpg файлы и начиная с самого низкого качества (например, 60) сохраняет их во временную папку, для полученных
изображений вычисляем PSNR, который сравниваем с пороговым значением (взял 39, тогда у сжатой получается немного артефактов).
Если вычисленное значение больше порогового, а размер файла меньше оригинального - копируем файл в текущую директорию (заменяем исходник).

{% gist 7114591 %}

#### Результаты работы

Взял картинки из результатов поиска и пропустил через скрипт

<div class="compare">
	<img src="/media/psnr_test/1_orig.jpg">
	<img src="/media/psnr_test/1.jpg">
</div>

Quality: 85 Result: filesize 80871 => 58887

<div class="compare">
	<img src="/media/psnr_test/2_orig.jpg">
	<img src="/media/psnr_test/2.jpg">
</div>

Quality: 69 Result: filesize 62633 => 28827

<div class="compare">
	<img src="/media/psnr_test/3_orig.jpg">
	<img src="/media/psnr_test/3.jpg">
</div>

Quality: 86 Result: filesize 37174 => 34110