# Interview - Web (Browsers, Engines)

## Concepts

- What are service workers and what are the advantages?
- Can you access hard drive from browser?
- Various methods to do API calls.
- What is a PWA?
- webservices
- websockets
- webworkers
- [!] How is caching implemented in browsers?

## Questions

---

**(?) Rendering Engine or Browser Engine or Layout Engine**

**Jak parsowany jest html przez przeglądarkę?**

Silnik przeglądarki renderujący kod HTML.

Dla `Chromium` jest to `Blink`.
Dla `Mozilla` jest to `Gecko`.
Dla `Edge` jest to `Blink`.
Dla `Safari` jest to `WebKit`, do wersji 27 także przez `Chrome`.

Pobrany kod jest parsowany przez silnik, elementy są natychmiast renderowane lecz gdy silnik natknie się na znacznik script z src lub inline renderowanie zatrzyma się a przeglądarka wczyta i wykona kod JS, style CSS natomiast zostaną dodane gdy zbudowany zostanie `CSSOM` CSS Object Model.

--- 

**(?) Javascript Engines**

Chrome => Chrome V8 Engine
Firefox => SpiderMonkey
Safari => JavaScriptCore
Edge => Chakra

[JavaScript engines - how do they even?](https://www.youtube.com/watch?v=p-iiEDtpy6I)

---

**Jakie znasz metody przechowywania danych przez przeglądarkę?**

**What are various types of storages? What is the difference and possible use cases for: localStorage, sessionstorage, cookie, indexdb?**

Wszystkie posiadają strukturę przechowywania klucz-wartość. 

- Local Storage (lokalny magazyn danych)
- Session Storage
- Cookies

`Cookies` jednak przsyłane są poprzez nagłówki żądań i odpowiedzi HTTP i są ograniczone do 4096 znaków. Niewielkie informacje tekstowe, wysyłane przez serwer WWW i zapisywane po stronie użytkownika (zazwyczaj na twardym dysku). Domyślne parametry ciasteczek pozwalają na odczytanie informacji w nich zawartych jedynie serwerowi, który je utworzył.

`Session Storage` dostępne do czasu zamknięcia karty/przeglądarki.

`Local Storage` dostępne do czasu usunięcia przez kod strony.
Obydwa typy mogą w zależności od przeglądarki przechowywać nawet do kilkudziesięciu megabajtów. 

---

## Sources

[fedev.tech](https://fedev.tech/topic/)

[FullStack.Café](https://www.fullstack.cafe/)

[30secondsofcode](https://www.30secondsofcode.org/react/p/1)

[JS: interview Questions](http://thatjsdude.com/interview/dom.html#windwoVsDocument)

[JavaScript Array Functions CheatSheet - DEV](https://dev.to/vincenius/javascript-array-functions-cheatsheet-1c15)

[8 Ultimate Full Stack Interview Questions and Answers - DEV](https://dev.to/fullstackcafe/8-ultimate-full-stack-interview-questions-dj5)

[GitHub - sindresorhus/awesome: 😎 Awesome lists about all kinds of interesting topics](https://github.com/sindresorhus/awesome#media)

[GitHub - MaximAbramchuck/awesome-interview-questions: A curated awesome list of lists of interview questions. Feel free to contribute!](https://github.com/MaximAbramchuck/awesome-interview-questions)

[GitHub - denysdovhan/wtfjs: A list of funny and tricky JavaScript examples](https://github.com/denysdovhan/wtfjs#-is-equal-)

[javascript-interview-questions: List of 1000 JavaScript Interview Questions](https://github.com/sudheerj/javascript-interview-questions)

[123-Essential-JavaScript-Interview-Questions: JavaScript interview Questions](https://github.com/ganqqwerty/123-Essential-JavaScript-Interview-Questions)
