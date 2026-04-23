# Tendencias-y-patrones-en-la-cobertura-medi-tica-del-fentanilo-Colombia-2016---2024
Segunda parte del proyecto  Analisis-de-titulares-fentanilo-2016-2024 

## Disclaimer

Este es un proyecto a nivel personal en donde quise poner en práctica el conocimiento que he adquirido relacionado al análisis de datos y análisis de texto, además de trabajar un tema que me toca de cerca que son las sustancias psicoactivas.

No soy experto, ni especialista en el tema de datos pero, todo el trabajo realizado fue con la mayor entrega y esfuerzo posible.

Teniendo en cuenta lo anterior, invito a aquellas personas que tienen más conocimientos en este tema a que revisen el proyecto y que lo complementen con todo lo que a mi se me pudo haber pasado o que por favor corrijan si me equivoqué en algo. He compartido absolutamente todos los archivos relacionados a este proyecto con ese objetivo, para que siga siendo trabajado y mejorado por cualquier persona que quiera.


# Contexto de la segunda parte del proyecto

Luego del trabajo realizado en la primera parte de este proyecto, en donde se recolectaron y se analizaron titulares de medios de comunicación en Canadá, Estados Unidos, México y Colombia con el objetivo de identificar tendencias y patrones significativos y analizar qué tipo de impacto pueden tener estas noticias en la percepción pública y el comportamiento de las personas que las consumen, esta segunda parte del proyecto se enfoca específicamente en el ecosistema mediático colombiano.


# Objetivos del proyecto

## Objetivo principal:
Analizar el cubrimiento mediático relacionado al fentanilo entre los años 2016-2024 en Colombia..

## Objetivos generales:
Identificar tendencias y patrones significativos mediante el análisis de lenguaje natural de las noticias publicadas por diversos medios en Colombia.

Analizar qué tipo de impacto pueden tener estas noticias en la percepción pública.

# Acciones

- Realizar el preprocesamiento y procesamiento de la base de datos de noticias extraídas utilizando Python, mediante el uso de librerías y herramientas especializadas en Web Scraping, procesamiento del lenguaje natural, análisis de tópicos y extracción de entidades más nombradas. Esto incluiyó la extracción de datos relevantes, la limpieza y normalización de los datos, y el uso de herramientas de procesamiento de lenguaje natural.

## Obtener y cargar los datos

Extracción de la información:
Debido a la variabilidad de las estructuras de las diferentes páginas web la extracción de los textos de los contenidos escritos (artículos, análisis, noticias, opinión) no se dio de la misma forma en todos los medios. Para aquellas páginas web que están hechas en su mayor parte con el idioma de programación html se generaron códigos haciendo uso de BeautifulSoup y Requests, dos herramientas muy útiles para este tipo de sitios. 

Para los medios que en sus páginas web usan una combinación de html, javascript y css se usaron scripts combinando herramientas más poderosas como Selenium y varios de sus módulos. En los casos en los cuales los resultados de las búsquedas en las páginas web de los medios de comunicación eran menos de 30 o donde la variabilidad de la estructura de su sitio web es demasiado dinámica y compleja se optó por extraer la información manualmente.

El estudio de las estructuras de las páginas web y la escritura de los scripts hubiera requerido mucho más tiempo. Los casos específicos fueron: La república, Caracol, 010, Colombiacheck, El Espectador, El País.com.co, La República, Las 2 Orillas, La Silla Vacía, Razón Pública y RCN.

Algunos medios tienen estructuras muy cambiantes en sus sitios web, barreras de inicio de sesión o barreras de suscripción para poder acceder al contenido escrito, es por esa razón por la cuál varias notas no pudieron ser extraídas. La información extraída fue guardada en un documento csv para su tratamiento en los siguientes pasos del proyecto.

## Limpieza de la información:

Debido a la variabilidad de formatos en los que se establecieron las fechas de publicación de los contenidos escritos (artículos, análisis, noticias, opinión) y teniendo en cuenta las buenas prácticas de manejo de bases de datos e información se estandarizaron todas las fechas de las noticias extraídas a formato DD-MM-AAAA.

