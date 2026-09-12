# 📋 REGISTRO DE DEUDA TÉCNICA Y BACKLOG — HEH-001 v0.2.5

Este documento consolida la deuda técnica, hallazgos y áreas de optimización identificadas durante el ciclo v0.2.5, transferidas formalmente como insumo para el diseño de **HEH-002**:

| ID | Área | Descripción | Impacto | Destino en HEH-002 |
| :--- | :--- | :--- | :---: | :--- |
| **DEBT-001** | SSR / SSG | Migración progresiva de SPA Vite a Next.js (App Router) para SSR nativo en tiempo real. | Medio | Fase de Expansión HEH-002 |
| **DEBT-002** | Multi-Device SMS | Expansión del gateway SMSGate a doble SIM (Claro + Altice) con balanceo round-robin. | Bajo | Módulo Communication Core |
| **DEBT-003** | RLS Security Audit | Auditoría transversal de directivas RLS en Supabase para evitar caídas silenciosas con anon key. | Alto | Quality Gate HEH-002 |
