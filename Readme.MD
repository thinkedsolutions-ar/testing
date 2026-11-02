```mermaid
graph TD
    %% Estilos
    classDef empleado fill:#e0f2fe,stroke:#0284c7,stroke-width:2px,color:#0f172a;
    classDef jefe fill:#dcfce7,stroke:#16a34a,stroke-width:2px,color:#0f172a;
    classDef rrhh fill:#fef3c7,stroke:#d97706,stroke-width:2px,color:#0f172a;
    classDef operacion fill:#fee2e2,stroke:#dc2626,stroke-width:2px,color:#0f172a;
    classDef finanzas fill:#f3e8ff,stroke:#9333ea,stroke-width:2px,color:#0f172a;

    %% Nodos
    A([Inicio: Empleado ingresa a 'Mis Vacaciones']) ::: empleado
    B{¿Tiene fecha de ingreso<br>y saldo según LCT?} ::: empleado
    C[El sistema calcula días y alerta<br>si es <7 días o si es temporada alta] ::: empleado
    D[Envía Solicitud de Vacaciones] ::: empleado
    
    E([Responsable de Sector recibe solicitud]) ::: jefe
    F{¿Supera el cupo máximo<br>de ausencias del sector?} ::: jefe
    G[ALERTA: Se compromete la operación] ::: jefe
    H{Decisión de Jefatura} ::: jefe
    
    I[Rechaza Solicitud] ::: jefe
    J[Modifica Fechas] ::: jefe
    K[Aprueba Solicitud<br>Justifica si es <7 días] ::: jefe
    
    L([Capital Humano recibe solicitud aprobada]) ::: rrhh
    M{¿Cumple alternancia<br>Verano / Invierno?} ::: rrhh
    N[ALERTA: Tuvo verano el año pasado] ::: rrhh
    O[Genera e Imprime Planilla Oficial] ::: rrhh
    P[Firma de puño y letra<br>Empleado + Jefe] ::: rrhh
    Q[Se archiva en Legajo físico<br>Estado: ARCHIVADO] ::: rrhh
    
    R([IMPACTO OPERATIVO INMEDIATO]) ::: operacion
    S[Diagramación: Conductor bloqueado<br>para asignación en esas fechas] ::: operacion
    T[Taller: Mecánico excluido<br>de controles matutinos] ::: operacion
    
    U([Administración y Finanzas]) ::: finanzas
    V[Exporta reporte mensual CSV] ::: finanzas
    W([FIN: Vacaciones Liquidadas]) ::: finanzas

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