En cuanto a los textos de los cuerpos de las noticias extraídas, estos pasaron por revisión ortográfica y se convirtieron todas las letras en minúsculas desde LibreOffice Calc y se eliminaron todos los caracteres especiales como comas, tildes, entre otros, haciendo uso del modelo de procesamiento de lenguaje Spacy en python, con el objetivo de lograr un mejor rendimiento.

Luego de los pasos anteriores se hizo un conteo de las veces que la palabra fentanilo aparece dentro del cuerpo de la noticia. Esto se hizo ya que si la palabra aparece menos de 3 veces, lo más probable es que la noticia no esté del todo relacionada con el tema, este paso redujo el número final de noticias extraídas de los sitios web de los medios de comunicación. 

La palabra fentanilo suele aparecer mucho en hiperenlaces, recomendaciones u otras secciones dentro de las páginas web de los medios de comunicación de donde se extrajeron los datos. Es una palabra muy usada solo con el objetivo de generar interacción y visitas. 

Se reemplazaron siglas como EE.UU por las palabras completas, Estados Unidos, con el objetivo de lograr una mejor comprensión en las personas que vean los resultados de la segunda parte de este ejercicio de análisis de datos.

## Análisis exploratorio de los datos

Análisis de texto:
La siguiente parte del procesamiento del texto se hizo con la librería de python, Spacy, y consistió en eliminar palabras vacías, aquellas que no aportan nada al análisis, como por ejemplo artículos; de, que, en, un, a, etc. Se lematizaron todos los textos, eso quiere decir que las palabras fueron llevadas a su raíz (cantamos = cantar, corriendo = correr) y todas las letras fueron convertidas a minúsculas.

El siguiente paso es la creación de nubes de palabras para ver cuáles son las que más se repiten dentro de los titulares y dentro del cuerpo de las noticias. Se repite lo que se observó en la primera parte de este ejercicio de análisis, las palabras que más se usan están relacionadas a la punitividad, la seguridad, el crimen, el negocio y la muerte.

Aunque en la nube de palabras hecha con el cuerpo de las noticias se logran colar de manera discreta palabras como médico, medicamento y salud, si se van leyendo las palabras, de las más grandes a las más pequeñas, la impresión que queda es el reflejo de la realidad del discurso que viene predominando: Esta es una droga ilegal producida en México hecha con sintéticos traídos de China que afecta a las personas de Estados Unidos, principalmente. Una gran simplificación de un tema con varias capas de complejidad.


<img width="1220" height="500" alt="imagen" src="https://github.com/user-attachments/assets/ceb56a42-98ec-4421-98cb-dc07bfd1e63c" />


Las demás realidades que hacen parte de este tema tan amplio quedan ocultas para poder justificar acciones de Estados Unidos en contra de otros países en el mundo, alegando seguridad y defensa. Como lo que pasó con los aranceles económicos en contra México, Canadá y China para combatir el tráfico de fentanilo y lo más actual, el bombardeo de lanchas y embarcaciones en el Caribe y en el Pacífico para impedir la entrada de cocaína a su territorio.

Haciendo un análisis de temas con todo el texto reunido, usando BERTopic (gran modelo lingüístico para procesamiento de lenguaje natural), se ven cuáles son las realidades más representadas por los medios al hablar del tema.


<img width="950" height="260" alt="imagen" src="https://github.com/user-attachments/assets/533bdb05-05a5-45d5-bee5-78bc63688b76" />


El tema más representado gira alrededor de las palabras México, unidos, cartel, estadounidense y Trump. Un reflejo en los medios del discurso que dicta Estados Unidos; responsabilizando a todos los demás por sus problemas de consumo, sobredosis y muerte, deshaciéndose completamente de las responsabilidades que tiene con sus habitantes.

El segundo se asocia a las palabras fentanilo, sobredosis, droga, opioide y muerte y el tercero a fentanilo, droga, heroína, sobredosis y persona.

¿Como se habló del fentanilo en Colombia? Se dijo que es una droga opioide que causa sobredosis y muerte, solo eso, no existe más.

Del fentanilo solo se dijo que es una droga x veces más potente que la heroína y que mata. Poco se habló de que usos tiene a nivel médico, ni como ha ayudado a muchas personas a sobrellevar el dolor y sus últimos momentos de vida.

