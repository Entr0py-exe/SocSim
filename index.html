<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AETHER SIEM - Tabletop Exercise (Cacería de Amenazas)</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
    
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #030712; }
        .terminal-text { font-family: 'JetBrains Mono', monospace; }
        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: #0b0f19; }
        ::-webkit-scrollbar-thumb { background: #1f2937; border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: #374151; }
        
        @keyframes pulse-red {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.4; transform: scale(1.02); }
        }
        .pulse-critical { animation: pulse-red 2s infinite; }
        @keyframes scan-line {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(100%); }
        }
        .radar-scan { position: relative; overflow: hidden; }
        .radar-scan::after {
            content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 4px;
            background: rgba(16, 185, 129, 0.4); animation: scan-line 4s linear infinite;
        }

        @keyframes dash-flow {
            to { stroke-dashoffset: -20; }
        }
        .flow-active { stroke: #ef4444; stroke-dasharray: 5; animation: dash-flow 1s linear infinite; }
        .flow-warning { stroke: #f59e0b; stroke-dasharray: 5; animation: dash-flow 1s linear infinite; }
        .flow-blocked { stroke: #10b981; stroke-dasharray: 2 4; opacity: 0.3; animation: none; }
        .topo-node { transition: all 0.3s ease; }

        @keyframes slide-in-right {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        .toast-enter { animation: slide-in-right 0.4s ease-out forwards; }
    </style>
</head>
<body class="text-slate-100 min-h-screen flex flex-col h-screen overflow-hidden">

    <header class="bg-slate-900 border-b border-slate-800 px-6 py-3 flex flex-wrap items-center justify-between gap-4 shrink-0">
        <div class="flex items-center gap-3">
            <div class="w-10 h-10 bg-indigo-600 rounded-lg flex items-center justify-center shadow-lg shadow-indigo-900/30">
                <i class="fa-solid fa-crosshairs text-xl text-white"></i>
            </div>
            <div>
                <h1 class="text-lg font-bold tracking-wider uppercase text-indigo-400">Aether SIEM</h1>
                <p class="text-xs text-slate-400 terminal-text">THREAT HUNTING EDITION</p>
            </div>
        </div>

        <div class="flex items-center gap-6 bg-slate-950 px-4 py-2 rounded-lg border border-slate-800">
            <div class="text-center">
                <span class="block text-[10px] text-slate-500 uppercase tracking-widest">Fecha Evento</span>
                <span id="sim-date" class="font-bold text-amber-400 terminal-text">Cargando...</span>
            </div>
            <div class="h-8 w-[1px] bg-slate-800"></div>
            <div class="text-center">
                <span class="block text-[10px] text-slate-500 uppercase tracking-widest">Etapa de la Intrusión</span>
                <span id="sim-phase" class="font-bold text-emerald-400 uppercase tracking-wider">Cargando...</span>
            </div>
        </div>

        <div class="flex items-center gap-3">
            <button onclick="advancePhase()" id="btn-next" class="px-4 py-2 bg-indigo-600 hover:bg-indigo-500 text-white font-semibold text-sm rounded shadow-lg shadow-indigo-950/50 transition flex items-center gap-2">
                Avanzar Cronología <i class="fa-solid fa-forward-step"></i>
            </button>
        </div>
    </header>

    <main class="flex-grow flex flex-col p-4 gap-4 overflow-hidden h-full">
        
        <!-- ROW 1: SIEM | DIAGRAMA DE RED | IOCs -->
        <div class="flex-[11] flex flex-col lg:flex-row gap-4 min-h-0 shrink-0">
            
            <!-- COLUMNA IZQUIERDA: FEED DE LOGS (Solo Fase Actual) -->
            <section class="flex-[3] bg-slate-900/65 border border-slate-800 rounded-xl flex flex-col overflow-hidden min-h-0">
                <div class="p-3 border-b border-slate-800 bg-slate-900 flex items-center justify-between shrink-0">
                    <div class="flex items-center gap-2">
                        <span class="w-2 h-2 bg-red-500 rounded-full animate-ping"></span>
                        <h2 class="font-semibold text-slate-200 text-sm">Visor de Logs (SIEM)</h2>
                    </div>
                    <span id="log-count" class="text-[10px] bg-slate-800 text-slate-400 px-2 py-0.5 rounded-full terminal-text">0 Logs</span>
                </div>
                
                <div id="log-feed" class="flex-grow overflow-y-auto p-3 space-y-3 terminal-text text-xs">
                    <!-- Logs Dinámicos -->
                </div>
            </section>

            <!-- COLUMNA CENTRAL: TOPOLOGÍA DE RED EN VIVO -->
            <section class="flex-[6] bg-slate-900/65 border border-slate-800 rounded-xl flex flex-col overflow-hidden min-h-0 radar-scan">
                <div class="p-3 border-b border-slate-800 bg-slate-900 shrink-0">
                    <h2 class="font-semibold text-slate-200 flex items-center gap-2 text-sm">
                        <i class="fa-solid fa-network-wired text-indigo-400"></i> Diagrama de Red e Infraestructura
                    </h2>
                </div>
                
                <!-- Área interactiva de topología -->
                <div class="relative flex-grow bg-slate-950/50 p-2 overflow-hidden flex items-center justify-center">
                    
                    <!-- Enlaces (Líneas SVG) -->
                    <svg class="absolute inset-0 w-full h-full pointer-events-none z-0">
                        <line x1="15%" y1="20%" x2="35%" y2="50%" stroke="#334155" stroke-width="2" id="link-att-waf" class="transition-all duration-300" />
                        <line x1="35%" y1="50%" x2="50%" y2="50%" stroke="#334155" stroke-width="2" id="link-waf-erp" class="transition-all duration-300" />
                        <line x1="50%" y1="50%" x2="85%" y2="20%" stroke="#334155" stroke-width="2" id="link-erp-c2" class="transition-all duration-300" />
                        <line x1="50%" y1="50%" x2="85%" y2="80%" stroke="#334155" stroke-width="2" id="link-erp-int" class="transition-all duration-300" />
                    </svg>

                    <!-- Nodo 1: Atacante Externo -->
                    <div class="absolute left-[15%] top-[20%] -translate-x-1/2 -translate-y-1/2 flex flex-col items-center">
                        <div id="node-attacker" class="topo-node w-10 h-10 bg-slate-900 border-2 border-slate-700 rounded-full flex items-center justify-center text-slate-400 z-10">
                            <i class="fa-solid fa-user-secret text-sm"></i>
                        </div>
                        <span class="text-[9px] mt-1 text-slate-400 font-semibold text-center leading-tight">Threat Actor<br><span class="text-[8px] text-slate-500 terminal-text">WAN</span></span>
                    </div>

                    <!-- Nodo 2: WAF / Perímetro -->
                    <div class="absolute left-[35%] top-[50%] -translate-x-1/2 -translate-y-1/2 flex flex-col items-center">
                        <div id="node-waf" class="topo-node w-10 h-10 bg-slate-900 border-2 border-slate-700 rounded-lg flex items-center justify-center text-slate-400 z-10">
                            <i class="fa-solid fa-shield-halved text-sm"></i>
                        </div>
                        <span class="text-[9px] mt-1 text-slate-400 font-semibold text-center leading-tight">WAF Gateway<br><span class="text-[8px] text-slate-500 terminal-text">DMZ</span></span>
                    </div>

                    <!-- Nodo 3: Servidor ERP Principal -->
                    <div class="absolute left-[50%] top-[50%] -translate-x-1/2 -translate-y-1/2 flex flex-col items-center">
                        <div id="node-erp" class="topo-node w-12 h-12 bg-slate-900 border-2 border-slate-700 rounded-lg flex items-center justify-center text-slate-400 shadow-xl z-10">
                            <i class="fa-solid fa-server text-lg"></i>
                        </div>
                        <span class="text-[9px] mt-1 text-slate-400 font-semibold text-center leading-tight">ERP Server<br><span class="text-[8px] text-slate-500 terminal-text">192.168.10.5</span></span>
                    </div>

                    <!-- Nodo 4: Infraestructura C2 / Exfil -->
                    <div class="absolute left-[85%] top-[20%] -translate-x-1/2 -translate-y-1/2 flex flex-col items-center">
                        <div id="node-c2" class="topo-node w-10 h-10 bg-slate-900 border-2 border-slate-700 rounded-full flex items-center justify-center text-slate-400 z-10">
                            <i class="fa-solid fa-cloud text-sm"></i>
                        </div>
                        <span class="text-[9px] mt-1 text-slate-400 font-semibold text-center leading-tight">Infra C2<br><span class="text-[8px] text-slate-500 terminal-text">Internet</span></span>
                    </div>

                    <!-- Nodo 5: Red Interna -->
                    <div class="absolute left-[85%] top-[80%] -translate-x-1/2 -translate-y-1/2 flex flex-col items-center">
                        <div id="node-internal" class="topo-node w-10 h-10 bg-slate-900 border-2 border-slate-700 rounded-lg flex items-center justify-center text-slate-400 z-10">
                            <i class="fa-solid fa-network-wired text-sm"></i>
                        </div>
                        <span class="text-[9px] mt-1 text-slate-400 font-semibold text-center leading-tight">Red Interna<br><span class="text-[8px] text-slate-500 terminal-text">Subnets</span></span>
                    </div>
                </div>
            </section>

            <!-- COLUMNA DERECHA: IoCs ACUMULADOS -->
            <section class="flex-[3] bg-slate-900/65 border border-slate-800 rounded-xl flex flex-col overflow-hidden min-h-0">
                <div class="p-3 border-b border-slate-800 bg-slate-900 flex justify-between items-center shrink-0">
                    <h3 class="text-xs text-slate-400 uppercase tracking-widest terminal-text font-bold"><i class="fa-solid fa-microscope text-emerald-400 mr-2"></i>IoCs Activos</h3>
                </div>
                <div class="overflow-y-auto p-0 flex-grow">
                    <table class="w-full text-left text-[10px]">
                        <thead class="bg-slate-950/80 text-slate-400 sticky top-0">
                            <tr>
                                <th class="p-2 font-medium">Valor</th>
                                <th class="p-2 font-medium text-right">Intel</th>
                            </tr>
                        </thead>
                        <tbody id="ioc-table-body" class="divide-y divide-slate-800/50">
                            <!-- IoCs dinámicos -->
                        </tbody>
                    </table>
                </div>
            </section>
        </div>

        <!-- ROW 2: NARRATIVA E INTELIGENCIA + PLAYBOOK -->
        <div class="flex-[9] flex flex-col lg:flex-row gap-4 min-h-0 shrink-0">
            
            <!-- NARRATIVA Y CONTEXTO -->
            <section class="flex-[8] bg-slate-900/65 border border-slate-800 rounded-xl flex flex-col overflow-hidden min-h-0">
                <div class="p-3 border-b border-slate-800 bg-slate-900 shrink-0">
                    <h3 class="text-sm text-slate-200 font-bold"><i class="fa-solid fa-brain text-indigo-400 mr-2"></i>Evaluación de Inteligencia (Narrativa)</h3>
                </div>
                <div class="p-4 text-sm text-slate-300 leading-relaxed overflow-y-auto flex-grow" id="intelligence-brief">
                    <!-- Dinámico -->
                </div>
                <div class="bg-amber-950/30 border-t border-amber-900/50 p-3 flex items-start gap-3 shrink-0">
                    <i class="fa-solid fa-lightbulb text-amber-400 mt-0.5"></i>
                    <div>
                        <span class="text-xs font-bold text-amber-400 uppercase tracking-wider block mb-1">Pista de Cacería (Hint)</span>
                        <span class="text-xs text-amber-200/80" id="phase-hint">Cargando pista...</span>
                    </div>
                </div>
            </section>

            <!-- PLAYBOOKS -->
            <section class="flex-[4] bg-slate-900/65 border border-slate-800 rounded-xl flex flex-col overflow-hidden min-h-0">
                <div class="p-3 border-b border-slate-800 bg-slate-900 shrink-0">
                    <h2 class="font-semibold text-slate-200 flex items-center gap-2 text-sm">
                        <i class="fa-solid fa-clipboard-list text-blue-500"></i> Decisiones del Playbook
                    </h2>
                </div>
                
                <div class="flex-grow overflow-y-auto p-3 space-y-2" id="playbook-actions">
                    <!-- Se generan dinámicamente vía JS -->
                </div>
            </section>
        </div>
    </main>

    <footer class="bg-slate-950 border-t border-slate-800 px-6 py-4 grid grid-cols-1 md:grid-cols-4 gap-4 items-center shrink-0">
        <div class="flex items-center gap-4">
            <div class="w-10 h-10 rounded bg-emerald-950 border border-emerald-800 flex items-center justify-center">
                <i class="fa-solid fa-server text-emerald-400"></i>
            </div>
            <div class="flex-grow">
                <div class="flex justify-between text-xs font-semibold mb-1">
                    <span>Integridad de Operaciones</span>
                    <span id="metric-integrity" class="text-emerald-400 terminal-text">100%</span>
                </div>
                <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                    <div id="bar-integrity" class="bg-emerald-500 h-full transition-all duration-500" style="width: 100%;"></div>
                </div>
            </div>
        </div>

        <div class="flex items-center gap-4">
            <div class="w-10 h-10 rounded bg-rose-950 border border-rose-900 flex items-center justify-center">
                <i class="fa-solid fa-file-export text-rose-400"></i>
            </div>
            <div class="flex-grow">
                <div class="flex justify-between text-xs font-semibold mb-1">
                    <span>Datos Exfiltrados</span>
                    <span id="metric-leakage" class="text-rose-400 terminal-text">0%</span>
                </div>
                <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                    <div id="bar-leakage" class="bg-rose-500 h-full transition-all duration-500" style="width: 0%;"></div>
                </div>
            </div>
        </div>

        <div class="flex items-center gap-4">
            <div class="w-10 h-10 rounded bg-blue-950 border border-blue-900 flex items-center justify-center">
                <i class="fa-solid fa-star text-blue-400"></i>
            </div>
            <div class="flex-grow">
                <div class="flex justify-between text-xs font-semibold mb-1">
                    <span>SLA / Eficiencia</span>
                    <span id="metric-sla" class="text-blue-400 terminal-text">100%</span>
                </div>
                <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                    <div id="bar-sla" class="bg-blue-500 h-full transition-all duration-500" style="width: 100%;"></div>
                </div>
            </div>
        </div>

        <div class="flex justify-end">
            <div class="flex flex-col items-end gap-2">
                <button onclick="exportDebrief()" class="px-3 py-1.5 bg-slate-800 hover:bg-slate-700 text-slate-300 border border-slate-700 rounded text-xs font-semibold shadow transition flex items-center gap-2">
                    <i class="fa-solid fa-download"></i> Exportar Debrief
                </button>
                <div class="text-[10px] text-slate-500 text-right">
                    Aether Security Simulations<br>
                    Tabletop Engine v2.0
                </div>
            </div>
        </div>
    </footer>

    <!-- Modal Alerta/Mensaje Genérico -->
    <div id="msg-modal" class="fixed inset-0 bg-slate-950/90 backdrop-blur-sm items-center justify-center z-50 hidden p-4">
        <div class="bg-slate-900 border border-slate-700 rounded-xl shadow-2xl w-full max-w-md overflow-hidden flex flex-col">
            <div class="p-4 bg-slate-800 border-b border-slate-700 flex justify-between items-center">
                <h3 class="text-md font-bold text-white flex items-center gap-2" id="msg-title">Notificación</h3>
            </div>
            <div class="p-6 text-sm text-slate-300" id="msg-content"></div>
            <div class="p-4 bg-slate-950 border-t border-slate-800 flex justify-end">
                <button onclick="closeModal('msg-modal')" class="px-4 py-2 bg-indigo-600 hover:bg-indigo-500 text-white rounded text-xs font-semibold transition">Entendido</button>
            </div>
        </div>
    </div>

    <!-- Modal Raw Log -->
    <div id="raw-log-modal" class="fixed inset-0 bg-slate-950/90 backdrop-blur-sm items-center justify-center z-50 hidden p-4">
        <div class="bg-slate-900 border border-slate-700 rounded-xl shadow-2xl w-full max-w-2xl overflow-hidden flex flex-col">
            <div class="p-4 bg-slate-800 border-b border-slate-700 flex justify-between items-center">
                <h3 class="text-sm font-bold text-slate-200 flex items-center gap-2"><i class="fa-solid fa-code text-indigo-400"></i> Evento SIEM en crudo (RAW)</h3>
                <button onclick="closeLogDetails()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <div class="p-4 bg-slate-950 text-slate-300 overflow-y-auto max-h-96">
                <pre id="raw-log-content" class="text-[10px] terminal-text whitespace-pre-wrap break-words"></pre>
            </div>
        </div>
    </div>

    <!-- Contenedor de Toasts (Distractores) -->
    <div id="toast-container" class="fixed bottom-20 right-6 z-50 flex flex-col gap-3 pointer-events-none"></div>

    <!-- AUDIO SENSOR PARA EFECTOS DE ALERTA CRÍTICA -->
    <audio id="alert-sound" src="https://assets.mixkit.co/active_storage/sfx/2869/2869-84.wav" preload="auto"></audio>

    <script>
        // ESTADO GLOBAL
        let state = {
            currentPhase: 0,
            integrity: 100,
            leakage: 0,
            sla: 100,
            appliedActions: [],
            revealedIoCs: [],
            phaseLogs: [], // Solo logs de la fase actual
            actionHistory: [] // Registro para el debrief
        };

        // DICCIONARIO DE ACCIONES (Correctas e Incorrectas)
        const allActions = [
            // FASE 1
            { id: "block_post", label: "Bloquear peticiones POST inusuales", desc: "Regla WAF para /PSEMHUB/hub", correct: true, phase: 1 },
            { id: "block_ssrf", label: "Sanitizar Cabeceras (Anti-SSRF)", desc: "Bloquear IPs de loopback en HTTP Headers", correct: true, phase: 1 },
            { id: "restrict_smb", label: "Restringir Tráfico TCP 445 (SMB)", desc: "Cortafuegos de salida en el servidor", correct: true, phase: 1 },
            { id: "reboot_server", label: "Reiniciar el Servidor ERP", desc: "Apagar y encender la máquina", correct: false, phase: 1, penaltyMsg: "¡ERROR GRAVE! Reiniciar la máquina eliminó todos los artefactos de la memoria RAM, impidiendo el análisis forense de la intrusión inicial." },
            
            // FASE 2
            { id: "block_prep_ips", label: "Bloquear IPs del Rango 142.11.200.x", desc: "Añadir a lista negra del Firewall Perimetral", correct: true, phase: 2 },
            { id: "block_all_ext", label: "Bloquear TODO el tráfico saliente", desc: "Aislamiento total perimetral", correct: false, phase: 2, penaltyMsg: "¡DENEGACIÓN DE SERVICIO! Has bloqueado aplicaciones legítimas, causando interrupción masiva a las operaciones de la organización." },
            
            // FASE 3
            { id: "monitor_edr", label: "Incrementar Telemetría EDR", desc: "Activar modo de caza profunda de binarios", correct: true, phase: 3 },
            { id: "reset_all_passwords", label: "Forzar Reseteo de Contraseñas Global", desc: "Obligar a todos los usuarios a cambiar su clave", correct: false, phase: 3, penaltyMsg: "¡DESGASTE OPERATIVO! El atacante tiene acceso nivel sistema a través de una vulnerabilidad de aplicación (RCE) y webshells. Cambiar contraseñas no les quita el acceso, pero genera pánico y saturación en la Mesa de Ayuda." },
            { id: "block_rdp", label: "Bloquear Puerto 3389 (RDP) Interno", desc: "Deshabilitar Escritorio Remoto en la Intranet", correct: false, phase: 3, penaltyMsg: "¡MITIGACIÓN INEFICAZ! Bloqueaste RDP, pero el atacante está utilizando scripts bash (Linux) y preparándose para moverse lateralmente por SSH (Puerto 22). Has desperdiciado tiempo valioso." },
            
            // FASE 4
            { id: "isolate_erp", label: "Aislar Servidor ERP Inmediatamente", desc: "Cuarentena de red vía agente EDR", correct: true, phase: 4 },
            { id: "purge_webshells", label: "Buscar y Purgar Webshells (.jsp)", desc: "Limpiar directorio de la aplicación Java", correct: true, phase: 4 },
            { id: "block_exfil", label: "Bloquear IP Tor de Destino", desc: "Cortar tráfico hacia 176.120.22.24", correct: true, phase: 4 },
            { id: "restore_backup", label: "Restaurar Servidor desde Backup", desc: "Sobrescribir el disco con copia de ayer", correct: false, phase: 4, penaltyMsg: "¡ERROR ESTRATÉGICO! Restauraste el servidor sin parchar la vulnerabilidad ni entender cómo entraron. El atacante te volvió a comprometer en 5 minutos." },
            
            // FASE 6
            { id: "apply_patch", label: "Aplicar Parche de Emergencia del Fabricante", desc: "Actualizar aplicación y deshabilitar módulos afectados", correct: true, phase: 6 },
            { id: "run_full_av_scan", label: "Ejecutar Escaneo Antivirus Completo", desc: "Forzar escaneo profundo en todos los discos", correct: false, phase: 6, penaltyMsg: "¡PÉRDIDA DE TIEMPO! Estás lidiando con una vulnerabilidad de día cero en la arquitectura web (CVE). Un escaneo de antivirus no detectará ni solucionará la falla en el código." },
            { id: "migrate_cloud", label: "Migrar el Servidor a la Nube (AWS/Azure)", desc: "Crear una nueva instancia fuera de on-premise", correct: false, phase: 6, penaltyMsg: "¡FUERA DE ALCANCE! Una migración toma semanas o meses. Además, estarías moviendo un aplicativo vulnerable a otro lugar. Necesitas parchar la vulnerabilidad ahora mismo." }
        ];

        const phaseMetadata = [
            null, // Offset index 0
            {
                title: "Fase 1: Intrusión Inicial y Explotación",
                date: "27 de Mayo, 2026",
                brief: "Se detectan anomalías críticas en el Sistema ERP Principal. El WAF (Web Application Firewall) registra un volumen inusual de peticiones POST hacia endpoints de administración interna. Paralelamente, el cortafuegos perimetral detecta intentos del servidor web de comunicarse hacia internet por un puerto asociado a compartir archivos en red.",
                hint: "Presten atención a los puertos salientes. ¿Por qué un servidor web en la DMZ intentaría iniciar tráfico SMB (TCP 445) hacia una IP externa desconocida? Revisa el payload de las cabeceras HTTP.",
                newIoCs: [
                    { type: "IP Atacante", value: "142.11.200.186" }
                ],
                logs: [
                    { sev: "critical", src: "Gateway WAF", txt: "CRITICAL: Suspicious Inbound POST to /PSEMHUB/hub - Potential SSRF (127.0.0.1 loopback detected in headers)" },
                    { sev: "warning", src: "ERP App Server", txt: "WARNING: High Outbound Traffic Spike on Port TCP 445 (SMB) pointing to 142.11.200.186" },
                    { sev: "info", src: "Network IDS", txt: "INFO: Malformed XML payload detected in HTTP request body." }
                ],
                actionsToShow: ["block_post", "block_ssrf", "restrict_smb", "reboot_server"]
            },
            {
                title: "Fase 2: Preparación de la Infraestructura C2",
                date: "27 de Mayo, 2026 (En progreso)",
                brief: "El atacante ha ganado ejecución de código y ahora busca establecer persistencia. Nuestros sensores pasivos de Threat Intelligence (fuera de la red) detectan que la IP atacante pertenece a un bloque que aloja servidores de staging (archivos expuestos por puerto 8888). Se detectan peticiones SSL desde nuestra red hacia un dominio sospechoso.",
                hint: "Un dominio que se disfraza de servicios legítimos en la nube (ej. Azure, AWS) es un indicador clásico de Comando y Control (C2). Busquen el nombre del ejecutable que están descargando.",
                newIoCs: [
                    { type: "IP C2", value: "142.11.200.187" },
                    { type: "IP C2", value: "142.11.200.188" },
                    { type: "IP C2", value: "142.11.200.189" },
                    { type: "IP C2", value: "142.11.200.190" },
                    { type: "Dominio C2", value: "azurenetfiles.net" },
                    { type: "Hash (meshagent64-azure-ops.exe)", value: "f02a924c9ff92a8780ce812511341182c6b509d45bc59f3f7b522e37225d24fc" },
                    { type: "Hash (meshagent64-v2.exe)", value: "d83fdb9e53c5ff03c4cb0451ea1bebd79b53f29eadc1e2fa394c7af13a86ce2f" },
                    { type: "Hash (meshagent32-azure-ops.exe)", value: "c7e9332731b06644fc73e0046a2a89eaa59b09f54250e9bd622467187351711f" },
                    { type: "Hash (meshagent linux)", value: "68257a6f9ff196179ec03624e849927f26599eb180a7c82e14ef5bc4e93bc309" }
                ],
                logs: [
                    { sev: "warning", src: "Threat Intel", txt: "INTEL: Active staging servers exposed on IPs 142.11.200.186 - 142.11.200.190 (Port 8888)" },
                    { sev: "critical", src: "ERP App Server", txt: "CRITICAL: Outbound HTTPS request initiated to fraudulent domain: azurenetfiles.net" },
                    { sev: "warning", src: "EDR", txt: "EDR_SUSPICIOUS: ACME Client binary detected attempting automatic SSL generation for domain spoofing" }
                ],
                actionsToShow: ["block_prep_ips", "block_all_ext"]
            },
            {
                title: "Fase 3: Verificación de Herramientas",
                date: "29 de Mayo, 2026",
                brief: "Los atacantes están consolidando su posición y preparando herramientas para la fase final. Han comenzado a interactuar directamente con la consola interactiva remota. La telemetría de comandos captura auditorías inusuales realizadas por la cuenta 'root' o de servicio del sistema.",
                hint: "El atacante revisa herramientas de validación de firmas de código ('authenticode'). ¿Por qué querrían saber si pueden manipular firmas digitales en binarios?",
                newIoCs: [],
                logs: [
                    { sev: "info", src: "Host Audit", txt: "AUDIT: Shell cmd triggered by root: 'npm list global authenticode'" },
                    { sev: "warning", src: "EDR", txt: "EDR_DETECTION: Process injection patterns matching known RMM tools observed in memory." }
                ],
                actionsToShow: ["monitor_edr", "reset_all_passwords", "block_rdp"]
            },
            {
                title: "Fase 4: Movimiento Lateral y Exfiltración",
                date: "A principios de Junio 2026",
                brief: "¡FASE CRÍTICA! El atacante ha desplegado webshells para acceso permanente. Un script automatizado se está ejecutando desde el servidor ERP comprometido para descubrir otras máquinas en la subred. Simultáneamente, el tráfico de salida se dispara: están comprimiendo archivos críticos y enviándolos fuera de la red.",
                hint: "Picos de uso de CPU por herramientas de compresión ('zstd') combinados con tráfico saliente masivo hacia IPs desconocidas indican que la exfiltración de datos está ocurriendo EN ESTE MOMENTO. Corta la comunicación o aísla el activo.",
                newIoCs: [
                    { type: "IP Destino Exfil", value: "176.120.22.24" },
                    { type: "Script Malicioso", value: "SRV_ECORP_fanout.sh" },
                    { type: "Archivo/Nota de Rescate", value: "README-IF-YOU-SEE-THIS-YOUVE-BEEN-HACKED.TXT" },
                    { type: "Hash (.bash_history)", value: "2ab684d93c1553fad87041b4dea97188a97e78589deee2a7bacff905564f3a35" }
                ],
                logs: [
                    { sev: "critical", src: "File Integrity", txt: "CRITICAL: Unofficial .jsp Webshell file created inside /PSEMHUB.war/ directory" },
                    { sev: "critical", src: "Internal IPS", txt: "CRITICAL: Lateral Movement! Internal SSH credential spraying from ERP Server to internal subnets via SRV_ECORP_fanout.sh" },
                    { sev: "critical", src: "Network Monitor", txt: "CRITICAL: Large data compression (zstd) followed by massive outbound traffic (40GB) to IP 176.120.22.24" },
                    { sev: "warning", src: "Host Monitor", txt: "WARNING: Extortion marker dropped: README-IF-YOU-SEE-THIS-YOUVE-BEEN-HACKED.TXT" }
                ],
                actionsToShow: ["isolate_erp", "purge_webshells", "block_exfil", "restore_backup"]
            },
            {
                title: "Fase 5: Descubrimiento Público",
                date: "09 de Junio, 2026",
                brief: "La operación se vuelve pública. Un investigador de ciberseguridad independiente publica hallazgos sobre la infraestructura del atacante en la red social X. Peor aún, un conocido cártel cibercriminal actualiza su sitio de la dark web atribuyéndose el robo de datos y amenazando con publicarlos.",
                hint: "El daño técnico ya está hecho; ahora inicia la crisis reputacional y legal. Busca qué actor de amenazas opera típicamente mediante robo de datos en el sector educativo superior y usa tácticas de extorsión directa sin ransomware (Cifrado).",
                newIoCs: [],
                logs: [
                    { sev: "warning", src: "Social Media Intel", txt: "INTEL OSINT: Investigator leaks active C2 infrastructure details. Media panic initiating." },
                    { sev: "critical", src: "Dark Web Monitor", txt: "THREAT: Threat Actor Group (UNC6240) updates Tor leak site (DLS) exposing corporate databases." }
                ],
                actionsToShow: []
            },
            {
                title: "Fase 6: Remediación y Parches",
                date: "10 al 12 de Junio, 2026",
                brief: "Bajo presión de la comunidad, el proveedor del software afectado emite un parche fuera de ciclo (Out-of-Band) para tapar la vulnerabilidad explotada como día-cero. CISA emite una orden directa para parchear inmediatamente.",
                hint: "¡La vulnerabilidad explotada era CVE-2026-35273 en Oracle PeopleSoft! Revisen sus notas para ver cómo todas las pistas (endpoints /PSEMHUB, el componente WebLogic, etc.) encajan en este caso real.",
                newIoCs: [],
                logs: [
                    { sev: "info", src: "Vendor Advisory", txt: "ADVISORY: Emergency out-of-band patch released for Critical RCE vulnerability." },
                    { sev: "info", src: "Gov Alert", txt: "ADVISORY: Vulnerability added to KEV Catalog. Emergency implementation mandatory." }
                ],
                actionsToShow: ["apply_patch", "run_full_av_scan", "migrate_cloud"]
            }
        ];

        function loadPhase(phaseNum) {
            state.currentPhase = phaseNum;
            const phaseData = phaseMetadata[phaseNum];
            
            // UI Updates
            document.getElementById('sim-date').textContent = phaseData.date;
            document.getElementById('sim-phase').textContent = phaseData.title;
            document.getElementById('intelligence-brief').innerHTML = `<p>${phaseData.brief}</p>`;
            document.getElementById('phase-hint').textContent = phaseData.hint;

            // Limpiar logs anteriores y añadir nuevos
            state.phaseLogs = [];
            phaseData.logs.forEach(log => {
                const timestamp = new Date().toISOString().replace('T', ' ').substring(0, 19);
                state.phaseLogs.unshift({ timestamp, sev: log.sev, src: log.src, txt: log.txt });
            });
            renderLogs();

            // Actualizar panel de IoCs
            phaseData.newIoCs.forEach(ioc => {
                if(!state.revealedIoCs.find(i => i.value === ioc.value)) {
                    state.revealedIoCs.push(ioc);
                }
            });
            renderIoCs();

            // Actualizar Playbooks
            renderPlaybooks(phaseData.actionsToShow);

            updateTopology();

            // Sonido de alerta si hay criticos
            if(phaseData.logs.some(l => l.sev === 'critical')) {
                const sound = document.getElementById('alert-sound');
                if(sound) sound.play().catch(()=>{});
            }

            // Si es la última fase, cambiar texto de botón
            if(phaseNum === phaseMetadata.length - 1) {
                const btn = document.getElementById('btn-next');
                btn.innerHTML = 'Finalizar Ejercicio <i class="fa-solid fa-flag-checkered"></i>';
                btn.classList.replace('bg-indigo-600', 'bg-emerald-600');
                btn.classList.replace('hover:bg-indigo-500', 'hover:bg-emerald-500');
            }
        }

        function advancePhase() {
            if (state.currentPhase < phaseMetadata.length - 1) {
                calculatePhasePenalties();
                loadPhase(state.currentPhase + 1);
            } else {
                calculatePhasePenalties();
                showModal("Ejercicio Finalizado", `¡El Tabletop ha terminado!<br><br>
                <strong>Métricas Finales:</strong><br>
                Integridad: ${state.integrity}%<br>
                SLA Respuesta: ${state.sla}%<br>
                Datos Fugas: ${state.leakage}%<br><br>
                Aprovecha este momento para discutir con tu equipo qué acciones tomaron a tiempo y cuáles ignoraron.`);
            }
        }

        function renderPlaybooks(actionIds) {
            const container = document.getElementById('playbook-actions');
            container.innerHTML = '';
            
            if(actionIds.length === 0) {
                container.innerHTML = `<div class="p-3 text-center text-slate-500 text-xs italic">No hay acciones de playbook disponibles para esta fase. Permanezcan atentos.</div>`;
                return;
            }

            const phaseActions = allActions.filter(a => actionIds.includes(a.id));
            
            phaseActions.forEach(act => {
                const isChecked = state.appliedActions.includes(act.id);
                const html = `
                <div class="p-3 bg-slate-950/80 border border-slate-800 rounded-lg hover:border-slate-700 transition">
                    <label class="flex items-start gap-3 cursor-pointer">
                        <input type="checkbox" onchange="toggleAction('${act.id}')" ${isChecked ? 'checked' : ''} class="mt-1 accent-indigo-500">
                        <div>
                            <span class="block text-xs font-semibold text-slate-300">${act.label}</span>
                            <span class="block text-[10px] text-slate-500">${act.desc}</span>
                        </div>
                    </label>
                </div>`;
                container.innerHTML += html;
            });
        }

        function toggleAction(actionId) {
            const actionDef = allActions.find(a => a.id === actionId);
            if (!actionDef) return; // Salvaguarda si la acción no se encuentra

            if (!state.appliedActions.includes(actionId)) {
                state.appliedActions.push(actionId);
                
                // Registrar en historial para debrief
                const now = new Date().toLocaleTimeString();
                state.actionHistory.push({
                    phase: state.currentPhase,
                    time: now,
                    label: actionDef.label,
                    correct: actionDef.correct
                });

                // Penalizaciones inmediatas si elige una acción trampa
                if (actionDef.correct === false) {
                    showModal("🚨 Error Crítico de Procedimiento", `<span class="text-rose-400 font-bold">Has seleccionado una acción perjudicial.</span><br><br>${actionDef.penaltyMsg || 'Acción inválida.'}`);
                    state.integrity = Math.max(0, state.integrity - 20);
                    state.sla = Math.max(0, state.sla - 15);
                    updateMeters();
                }

            } else {
                state.appliedActions = state.appliedActions.filter(a => a !== actionId);
            }
            
            updateTopology();
        }

        function updateTopology() {
            const p = state.currentPhase;
            const actions = state.appliedActions;
            
            const removeColors = (node) => {
                node.classList.remove('border-rose-500', 'bg-rose-950/50', 'text-rose-400', 'border-amber-500', 'bg-amber-950/50', 'text-amber-400', 'border-blue-500', 'bg-blue-950/50', 'text-blue-400', 'animate-pulse', 'border-slate-700', 'bg-slate-900', 'text-slate-400');
            };

            // Restablecer estados de Nodos
            ['node-attacker', 'node-waf', 'node-erp', 'node-internal', 'node-c2'].forEach(id => {
                const node = document.getElementById(id);
                removeColors(node);
                node.classList.add('border-slate-700', 'bg-slate-900', 'text-slate-400');
            });

            // Restablecer estados de Enlaces
            ['link-att-waf', 'link-waf-erp', 'link-erp-c2', 'link-erp-int'].forEach(id => {
                const link = document.getElementById(id);
                link.classList.remove('flow-active', 'flow-warning', 'flow-blocked');
            });

            const setNode = (id, colorClass) => {
                const node = document.getElementById(id);
                removeColors(node);
                if(colorClass === 'rose') node.classList.add('border-rose-500', 'bg-rose-950/50', 'text-rose-400');
                if(colorClass === 'rose-pulse') node.classList.add('border-rose-500', 'bg-rose-950/50', 'text-rose-400', 'animate-pulse');
                if(colorClass === 'amber') node.classList.add('border-amber-500', 'bg-amber-950/50', 'text-amber-400');
                if(colorClass === 'amber-pulse') node.classList.add('border-amber-500', 'bg-amber-950/50', 'text-amber-400', 'animate-pulse');
                if(colorClass === 'blue') node.classList.add('border-blue-500', 'bg-blue-950/50', 'text-blue-400');
                if(colorClass === 'slate') node.classList.add('border-slate-700', 'bg-slate-900', 'text-slate-400');
            };

            const setLink = (id, type) => {
                document.getElementById(id).classList.add(`flow-${type}`);
            };

            // Lógica por Fases
            setNode('node-attacker', 'rose');

            if (p === 1) {
                setLink('link-att-waf', 'warning');
                setLink('link-waf-erp', 'warning');
                setNode('node-waf', 'amber-pulse');
            } else if (p === 2) {
                setNode('node-c2', 'amber');
                setLink('link-erp-c2', 'warning');
                setNode('node-erp', 'amber-pulse');
            } else if (p === 3) {
                setNode('node-erp', 'amber-pulse');
                setNode('node-c2', 'rose');
            } else if (p === 4) {
                setNode('node-c2', 'rose');
                setNode('node-internal', 'rose-pulse');
                setNode('node-erp', 'rose-pulse');
                setLink('link-erp-int', 'active');
                setLink('link-erp-c2', 'active');
            } else if (p >= 5) {
                setNode('node-c2', 'rose-pulse');
                setNode('node-erp', 'rose');
            }

            // Anulaciones por Acciones de Mitigación (Playbooks)
            if (actions.includes('block_prep_ips') && p >= 2) {
                document.getElementById('link-erp-c2').classList.remove('flow-warning', 'flow-active');
                setLink('link-erp-c2', 'blocked');
            }
            if (actions.includes('block_exfil') && p >= 4) {
                document.getElementById('link-erp-c2').classList.remove('flow-warning', 'flow-active');
                setLink('link-erp-c2', 'blocked');
                setNode('node-c2', 'slate');
            }
            if (actions.includes('isolate_erp')) {
                setNode('node-erp', 'blue');
                ['link-waf-erp', 'link-erp-c2', 'link-erp-int'].forEach(id => {
                    document.getElementById(id).classList.remove('flow-warning', 'flow-active');
                    setLink(id, 'blocked');
                });
            }
        }

        function calculatePhasePenalties() {
            // Verificar si faltaron acciones correctas de la fase actual
            const requiredActions = allActions.filter(a => a.phase === state.currentPhase && a.correct === true);
            let missingPenalty = 0;
            
            requiredActions.forEach(req => {
                if(!state.appliedActions.includes(req.id)) {
                    missingPenalty += 10;
                    state.sla -= 5;
                }
            });

            state.integrity = Math.max(0, state.integrity - missingPenalty);

            // Lógica crítica de exfiltración (Fase 4 a 5)
            if (state.currentPhase === 4) {
                if (!state.appliedActions.includes('isolate_erp') && !state.appliedActions.includes('block_exfil')) {
                    state.leakage = 100; // Total compromise
                    state.integrity -= 30;
                } else if (state.appliedActions.includes('block_exfil') && !state.appliedActions.includes('isolate_erp')) {
                    state.leakage = 35; // Partial leakage
                    state.integrity -= 10;
                }
            }

            // Reputación cae en Fase 5 si hubo fuga
            if (state.currentPhase === 5 && state.leakage > 0) {
                state.integrity -= 25;
            }

            updateMeters();
        }

        function updateMeters() {
            document.getElementById('metric-integrity').textContent = `${state.integrity}%`;
            document.getElementById('bar-integrity').style.width = `${state.integrity}%`;
            document.getElementById('metric-leakage').textContent = `${state.leakage}%`;
            document.getElementById('bar-leakage').style.width = `${state.leakage}%`;
            document.getElementById('metric-sla').textContent = `${state.sla}%`;
            document.getElementById('bar-sla').style.width = `${state.sla}%`;

            // Colores
            document.getElementById('bar-integrity').className = `h-full transition-all duration-500 ${state.integrity < 50 ? 'bg-rose-500' : (state.integrity < 80 ? 'bg-amber-500' : 'bg-emerald-500')}`;
            document.getElementById('bar-leakage').className = `h-full transition-all duration-500 ${state.leakage > 50 ? 'bg-rose-600' : (state.leakage > 0 ? 'bg-amber-500' : 'bg-emerald-500')}`;
        }

        function renderLogs() {
            const feed = document.getElementById('log-feed');
            feed.innerHTML = '';
            
            state.phaseLogs.forEach((log, index) => {
                let sevColor = "text-blue-400 bg-blue-950/50 border-blue-900";
                let pulseClass = "";
                if(log.sev === "critical") {
                    sevColor = "text-rose-400 bg-rose-950/80 border-rose-800";
                    pulseClass = "pulse-critical";
                } else if (log.sev === "warning") {
                    sevColor = "text-amber-400 bg-amber-950/80 border-amber-800";
                }

                const logItem = `
                <div onclick="openLogDetails(${index})" class="p-2.5 bg-slate-950 hover:bg-slate-900 rounded-lg border border-slate-850 flex flex-col gap-1.5 cursor-pointer transition ${pulseClass}" title="Haz clic para ver el RAW log">
                    <div class="flex items-center justify-between">
                        <span class="px-2 py-0.5 rounded border text-[10px] font-bold uppercase tracking-wider ${sevColor}">${log.sev}</span>
                        <span class="text-slate-500 text-[10px]">${log.timestamp}</span>
                    </div>
                    <p class="text-slate-300 font-medium">${log.txt}</p>
                    <div class="flex items-center justify-between text-[10px] text-slate-500 border-t border-slate-900/50 pt-1">
                        <span>Origen: ${log.src}</span>
                        <span class="text-indigo-400 flex items-center gap-1"><i class="fa-solid fa-magnifying-glass"></i> RAW</span>
                    </div>
                </div>`;
                feed.innerHTML += logItem;
            });
            document.getElementById('log-count').textContent = `${state.phaseLogs.length} Logs Fase Actual`;
        }

        function renderIoCs() {
            const tbody = document.getElementById('ioc-table-body');
            if(!tbody) return; // Salvaguarda por si el DOM no ha cargado
            tbody.innerHTML = '';
            
            if(state.revealedIoCs.length === 0) {
                tbody.innerHTML = `<tr><td colspan="2" class="p-4 text-center text-slate-500 italic">Sin descubrimientos.</td></tr>`;
                return;
            }

            state.revealedIoCs.forEach(ioc => {
                if(!ioc || !ioc.type || !ioc.value) return; // Salvaguarda de datos inválidos

                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-950/50 transition";
                
                // Determinar si es un archivo/hash/script
                const isFile = ioc.type.includes("Archivo") || ioc.type.includes("Hash") || ioc.type.includes("Script");
                const safeValue = encodeURIComponent(ioc.value);
                
                // Enlace genérico de VirusTotal (Aplica para IPs, Dominios y Hashes)
                let buttons = `<a href="https://www.virustotal.com/gui/search?query=${safeValue}" target="_blank" rel="noopener noreferrer" class="inline-block px-1.5 py-0.5 bg-slate-800 hover:bg-indigo-900 border border-slate-700 hover:border-indigo-700 text-slate-300 hover:text-white text-[9px] rounded transition ml-0.5 text-center" title="Buscar en VirusTotal">VT</a>`;
                
                // Enlace de AbuseIPDB (Solo se muestra si NO es un archivo/hash)
                if (!isFile) {
                    buttons += `<a href="https://www.abuseipdb.com/check/${safeValue}" target="_blank" rel="noopener noreferrer" class="inline-block px-1.5 py-0.5 bg-slate-800 hover:bg-rose-900 border border-slate-700 hover:border-rose-700 text-slate-300 hover:text-white text-[9px] rounded transition ml-0.5 text-center" title="Buscar en AbuseIPDB">IPDB</a>`;
                }

                tr.innerHTML = `
                    <td class="p-2">
                        <span class="block text-emerald-400 terminal-text font-bold truncate max-w-[150px]" title="${ioc.value}">${ioc.value}</span>
                        <span class="block text-[8px] text-slate-500">${ioc.type}</span>
                    </td>
                    <td class="p-2 text-right whitespace-nowrap">
                        ${buttons}
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        function showModal(titleTxt, contentHtml) {
            document.getElementById('msg-title').innerHTML = titleTxt;
            document.getElementById('msg-content').innerHTML = contentHtml;
            document.getElementById('msg-modal').classList.remove('hidden');
            document.getElementById('msg-modal').style.display = 'flex';
        }

        function closeModal(id) {
            document.getElementById(id).classList.add('hidden');
            document.getElementById(id).style.display = 'none';
        }

        // --- NUEVAS FUNCIONALIDADES ---

        // 1. Raw Logs
        function openLogDetails(index) {
            const log = state.phaseLogs[index];
            const rawJson = {
                "@timestamp": log.timestamp,
                "agent": {
                    "type": "SIEM_Collector",
                    "version": "8.11.2"
                },
                "event": {
                    "severity_name": log.sev.toUpperCase(),
                    "category": ["intrusion_detection", "network"]
                },
                "host": {
                    "name": log.src
                },
                "message": log.txt,
                "observer": {
                    "hostname": "SOC_AETHER_CORE",
                    "type": "siem"
                },
                "related": {
                    "ip": log.txt.match(/\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b/g) || []
                }
            };
            
            document.getElementById('raw-log-content').textContent = JSON.stringify(rawJson, null, 2);
            document.getElementById('raw-log-modal').classList.remove('hidden');
            document.getElementById('raw-log-modal').style.display = 'flex';
        }

        function closeLogDetails() {
            document.getElementById('raw-log-modal').classList.add('hidden');
            document.getElementById('raw-log-modal').style.display = 'none';
        }

        // 2. Exportar Debrief
        function exportDebrief() {
            let report = "=================================================\n";
            report += "      AETHER SIEM - REPORTE DE DEBRIEFING\n";
            report += "=================================================\n\n";
            report += `FECHA DE GENERACIÓN: ${new Date().toLocaleString()}\n`;
            report += `FASE ALCANZADA: ${state.currentPhase} / 6\n\n`;
            
            report += "--- MÉTRICAS FINALES DE IMPACTO ---\n";
            report += `Integridad de Operaciones: ${state.integrity}%\n`;
            report += `Datos Exfiltrados: ${state.leakage}%\n`;
            report += `SLA / Eficiencia: ${state.sla}%\n\n`;

            report += "--- HISTORIAL DE DECISIONES (PLAYBOOKS) ---\n";
            if (state.actionHistory.length === 0) {
                report += "No se tomaron acciones.\n";
            } else {
                state.actionHistory.forEach((a, i) => {
                    const status = a.correct ? "[CORRECTA]" : "[INCORRECTA (Penalizada)]";
                    report += `${i + 1}. [Fase ${a.phase}] - ${a.time} - ${a.label} ${status}\n`;
                });
            }

            report += "\n--- INDICADORES DE COMPROMISO (IoCs) REVELADOS ---\n";
            if (state.revealedIoCs.length === 0) {
                report += "No se descubrieron IoCs.\n";
            } else {
                state.revealedIoCs.forEach(ioc => {
                    report += `- ${ioc.type}: ${ioc.value}\n`;
                });
            }

            report += "\n=================================================\n";
            report += "Fin del Reporte.\n";

            const blob = new Blob([report], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `Debriefing_Tabletop_${new Date().getTime()}.txt`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }

        // 3. Notificaciones y Distractores (Popups/Toasts)
        const distractorMessages = [
            { title: "CEO (Mensaje Directo)", msg: "Los sistemas están súper lentos hoy. ¿Es un ataque? Necesito un reporte en mi escritorio YA.", type: "urgent" },
            { title: "Analista Tier 1", msg: "Chicos, encontré un montón de tráfico en el puerto 53 hacia Rusia. ¿Bloqueamos DNS?", type: "info" },
            { title: "Mesa de Ayuda (Helpdesk)", msg: "Tenemos 50 tickets de usuarios que no pueden entrar al ERP. ¿Qué les decimos?", type: "info" },
            { title: "RRHH", msg: "¿Pueden habilitar el acceso a la carpeta compartida externa? No podemos procesar nóminas.", type: "info" },
            { title: "CISO", msg: "Recuerden los SLAs. Toda decisión debe estar documentada. Ojo con apagar servidores a lo loco.", type: "urgent" },
            { title: "Ingeniero de Redes", msg: "Acabo de ver un pico de tráfico TCP 445... debe ser el escaneo de vulnerabilidades que programé, ignórenlo.", type: "info" } // Distractor engañoso para la fase 1
        ];

        function showToast(title, message, type) {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            
            let colorClasses = type === "urgent" ? "bg-rose-950 border-rose-800 text-rose-200 shadow-rose-900/50" : "bg-slate-800 border-slate-700 text-slate-200 shadow-slate-900/50";
            let icon = type === "urgent" ? "fa-triangle-exclamation text-rose-500" : "fa-comment-dots text-indigo-400";

            toast.className = `toast-enter p-3 rounded-lg border shadow-xl flex gap-3 max-w-xs pointer-events-auto ${colorClasses}`;
            toast.innerHTML = `
                <i class="fa-solid ${icon} mt-1"></i>
                <div class="flex-grow">
                    <h4 class="text-xs font-bold mb-1">${title}</h4>
                    <p class="text-[10px] leading-tight opacity-90">${message}</p>
                </div>
                <button class="text-slate-400 hover:text-white mt-[-4px]" onclick="this.parentElement.remove()"><i class="fa-solid fa-xmark text-xs"></i></button>
            `;

            container.appendChild(toast);

            // Desaparecer después de 12 segundos
            setTimeout(() => {
                if (toast.parentElement) {
                    toast.style.opacity = '0';
                    toast.style.transform = 'translateX(100%)';
                    toast.style.transition = 'all 0.4s ease-in';
                    setTimeout(() => toast.remove(), 400);
                }
            }, 12000);
        }

        function startDistractors() {
            // Evaluamos cada 20 segundos si mostramos un distractor (35% de probabilidad de aparición)
            setInterval(() => {
                if (state.currentPhase > 0 && state.currentPhase < phaseMetadata.length - 1 && Math.random() < 0.35) {
                    const msg = distractorMessages[Math.floor(Math.random() * distractorMessages.length)];
                    showToast(msg.title, msg.msg, msg.type);
                }
            }, 20000);
        }

        // INIT
        window.onload = function() {
            loadPhase(1); // Inicia en Fase 1
            updateTopology(); // Dibuja la topología inicial
            startDistractors(); // Inicia el motor de ruido/distractores
        };
    </script>
</body>
</html>
