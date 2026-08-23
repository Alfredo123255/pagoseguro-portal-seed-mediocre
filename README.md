# PagoSeguro — Portal de Estado de Transacciones (repo semilla `mediocre`)

Aplicación de una sola vista donde un comercio afiliado consulta el estado de sus
transacciones del día. Este repositorio trae **40 días de historial
de despliegues ya sembrado** para que puedas calcular métricas DORA sin esperar semanas.

## Estructura

- `app/index.html` — el portal.
- `.github/workflows/deploy.yml` — el pipeline (léelo: es material del Bloque 3).
- `deployments.csv` — **el ledger de despliegues.** Cada fila es una corrida del
  pipeline a producción, con su resultado. Es tu fuente de datos para DORA.
- `.nvmrc`, `package.json` — runtime e instalación fijados en el repo.

## De dónde salen las métricas

No mires la pestaña *Actions* para el historial: esos runs solo existirán cuando
**tú** hagas push. El historial sembrado vive en dos lugares que se cruzan entre sí:

| Fuente | Qué te da |
|---|---|
| `git log` (fechas de commit reales y retroactivas) | cuándo se creó cada cambio |
| `deployments.csv` (ledger) | cuándo se desplegó, si pasó o falló, y cuándo se restauró |

Verifica que concuerdan: la columna `commit_sha` del ledger existe en `git log`,
y `commit_time` coincide con la fecha de ese commit.

## Tu tarea

Con `deployments.csv` (y `git log` para cruzar), calcula **cuatro** indicadores del
proceso de despliegue de los últimos 40 días. Propón tú los nombres
y las fórmulas. Los formalizamos en el debrief.

> Pista de arranque: dos de los cuatro se responden solo contando filas del ledger.
> Los otros dos necesitan restar dos fechas.

Cuando termines, haz **tu propio** deploy (Bloque 3). Ese es el dato número
26, y ese sí aparece en la pestaña Actions con su hora real.
