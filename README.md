# Создание VPK-HUD-dota2
Большая благодарность и основателя инструкции [unlikexd](https://github.com/unlikexd)

# Подготовка файлов

1. Скачиваем сборку и закидываем папки в steamapps (тут установлены Ваши игры от стим).
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
resourcecompiler -v -pauseiferror -i "G:\SteamLibrary\steamapps\common\dota 2 beta\content\dota_broudcast\*" -r -game "G:\SteamLibrary\steamapps\common\dota 2 beta\game\dota"
```
![image](https://github.com/user-attachments/assets/0b405e80-efce-48e6-84ad-0cc39a07061c)

3. После ввода адресов нажимаем `Enter`
  Ожиадаем создание файлов. После обозначения должно быть написано сколько файлов создано.
	![image](https://github.com/user-attachments/assets/cce7f138-b299-400b-bde8-999d5edec692)

# Упаковка в VPK
1. Заходим в папку с игрой по следующему адресу: `G:\SteamLibrary\steamapps\common\dota 2 beta\game\dota_broudcast`
2. Создаем текстовый файл с названием vpk_list.txt и заполняем адрес файлов:
   ```
	Пример:
	panorama/layout/hud/hud_reborn.vxml_c
	panorama/styles/hud/hud_reborn_cast.vcss_c
   ```
3. Вызываем командную строку через адресную строку *(точно также как это было в разделе Перекодирование файлов в расширения стим пунтк 1.)*
4. В окне консоли запускаем команду (ТЭГ жесткого диска у Вас может быть другой и ни какой кириллицы)
   ```
   Код:
   "G:\SteamLibrary\steamapps\common\dota 2 beta\game\dota_broudcast\VPK\vpk.exe" -v a pak01 @vpk_list.txt
   ```
5. После воода адресов нажимаем `Enter`
6. Получаем результат, что архив создан с определенными файлами
	![image](https://github.com/user-attachments/assets/5cc43e54-04dd-4fd9-ac7f-17bc81dd10c9)

7. В папке появится файл pak01_dir.vpk
8. Теперь можете запускать DOTA2 и радоваться новому стилю, который Вы придумаете

# Обязательно gameinfo.gi
1. Заходим по адресу игры DOTA2 в папку *dota* `G:\SteamLibrary\steamapps\common\dota 2 beta\game\dota`
2. И вставляем строки *Game	dota_broudcast* и *Mod	dota_broudcast*
   ```
   Должно получиться вот так
   
         		Game				dota_broudcast
			Game				dota
			Game				core
			
			Mod				dota_broudcast
			Mod				dota

			Write				dota
   

   ```

# Индентификация нужных файлов в DOTA2
Для того чтобы определить какой файл Вам мужен, то в консоле игры добавляем команду `-dev` и в демке Вы можете найти необходимый файл через *html код*, который вызывается кнопкой `F6`.
Все позиции HUD DOTA2 кликабельные
	![image](https://github.com/user-attachments/assets/605040ac-42d7-49d1-8a06-63d86d43df1a)

# P.S.   
Первый раз может дольше заргуржать. Если все верно, то игра не будет крашится, если крашится (вылетает, закрывается), то что то сделано не так в файлах.
Не забываем тестить обновление на демке.   
Если ВАВЛ что-то изменит в файлах, то придется корретировать и Ваши файлы и заново упаковать.


[Информация панораме от ВАЛВ](https://developer.valvesoftware.com/wiki/Dota_2_Workshop_Tools/Panorama)
