# 📸 PhotoMatch – Fotós Portfólió és Ajánlatkérő Platform

A **PhotoMatch** egy felhőalapú portfólió- és ajánlatkérő platform, amely közvetlenül összeköti a professzionális fotósokat a potenciális megrendelőkkel (magánszemélyekkel és vállalkozásokkal).

---

## 🎯 Problémafelvetés és Koncepció

Amikor magánszemélyek vagy cégek fotóst keresnek egy eseményre (esküvő, céges rendezvény, portré), a közösségi oldalakon nehézkes a szakemberek felkutatása: a munkák szétszórtak, a képek minősége a tömörítés miatt romlik, és nem látszanak a pontos technikai részletek sem. A fotósoknak sincs egy olyan dedikált felületük, ahol szakmai szempontból, a képek részletes beállításaival és felszerelésükkel együtt mutathatnák be munkáikat.

### A rendszer fő felületei

* **🖥️ Fotós felület (Web):** A fotósok feltölthetik munkáikat és bemutathatják felszerelésüket (vázak, objektívek). Képfeltöltéskor a rendszer a beágyazott EXIF metaadatokból automatikusan kiolvassa és rögzíti a kamera beállításait (rekeszérték, záridő, ISO, gyújtótávolság, váz- és objektívtípus), amelyek láthatóságát a fotós képenként szabályozhatja. A fotósok ezen a felületen kezelhetik a beérkező ajánlatkéréseket is.
* **📱 Megrendelői felület (Mobilapp / Web):** Cégek és magánszemélyek böngészhetnek a fotósok és munkáik között, szűrhetnek kategóriák (pl. esküvő, portré, rendezvény, autó), helyszín vagy felszerelés szerint. Közvetlenül az alkalmazáson keresztül strukturált ajánlatkérést küldhetnek a kiszemelt fotósnak (időpont, helyszín, esemény típusa, leírás), majd a lezárt munkákat értékelhetik. *(A fizetés nem az alkalmazáson belül történik.)*
* **🛡️ Adminisztrátori felület (Web):** A rendszer felügyelete, kategóriák kezelése, a feltöltött képek moderálása és az aktivitási statisztikák áttekintése.

---

## 🛠️ Technológiai Stack

| Réteg | Technológia | Főbb funkciók és jellemzők |
| :--- | :--- | :--- |
| **Adatbázis & Környezet** | **PostgreSQL + Docker + pgAdmin** | Konténerizált, normalizált relációs adatbázis (`roles`, `accounts`, `profiles`, `companies`, `photos`, `photo_metadata`, `categories`, `photo_categories`, `inquiries`, `reviews`), puha törléssel (`deleted_at`) és archiválással (`archived_at`). |
| **Backend & ORM** | **NestJS (TypeScript) + Prisma ORM** | Moduláris REST API architektúra, típusbiztos Prisma adatbázis-réteg és migrációk, JWT autentikáció, szerepkör-alapú hozzáférés-vezérlés (RBAC), automatikus EXIF metaadat-kinyerés, bélyegkép-generálás és Swagger/OpenAPI dokumentáció. |
| **Webes Kliens** | **React (Vite) + TypeScript** | Reszponzív portfólió- és kezelőfelület, szűrhető képgalériák, képfeltöltő űrlap automatikus EXIF-beolvasással, ajánlatkérés-kezelő és adminisztrátori moderációs panel. |
| **Mobil Kliens** | **Android (Kotlin + Jetpack Compose)** | Képorientált natív mobilalkalmazás fotósok és portfóliók böngészéséhez, EXIF adatok megtekintéséhez, ajánlatkérések küldéséhez és a státuszok nyomon követéséhez. |
| **Tesztelés** | **Jest + Postman** | Automatizált NestJS backend egységtesztek (unit & e2e tests), Postman végpont-gyűjtemény és manuális tesztjegyzőkönyv. |

---

## 👥 Csapatunk és Munkamegosztás

Csapatunk a korábbi tanévben már sikeresen lefejlesztett egy közös szervizkezelő rendszert, így kiforrott munkamenettel és egyértelműen felosztott felelősségi körökkel dolgozunk:

* **Szakács Vendel – Backend Mérnök & Adatbázis Felelős**
  * PostgreSQL adatbázis és Docker (pgAdmin) környezet összeállítása, Prisma ORM séma és migrációk kezelése.
  * NestJS REST API architektúra kiépítése (Auth, RBAC, CRUD végpontok, ajánlatkérési folyamat).
  * Képfeltöltés, fájlkezelés, automatikus EXIF metaadat-kinyerés, Swagger dokumentáció és Jest backend tesztek.
* **Hajni – Web Frontend Fejlesztő (Fotós Portál & Admin Felület)**
  * Reszponzív webes felhasználói felület tervezése és fejlesztése (React + TypeScript).
  * Fotós portfóliókezelő, EXIF-adatokat megjelenítő képfeltöltő űrlap és ajánlatkezelő felület.
  * Adminisztrációs panel (moderáció, kategóriák) fejlesztése és REST API integráció.
* **Apró Bence – Mobil Kliens Fejlesztő & Rendszer-tesztelő / Dokumentációs Felelős**
  * Android mobilalkalmazás fejlesztése (Kotlin + Jetpack Compose) megrendelők és látogatók számára.
  * A mobilkliens összekötése a REST API végpontokkal.
  * Manuális tesztelési jegyzőkönyv összeállítása, a GitHub Organization/repók rendszerezése és a hivatalos műszaki dokumentáció összefogása.

---

## 🔄 Fejlesztési Folyamat és Eszközök

* **Konténerizáció:** Docker Desktop (`docker-compose.yml` a PostgreSQL és pgAdmin egységes futtatásához).
* **Projektmenedzsment:** GitHub Projects (Kanban tábla) a feladatok és sprintek követésére.
* **Verziókezelés:** Git & GitHub – különálló moduláris repository-k, védett `main` ág, közös `dev` ág és feladatonkénti `feature/...` ágak Pull Request alapú kódellenőrzéssel.
* **Kommunikáció:** Személyes egyeztetések és Discord.