También fueron pocas las menciones sobre lo que están haciendo muchas personas en varios países para evitar que las personas se mueran por su consumo fuera del entorno médico, más allá de estigmatizar, arrestar y judicializar.

Las palabras oficial, vehículo, agente y fronterizo en el quinto tópico más representado, son otro reflejo del discurso y de las políticas en contra de la migración hacia Estados Unidos desde el sur, con el supuesto objetivo de combatir las drogas y el crimen, sin importar las decisiones que deban tomarse o las personas que mueran en el proceso.

El siguiente paso dentro de este análisis consistió en usar el modelo de procesamiento de lenguaje para ver cuáles fueron las entidades más nombradas (localizaciones, personas y organizaciones). 

Colombia, país desde donde se hace este análisis, es la locación más nombrada, le sigue Washington, luego Europa, Texas, China, Nueva York y Asia. Washington como el centro del poder y toma de decisiones en Estados Unidos, Europa como otro posible mercado para la sustancia y China - Asia como proveedor químico.


<img width="307" height="311" alt="imagen" src="https://github.com/user-attachments/assets/b17f5987-db59-4713-88b4-516a842d5529" />


**¿Donde queda la información que de verdad aporte algo de importancia y beneficioso para la sociedad?**

La ONU (Organización de las Naciones Unidas) y los CDC (Centros para el Control y la Prevención de Enfermedades) de Estados Unidos fueron las organizaciones más nombradas dentro de la información recolectada. En primer lugar, una organización que ha estado de cerca en la fiscalización y restricción de las drogas ilegales en el mundo y en segundo lugar, la agencia nacional de salud pública de Estados Unidos.

De un lado está representada la prohibición de las sustancias en las últimas décadas y del otro lado la salud, dos cosas que son claramente contradictorias para los críticos de la guerra contra las drogas y las personas que apoyan la reforma a la política de drogas a nivel mundial. La salud nunca ha sido el verdadero objetivo cuando se habla de prohibir la oferta y consumo de sustancias ilegales, miles de personas han muerto y siguen muriendo bajo ese lema.

Donald, Manuel López Obrador y Joaquín Guzmán fueron los personajes más nombrados por los medios en Colombia cuando se habló de fentanilo. 

Los pares de palabras que mayor relación tuvieron entre sí en este análisis de texto son: muerte – sobredosis, droga – sintético, cartel – Sinaloa.


<img width="969" height="297" alt="imagen" src="https://github.com/user-attachments/assets/c6132a82-6e19-4193-98ec-b90adb93ce89" />


Todos los aportes que ha hecho el fentanilo en ámbitos médicos quedan totalmente invisibilizados y la información que de verdad pudo haber ayudado a educar y prevenir sobre sus peligros fuera del entorno médico, quedaron sepultados sobre cientos de noticias que solo buscaron generalizar una tendencia de alarma y miedo sin tener en cuenta que el contexto colombiano, incluso el sudamericano, es diferente al de América del Norte.

Aunque eso no asegura que Sudamérica esté el todo blindada contra una posible emergencia por consumo de fentanilo por fuera del ámbito médico, es una realidad que por ahora no está pasando. Son los medios de comunicación masivos los que han intentado imponer esa realidad desde sus editoriales e intereses particulares.

El medio que más publicó fue El tiempo, 338 noticias, le siguen SEMANA con 128 noticias y el País con 118. Las 3 palabras que más usaron fueron: fentanilo, droga y Estados Unidos.


<img width="1022" height="485" alt="imagen" src="https://github.com/user-attachments/assets/33f2f0ad-b5a9-4dd6-9e3a-8489363e3000" />


# Conclusiones

La falta de presencia de medios alternativos, independientes y comunitarios en el presente análisis responde a las agendas y decisiones editoriales de esos medios. Mientras que los medios con más alcance a nivel nacional y con sede en ciudades medianas y grandes fueron mucho más activos publicando noticias relacionadas al fentanilo, los medios más pequeños y con un alcance menor responden a sus contextos cercanos, en donde claramente este tema no tiene importancia dentro de sus contenidos.

La palabra fentanilo suele aparecer mucho en hiperenlaces, recomendaciones u otras secciones dentro de las páginas web de los medios de comunicación de donde se extrajeron los datos. Es una palabra muy usada solo con el objetivo de generar interacción y visitas. 

