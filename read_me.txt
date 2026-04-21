Proyecto: Identificación de operadores ineficaces (CallMeMaybe)

Este directorio contiene los archivos generados por el notebook "Operadores_ineficaces_CallMeMaybe.ipynb", así como los datos originales y procesados.

Estructura de archivos:
- data/telecom_dataset_new.csv  (datos brutos de llamadas)
- data/telecom_clients.csv      (datos brutos de clientes)
- data/processed/operators_cleaned.csv   (DataFrame limpio de operadores, con wait_time)
- data/processed/clients_cleaned.csv     (DataFrame limpio de clientes, fechas corregidas)
- ranking_operadores_completo.csv        (todos los operadores ordenados por puntuación de ineficiencia)
- operadores_ineficaces_score_3_o_mas.csv (solo operadores con puntuación >= 3)
- metrics_operadores.csv (métricas agregadas por operador antes del ranking)

El notebook realiza:
- Limpieza y EDA (con ponderación por calls_count)
- Construcción de métricas por operador
- Ranking con 5 reglas de ineficiencia
- Pruebas de hipótesis (Mann-Whitney, Spearman)
- Conclusiones y recomendaciones

Dashboard interactivo en Tableau Public:
[https://public.tableau.com/views/Listadeoperadores-CallMeMaybe/Dashboard2?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link]

El dashboard permite explorar los operadores ineficaces con filtros por puntaje general y particular.

Se agrega una presentación en PDF con los aspectos más relevantes del Análisis.