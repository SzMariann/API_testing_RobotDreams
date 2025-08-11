# API_teszteles_RobotDreams
A RobotDreams kurzusának feladata és megoldása

Az 1. feladat célja egy API tesztelési stratégia kidolgozása és megvalósítása egy webshop backend alkalmazásra. A webshop backend funkciói közé tartozik a termékek kezelése, a felhasználói fiókok kezelése, a rendeléskezelés és a kosár funkció. A tesztelési stratégia célja a backend API-ok megbízhatóságának, teljesítményének és alapszintű biztonságának biztosítása.

A 2. feladat célja az előző házi feladatban megadott követelményeknek megfelelően implementált alkalmazás tesztelése.

A mellékelt dokumentumok a következők:

- Excel: Tesztelési stratégia + a hozzá kapcsolódó tesztesetek címszavakban, service-enként csoportosítva, a futtatási eredményekkel. Load és security teszt eredményeket nem tartalmaz.

- Postman Environment beállítások és Collection

- Newman report

Észrevételek és talált hibák:

Mivel nincs mögötte DB, valószínűleg nem megoldott, hogy változnia kéne a cart-ban a darabszámoknak POST /cart/add és GET /cart meghívásakor.

Ha path paramban wrong format ID van megadva, akkor vajon 404-et vagy 405-öt kell-e visszaadnia? így 404-el kiegyeztem (ezt élesben fejlesztőtől megkérdezném).

Nekem a legsúlyosabb problémák a következőek:
1. Sikerült két usert generálni ugyanazokkal az adatokkal (user3 2x)
2. Update usernél engedi az üres emailt, üres passwordöt, üres bodyt.
3. Update productnál engedte a felülírást úgy, hogy különböző productId volt megadva path paramban és a bodyban is, ebből az lett, hogy lett 2db ugyanolyan ID-jú termék.
4. A DELETE /products/{id} és a DELETE /orders/{id} végpontokra nálam 415 jött 200 OK helyett. Valamiért a Postman a DELETE metódusnál panaszkodott a Json formátum miatt a headerben.
5. A Cart összegeinél nálam nem volt mindig jó, de ez lehet, nálam volt.
6. DELETE /cart/remove-nál sikerült nem létező itemet törölni.
7. POST /cart/add-nál sikerült több itemet hozzáadnia kosárhoz, mint amennyi volt készleten.
8. POST /orders-nél sikerült több itemet hozzáadni, mint amennyi volt készleten.
