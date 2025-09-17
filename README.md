# API_testing_RobotDreams
**A RobotDreams kurzusának feladata és megoldása**

https://github.com/tcsako/python-api-app

Az 1. feladat célja egy API tesztelési stratégia kidolgozása és megvalósítása egy webshop backend alkalmazásra. A webshop backend funkciói közé tartozik a termékek kezelése, a felhasználói fiókok kezelése, a rendeléskezelés és a kosár funkció. A tesztelési stratégia célja a backend API-ok megbízhatóságának, teljesítményének és alapszintű biztonságának biztosítása.

A 2. feladat célja az előző házi feladatban megadott követelményeknek megfelelően implementált alkalmazás tesztelése.

**A mellékelt dokumentumok a következők:**

- Excel: Tesztelési stratégia + a hozzá kapcsolódó tesztesetek címszavakban, service-enként csoportosítva, a futtatási eredményekkel. Load és security teszt eredményeket nem tartalmaz.

- Postman Environment beállítások és Collection

- Newman report

**Észrevételek és talált hibák:**

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

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Assignment and Solution for the RobotDreams Course**

https://github.com/tcsako/python-api-app

Task 1: The goal is to design and implement an API testing strategy for a webshop backend application. The webshop backend functions include product management, user account management, order management, and the shopping cart. The testing strategy aims to ensure the reliability, performance, and basic security of the backend APIs.

Task 2: The goal is to test the application implemented according to the requirements defined in the previous assignment.

**Attached documents include:**

- Excel: Testing strategy + related test cases summarized, grouped by service, with execution results. Load and security test results are not included.

- Postman: Environment settings and Collection

- Newman report

**Observations and issues found:**

Since there is no database behind it, it’s likely not implemented that the quantities in the cart should change when calling POST /cart/add and GET /cart.

If a wrong format ID is provided in the path param, should it return 404 or 405? I settled with 404 (in production I would confirm this with a developer).

The most critical issues for me were:
1. I was able to create two users with the same data (user3 twice).
2. For updating a user, it allows empty email, empty password, and empty body.
3. For updating a product, it allowed overwriting even when different productIds were provided in the path param and in the body, which resulted in two products with the same ID.
4. On DELETE /products/{id} and DELETE /orders/{id}, I received 415 instead of 200 OK. For some reason Postman complained about the JSON format in the header for the DELETE method.
5. The cart totals were not always correct for me, though this may have been on my side.
6. On DELETE /cart/remove, I was able to delete a non-existent item.
7. On POST /cart/add, I was able to add more items to the cart than were available in stock.
8. On POST /orders, I was able to order more items than were available in stock.
