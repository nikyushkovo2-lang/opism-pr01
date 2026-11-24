# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж (ОК-13)  
**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії.

**Навчальна група:** 21  
**Варіант:** 8, група за додатком А: 1  
**Домен:** ripe.net  
**Середовище:** Windows PowerShell, curl 7.55.1  
**Дата експериментів:** 24.11.2026

## Частина A. Збір експериментальних даних

### A.1. HTTPS

Команда:

```powershell
curl.exe -v https://ripe.net 2>&1 | Tee-Object -FilePath raw\a1-curl-https.txt
```

Повний вивід:

```text
* Rebuilt URL to: https://ripe.net/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 193.0.11.51...
* TCP_NODELAY set
* Connected to ripe.net (193.0.11.51) port 443 (#0)
* schannel: SSL/TLS connection with ripe.net port 443 (step 1/3)
* schannel: checking server certificate revocation
* schannel: sending initial handshake data: sending 179 bytes...
* schannel: sent initial handshake data: sent 179 bytes
* schannel: SSL/TLS connection with ripe.net port 443 (step 2/3)
* schannel: failed to receive handshake, need more data
* schannel: SSL/TLS connection with ripe.net port 443 (step 2/3)
* schannel: encrypted data got 4096
* schannel: encrypted data buffer: offset 4096 length 4096
* schannel: encrypted data length: 3994
* schannel: encrypted data buffer: offset 3994 length 4096
* schannel: received incomplete message, need more data
* schannel: SSL/TLS connection with ripe.net port 443 (step 2/3)
* schannel: encrypted data got 416
* schannel: encrypted data buffer: offset 4410 length 5018
* schannel: sending next handshake data: sending 93 bytes...
* schannel: SSL/TLS connection with ripe.net port 443 (step 2/3)
* schannel: encrypted data got 51
* schannel: encrypted data buffer: offset 51 length 5018
* schannel: SSL/TLS handshake complete
* schannel: SSL/TLS connection with ripe.net port 443 (step 3/3)
* schannel: stored credential handle in session cache
> GET / HTTP/1.1

> Host: ripe.net

> User-Agent: curl/7.55.1

> Accept: */*

> 

<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx</center>
</body>
</html>
* schannel: client wants to read 102400 bytes
* schannel: encdata_buffer resized 103424
* schannel: encrypted data buffer: offset 0 length 103424
* schannel: encrypted data got 380
* schannel: encrypted data buffer: offset 380 length 103424
* schannel: decrypted data length: 351
* schannel: decrypted data added: 351
* schannel: decrypted data cached: offset 351 length 102400
* schannel: encrypted data buffer: offset 0 length 103424
* schannel: decrypted data buffer: offset 351 length 102400
* schannel: schannel_recv cleanup
* schannel: decrypted data returned 351
* schannel: decrypted data buffer: offset 0 length 102400
< HTTP/1.1 301 Moved Permanently

< Server: nginx

< Date: Tue, 24 Nov 2026 08:46:14 GMT

< Content-Type: text/html

< Content-Length: 162

< Connection: keep-alive

< Location: https://www.ripe.net/

< 

{ [162 bytes data]

100   162  100   162    0     0    162      0  0:00:01 --:--:--  0:00:01   288
* Connection #0 to host ripe.net left intact

```

### A.2. HTTP

Команда:

```powershell
curl.exe -v http://neverssl.com 2>&1 | Tee-Object -FilePath raw\a2-curl-http.txt
```

Повний вивід:

```text
* Rebuilt URL to: http://neverssl.com/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 34.223.124.45...
* TCP_NODELAY set

  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:03 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:04 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:05 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:06 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:07 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:08 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:09 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:10 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:11 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:12 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:13 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:14 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:15 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:16 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:17 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:18 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:19 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:20 --:--:--     0* connect to 34.223.124.45 port 80 failed: Timed out
* Failed to connect to neverssl.com port 80: Timed out
* Closing connection 0
curl: (7) Failed to connect to neverssl.com port 80: Timed out

```

### A.3. DNS — перший запит

Команда:

```powershell
Resolve-DnsName ripe.net | Tee-Object -FilePath raw\a3-dns-1.txt
```

Повний вивід:

```text

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
ripe.net                                       AAAA   300   Answer     2001:67c:2e8:25::c100:b33
ripe.net                                       A      300   Answer     193.0.11.51


```

### A.3. DNS — другий запит

Команда:

```powershell
Resolve-DnsName ripe.net | Tee-Object -FilePath raw\a3-dns-2.txt
```

Повний вивід:

```text

Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
ripe.net                                       AAAA   300   Answer     2001:67c:2e8:25::c100:b33
ripe.net                                       A      300   Answer     193.0.11.51


```