Al igual como se observó en la primera parte de este ejercicio de análisis, Tendencias y patrones en la cobertura mediática del fentanilo en América del Norte y Colombia, 2016 – 2024, el discurso usado se encuentra entre la punitividad, la seguridad, el crimen, el negocio y la muerte.

En la nube de palabras hecha con el cuerpo de las noticias recolectadas se logran colar de manera discreta palabras como médico, medicamento y salud pero si se leen las palabras, de las más grandes a las más pequeñas, la impresión que queda es el reflejo de la realidad del discurso que viene predominando: Esta es una droga ilegal producida en México hecha con sintéticos traídos de China que afecta a las personas de Estados Unidos, principalmente.

Las demás realidades que hacen parte de este tema tan complejo quedan ocultas para poder justificar acciones de Estados Unidos en contra de otros países en el mundo, alegando seguridad y defensa. Como lo que pasó con los aranceles económico en contra México, Canadá y China para combatir el tráfico de fentanilo y lo más actual, el bombardeo de lanchas y embarcaciones en el Caribe para impedir la entrada de cocaína a su territorio.

Del fentanilo solo se dijo que es una droga x veces más potente que la heroína y que mata. Nunca se habló de que usos tiene a nivel médico, ni como ha ayudado a muchas personas a sobrellevar el dolor y sus últimos momentos de vida.

Tampoco se dijo lo que están haciendo muchas personas en varios países para evitar que las personas se mueran por su consumo fuera del entorno médico, más allá de estigmatizar, arrestar y judicializar.

Colombia, país desde donde se hace este análisis, es la locación más nombrada, le sigue Washington, luego Europa, Texas, China, Nueva York y Asia. Washington como el centro del poder y toma de decisiones en Estados Unidos, Nueva York y Texas como ciudades con emergencias derivadas del consumo de fentanilo, Europa como otro mercado para la sustancia y China - Asia como proveedor químico.

La ONU (Organización de las Naciones Unidas) y los CDC (Centros para el Control y la Prevención de Enfermedades) de Estados Unidos fueron las organizaciones más nombradas dentro de la información recolectada. En primer lugar, una organización que ha estado de cerca en la fiscalización y restricción de las drogas ilegales en el mundo y en segundo lugar, la agencia nacional de salud pública de Estados Unidos.

De un lado está representada la prohibición de las sustancias en las últimas décadas y del otro lado la salud, dos cosas que son claramente contradictorias para los críticos de la guerra contra las drogas y las personas que apoyan la reforma a la política de drogas a nivel mundial. La salud nunca ha sido el verdadero objetivo cuando se habla de prohibir la oferta y consumo de sustancias ilegales, miles de personas han muerto y siguen muriendo bajo ese lema.

Los pares de palabras que mayor relación tuvieron entre sí en este análisis de texto son: Colombia – droga, alerta – droga, Colombia – consumo, consumo – droga, alerta – consumo y amenaza – chino. 

Todos los aportes que ha hecho el fentanilo en ámbitos médicos quedan totalmente invisibilizados y la información que de verdad pudo haber ayudado a educar y prevenir sobre sus peligros fuera del entorno médico, quedaron sepultados sobre cientos de noticias que solo buscaron generalizar una tendencia de alarma y miedo sin tener en cuenta que el contexto colombiano, incluso el sudamericano, es diferente al de América del Norte.

Aunque eso no asegura que Sudamérica esté el todo blindada contra una posible emergencia por consumo de fentanilo por fuera del ámbito médico, es una realidad que por ahora no está pasando. Son los medios de comunicación los que han intentado implantar esa realidad alternativa desde sus editoriales e intereses particulares.

**El medio que más publicó fue el tiempo, 338 noticias, le siguen SEMANA con 128 noticias y el País con 118. Las 3 palabras que más usaron fueron: fentanilo, droga y Estados Unidos.**

