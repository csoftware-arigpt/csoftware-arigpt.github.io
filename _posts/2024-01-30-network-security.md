---
layout: post
title: Защищаем от брутфорса ваши аккаунты и WiFi сеть
---

Всем привет, csoftware на свзяи

Мной было замечено что многие сети моего города уязвимы к брутфорсу сети используя при этом всего 1 словарь - rockyou.txt
Большая часть паролей очень просты и содержатся во многих базах данных, при этом сервисы по "наличию слитых паролей" может даже их не найти в базах.

Тогда как обеспечить себя от взлома методом брутфорса?

Сразу дам вам совет - **не вводите лучше свои пароли в сервисы по "проверки на наличие слитого пароля в базах даннах"**. Вы точно доверите ему свой пароль который неожиданно "может утечь"?

Проверяйте в списках сами. Ищите на breachforums, github и других подобных сервисов

Я вам дам пару списков по которым вы можете проверить свой пароль на наличие в базах данных:

[SecLists - GitHub](https://github.com/danielmiessler/SecLists)

[Список словарей - GitHub by Hob0Rules](https://github.com/praetorian-inc/Hob0Rules/tree/master/wordlists)

[Софт который выкачает список паролей с сайта haveibeenpwned (Написан на C#)](https://github.com/HaveIBeenPwned/PwnedPasswordsDownloader)

[Список от skullsecurity](https://wiki.skullsecurity.org/index.php/Passwords)

[Список от crackstation](https://crackstation.net/crackstation-wordlist-password-cracking-dictionary.htm)

[Список от InsidePro (Web Archive)](https://web.archive.org/web/20120207113205/http://www.insidepro.com/eng/download.shtml)


И это только малая часть. Все списки даны с целей проверки на наличие паролей в базах данных и не имеет цели "для взлома". Вся ответственность на вас

А с вами был csoftware