### A.4. Контрольний ресурс

Команда:

```powershell
curl.exe -v https://google.com 2>&1 | Tee-Object -FilePath raw\a4-google.txt
```

Повний вивід:

```text
* Rebuilt URL to: https://google.com/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 142.250.130.100...
* TCP_NODELAY set
* Connected to google.com (142.250.130.100) port 443 (#0)
* schannel: SSL/TLS connection with google.com port 443 (step 1/3)
* schannel: checking server certificate revocation
* schannel: sending initial handshake data: sending 181 bytes...
* schannel: sent initial handshake data: sent 181 bytes
* schannel: SSL/TLS connection with google.com port 443 (step 2/3)
* schannel: failed to receive handshake, need more data
* schannel: SSL/TLS connection with google.com port 443 (step 2/3)
* schannel: encrypted data got 3757
* schannel: encrypted data buffer: offset 3757 length 4096
* schannel: sending next handshake data: sending 93 bytes...
* schannel: SSL/TLS connection with google.com port 443 (step 2/3)
* schannel: encrypted data got 295
* schannel: encrypted data buffer: offset 295 length 4096
* schannel: SSL/TLS handshake complete
* schannel: SSL/TLS connection with google.com port 443 (step 3/3)
* schannel: stored credential handle in session cache
> GET / HTTP/1.1

> Host: google.com

> User-Agent: curl/7.55.1

> Accept: */*

> 

* schannel: client wants to read 102400 bytes
* schannel: encdata_buffer resized 103424
* schannel: encrypted data buffer: offset 0 length 103424
* schannel: encrypted data got 861
* schannel: encrypted data buffer: offset 861 length 103424
* schannel: decrypted data length: 832
* schannel: decrypted data added: 832
* schannel: decrypted data cached: offset 832 length 102400
* schannel: encrypted data buffer: offset 0 length 103424
* schannel: decrypted data buffer: offset 832 length 102400
* schannel: schannel_recv cleanup
* schannel: decrypted data returned 832
* schannel: decrypted data buffer: offset 0 length 102400
< HTTP/1.1 301 Moved Permanently

< Location: https://www.google.com/

< Content-Type: text/html; charset=UTF-8

< Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-grU2cqckSAicwGlm59s97A' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp

< Date: Tue, 24 Nov 2026 09:01:26 GMT

< Expires: Thu, 24 Dec 2026 09:01:26 GMT

< Cache-Control: public, max-age=2592000

< Server: gws

< Content-Length: 220

< X-XSS-Protection: 0

< X-Frame-Options: SAMEORIGIN

< Alt-Svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000

< 

{ [220 bytes data]

100   220  100   220    0     0    220      0  0:00:01 --:--:--  0:00:01   827
* Connection #0 to host google.com left intact
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>

```

### A.5. Прострочений сертифікат

Команда:

```powershell
curl.exe -v https://expired.badssl.com 2>&1 | Tee-Object -FilePath raw\a5-expired.txt
```

Повний вивід:

```text
* Rebuilt URL to: https://expired.badssl.com/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 104.154.89.105...
* TCP_NODELAY set
* Connected to expired.badssl.com (104.154.89.105) port 443 (#0)
* schannel: SSL/TLS connection with expired.badssl.com port 443 (step 1/3)
* schannel: checking server certificate revocation
* schannel: sending initial handshake data: sending 189 bytes...
* schannel: sent initial handshake data: sent 189 bytes
* schannel: SSL/TLS connection with expired.badssl.com port 443 (step 2/3)
* schannel: failed to receive handshake, need more data

  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0* schannel: SSL/TLS connection with expired.badssl.com port 443 (step 2/3)
* schannel: encrypted data got 1420
* schannel: encrypted data buffer: offset 1420 length 4096
* schannel: encrypted data length: 1350
* schannel: encrypted data buffer: offset 1350 length 4096
* schannel: received incomplete message, need more data
* schannel: SSL/TLS connection with expired.badssl.com port 443 (step 2/3)
* schannel: encrypted data got 2746
* schannel: encrypted data buffer: offset 4096 length 4096
* schannel: received incomplete message, need more data
* schannel: SSL/TLS connection with expired.badssl.com port 443 (step 2/3)
* schannel: encrypted data got 579
* schannel: encrypted data buffer: offset 4675 length 5120
* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - ╧юыєўхэ ёхЁЄшЇшърЄ ё шёЄхъ°шь ёЁюъюь фхщёЄтш .

  0     0    0     0    0     0      0      0 --:--:--  0:00:03 --:--:--     0
* Closing connection 0
* schannel: shutting down SSL/TLS connection with expired.badssl.com port 443
* schannel: clear security context handle
curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - ╧юыєўхэ ёхЁЄшЇшърЄ ё шёЄхъ°шь ёЁюъюь фхщёЄтш .

```

