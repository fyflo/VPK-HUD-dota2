# Создание VPK-HUD-dota2
Большая благодарность и основателя инструкции [unlikexd](https://github.com/unlikexd)

# Подготовка файлов

1. Скачиваем сборку бокуру и закидываем папки в steamapps (тут установлены Ваши игры от стим).
2. Скачиваем [Source 2 Resource Viewer](https://valveresourceformat.github.io/) и доп. контент Dota2 в стим Dota 2 Worksop Tools DLC
![image](https://github.com/user-attachments/assets/f6f43432-276c-43b4-a1fa-aee6b768eb8f)

3. Запускаем  `Source 2 Resource Viewer` *разварачиваем DOTA 2* и кликаем мышкой на файл `game/dota/pak01_dir.vpk`
![image](https://github.com/user-attachments/assets/f304d65f-8d99-4807-8536-81ed9f7742cb)
![image](https://github.com/user-attachments/assets/2dee52fc-d7c8-4682-b061-7f6b58279e54)

4. Все файлы, которые можно менять имеют разрешение vxml_c и vcss_c (может быть можно и vts_c менять, но лучше туда не залезать, если не разбираетесь)
   а. Выбираем необходимые файлы левой кнопкой мышки из папок panorama/layout/hud/ и  panorama/styles/hud/. Они у Вас откроются в новой вкладке. 
   б. Теперь нажимаем правую кнопку мыши на эту вкладку и нажимаем левой кнопкой мыши `Decompile & export` и сохранем файлы в папках: *xml в `\layout\hud`* | css в *`\styles\hud`*, которые расположены в папке `common\dota 2 beta\*content*\dota_broudcast\panorama`
   в. В название файлов добавляем `_cast` (пример: dota_hud_ability_panel *_cast*.css), чтобы не пересекались с оригиналами во время просмотра демки или DOTA2TV.
   
![image](https://github.com/user-attachments/assets/af47b7ef-8a59-4b1b-8649-110ba1528919)
![image](https://github.com/user-attachments/assets/edb8a865-9f78-4ce5-a7c1-6a85bb355b2f)

6. Производим изменения в файлах в css стили div и class необходимых разделов.
7. Теперь в таком же файле, но xml необходимо добавить ссылки на файлы css.
![image](https://github.com/user-attachments/assets/9b9800f5-dd79-45bc-8202-59b5b25350be)



*Теперь самый сложный этап*
# Перекодирование файлов в расширения стим

1. Заходим в папку с игрой по следующему пути:
   *G*:\SteamLibrary\steamapps\common\dota 2 beta\game\bin\win64
   и запускаем из адресной строки cmd.
![image](https://github.com/user-attachments/assets/81822c6f-e51f-4cd7-87a9-b36e0b24157b)

2. В окне консоли запускаем команду (ТЭГ жесткого диска у Вас может быть другой и ни какой кириллицы)
   
```
Код:
resourcecompiler -v -pauseiferror -i "G:\SteamLibrary\steamapps\common\dota 2 beta\content\dota_broudcast2\*" -r -game "G:\SteamLibrary\steamapps\common\dota 2 beta\game\dota"
```
![image](https://github.com/user-attachments/assets/0b405e80-efce-48e6-84ad-0cc39a07061c)

3. После воода адресов нажимаем `Enter`
  Ожиадаем создание файлов. После обозначения должно быть написано сколько файлов создано.
![image](https://github.com/user-attachments/assets/cce7f138-b299-400b-bde8-999d5edec692)

# Упаковка в VPK
1. Заходим в папку с игрой по следующему адресу: `G:\SteamLibrary\steamapps\common\dota 2 beta\game\dota_broudcast`
2. Закидываем сюда

