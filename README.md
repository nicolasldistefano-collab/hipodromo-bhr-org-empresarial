# Sistema de Gestión Hípica - Hipódromo B.H.R.

Repositorio oficial de documentación técnica y artefactos del proyecto integrador de la cátedra **Organización Empresarial** (Tecnicatura Universitaria en Programación - UTN).

## Descripción del Sistema

Plataforma integral de autogestión y automatización de la programación hípica del **Hipódromo B.H.R.** (caso de estudio ficticio basado en hechos reales). El módulo central es el de **Programación de Carreras e Inscripciones Web**, que reemplaza el circuito manual en papel y el sistema heredado de los años 90.

El sistema abarca:

- Inscripción digital de ejemplares Sangre Pura de Carrera (SPC) por parte de entrenadores y propietarios.
- Validaciones lógicas automáticas (completitud de datos y condición sanitaria del ejemplar).
- Ratificación o baja de inscriptos en la etapa de depurados.
- Emisión automática del programa oficial de carreras.

## Integrantes (Comisión 3)

- Nicolás Luciano Di Stefano

## Enlaces de Interés

- [Tablero Ágil de Gestión (GitHub Projects)](https://github.com/users/nicolasldistefano-collab/projects/1)
- [Diagrama BPMN](docs/diagrama-bpmn.png)

## Modelado de Procesos (BPMN)

El proceso de **Inscripción, Depurados y Programa Oficial** se modeló con notación BPMN estándar:

- **Dos Pools:** *Entrenador (actor externo)* y *Sistema de Gestión Hípica - Hipódromo B.H.R.*
- **Dos Lanes** dentro del Pool del Hipódromo: *Plataforma Web / Sistema (Automatizado)* y *Secretaría Hípica (Interno)*.
- **Tres flujos de mensaje** entre Pools: solicitud de inscripción, listado de inscriptos y confirmación de ejemplares.
- **Compuertas exclusivas** para las excepciones del proceso: datos incompletos, rechazo veterinario y confirmar/borrar.

![Diagrama BPMN](docs/diagrama-bpmn.png)

## Historias de Usuario

Gestionadas como Issues del repositorio y seguidas en el tablero (Por Hacer / En Progreso / Listo):

| Historia | Descripción | Issue |
|---|---|---|
| HU1 | Autogestión e Inscripción Web de SPC | [#2](https://github.com/nicolasldistefano-collab/hipodromo-bhr-org-empresarial/issues/2) |
| HU2 | Ratificación y Depuración de Inscriptos / Forfait | [#3](https://github.com/nicolasldistefano-collab/hipodromo-bhr-org-empresarial/issues/3) |
| HU3 | Confección Automatizada del Programa Oficial | [#4](https://github.com/nicolasldistefano-collab/hipodromo-bhr-org-empresarial/issues/4) |

## Dinámica de Versionado

- **`main`:** rama estable con la documentación y los artefactos finales.
- **`feature/modelado-bpmn`:** rama secundaria usada para el diseño y la carga de los diagramas BPMN y la matriz de datos.
- **Commits descriptivos** con convención clara (por ejemplo: `docs: añade diagrama BPMN, matriz de datos y especificaciones del flujo`).
- **Pull Request #1:** *Merge feature/modelado-bpmn into main*, con revisión de cambios y verificación de ausencia de conflictos.


## Indicadores de Control (KPIs)

| Indicador | Objetivo |
|---|---|
| Tasa de errores de transcripción manual en anotaciones | Cercana a 0% gracias a la validación en tiempo real del formulario web |
| Tiempo de confección del programa oficial | Menos de 3 minutos tras el cierre del período de depuración |
| Tasa de adopción digital por parte de entrenadores | Al menos 85% para la tercera reunión hípica posterior al lanzamiento |

## Declaración de Uso de Inteligencia Artificial

Se utilizaron asistentes de IA (**Gemini** y **Claude**) como soporte metodológico y de consulta, no como autores del trabajo. A continuación se detallan los prompts principales, su justificación y las correcciones humanas efectuadas sobre los resultados.

> Esta declaración corresponde a la Entrega N° 4. El uso de IA en las entregas 1, 2 y 3 (Gemini) se declara en cada sección del informe.

### Prompts utilizados y justificación

#### Gemini (Entrega N° 4: BPMN, backlog ágil y control)

**Prompt 1: Modelado de Procesos de Negocio (BPMN)**
> "Necesito mapear el proceso de inscripción y confección del programa oficial usando la notación estándar BPMN. Estructurá el diagrama en un Pool ('Sistema de Gestión Hípica') con 3 Lanes ('Entrenador', 'Plataforma Web / Sistema' y 'Secretaría Hípica'). Organizá el flujo en 3 fases (Inscripción, Depurados/Ratificación y Programa Oficial), incluyendo compuertas exclusivas de decisión para datos incompletos y borrado de inscriptos."

*Justificación y corrección:* se usó para partir de una estructura de fases y compuertas. El resultado se corrigió: el Entrenador pasó de Lane a Pool propio con flujos de mensaje, y se agregaron el rechazo veterinario, la validación previa a la compuerta y los eventos de inicio y fin.

**Prompt 2: Backlog Ágil e Historias de Usuario**
> "Redactá 3 Historias de Usuario en formato formal ('Como [rol], quiero [funcionalidad], para [beneficio]') para gestionar en un tablero de GitHub Projects. Las historias deben cubrir: 1) Autogestión de inscripción web por el entrenador, 2) Ratificación/Depuración de ejemplares (forfait), y 3) Confección automatizada de la grilla del programa oficial por la Secretaría."

*Justificación y corrección:* se usó para garantizar el formato formal exigido por la consigna.

**Prompt 3: Indicadores Clave de Desempeño (KPIs)**
> "Definí 3 indicadores clave de desempeño (KPIs) para auditar el éxito operativo del sistema tras su lanzamiento. Incluí métricas para medir la reducción de errores de transcripción manual (0%), el tiempo de procesamiento automático del borrador del programa oficial (< 3 minutos) y la tasa de adopción digital por parte de los entrenadores (> 85%)."

*Justificación y corrección:* se usó para obtener indicadores medibles alineados con las metas del proyecto. El objetivo de 0% de errores se ajustó a "cercana a 0%" por considerarlo poco realista como valor absoluto.

#### Claude (revisión de coherencia y ajuste del diagrama de la Entrega N° 4)

| Prompt (resumen fiel de la consulta) | Propósito | Justificación |
|---|---|---|
| Se adjuntó el informe completo y se pidió revisar si tenía coherencia y si la conclusión estaba bien | Revisión crítica del trabajo | Detectar inconsistencias entre entregas y contra las consignas |
| Se consultó cómo separar al Entrenador del resto del proceso en el BPMN | Cumplir el requisito de Pools para actores externos | Entender la regla de notación (flujos de mensaje entre Pools) y aplicarla en Bizagi |
| Se enviaron capturas del diagrama preguntando qué más corregir | Revisión iterativa del diagrama | Verificar validez de la notación y coherencia con el texto |
| Se consultó si los carriles podían tener eventos de inicio propios | Mejorar la lógica del proceso | Evaluar un disparador para el Hipódromo ("Inscripciones Abiertas") |
| Se pidió redactar la descripción del flujo y un borrador del README | Alinear texto, diagrama y repositorio | Mantener consistencia entre el informe y el README; ambos fueron luego ajustados por el autor |

### Correcciones humanas efectuadas sobre los resultados

- **Pools y Lanes:** el primer diagrama tenía al Entrenador como Lane dentro del mismo Pool. Se lo separó en un Pool propio, comunicado mediante flujos de mensaje, como exige la notación para actores externos.
- **Validación sanitaria:** se incorporó el rechazo veterinario al flujo para mantener coherencia con la Entrega 1 y con las metas de la Entrega 2.
- **Orden lógico:** la validación pasó a ocurrir antes de la compuerta de decisión.
- **Eventos:** se agregaron el evento de inicio "Inscripciones Abiertas" y el evento de fin "Confirmación enviada".
- **KPI:** el objetivo de 0% de errores se ajustó a "cercana a 0%" por realismo.
- **Control final:** todo el contenido fue revisado y adaptado por el integrante del proyecto, quien asume la responsabilidad intelectual y técnica del resultado.