# Interview - (Network|Security)

## Concepts

### OSI Model

Conceptual model that characterises and standardises the communication functions of a telecommunication or computing system.

Layer architecture:

Layer 1: Physical Layer
Layer 2: Data Link Layer
Layer 3: Network Layer
Layer 4: Transport Layer
Layer 5: Session Layer
Layer 6: Presentation Layer
Layer 7: Application Layer

---

### HTTP 1.1

[RFC 2616 - HTTP/1.1](https://tools.ietf.org/html/rfc2616)

Najczęściej HTTP wykorzystuje protokół TCP, czasem jednak UDP. 

Na każdy request serwer odpowiada response.

`request` - żądanie HTTP składa się z:
- 1 linia (method, url address, protocol version)
- 2 linia (nagłówek Host - jedyny wymagany, adres serwera)
  - linia na końcu zawiera separator (separator lini protokołu HTTP tzw. CRLF, 0d0a0d0a)
- po wszystkich nagłówkach ponownie pusta linia (CRLF)

`response` - odpowiedź serwera składa się z:
- status odpowiedzi (HTTP/1.1 200 OK)
- pozostałe nagłówki (Date, Server, Last-Modified, ETag, Content-Type)
- pusta linia
- body response

W HTTP 1.0 nie wymagany jest żaden nagłówek, w 1.1 wyłącznie `Host`. Wersja 0.9 nie ma pojęcia nagłówków w ogóle.

#### Metody HTTP

[RFC 2616 - Methodes](https://tools.ietf.org/html/rfc2616#section-5.1.1)

- GET 
- HEAD (bez ciała odpowiedzi, zamiast tego przychodzi pusta linia na końcu)
- POST
- PUT
- DELETE
- TRACE
- OPTIONS (wskazuje obsługiwane przez serwer metody)
- CONNECT
Spotykamy ich jendak znacznie więcej: [Hypertext Transfer Protocol (HTTP) Method Registry](https://www.iana.org/assignments/http-methods/http-methods.xhtml)

#### Nagłówki

Ich nazwy mogą być reprezentowane w różnych kombinacjach znaków małe i duże litery.

Request:
- Host* (wymagany)
- Referer (adres poprzednio odwiedzanej strony)
- Cookie (wysyła ciasteczko 1>więcej do serwera)
- X-Forwarded-For

Response:
- Date
- Server (typ wersja systemu odpowiadającego - czasem)
- Content-Length (np. 39)
- Content-Type (np. text/html; charset=UTF-8)
- Set-Cookie (ustawia ciasteczko u klienta)
- Strict-Transport-Security
- Location (Przekierowanie klienta na inny adres)

#### Status codes 

[List of HTTP status codes - Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)
[HTTP Error Codes](https://www.digitalocean.com/community/tutorials/how-to-troubleshoot-common-http-error-codes)

`1xx` informational response – the request was received, continuing process

`2xx` successful – the request was successfully received, understood, and accepted
- 200 OK
- 201 Created
- 202 Accepted
- 204 No Content

`3xx` redirection – further action needs to be taken in order to complete the request
- 301 Moved Permanently
- 302 Moved Temporarily

`4xx` client error – the request contains bad syntax or cannot be fulfilled
- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found

`5xx` server error – the server failed to fulfil an apparently valid request
- 500 Internal Server Error
- 502 Bad Gateway
- 503 Service Unavailable
- 504 Gateway Timeout

---

### HTTP/2

[Introduction to HTTP/2  \|  Web Fundamentals  |  Google Developers](https://developers.google.com/web/fundamentals/performance/http2)

#### Cele

`Binary framing layer` - core of all performance enhancements of HTTP/2 is the new binary framing layer, which dictates how the HTTP messages are encapsulated and transferred between the client and server.

Przyspieszenie działania aplikacji webowych, tj. zwiększenie wydajności komunikacji pomiędzy klientem a serwerem przy jednoczesnym zachowaniu maksymalnej kompatybilności. 

- zmniejszenie opóźnień komunikacji
- kompresja pól nagłówków HTTP
- wsparcie priorytetów 
- server push

#### Budowa

Struktura z HTTP/1.1 tj. żądania, odpowiedzi, metody, nagłówki). Głównej zmianie uległa warstwa transportowa tj. protokół TCP. Teraz komunikacja odbywa się jedym połączeniem którym przesyłane są ramki HTTP/2.

#### Zmiany 

Poprzednia wersja 1.1 przesyła wielokrotnie te same nagłówki (w żądaniu i odpowiedzi). 

Nowa wersja wprowadza zamiast pipeliningu mechanizm multiplexingu. W jedym połączeniu możemy mieć wiele ramek, zawierających nagłówki lub ciałą, ramki organizowane są w strumienie. Żeby wysłać kolejne żądanie nie jest konieczne oczekiwanie na poprzednią odpowiedź.

- zmiana tekstowego formatu komunikatów na binarny
- zaawansowana kompresja nagłówków

HTTP/2 no longer needs multiple TCP connections to multiplex streams in parallel;

#### Badanie zgodności serwera z HTTP/2

Może za to odpowiadać narzędzie [h2spec](https://github.com/summerwind/h2spec) które testuje poprawność serwera pod kątem bezpieczeństwa wprowadzonego zaimplementowanego protokołu.

#### Why not HTTP/1.2?

HTTP/2 introduces a new binary framing layer that is not backward compatible with previous HTTP/1.x.

#### Komunikacja 

W HTTP/1.1 jak i HTTP/2 połączenie rozpoczyna się od `3-way handshake` ale w wersji 1 wysyłane jest bezpośrednio po tym żądanie HTTP natomiast w 2 wysyłane są jeszcze 2 strumienie, zerowy do parametrów kontrolnych całego strumienia, o id 1 utworzony przy pomocy HEADERS (nagłówki odpowiedzi) oraz DATA (ciało odpowiedzi) po tym jest wysyłana prośba o zamknięcie połączenia `GOAWAY`. 

---

### Cookies

Mechanizm zarządzania sesją. Potrzebne do utworzenia sesji pomiędzy serwerem (HTTP) a użytkownikiem (klient HTTP) - najczęściej przeglądarką. Serwer wysyła nagłówek Set-Cookie, który instruuje przeglądarkę by zapisać ciasteczko o określonej nazwie i wartości. Przeglądarka dołączy to ciasteczko do kolejnych requestów do określonej domeny.

Niewielkie informacje wysyłane przez portale (aplikacje webowe) i automatycznie zapisywane w mechanizmach naszej przeglądarki. Informacje zapisane w cookies są w automatyczny sposób wysyłane przez przeglądarki internetowe do aplikacji / portali, które wcześniej te ciastka ustawiły. Mechanizm ten działa również po restarcie przeglądarki.

Błędnie nazywane plikami, obecnie to fragmenty kodu, być może kiedyś były to pliki.

#### Przechowywanie

- `Firefox` - w bazie danych – SQLite.
- `Chrome` – w bazie danych – SQLite, dokładnie: C:\Users\nazwa_mojego_usersa\AppData\Local\Google\Chrome\User Data\Default\Cookies.
- `Internet Explorer` - w postaci zwykłych plików tekstowych.
- `Opera` - swój format przechowywania, jest to plik cookies4.dat.

#### Zastosowanie

Jest ich wiele, ale można wyróżnić:
 - rozpoznanie konkretnego użytkownika, przechowywanie jego sesji (najczęściej spotykane)
 - dostosowanie portalu pod własne potrzeby - tzw. customizacja, info o niej zapisane w cookie
 - reklamy, informacje o liczbie odwiedzin, śledzenie zachowań

#### Przykłady
```https
Set-Cookie: GoogleAccountsLocale_session=pl; Secure
Set-Cookie: GAPS=1:toEZ32pVxGQSduz-wdTWY2PYPtDxqA:PkoJytbwoKP_37qC;Path=/;Expires=Mon, 23-Mar-2015 08:18:19 GMT;Secure;HttpOnly
Set-Cookie: GALX=AM5B51_4dNg;Path=/;Secure
```

Pozostałe informacje – jak np. Path, Secure, HttpOnly – to parametry ciastek.

---

### REST API

Jest to aplikacja webowa, która jest ustruktyryzowana w pewnien sposób, nie jest frameworkiem, tak jak na przykład SOAP. REST jest jedynie zbiorem pewnych dobrych praktyk, które mają działać jako drogowskaz. Dla przykładu SOAP jest ograniczone jedynie formatu XML, podczas gdy REST jest w stanie pracować z XML, JSON lub nawet YAML.

> Żądanie typu GET nie może zmieniać stan systemu


`REST` - REpresentational State Transfer

`API` - Application Programming Interface

#### 6 Principles of REST API:

- `Client–server` – By separating the user interface concerns from the data storage concerns, we improve the portability of the user interface across multiple platforms and improve scalability by simplifying the server components.


- `Stateless` – Each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server. 
 
Nie przechowuje danych w cache/sesji. Cała reprezentacja stanu obiektu lub zasobu powinna być przesyłana. Tak więc, jeśli przesyłamy całość stanu, to po co nam sesja lub mechanizm cache'a w pamięci.

- `Cacheable` – Cache constraints require that the data within a response to a request be implicitly or explicitly labeled as cacheable or non-cacheable. If a response is cacheable, then a client cache is given the right to reuse that response data for later, equivalent requests.


- `Uniform interface` – By applying the software engineering principle of generality to the component interface, the overall system architecture is simplified and the visibility of interactions is improved. In order to obtain a uniform interface, multiple architectural constraints are needed to guide the behavior of components. REST is defined by four interface constraints: identification of resources; manipulation of resources through representations; self-descriptive messages; and, hypermedia as the engine of application state.


- `Layered system` – The layered system style allows an architecture to be composed of hierarchical layers by constraining component behavior such that each component cannot “see” beyond the immediate layer with which they are interacting.


- `Code on demand` (optional) – REST allows client functionality to be extended by downloading and executing code in the form of applets or scripts. This simplifies clients by reducing the number of features required to be pre-implemented.

All these principles help RESTful applications to be simple, lightweight, and fast.

#### REST != HTTP

Till the time, you are honoring the 6 guiding principles of REST, you can call your interface RESTful. A large number of people wrongly relate resource methods to HTTP GET/PUT/POST/DELETE methods. Roy Fielding has never mentioned any recommendation around which method to be used in which condition. All he emphasizes is that it should be uniform interface. If you decide HTTP POST will be used for updating a resource – rather than most people recommend HTTP PUT – it’s alright and application interface will be RESTful.

#### Sources 

[What is REST](https://restfulapi.net/)
[REST Principles and Architectural Constraints – REST API Tutorial](https://restfulapi.net/rest-architectural-constraints/)

---

### SSL | TLS | HTTPS

SSL - Secure Sockets Layers
TLS - Transport Layer Security

[Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security)

SSL and TLS are both cryptographic protocols that provide authentication and data encryption between servers, machines, and applications operating over a network (e.g. a client connecting to a web server).

> Renaming from "SSL" to "TLS", were a face-saving gesture to Microsoft, "so it wouldn't look the IETF was just rubberstamping Netscape's protocol".

> The differences between this protocol and SSL 3.0 are not dramatic, but they are significant enough that TLS 1.0 and SSL 3.0 do not interoperate.

For HTTP TLS connection we are using 443 port number.  

Once the client and server have agreed to use TLS, they negotiate a stateful connection by using a handshaking procedure

#### Versions 

SSL 1.0	Unpublished	Unpublished
SSL 2.0	1995	Deprecated in 2011 (RFC 6176)
SSL 3.0	1996	Deprecated in 2015 (RFC 7568)
TLS 1.0	1999	Deprecated in 2020[11][12][13]
TLS 1.1	2006	Deprecated in 2020[11][12][13]
TLS 1.2	2008	
TLS 1.3	2018	

---

### CORS

**Czym jest `origin`?**

Definiuje jednoznacznie pojedynczą aplikację.

- protokół (schemat)
- host (rygorystyczny - sprawdza nawet czy subdomena jest tożsama z domeną)
- port

**Przykład:**
`ftp://127.0.0.1:5000`, jeśli port jest pominięty to jest obecny jako `implicite` i dla http wynosi 80 a dla https 443 np. `https://google.com`

Aby zrozumieć CORS należy poznać `SOP` 

**SOP - Same-Origin Policy**

Mechanizm polega na tym, że strony posiadające to samo pochodzenie (origin) mogą komunikować między sobą i wymieniać dane - często jest to komunikacja na drodze klient - serwer. Jeśli to sprawdzenie nie przejdzie (czyli przynajmniej jeden z elementów origin będzie różny) to przeglądarka zablokuje taką komunikację i klient nie dostanie danych o jakie prosi.

**CORS - Cross-Origin Resource Sharing**

[Cross-Origin Resource Sharing (CORS) - HTTP \| MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

Mechanism that uses additional HTTP headers to tell browsers to give a web application running at one origin, access to selected resources from a different origin. 

Osłabia działanie SOP, ponieważ dopuszcza komunikację z zew. serwerem. Spowodowane jest to wymaganiami obecnie budowanych aplikacji gdzie front-end jest uruchomiony przez osobny serwer niż back-end. Przy pomocy nagłówków HTTP informuje przeglądarkę, że ufa klienowi i może odpytywać o dane.

#### Istnieją 2 typy requestów

**Simple Request**

- Klient wysyła zapytanie do serwera
- Przeglądarka dołącza do zapytania nagłówek Origin
- Serwer zwraca odpowiedź wraz z nagłówkiem Access-Control-Allow-Origin
– Przeglądarka sprawdza czy wartość w Access-Control-Allow-Origin zgadza się z wartością Origin klienta
- Jeśli wartość się nie zgadza to przeglądarka blokuje klienta przed otrzymaniem danych z serwera

**Preflight Request**

- Klient chce wysłać zapytanie do serwera ale zapytanie nie spełnia założeń simple request
- Zapytanie jest wstrzymywane przez przeglądarkę i jest wysyłane zapytanie preflight, którego celem jest sprawdzenie czy klient może wykonać zamierzone zapytanie
– Zapytanie preflight charakteryzuje się kilkoma elementami:
- wysłane zapytanie ma metodę OPTIONS
- wysyłane są dodatkowe nagłówki Access-Control-Request-Method, Access-Control-Request-Headers oraz ORIGIN (o samych nagłówkach będzie za chwilę)
- W momencie gdy przeglądarka dostaje odpowiedź na zapytanie sprawdza zawartość nagłówków Access-Control-Allow-Origin, Access-Control-Allow-Methods, Access-Control-Allow-Headers w odpowiedzi
- Jeśli wszystko jest w porządku to jest wysyłane oryginalne zapytanie tak jak w przypadku Simple Request

#### Nagłówki

Po stronie klienta:

- Origin - Orign klienta
- Access-Control-Request-Method - w zapytaniu preflight jest tu wpisywana nazwa metody z jaką klient chciał wykonać zapytanie
- Access-Control-Request-Headers - znajdują się tam nagłówki, które zostaną wykorzystane przy normalnym zapytaniu

Po stronie serwera:

- Access-Control-Allow-Origin - serwer zwraca tutaj informacje jaki Origin musi mieć klient by był w stanie wykonać request. Oprócz podania konkretnej wartości można podać tutaj wartość * co oznacza, że każdy może wykonać zapytanie.
- Access-Control-Allow-Methods - tutaj serwer zwraca jakie rodzaje zapytań są dozwolone
- Access-Control-Allow-Headers - tutaj serwer zwraca informację jakie nagłówki może wysłać klient

---

### CSP

Zabezpiecza głównie przed XSS ale także clickjacking. Jest to nagłówek HTTP lub element `<meta>` zawierający instrukcję dla przeglądarki mówiący, które zasoby pobierane na stronie mogą zostać wyświetlone a które zablokowane. 

Pozwala twórcy aplikacji webowej na ścisłe zdefiniowanie, skąd mogą pochodzić dodatkowe zasoby, z których korzysta aplikacja www (pliki zewnętrzne JavaScript czy CSS, obrazki i inne elementy multimedialne). Ograniczenie to ma zapobiegać atakom XSS, które dołączają do źródeł strony skrypty doczytywane z innych lokalizacji sieciowych.

`Content-Security-Policy`

`Content-Security-Policy-Report-Only`

#### Typy dyrektyw

default-src
connect-src
font-src
frame-src
img-src
media-src
object-src
style-src

Użycie `unsafe-inline` zezwala przeglądarce na wykonanie kodu JavaScript, znajdującego się:
- jako fragment strony, pomiędzy znacznikami <script> oraz </script>
- jako kod zdefiniowany w postaci atrybutu znacznika HTML on[event], np. onclick=”jakasfunckja()”. Także taki kod zadziała prawidłowo, gdy użyjemy unsafe-inline

---

### Public and private keys

---

### XSS

---

### SQL Injection

---

### CSRF

---

### JWT

---

### XHR

---

### Websockets

---

## Questions

### Różnica pomiędzy uwierzytelnianiem (ang. authentication) a autoryzacją (ang. authorization)?

Autoryzacja następuje po etapie uwierzytelniania (np. zapisania ciasteczka) i potwierdzeniu podmiotu. Autoryzacja ma na celu zbadanie jakie akcje może wykonywać określony użytkownik systemu i do jakich zasobów ma dostęp. Następować powinna przy każdym dostępie do zasobu (odczyt, zapis, usunięcie).

### Jakie istnieją metody uwierzytelniania użytkownika?

- Cookie

- HTTP Basic Authentication
Przesyłanie dodatkowego nagłówka `Authorization`. Składa się z dwóch elementów, słowa `Basic` i ciągu znaków w formacie `Base64`, który zawiera zakodowane `login:hasło` i porówna z danymi z bazy danych.

- Klucze API
Nagłówek `X-API-Key` stosowane w aplikacjach klasy API, mogą pełnią funkcję podstawową lub uzupełniającą. Przesyłany jest ciąg znaków rozpoznawany przez system. 

### Difference between http and https?

### Give some examples of tree shaking algorithms and how they works?

### How is working SSH Public Key authentication?
