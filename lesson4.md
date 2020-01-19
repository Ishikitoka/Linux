# Задание 1.
Написать регулярное выражение, которое проверяет валидный IP-адрес. 
Например, 192.168.1.1 подойдет, а 256.300.1.1 — нет.

irina@irina-300E4C-300E5C-300E7C:~$ cat IPaddress 

192.168.1.1

256.300.1.1

192.168.2.1

192.168.2.2

200.168.1.1

192.250.1.1

2255.1.1.1

0.1.0.1

255.255.255.255

01.256.276.1

250.168.2.5

0.0.5.1

1.1.1.1

55.250.2.5

irina@irina-300E4C-300E5C-300E7C:~$ sed -En '/^(25[0-5]|2[0-4][0-9]|[01]?[0-9]{2}|[0-9]{2}|[0-9])(\.(25[0-5]|2[0-4][0-9]|[01]?[0-9]{2}|[0-9]{2}|[0-9])){3}$/p' IPaddress

192.168.1.1

192.168.2.1

192.168.2.2

200.168.1.1

192.250.1.1

0.1.0.1

255.255.255.255

250.168.2.5

0.0.5.1

1.1.1.1

55.250.2.5



# Задание 2

Написать регулярное выражение, которое проверяет, 
является ли указанный файлом нужного типа 
(на выбор .com,.exe или .jpg,.png,.gif и т.д.). 


irina@irina-300E4C-300E5C-300E7C:~$ touch filecheck

irina@irina-300E4C-300E5C-300E7C:~$ cat filecheck

doc.com

doc.exe

foto.jpg

drawing.png

pic.gif

file.exe

doc1.com

file.txt

file5

drawingpng

irina@irina-300E4C-300E5C-300E7C:~$ sed -En 's/^(.*+\.(\w|com|exe|jpg|gif|png))$/\1/p' filecheck

doc.com

doc.exe

foto.jpg

drawing.png

pic.gif

file.exe

doc1.com

Написать регулярное выражение для проверки, 
ведет ли ссылка URL на некоторый файл, 
и это действительно ссылка на картинку 
(например, http://site.com/folder/1.png), 
а не на любой файл.

irina@irina-300E4C-300E5C-300E7C:~$ cat linkscheck 

http://site.com/folder/1.png

http://site.com/folder/1.com

http://site.com/folder/1.exe

http://site.com/folder/2.jpg

http://site.com/folder/3.gif

http://site.com/folder/1

http://site.com/folder/1.links

irina@irina-300E4C-300E5C-300E7C:~$ grep -E -o '^((https?)\:\/\/)?(\w+)*\.([a-z]+)(\/.+\.(jpg|gif|png))$' linkscheck

http://site.com/folder/1.png

http://site.com/folder/2.jpg

http://site.com/folder/3.gif




