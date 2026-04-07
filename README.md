# Registro Gestión — Control Horario

Sistema de control horario para empresas vinculadas a Registros de la Propiedad. Cumple con **RDL 8/2019 (art. 34.9 ET)**, **RGPD (UE 2016/679)** y **LOPDGDD**.

Aplicación React de archivo único, sin backend, con datos de demo precargados (31 usuarios, fichajes, vacaciones, solicitudes, horas extra).

## Características

- 3 roles: **Administrador**, **Responsable**, **Usuario**
- Fichaje en tiempo real con doble timestamp anti-fraude
- Gestión de vacaciones con pools por año
- Solicitudes de incidencias configurables (12 tipos por defecto del convenio)
- Plan vacacional tipo Gantt con detección de solapamientos
- Dashboard con 4 tipos de gráficos (barras H/V, circular, tabla)
- Horas extra y compensaciones
- Sistema de mensajes obligatorios bloqueantes
- Gestión de usuarios y pools vacacionales
- Configuración de tipos de incidencia y override por usuario
- Calendario laboral con festivos
- Importación/exportación CSV (BOM UTF-8) y backup JSON
- Control de accesos con log completo

## Stack

- React 18 + Vite
- Sin dependencias externas de UI (todo SVG inline)
- Estado en memoria React (sin localStorage)

## Desarrollo local

```bash
npm install
npm run dev
```

Abre `http://localhost:5173`.

## Build de producción

```bash
npm run build
```

El resultado se genera en `dist/`.

## Credenciales demo

| Rol | Email | Contraseña |
|-----|-------|------------|
| Administrador | `admin@registro.es` | `admin123` |
| Responsable | `maria.garcia@registro.es` | `resp123` |
| Usuario | `carlos.lopez@registro.es` | `user123` |

Otros responsables: `javier.sanchez@registro.es`, `elena.torres@registro.es`, `roberto.jimenez@registro.es`.

## Despliegue en Vercel

### Opción A — desde GitHub (recomendado)

1. Crea un repositorio nuevo en GitHub.
2. Sube este proyecto:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/registro-gestion.git
   git push -u origin main
   ```
3. Entra en [vercel.com](https://vercel.com) y pulsa **Add New → Project**.
4. Importa el repositorio. Vercel detecta automáticamente Vite.
5. Pulsa **Deploy**. En ~1 minuto tendrás la URL pública.

### Opción B — Vercel CLI

```bash
npm install -g vercel
vercel
```

Sigue las instrucciones interactivas. La configuración automática para Vite funciona sin tocar nada.

## Despliegue en otros hosts

Cualquier host que sirva estáticos vale (Netlify, Cloudflare Pages, GitHub Pages):

```bash
npm run build
# Sube la carpeta dist/
```

Para **GitHub Pages**, añade `base: "/nombre-del-repo/"` en `vite.config.js`.

## Avisos importantes

- El sistema **no persiste datos** al recargar (estado en memoria). Para persistencia real se necesita un backend.
- Las credenciales usan hash básico (`btoa`), solo válido para demo. **No usar en producción** sin backend con bcrypt o equivalente.
- El `serverTime` del sistema anti-fraude se ejecuta en el cliente; en producción debe venir del backend.
- Los festivos no se descuentan aún del cálculo de días laborables (mejora pendiente).

## Licencia

Proyecto base privado. Adaptar a las necesidades del cliente.
