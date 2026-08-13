# Análisis de Marketing y Comportamiento de Usuarios — Showz 2017-2018
Showz invierte $329,131 en marketing pero no sabe qué canales realmente funcionan. El canal que consume el 42.9% del presupuesto genera el ROMI más bajo del período, mientras el más rentable recibe una fracción mínima de inversión. Este análisis identifica dónde está el dinero mal asignado y qué hacer al respecto.

### Herramientas y tipo de proyecto
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/MATPLOTLIB-blue?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/SEABORN-blue?style=for-the-badge)
![Limpieza de Datos](https://img.shields.io/badge/LIMPIEZA_DE_DATOS-blue?style=for-the-badge)
![Transformación de Datos](https://img.shields.io/badge/TRANSFORMACI%C3%93N_DE_DATOS-blue?style=for-the-badge)
![Análisis de Datos](https://img.shields.io/badge/AN%C3%81LISIS_DE_DATOS-blue?style=for-the-badge)
![Visualización de Datos](https://img.shields.io/badge/VISUALIZACI%C3%93N_DE_DATOS-blue?style=for-the-badge)
![Análisis de Cohortes](https://img.shields.io/badge/AN%C3%81LISIS_DE_COHORTES-blue?style=for-the-badge)
![Métricas de Negocio](https://img.shields.io/badge/M%C3%89TRICAS_DE_NEGOCIO-blue?style=for-the-badge)


## Preguntas clave:
1. ¿Cómo interactúan los usuarios con la plataforma y cuánto tiempo tardan en convertir?
2. ¿Cuándo y cuánto compran — existe estacionalidad relevante?
3. ¿Qué canales de marketing generan mayor retorno sobre la inversión?
4. ¿Qué cohortes de usuarios generan mayor valor de vida (LTV)?

## Metodología
Se analizaron registros de visitas, órdenes y gasto en marketing del período junio 2017 — mayo 2018. Se eliminaron sesiones mayores a 30 minutos (7.76% del total) por representar navegadores abandonados más que comportamiento real de compra. Se usó la mediana como métrica central en distribuciones con sesgo positivo. El análisis de cohortes permitió rastrear el comportamiento de cada grupo de usuarios a lo largo del tiempo. Se calcularon métricas clave de negocio: CAC, ROMI y LTV por fuente de adquisición y cohorte.

Nota: El dataset no cubre el período completo — los primeros y últimos meses pueden mostrar valores atípicos por datos parciales. Las tendencias de inicio y cierre deben interpretarse con cautela.
## Insights clave:
1. **El usuario de Showz llega con intención de compra.** El 67.9% convierte el mismo día de su primera visita y el tiempo mediano hasta la primera compra es de 0 días. Sin embargo, la media de 17.42 días revela un segmento que tarda considerablemente más — oportunidad directa para campañas de retargeting.
2. **La tasa de conversión del 14.62% supera ampliamente al ecommerce general (1-4%).** Pero más visitas no garantizan más conversiones: noviembre de 2017 fue el mes de mayor actividad y no coincidió con el pico de conversión, lo que indica que el volumen de tráfico y la calidad de ese tráfico son variables independientes.
3. **La estacionalidad navideña es el evento más predecible del año.** Diciembre 2017 registró el pico de ventas y la cohorte de septiembre 2017 mostró un salto notable en su tercer mes de vida — que corresponde exactamente a diciembre. El equipo de marketing debería preparar campañas con anticipación a ese período.
4. **La retención cae drásticamente después del primer mes.** Las tasas pasan de 13-15% en el mes 0 a menos del 2% en los meses siguientes para todas las cohortes. Showz opera con una base principalmente transaccional — la mayoría compra una sola vez y no regresa.
5. **El hallazgo más crítico:** la fuente 3 es la más cara y la menos rentable.

   | Fuente | Inversión | CAC | ROMI |
   |----|----|----|----|
   | Fuente 3 | $141,321 (42.9%) | 10.21 | 1.10 |
   | Fuente 1 | $20,833 | 2.92 | 109.31 |
   | Fuente 9 | Reducida | 1.98 | 5.59 |
   | Fuente 7 |	Con costos | - | 0 compradores |

*La fuente 1 genera 99x más retorno que la fuente 3 con una fracción del presupuesto.*

## Recomendaciones estratégicas:
1. **Reasignar presupuesto de fuente 3 hacia fuente 1 de forma gradual** — es el cambio de mayor impacto inmediato en rentabilidad sin aumentar el gasto total.
2. **Investigar fuentes 6 y 7 antes de renovar cualquier inversión** — la fuente 7 registra costos sin compradores asociados y la fuente 6 no tiene registros en el período.
3. **Incrementar gradualmente la inversión en fuente 9** — mejor rendimiento que fuentes con presupuesto similar, con margen de escalabilidad sin explorar.
4. **Concentrar mayor inversión entre septiembre y diciembre para aprovechar la estacionalidad identificada** — el dato de la cohorte de septiembre confirma que ese período tiene multiplicador natural de LTV.
5. **Diseñar campaña de retargeting para el 32.1% que no convierte el primer día** — este segmento tiene intención demostrada pero necesita un empujón adicional.
6. **Implementar estrategia de reactivación justo antes del punto de estancamiento por cohorte** — los datos muestran períodos claros donde el LTV deja de crecer, que son la ventana ideal para intervenir.


## Diccionario de datos

El análisis integra tres fuentes de datos del período junio 2017 — mayo 2018:

**Tabla `visits` — registros de sesiones en el sitio web:**
- `Uid` — identificador único del usuario
- `Device` — dispositivo usado durante la sesión
- `Start Ts` — fecha y hora de inicio de sesión (formato AAAA-MM-DD)
- `End Ts` — fecha y hora de término de sesión (formato AAAA-MM-DD)
- `Source Id` — identificador de la fuente de anuncios de origen

**Tabla `orders` — datos sobre pedidos:**
- `Uid` — identificador único del usuario que realiza el pedido
- `Buy Ts` — fecha y hora del pedido
- `Revenue` — ingreso generado por el pedido

**Tabla `costs` — datos sobre gasto en marketing:**
- `source_id` — identificador de la fuente de anuncios
- `dt` — fecha del gasto
- `costs` — inversión del día en esa fuente de anuncios

## Cómo reproducir el análisis

```bash
git clone https://github.com/sgcuervo/showz-marketing-analysis

cd showz-marketing-analysis

pip install -r requirements.txt

jupyter notebook notebooks/analysis.ipynb
```