### A.5. Невідповідність імені

Команда:

```powershell
curl.exe -v https://wrong.host.badssl.com 2>&1 | Tee-Object -FilePath raw\a5-wrong-host.txt
```

Повний вивід:

```text
* Rebuilt URL to: https://wrong.host.badssl.com/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 104.154.89.105...
* TCP_NODELAY set
* Connected to wrong.host.badssl.com (104.154.89.105) port 443 (#0)

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* schannel: SSL/TLS connection with wrong.host.badssl.com port 443 (step 1/3)
* schannel: checking server certificate revocation
* schannel: sending initial handshake data: sending 192 bytes...
* schannel: sent initial handshake data: sent 192 bytes
* schannel: SSL/TLS connection with wrong.host.badssl.com port 443 (step 2/3)
* schannel: failed to receive handshake, need more data
* schannel: SSL/TLS connection with wrong.host.badssl.com port 443 (step 2/3)
* schannel: encrypted data got 4096
* schannel: encrypted data buffer: offset 4096 length 4096
* schannel: encrypted data length: 4026
* schannel: encrypted data buffer: offset 4026 length 4096
* schannel: received incomplete message, need more data
* schannel: SSL/TLS connection with wrong.host.badssl.com port 443 (step 2/3)
* schannel: encrypted data got 400
* schannel: encrypted data buffer: offset 4426 length 5050
* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - ├ыртэюх ъюэхўэюх шь  эхтхЁэю.

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
* Closing connection 0
* schannel: shutting down SSL/TLS connection with wrong.host.badssl.com port 443
* schannel: clear security context handle
curl: (35) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - ├ыртэюх ъюэхўэюх шь  эхтхЁэю.

```

### A.5. Самопідписаний сертифікат

Команда:

```powershell
curl.exe -v https://self-signed.badssl.com 2>&1 | Tee-Object -FilePath raw\a5-self-signed.txt
```

Повний вивід:

```text
* Rebuilt URL to: https://self-signed.badssl.com/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 104.154.89.105...
* TCP_NODELAY set
* Connected to self-signed.badssl.com (104.154.89.105) port 443 (#0)
* schannel: SSL/TLS connection with self-signed.badssl.com port 443 (step 1/3)
* schannel: checking server certificate revocation
* schannel: sending initial handshake data: sending 193 bytes...
* schannel: sent initial handshake data: sent 193 bytes
* schannel: SSL/TLS connection with self-signed.badssl.com port 443 (step 2/3)
* schannel: failed to receive handshake, need more data
* schannel: SSL/TLS connection with self-signed.badssl.com port 443 (step 2/3)
* schannel: encrypted data got 1325
* schannel: encrypted data buffer: offset 1325 length 4096
* schannel: next InitializeSecurityContext failed: SEC_E_UNTRUSTED_ROOT (0x80090325) - ╓хяюўър ёхЁЄшЇшърЄют т√яє∙хэр ЎхэЄЁюь ёхЁЄшЇшърЎшш, эх шьх■∙шь фютхЁш .

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
* Closing connection 0
* schannel: shutting down SSL/TLS connection with self-signed.badssl.com port 443
* schannel: clear security context handle
curl: (77) schannel: next InitializeSecurityContext failed: SEC_E_UNTRUSTED_ROOT (0x80090325) - ╓хяюўър ёхЁЄшЇшърЄют т√яє∙хэр ЎхэЄЁюь ёхЁЄшЇшърЎшш, эх шьх■∙шь фютхЁш .

```

## Частина B. Власна модель рівнів

| Поле | Значення |
|---|---|
| Студент | [вказати ПІБ за вимогами викладача] |
| Група | 21 |
| Група за додатком А | 1 |
| Варіант | 8 |
| Домен | ripe.net |
| Кількість груп | 4 |

| № | Назва групи | Рядки виводу | Обґрунтування |
|---|---|---|---|
| 1 | Обмін вебданими | `> GET / HTTP/1.1`; `< HTTP/1.1 301 Moved Permanently`; `< Location: https://www.ripe.net/` | Запит, відповідь і перенаправлення безпосередньо визначають результат звернення. |
| 2 | Перевірка довіри та захист | `* schannel: SSL/TLS handshake complete`; `SEC_E_CERT_EXPIRED`; `SEC_E_WRONG_PRINCIPAL`; `SEC_E_UNTRUSTED_ROOT` | Ці повідомлення стосуються узгодження захищеного каналу та перевірки сертифікатів. |
| 3 | Визначення адреси | `ripe.net` — записи A та AAAA, TTL 300 | Ім’я перетворюється на адреси, потрібні для підключення. |
| 4 | Встановлення транспортного з’єднання | `* Connected to ripe.net (193.0.11.51) port 443 (#0)`; `* TCP_NODELAY set`; `* Failed to connect to neverssl.com port 80: Timed out` | Ці повідомлення описують підключення до конкретної адреси й порту; це найближча до мережевого транспорту група в моїх спостереженнях. |

