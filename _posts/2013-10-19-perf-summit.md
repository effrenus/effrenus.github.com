---
layout: post
title: Встреча оптимизаторов
video_url: //www.youtube.com/embed/IyVh74_SPCI
video_host: youtube
---

### Выступление Джефа Арчибальда (Jaff Archibald), Google relation team
Прошло в форме интерактивного опроса на знание работы браузеров: парсинг документов, исполнение джаваскрипт.
Участники отвечали применительно к Chrome, Safari, Firefox, IE (Opera не было).

Вопросы:

*	Какие браузеры загрузят картинку, если в коде напишем `<image src="image.png">`
	Ответ: все, страховка на случай, когда разработчик неверно пишет тег `img`, пошло с древних времен
*	А в этом случае `<image src="image.png" style="display:none">`?
	Все, т.к. при парсинге не применяются стили и картинка отправляется на загрузку
*	`<div style="display:none"><div style="background-image:url(image.png)></div></div>`
	Никто не будет загружать, у родительского элемента `display:none`, он не попадает в Render tree, и для
	дочерних элементов не выполняется style calculation