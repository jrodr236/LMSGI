# AJAX

> **AJAX** (**A**synchronous **J**avaScript **A**nd **X**ML) és un tècnica que permet comunicar-se amb el servidor i actualizar el contingut d'una pàgina web sense haver de recarregar tota la pàgina.

En les **aplicacions web tradicionals:**

1. Les accions de l'usuari (clicar un enllaç, enviar formulari, etc.) desencadenen crides al servidor.&#x20;
2. Un cop processada la petició de l'usuari, **el servidor retorna una nova pàgina** HTML al navegador de l'usuari.
3. En realitzar peticions contínues al servidor, l'usuari ha d'**esperar que es recarregui la pàgina** amb els canvis sol·licitats i això pot resultar molest.

**AJAX** permet millorar la interacció de l'usuari modificant part de la pàgina sense haver de recarregar la pàgina completament.

1. L'**intercanvi d'informació** amb el servidor l’executa el Javascript fent una petició AJAX en un segon pla.\
   Ajax és **asíncron** perquè **** les dades addicionals són demanades i carregades en un segon pla, sense interferir en la presentació i el comportament de la pàgina
2. Un cop es rep la resposta del servidor, es canvien **únicament les parts necessàries** de la pàgina.

![](../.gitbook/assets/ajax\_logo.jpg)

### **Mètodes AJAX natius**

Actualment existeix dues maneres d'**utilitzar AJAX de forma nativa** (sense ús de Frameworks) en Javascript.

* **XMLHttpRequest**
* **API Fetch**

### Objecte **XMLHttpRequest**

**Funcionament d’una aplicació AJAX**

1r. Un esdeveniment desencadena la necessitat de sol·licitar informació al servidor.

2n. **Instanciar l’objecte XMLHttpRequest** que en ens proporciona funcionalitat necessària per enviar i rebre informació de forma asíncrona.

3r. **Preparar la funció de resposta** que s’encarregarà de processar la informació de resposta del servidor.

4t. **Crear la petició** a servidor.

5è. **Enviament de la petició** al servidor.

6è. Executar la **funció de resposta**.

```javascript
function enviarPeticioAJAX() {
    // 1. Instanciar l’objecte XMLHttpRequest
    var xhttp= new XMLHttpRequest();
    
    // 2. Preparar la funció de resposta
    xhttp.onreadystatechange = function() {
      	//codi a executar quan es rep la resposta        
      
        if (this.readyState == 4 && this.status == 200) {
           //Si l'estat de la resposta és 4 = DONE (Petició completada)
           //i el codi de resposta és 200 = OK (Resposta correcte)
           document.getElementById("demo").innerHTML = this.responseText;
        }
    };
    
    // 3. Crear la petició a servidor
    xhttp.open("GET", "http://url_solicitada");
    
    // 4. Enviament de la petició
    xhttp.send();
}
```

### API Fetch

```javascript
function enviarPeticioAJAX() {
    
   fetch('http://url_solicitada')
      .then(
         //codi a executar quan es rep la resposta
         response => {      //response contindrà la resposta del servidor
             let dades = JSON.parse(response).results;
             console.log('Este es el objeto amb les dades', dades);
        }
      )
      .catch(
         //codi a executar quan la petició ha fallat
         err => {         //err contindrà l'error produït
           console.log(err);
         }
      );
}
```

### Exemple utilitzant la API [OpenWeather](https://openweathermap.org/) <a href="#enviament-de-dades" id="enviament-de-dades"></a>

```javascript
//Utilitzem API FETCH. fetch() retorna una Promesa
  fetch("http://api.openweathermap.org/data/2.5/weather?q=" + ciutat + "&units=metric&lang=ca&mode=html&APPID=" + api_key)
    .then((res) => {
      //Si la promesa es resolt

      //Si la resposta és correcta ? transformem la resposta a text i passem al següent then : Sinó executem el catch
      return res.ok ?  res.text() : Promise.reject(res);
      
      //Si la resposta és un JSON
      //return res.ok ?  res.json() : Promise.reject(res);
    })
    .then((html) => {
      //Mostrem la resposta que és un HTML
      document.getElementById("predicciohtml").innerHTML = html;
    })
    
    .catch(err => {
      //Si la promesa no es resolt
      console.log(err);
    })
    
    .finally(
      //S'executa sempre
    )
```

### Enviament de dades JSON <a href="#enviament-de-dades" id="enviament-de-dades"></a>

El mètode `JSON.stringify()` permet convertir un objecte Javascript en una cadena _(string)_ JSON, preparada per enviar-la a un servidor web.

[Exemple](https://www.w3schools.com/js/tryit.asp?filename=tryjson\_send)

### Recepció de dades JSON <a href="#recepcio-de-dades" id="recepcio-de-dades"></a>

El mètode `JSON.parse()` permet convertir els cadenes _(strings)_ JSON rebudes del servidor web en un objecte JavaScript.

[Exemple](https://www.w3schools.com/js/tryit.asp?filename=tryjson\_receive)