Рядки, які складно віднести до однієї групи:

| Рядок | Причина |
|---|---|
| `* Connection #0 to host ripe.net left intact` | Відображає рішення клієнта щодо повторного використання з’єднання після обміну вебданими. |
| `* Rebuilt URL to: https://ripe.net/` | Підготовка адреси самим клієнтом, а не окремий обмін із сервером. |

## Частина C. Обговорення

Виконується аудиторно; результати обговорення ще не зафіксовано.

## Контрольні питання

1. У збереженому файлі A.1 перед першим рядком HTML є 39 фізичних рядків, з них 31 містить діагностичні позначки `*` або `>` (включно з Trying, об’єднаним із рядком прогресу). Через об’єднання потоків виводу HTML записано раніше за заголовки відповіді.
2. В A.1 наявні `SSL/TLS handshake complete`, `checking server certificate revocation`, `GET / HTTP/1.1` та заголовки відповіді. TLS потрібний для HTTPS, а HTTP його не використовує. Відсутність GET і відповіді в A.2 додатково пояснюється тайм-аутом TCP-з’єднання.
3. 443 — стандартний порт HTTPS, який curl вибирає за схемою URL.
4. TTL обох записів залишився 300 секунд. Це залишок часу життя DNS-запису в кеші. Можливе пояснення — оновлення кешу між запитами; точну причину вивід не встановлює.
5. `SEC_E_CERT_EXPIRED` — закінчився строк дії сертифіката; `SEC_E_WRONG_PRINCIPAL` — ім’я не відповідає домену; `SEC_E_UNTRUSTED_ROOT` — відсутня довіра до кореня ланцюжка сертифікатів.
6. Кандидати на три рядки (потрібно звірити з матеріалом лекції 1):

| № | Рядок виводу | Джерело |
|---|---|---|
| 1 | `* TCP_NODELAY set` | A.1 |
| 2 | `* schannel: stored credential handle in session cache` | A.1 |
| 3 | `* schannel: encdata_buffer resized 103424` | A.1 |

## Частина D. Висновки

Під час експерименту з доменом ripe.net несподіваним виявилося те, що успішне захищене з’єднання не обов’язково завершується отриманням основної сторінки. Рядок `* schannel: SSL/TLS handshake complete` підтвердив завершення узгодження захищеного каналу, але сервер повернув `HTTP/1.1 301 Moved Permanently` і запропонував іншу адресу. Подібне перенаправлення спостерігалося також для google.com.

Запит до neverssl.com завершився повідомленням `Failed to connect to neverssl.com port 80: Timed out`. Отже, визначення IP-адреси саме по собі не гарантує встановлення з’єднання. У двох DNS-запитах адреси залишилися однаковими, як і TTL, що становив 300 секунд. Це може пояснюватися оновленням кешу.

Для власної моделі я виділив чотири групи, оскільки у виводах можна розрізнити обмін вебданими, перевірку довіри, визначення адреси та встановлення транспортного з’єднання. Особливо показовими стали три перевірки сертифікатів: TCP-з’єднання встановлювалося, але захищений канал не завершувався через різні причини недовіри. Це обґрунтовує відокремлення перевірки сертифікатів від встановлення з’єднання. Я змінив би кількість груп, якби додаткові вимірювання дозволили окремо спостерігати маршрутизацію або передавання даних на фізичному рівні.

Після виконання роботи залишилося питання: чому саме підключення до neverssl.com завершилося тайм-аутом, хоча IP-адресу було отримано? Наявний вивід не дозволяє встановити, на якому проміжному етапі виникла проблема.

## Декларування використання ШІ (Р3)

Використано ChatGPT для пояснення команд PowerShell, інтерпретації результатів, підготовки чернетки моделі, відповідей та висновків, а також оформлення Markdown. Усі експериментальні виводи отримані студентом на власному комп’ютері та перенесені з оригінальних файлів.

Дослівні текстові запити:

- «Як зробити цю практичну?»
- «Моя группа: 1. Номер в списке: 8. Устройство: Windows. Помоги выполнить практическую пошагово.»
- «отправлял вам в чат»

Також передано фактичні виводи команд, фотографії термінала та вісім текстових файлів. Перед поданням студенту необхідно перевірити чернетку, доповнити відомості про аудиторне обговорення та звірити питання 6 з лекцією.
