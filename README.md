# Validació d'un XML amb Java

Aquest document explica el funcionament del següent codi Java, que permet **validar un fitxer XML** utilitzant les llibreries estàndard de Java per al processament de XML.

## Codi

```java
import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import java.io.File;

public class ValidarXML {
    public static void main(String[] args) {
        try {
            DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
            factory.setValidating(true);

            DocumentBuilder builder = factory.newDocumentBuilder();
            builder.parse(new File("cataleg.xml"));

            System.out.println("XML valid!");
        } catch (Exception e) {
            System.out.println("XML no valid");
        }
    }
}
```

---

# Explicació del codi

## 1. Importació de llibreries

```java
import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import java.io.File;
```

Aquestes llibreries permeten treballar amb documents XML:

- **DocumentBuilderFactory** → crea parsers XML.
- **DocumentBuilder** → analitza i processa el document XML.
- **File** → permet accedir a fitxers del sistema.

---

# 2. Classe principal

```java
public class ValidarXML
```

Defineix la classe principal del programa Java.

---

# 3. Mètode main

```java
public static void main(String[] args)
```

És el punt d'entrada del programa.

Quan executem el programa, Java comença ací.

---

# 4. Bloc try-catch

```java
try {
   ...
} catch (Exception e) {
   ...
}
```

Aquest bloc serveix per **gestionar errors**.

Si ocorre algun problema:
- XML mal format
- error de validació
- fitxer inexistent

es captura l'excepció.

---

# 5. Creació del DocumentBuilderFactory

```java
DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
```

Crea una **fàbrica de parsers XML**.

Aquest objecte permet configurar com es processaran els XML.

---

# 6. Activar la validació

```java
factory.setValidating(true);
```

Això indica que el parser ha de **validar l'XML**.

La validació comprova que:
- el XML és correcte
- compleix el **DTD** definit al document

Exemple de XML amb DTD:

```xml
<!DOCTYPE cataleg SYSTEM "cataleg.dtd">
```

---

# 7. Crear el parser

```java
DocumentBuilder builder = factory.newDocumentBuilder();
```

Ací es crea l'objecte que **llegirà i analitzarà l'XML**.

---

# 8. Llegir el fitxer XML

```java
builder.parse(new File("cataleg.xml"));
```

Aquest mètode:

1. Llegeix el fitxer `cataleg.xml`
2. Comprova que és **ben format**
3. Si hi ha DTD, comprova que **compleix l'estructura definida**

Si hi ha algun error, es llença una **excepció**.

---

# 9. Missatge si és correcte

```java
System.out.println("XML valid!");
```

Si no hi ha cap error durant el parse, el programa mostra aquest missatge.

---

# 10. Missatge si hi ha error

```java
System.out.println("XML no valid");
```

Aquest missatge apareix si:

- el XML té errors de sintaxi
- no compleix el DTD
- el fitxer no existeix
- hi ha qualsevol altra excepció

---

# Exemple de XML vàlid

```xml
<?xml version="1.0"?>

<!DOCTYPE cataleg SYSTEM "cataleg.dtd">

<cataleg>
    <llibre categoria="novel·la">
        <titol>La ciutat perduda</titol>
        <autor>Marta Soler</autor>
        <any>2019</any>
        <preu>18.90</preu>
    </llibre>
</cataleg>
```

---

# Resum

Aquest programa:

1. Crea un **parser XML**
2. Activa la **validació amb DTD**
3. Llegeix un fitxer XML
4. Mostra si és **vàlid o no**

---

# Conclusió

Aquest codi és un exemple senzill de **validació XML en Java utilitzant DOM** i **DTD**, útil per a aplicacions que necessiten verificar l'estructura d'un document XML abans de processar-lo.