# Bibliografía

    • Boté-Vericad, J.-J.; H.-S. Afonso-Mendonça; E. Adilovic (2024). Agregadores de noticias: una aproximación al estado del arte sobre las consideraciones éticas en los algoritmos de recomendación. Documentación de las Ciencias de la Información, 47, 5-13. https://revistas.ucm.es/index.php/DCIN/article/view/90547.
    • Fletcher Richard (2023). Actitudes hacia los algoritmos y su impacto en las noticias. https://reutersinstitute.politics.ox.ac.uk/es/digital-news-report/2023/actitudes-algoritmos-impacto-noticias.
    • Riesgos de la desinformación en Colombia (2023). https://www.uniandes.edu.co/es/noticias/periodismo-y-comunicaciones/riesgos-de-la-desinformacion-en-colombia.
    • Sierra Caballero, Francisco, & Sola-Morales, Salomé. (2020). Golpes mediáticos y desinformación en la era digital. La guerra irregular en América Latina. Comunicación y sociedad, 17, e7604. Epub 27 de enero de 2021. https://doi.org/10.32870/cys.v2020.7604.
    • López-Borrull, Alexandre (2023). “En busca de la verdad perdida: redes sociales y desinformación”. Anuario ThinkEPI, v. 17, e17a44. https://doi.org/10.3145/thinkepi.2023.e17a44.
    • Cabral Brenda (2023). Manipulación de la información en medios de comunicación digitales e impresos. Instituto de Investigaciones Bibliotecológicas y de la Información Universidad Nacional Autónoma de México. https://thinkepi.scimagoepi.com/index.php/ThinkEPI/article/view/91621.
    • Calviño Vanessa (2023). La Desinformación en las Redes Sociales y el Periodismo. Artículo académico del doctorado en Ciencias de la Comunicación Social de la asignatura Industrias Culturales, impartida por el  Dr. Bladimir Cedeño Vega / Facultad de Comunicación Social de la Universidad de Panamá. https://launiversidad.up.ac.pa/node/3196.
    • Consultorio ético (2019). ¿Se está perdiendo la ética periodística por la inmediatez de la noticia?https://fundaciongabo.org/es/consultorio-etico/consulta/2140.
    • Lazo Carmen (2024). La desinformación, enfermedad de la sociedad posdigital: amenazas y desafíos. https://www.funcas.es/articulos/la-desinformacion-enfermedad-de-la-sociedad-posdigital-amenazas-y-desafios/.
    • Bernal Julián (2023). Ir en búsqueda del origen: herramientas para combatir la desinformación. https://fundaciongabo.org/es/recursos/relatorias/ir-en-busqueda-del-origen-herramientas-para-combatir-la-desinformacion.
    • Tuñón Navarro, Jorge y Sánchez del Vas, Rocío (2022). Verificación: ¿la cuadratura del círculo contra la desinformación y las noticias falsas?. En: adComunica. Revista Científica de Estrategias, Tendencias e Innovación en Comunicación, nº23. Castellón de la Plana: Departamento de Ciencias de la Comunicación de la Universitat Jaume I, 75-95. DOI: http://dx.doi.org/10.6035/adcomunica.6347.
    • Federico Rey Lennon. «Credibilidad, miedo y comunicación». Comunicación y Hombre. 2023, nº 19, pp 109-123. DOI: https://doi.org/10.32466/eufv-cyh.2023.19.767.109-123.
    • Fernández Carles (2003). Este contenido ha sido publicado en la sección Artículos Técnicos de Prevención de Riesgos Laborales en Prevention world. https://prevention-world.com/actualidad/articulos-tecnicos/amplificacion-social-riesgo-medios-comunicacion-y-percepcion-riesgo-i-teorias-sociales-riesgo/.
    • Carranza Maribel (2022). América Latina, relaciones políticas internacionales, medios de comunicación. Discriminación. Universidad de Granma. Bayamo MN, Cuba. https://dialnet.unirioja.es/servlet/articulo?codigo=8436933.
    • Salazar Echeagaray, Melissa. La dimensión mediática de la estrategia de miedo y securitización en América Latina. El Cotidiano, núm. 170, 2011, pp. 101-110. Universidad Autónoma Metropolitana Unidad Azcapotzalco, Distrito Federal, México. https://www.redalyc.org/pdf/325/32520935011.pdf.
    • Bonilla Jorge, Tamayo Camilo (2006). Medios de comunicación y violencias en América Latina: preocupaciones, rutas y sentidos. Revista Controversia. https://doi.org/10.54118/controver.v0i187.168.
