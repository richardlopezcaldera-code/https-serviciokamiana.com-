# Graph Report - .  (2026-07-16)

## Corpus Check
- Corpus is ~5,375 words - fits in a single context window. You may not need a graph.

## Summary
- 33 nodes · 41 edges · 5 communities
- Extraction: 88% EXTRACTED · 12% INFERRED · 0% AMBIGUOUS · INFERRED: 5 edges (avg confidence: 0.76)
- Token cost: 0 input · 78,184 output

## Community Hubs (Navigation)
- PDF Engine & App Shell
- Sales & Order Pipeline
- App Core & Navigation
- Auth, Roles & Users
- Catalog & Datasheets

## God Nodes (most connected - your core abstractions)
1. `PDF Engine (membrete Kamiana)` - 6 edges
2. `Cotizaciones (Quotes) View & Model` - 5 edges
3. `Pedidos (Orders) View & Model` - 5 edges
4. `Kamiana CRM Pro (SPA)` - 4 edges
5. `Auth & Permissions (doLogin/hasPerm/ROLES)` - 4 edges
6. `Productos (Catalog) View & Model` - 4 edges
7. `Role Model (admin/gerente/vendedor/bodega/lector)` - 3 edges
8. `DB_USERS data model` - 3 edges
9. `App State (S) & re() render loop` - 3 edges
10. `Clientes (Customers) View & Model` - 3 edges

## Surprising Connections (you probably didn't know these)
- `Kamiana Repository README` --references--> `Kamiana CRM Pro (SPA)`  [INFERRED]
  README.md → kamiana-crm-pro (1).html

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **CRM Module Views Navigation Flow** — kamiana_crm_pro_1_dashboard, kamiana_crm_pro_1_cotizaciones, kamiana_crm_pro_1_pedidos, kamiana_crm_pro_1_clientes, kamiana_crm_pro_1_ventas, kamiana_crm_pro_1_cobranza, kamiana_crm_pro_1_productos, kamiana_crm_pro_1_proveedores, kamiana_crm_pro_1_fichas, kamiana_crm_pro_1_rutas, kamiana_crm_pro_1_usuarios [EXTRACTED 1.00]
- **Quote-to-Order-to-Collection Flow** — kamiana_crm_pro_1_cotizaciones, kamiana_crm_pro_1_pedidos, kamiana_crm_pro_1_cobranza, kamiana_crm_pro_1_cottoped [INFERRED 0.85]
- **Kamiana PDF Generation System** — kamiana_crm_pro_1_pdf_engine, kamiana_crm_pro_1_pdfcotizacion, kamiana_crm_pro_1_pdfpedido, kamiana_crm_pro_1_pdfficha, kamiana_crm_pro_1_jspdf [EXTRACTED 1.00]

## Communities (5 total, 0 thin omitted)

### Community 0 - "PDF Engine & App Shell"
Cohesion: 0.25
Nodes (9): Kamiana CRM Pro (SPA), Servicio Kamiana SPA (EMP company data), exportProductosCSV() export, Google Fonts (Inter, JetBrains Mono), jsPDF + AutoTable (CDN), PDF Engine (membrete Kamiana), pdfCotizacion() generator, pdfPedido() generator (+1 more)

### Community 1 - "Sales & Order Pipeline"
Cohesion: 0.36
Nodes (8): Clientes (Customers) View & Model, Cobranza (Collections) View & Model, Cotizaciones (Quotes) View & Model, cotToPed() quote-to-order conversion, Oportunidades (Deals) data model, Pedidos (Orders) View & Model, Rutas (Routes) View & Model, Pipeline Ventas (Opportunities) View

### Community 2 - "App Core & Navigation"
Cohesion: 0.29
Nodes (7): Dashboard View, In-memory DB store, nav() permission-gated router, renderModal() dispatcher, Sidebar Navigation, App State (S) & re() render loop, Toast notification system

### Community 3 - "Auth, Roles & Users"
Cohesion: 0.60
Nodes (5): Auth & Permissions (doLogin/hasPerm/ROLES), DB_USERS data model, Login / Access Screen, Role Model (admin/gerente/vendedor/bodega/lector), Usuarios (User Management) View

### Community 4 - "Catalog & Datasheets"
Cohesion: 0.67
Nodes (4): Fichas Tecnicas (Datasheets) View & Model, pdfFicha() generator, Productos (Catalog) View & Model, Proveedores (Suppliers) View & Model

## Knowledge Gaps
- **5 isolated node(s):** `Kamiana Repository README`, `Login / Access Screen`, `Dashboard View`, `Google Fonts (Inter, JetBrains Mono)`, `Toast notification system`
  These have ≤1 connection - possible missing edges or undocumented components.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `PDF Engine (membrete Kamiana)` connect `PDF Engine & App Shell` to `Catalog & Datasheets`?**
  _High betweenness centrality (0.185) - this node is a cross-community bridge._
- **Why does `Cotizaciones (Quotes) View & Model` connect `Sales & Order Pipeline` to `PDF Engine & App Shell`, `Catalog & Datasheets`?**
  _High betweenness centrality (0.118) - this node is a cross-community bridge._
- **Why does `Pedidos (Orders) View & Model` connect `Sales & Order Pipeline` to `PDF Engine & App Shell`?**
  _High betweenness centrality (0.100) - this node is a cross-community bridge._
- **What connects `Kamiana Repository README`, `Login / Access Screen`, `Dashboard View` to the rest of the system?**
  _5 weakly-connected nodes found - possible documentation gaps or missing edges._