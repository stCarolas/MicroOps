### Проблематика

Если вы часто и много пользуетесь вимом, 
то наверное почувствовали, 
насколько тяжко бывает тянуться за клавишей Esc.
Лично мне еще далековато тянутся и за Enter, и за Control.

### Как будем решать

Наверное, 
единственная платформа, 
на которой известно как решить любую проблему с клавиатурой, 
это линукс.
Некоторые решают проблему с тем же Esc в виме через кастомный хоткей на уровне настроек вима - 
но это не наш путь, 
мы будем решать проблему глобально -
переписывать геометрию клавиатуры почти на уровне драйвера.

### XKB

В линуксе за обработку нажатий клавиатуры отвечает XKB - 
о нем достаточно немало написано, 
не буду поэтому тут повторяться - 
в конце концов, 
зачем писать то, что написали до тебя. 

Общее описание концепций: (https://wiki.archlinux.org/index.php/X_KeyBoard_extension)

Как настроить свою кастомную раскладку (http://hack.org/mc/writings/xkb.html)

### CapsLock = Control

На клавиатуре есть клавиша, 
достаточно близко расположенная к домашней позиции, 
при это практически не используемая, - CapsLock. 
Кажется, ее можно сделать более полезной - 
переместить к примеру на нее Left Control, 
который кажется таким далеким и таким используемым.
Для этого уже есть готовая опция для XKB:
```
Option "XKbOptions" "ctrl:swapcaps"
```
Прописывается в /etc/X11/xorg.conf.d/00-keyboard.conf.
Меняет местами ctrl и caps lock.
Если вы вдруг используете какой-либо гуй для настроек - 
однозначно можно задать и через настройки.
Поверьте, в итоге очень удобно нажимать хоткеи  ctrl-f ( поиск ), 
ctrl-w ( закрытие вкладки ), 
ctrl-e ( прыгнуть в конец строки в терминале ).

### Caps Lock = Escape

Кроме control есть еще одна далекая и популярная клавиша - Esc.
Казалось бы, еще свободных клавиш нет, но мы воспользуемся забавным приемом - 
заметим, 
что Esc мы обычно нажимаем без каких-либо других зажатых клавиш,
в то время как ctrl обычно используется как модификатор для других клавиш,
то есть зажимается вместе с ними.
Другими словами, если бы захотели настроить одну клавишу сразу как и Esc, 
и как ctrl,
то сделали бы так, что если капс нажат сам по себе - 
то это Esc,
если вместе с какой-то клавишей - то это ctrl-<какая-то клавиша>.
И - бинго! -  мы можем так настроить с помощью программы 
[xcape](http://example.net://github.com/alols/xcape).
C ее помощью многое можно настроить, 
но конкретно то, 
что нас интересует (caps как esc),
работает на дефолтном конфиге,
( что отмечено в README проекта ),
при условии, 
что вы уже поменяли ctrl на capslock,
так что все что требуется - запустить xcape и/или добавить в автозапуск системы.

В итоге, после двух пунктов у вас убер Caps Lock, работающий и как Esc, если нажат сам по себе, и как Left Control, если нажат вместе с какой-то клавишей.

### Асинхронная смена раскладок клавиатуры
to be done
