```mermaid
graph TD
    %% Nodos
    A([Inicio: Empleado ingresa a Mis Vacaciones])
    B{Tiene fecha de ingreso y saldo según LCT?}
    C[El sistema calcula días y alerta si es menos de 7 días o si es temporada alta]
    D[Envía Solicitud de Vacaciones]
    
    E([Responsable de Sector recibe solicitud])
    F{Supera el cupo máximo de ausencias del sector?}
    G[ALERTA: Se compromete la operación]
    H{Decisión de Jefatura}
    
    I[Rechaza Solicitud]
    J[Modifica Fechas]
    K[Aprueba Solicitud Justifica si es menos de 7 días]
    
    L([Capital Humano recibe solicitud aprobada])
    M{Cumple alternancia Verano / Invierno?}
    N[ALERTA: Tuvo verano el año pasado]
    O[Genera e Imprime Planilla Oficial]
    P[Firma de puño y letra Empleado + Jefe]
    Q[Se archiva en Legajo físico Estado: ARCHIVADO]
    
    R([IMPACTO OPERATIVO INMEDIATO])
    S[Diagramación: Conductor bloqueado para asignación en esas fechas]
    T[Taller: Mecánico excluido de controles matutinos]
    
    U([Administración y Finanzas])
    V[Exporta reporte mensual CSV]
    W([FIN: Vacaciones Liquidadas])

    %% Conexiones
    A --> B
    B -- No --> Z1([Fin: Contactar RRHH])
    B -- Sí --> C
    C --> D
    
    D --> E
    E --> F
    F -- Sí --> G
    G --> H
    F -- No --> H
    
    H -- Rechazar --> I
    I --> Z2([Fin del proceso])
    
    H -- Proponer nuevas fechas --> J
    J -. El empleado debe aceptar .-> A
    
    H -- Aprobar --> K
    K --> L
    
    L --> M
    M -- No --> N
    N --> O
    M -- Sí --> O
    O --> P
    P --> Q
    
    Q ==> R
    R ==> S
    R ==> T
    
    Q --> U
    U --> V
    V --> W

    %% Estilos (Aplicados por clases separadas para compatibilidad con GitHub)
    class A,B,C,D empleado;
    class E,F,G,H,I,J,K jefe;
    class L,M,N,O,P,Q rrhh;
    class R,S,T operacion;
    class U,V,W finanzas;

    classDef empleado fill:#e0f2fe,stroke:#0284c7,stroke-width:2px,color:#0f172a;
    classDef jefe fill:#dcfce7,stroke:#16a34a,stroke-width:2px,color:#0f172a;
    classDef rrhh fill:#fef3c7,stroke:#d97706,stroke-width:2px,color:#0f172a;
    classDef operacion fill:#fee2e2,stroke:#dc2626,stroke-width:2px,color:#0f172a;
    classDef finanzas fill:#f3e8ff,stroke:#9333ea,stroke-width:2px,color:#0f172a;
