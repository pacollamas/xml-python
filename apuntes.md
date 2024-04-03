---
title: apuntes
---

# DOM

Document Object Model (DOM) es una api de programacion con python para documentos HTML y XML que sirve para definir la estrucura de un documento como un arbol de objetos permitiendo acceder y manipular los elementos y contenido del documento XML.


## getElementById

- __elemento = document.getElementBy ("miElemento");__


## getElementsByTagName

- __name = x.getElementsByTagName("nom")[0].firstChild.data__


## Ejemplo imagen de minidom con funcionamiento

	
![](/domej.png)

# XPATH

XPath son cadenas de texto que se utilizan para especificar la ubicación de nodos en un documento XML

## Donde usar XPATH pruebas:
    
[Tester XPATH](https://www.freeformatter.com/xpath-tester.html "web1")

## USO de XPATH
    
[Nom del node] __Indica tots els fills del nom del node__

[/] __Indica l’element arrel__

[//] __Indica tots els elements del document__

[.] __Indica el node actual__

[..] __Indica el pare del node__

[@] __Indica l’atribut__


## Ejemplos de XPATH

- Llistat de tots els preus de les pel·lícules de la botiga.

//preu/text()

- Llistat dels títols de les pel·lícules en català.

//titol[@idioma='ca']/text()

- Llistat dels títols de les pel·lícules realitzades després o durant el 2008.

/botiga/bluray[any >= 2008]/titol/text()

# xslt
XSLT es un lenguaje utilizado para transformar documentos XML en otros formatos, como HTML, XML o texto plano. Utiliza reglas de transformación definidas en un archivo XSLT para modificar la estructura y el contenido del documento XML de entrada.

## Elementos de xslt
- `<xsl:template>`: Define una plantilla de transformación.

- `<xsl:apply-templates>`: Aplica una plantilla a los nodos seleccionados.

- `<xsl:value-of>`: Extrae el valor de un nodo y lo incluye en el resultado.

- `<xsl:for-each>`: Itera sobre una lista de nodos y aplica una plantilla a cada uno.

- `<xsl:if>` y `<xsl:choose>`: Se utilizan para aplicar transformaciones condicionales.

## Ejemplo de codigo xsl

## XSL
````<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  <html>
    <head>
      <style>
        svg {
          border: 1px solid black;
        }
      </style>
    </head>
    <body>
      <svg width="{dibuix/canvas/amplada}" height="{dibuix/canvas/alçada}" xmlns="http://www.w3.org/2000/svg">
        <xsl:for-each select="dibuix/figures/figura">
          <xsl:choose>
            <xsl:when test="@tipus = 'rectangle'">
              <rect x="{posicio/x}" y="{posicio/y}" width="{dimensions/amplada}" height="{dimensions/alçada}" fill="{@color}" />
            </xsl:when>
          </xsl:choose>
        </xsl:for-each>
      </svg>
    </body>
  </html>
</xsl:template>

</xsl:stylesheet>
````
## XML

````<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="dibuix.xsl"?>
<dibuix>
    <canvas>
        <amplada>400</amplada>
        <alçada>400</alçada>
    </canvas>
    <figures>
        <figura tipus="rectangle" color="red">
            <posicio>
                <x>100</x>
                <y>20</y>
            </posicio>
            <dimensions>
                <amplada>100</amplada>
                <alçada>100</alçada>
            </dimensions>
        </figura>
    </figures>
</dibuix>

````