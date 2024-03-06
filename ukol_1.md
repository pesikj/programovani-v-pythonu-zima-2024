# Domácí úkoly

## Zadání úkolu 1

Tvým úkolem je vytvořit aplikaci pro zjednodušený výpočet daně z nemovitostí, která bude postavená na principech OOP. Tato daň se vztahuje na pozemky, bytové a komerční prostory. Výše daně se odvíjí od několika faktorů, např. typu nemovitosti, velikosti, lokalitě, kde se nemovitost nachází atd.

V rámci aplikace nejprve vytvoř třídu `Locality`, která označuje lokalitu, kde se nemovitost nachází. Třída bude mít atributy `name` (název katastru/obce) a `coefficient` (koeficient, který se používá k výpočtu daně).

Vytvoř třídu `Property`, která bude reprezentovat nějakou nemovitost. Třída bude mít atribut `locality` (lokalita, kde se pozemek nachází, bude to objekt třídy `Locality`).

Dále vytvoř třídu `Estate`, která reprezentuje pozemek a je potomkem třídy `Property`. Třída bude mít atributy `locality`, `estate_type` (typ pozemku), `area` (plocha pozemku v metrech čtverečních). Dále přidej metodu `calculate_tax()`, která spočítá výši daně pro pozemek a vrátí hodnotu jak  celé číslo (pro zaokrouhlení použij funkci `ceil` z modulu `math`). Daň vypočítej pomocí vzorce: plocha pozemku * koeficient dle typu pozemku (atribut `estyte_type`) * koeficient obce. U atributu `estate_type` následující hodnoty a koeficienty:

- _land_ (zemědělský pozemek) má koeficient 0.85.
- _building site_ (stavební pozemek) má koeficient 9.
- _forrest_ (les) má koeficient 0.35. 

Uvažujme tedy například lesní pozemek o ploše 500 metrů čtverečních v obci s koeficientem 2. Potom je daň 500 * 0.35 * 2 = 350.

Jako druhou vytvoř třídu `Residence`, která reprezentuje byt, dům či jinou budovu a je potomkem třídy `Property`. Třída bude mít atributy `locality`, `area` (podlahová plocha bytu nebo domu) a `commercial` (pravdivostní hodnota, která určuje, zda se jedná o nemovitost používanou k podnikání). Dále přidej metodu `calculate_tax()`, která spočítá výši daně pro byt a vrátí hodnotu jako číslo. Daň vypočítej pomocí vzorce: podlahová plocha * koeficient lokality * 15. Pokud je hodnota parametru `commercial` `True`, tj. pokud jde o komerční nemovitost, vynásob celou daň číslem 2.

Uvažujme tedy například byt (určený k bydlení) o ploše 60 metrů čtverečních v lokalitě s koeficientem 3. Potom je daň 60 * 3 * 15 = 2700. Pokud by stejný byt byl používán k podnikání (např. jako kancelář), daň by byla 60 * 3 * 15 * 2 = 5400.

Vyzkoušej svůj program pomocí následujících nemovitostí:

- Zemědělský pozemek o ploše 900 metrů čtverečních v lokalitě Manětín s koeficientem 0.8. Daň z této nemovitosti je 900 * 0.85 * 0.8 = 612.
- Dům s podlahovou plochou 120 metrů čtverečních v lokalitě Manětín s koeficientem 0.8. Daň z této nemovitosti je 120 * 0.8 * 15 = 1440.
- Kancelář (tj. komerční nemovitost) s podlahovou plochou 90 metrů čtverečních v lokalitě Brno s koeficientem 3. Daň z této nemovitosti je 90 * 3 * 15 * 2 = 8100.

### Bonus

Ke třídě `Estate` a `Residence` přidej výpisy informací do metody `__str()__`. Např.: _Zemědělský pozemek, lokalita Manětín (koeficient 1), 900 metrů čtverečních, daň 765 Kč._
