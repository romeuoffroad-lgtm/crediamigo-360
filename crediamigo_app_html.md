<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crediamigo - Painel do Agente de Crédito</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        crediamigo: {
                            blue: '#00539F',
                            lightBlue: '#0083CA',
                            green: '#00A859',
                            lightGreen: '#E6F4EA',
                            dark: '#1E293B',
                            accent: '#FF7F00'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-slate-50 text-slate-800 font-sans antialiased min-h-screen flex flex-col">

    <!-- Header / Barra Superior -->
    <header class="bg-crediamigo-blue text-white shadow-md sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <div class="bg-white text-crediamigo-blue p-2 rounded-xl font-black text-xl shadow flex items-center justify-center w-10 h-10">
                    CA
                </div>
                <div>
                    <h1 class="font-bold text-lg leading-tight">Crediamigo • Agente Pro</h1>
                    <p class="text-xs text-blue-200">Crediamigo Unidade Andaraí • Agente: Caio</p>
                </div>
            </div>
            <div class="flex items-center space-x-3">
                <button onclick="openNotificationModal()" class="relative p-2 text-blue-100 hover:text-white transition">
                    <i class="fa-solid fa-bell text-xl"></i>
                    <span class="absolute top-1 right-1 bg-crediamigo-accent text-white text-[10px] w-4 h-4 rounded-full flex items-center justify-center font-bold">3</span>
                </button>
                <div class="hidden sm:flex items-center space-x-2 bg-blue-900/50 px-3 py-1.5 rounded-full border border-blue-400/30">
                    <div class="w-2.5 h-2.5 rounded-full bg-crediamigo-green animate-pulse"></div>
                    <span class="text-xs font-medium">Campo Ativo</span>
                </div>
            </div>
        </div>
    </header>

    <!-- Navegação por Abas -->
    <nav class="bg-white border-b border-slate-200 shadow-sm sticky top-[57px] z-40">
        <div class="max-w-7xl mx-auto px-4 flex space-x-6 overflow-x-auto scrollbar-none">
            <button onclick="switchTab('mensal')" id="btn-mensal" class="tab-btn py-3 px-1 border-b-2 font-semibold text-sm transition flex items-center space-x-2 border-crediamigo-blue text-crediamigo-blue shrink-0">
                <i class="fa-solid fa-calendar-days"></i>
                <span>Visão Mês Atual</span>
            </button>
            <button onclick="switchTab('proximo')" id="btn-proximo" class="tab-btn py-3 px-1 border-b-2 font-semibold text-sm transition flex items-center space-x-2 border-transparent text-slate-500 hover:text-slate-700 shrink-0">
                <i class="fa-solid fa-calendar-plus"></i>
                <span>Renovações Próximo Mês</span>
            </button>
            <button onclick="switchTab('rota')" id="btn-rota" class="tab-btn py-3 px-1 border-b-2 font-semibold text-sm transition flex items-center space-x-2 border-transparent text-slate-500 hover:text-slate-700 shrink-0">
                <i class="fa-solid fa-map-location-dot"></i>
                <span>Agenda & Rota Inteligente</span>
            </button>
            <button onclick="switchTab('fne')" id="btn-fne" class="tab-btn py-3 px-1 border-b-2 font-semibold text-sm transition flex items-center space-x-2 border-transparent text-slate-500 hover:text-slate-700 shrink-0">
                <i class="fa-solid fa-landmark"></i>
                <span>Visitas FNE</span>
            </button>
            <button onclick="switchTab('km')" id="btn-km" class="tab-btn py-3 px-1 border-b-2 font-semibold text-sm transition flex items-center space-x-2 border-transparent text-slate-500 hover:text-slate-700 shrink-0">
                <i class="fa-solid fa-gauge-high"></i>
                <span>Quilometragem</span>
            </button>
            <button onclick="switchTab('metas')" id="btn-metas" class="tab-btn py-3 px-1 border-b-2 font-semibold text-sm transition flex items-center space-x-2 border-transparent text-slate-500 hover:text-slate-700 shrink-0">
                <i class="fa-solid fa-chart-pie"></i>
                <span>Metas</span>
            </button>
        </div>
    </nav>

    <!-- Conteúdo Principal -->
    <main class="flex-1 max-w-7xl w-full mx-auto p-4 sm:p-6 pb-20">

        <!-- ABA 1: VISÃO MENSAL -->
        <section id="tab-mensal" class="tab-content space-y-6">
            <!-- Cards de Resumo Rápido -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-100 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-medium text-slate-400 uppercase tracking-wider">Renovações (Mês)</p>
                        <h3 class="text-2xl font-bold text-slate-800 mt-1">R$ 64.500</h3>
                        <p class="text-xs text-crediamigo-green font-medium mt-1"><i class="fa-solid fa-arrow-up"></i> 14 grupos (18 concluídos)</p>
                    </div>
                    <div class="w-12 h-12 bg-blue-50 text-crediamigo-blue rounded-xl flex items-center justify-center text-xl">
                        <i class="fa-solid fa-file-invoice-dollar"></i>
                    </div>
                </div>
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-100 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-medium text-slate-400 uppercase tracking-wider">Visitas FNE</p>
                        <h3 class="text-2xl font-bold text-slate-800 mt-1">8 Pendentes</h3>
                        <p class="text-xs text-purple-600 font-medium mt-1"><i class="fa-solid fa-landmark"></i> Fundo Constitucional</p>
                    </div>
                    <div class="w-12 h-12 bg-purple-50 text-purple-600 rounded-xl flex items-center justify-center text-xl">
                        <i class="fa-solid fa-building-columns"></i>
                    </div>
                </div>
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-100 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-medium text-slate-400 uppercase tracking-wider">Cobrança Pendente</p>
                        <h3 class="text-2xl font-bold text-red-600 mt-1">R$ 3.850</h3>
                        <p class="text-xs text-red-500 font-medium mt-1"><i class="fa-solid fa-triangle-exclamation"></i> 5 clientes em atraso</p>
                    </div>
                    <div class="w-12 h-12 bg-red-50 text-red-500 rounded-xl flex items-center justify-center text-xl">
                        <i class="fa-solid fa-hand-holding-dollar"></i>
                    </div>
                </div>
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-100 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-medium text-slate-400 uppercase tracking-wider">Km Rodados (Mês)</p>
                        <h3 class="text-2xl font-bold text-slate-800 mt-1">340 Km</h3>
                        <p class="text-xs text-amber-500 font-medium mt-1"><i class="fa-solid fa-car"></i> Prestação em dia</p>
                    </div>
                    <div class="w-12 h-12 bg-amber-50 text-amber-500 rounded-xl flex items-center justify-center text-xl">
                        <i class="fa-solid fa-gauge"></i>
                    </div>
                </div>
            </div>

            <!-- Filtros e Busca -->
            <div class="bg-white p-4 rounded-2xl shadow-sm border border-slate-100 flex flex-col sm:flex-row justify-between items-center gap-4">
                <div class="flex items-center space-x-2 w-full sm:w-auto">
                    <div class="relative w-full sm:w-80">
                        <span class="absolute inset-y-0 left-0 flex items-center pl-3 text-slate-400"><i class="fa-solid fa-search"></i></span>
                        <input type="text" placeholder="Buscar grupo, cliente ou rua..." class="w-full pl-10 pr-4 py-2 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-crediamigo-blue/50">
                    </div>
                </div>
                <div class="flex items-center space-x-2 w-full sm:w-auto justify-end">
                    <select id="filtro-mes" onchange="filterMonthlyList()" class="bg-slate-50 border border-slate-200 rounded-xl px-3 py-2 text-sm text-slate-700 focus:outline-none focus:ring-2 focus:ring-crediamigo-blue/50">
                        <option value="atual">Mês Atual (Novembro/2026)</option>
                        <option value="proximo">Próximo Mês (Dezembro/2026)</option>
                    </select>
                    <button onclick="showToast('Lista exportada com sucesso!')" class="bg-slate-100 hover:bg-slate-200 text-slate-700 px-3 py-2 rounded-xl text-sm font-medium transition flex items-center space-x-1">
                        <i class="fa-solid fa-download"></i>
                        <span class="hidden md:inline">Exportar</span>
                    </button>
                </div>
            </div>

            <!-- Tabela / Lista de Compromissos Mensais -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-100 overflow-hidden">
                <div class="p-4 border-b border-slate-100 flex justify-between items-center">
                    <h3 class="font-bold text-slate-800 flex items-center space-x-2">
                        <i class="fa-solid fa-list-check text-crediamigo-blue"></i>
                        <span>Cronograma de Renovações, Cobranças & FNE</span>
                    </h3>
                    <span class="text-xs text-slate-500 bg-slate-100 px-2.5 py-1 rounded-full font-medium">Total: 21 itens</span>
                </div>
                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse text-sm">
                        <thead>
                            <tr class="bg-slate-50 text-slate-500 text-xs uppercase tracking-wider font-semibold border-b border-slate-200">
                                <th class="p-4">Tipo / Status</th>
                                <th class="p-4">Grupo / Cliente</th>
                                <th class="p-4">Endereço / Rua</th>
                                <th class="p-4">Data Prevista</th>
                                <th class="p-4">Valor / Detalhe</th>
                                <th class="p-4 text-center">Ações</th>
                            </tr>
                        </thead>
                        <tbody id="monthly-table-body" class="divide-y divide-slate-100 text-slate-700">
                            <!-- Inserido dinamicamente via JS -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- ABA 2: RENOVAÇÕES PRÓXIMO MÊS -->
        <section id="tab-proximo" class="tab-content hidden space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-6">
                    <div>
                        <span class="bg-blue-50 text-crediamigo-blue font-bold text-xs px-2.5 py-1 rounded-full uppercase">Planejamento Antecipado</span>
                        <h3 class="text-xl font-bold text-slate-800 mt-2">Renovações de Dezembro/2026</h3>
                        <p class="text-sm text-slate-500">Grupos e clientes aptos para renovação no próximo mês. Antecipe os contatos para garantir a meta.</p>
                    </div>
                    <div class="flex items-center space-x-2">
                        <button onclick="showToast('Exportando caderneta do próximo mês...')" class="bg-slate-100 hover:bg-slate-200 text-slate-700 px-4 py-2.5 rounded-xl text-sm font-medium transition flex items-center space-x-1">
                            <i class="fa-solid fa-file-excel"></i>
                            <span>Exportar Caderneta</span>
                        </button>
                        <button onclick="showToast('Sincronizando novas renovações com o servidor...')" class="bg-crediamigo-blue hover:bg-blue-700 text-white px-4 py-2.5 rounded-xl text-sm font-medium transition shadow flex items-center space-x-1">
                            <i class="fa-solid fa-rotate"></i>
                            <span>Atualizar Dados</span>
                        </button>
                    </div>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 mb-6">
                    <div class="bg-slate-50 p-4 rounded-xl border border-slate-100">
                        <p class="text-xs text-slate-400 font-medium uppercase">Potencial de Desembolso</p>
                        <h4 class="text-2xl font-bold text-slate-800 mt-1">R$ 112.000</h4>
                    </div>
                    <div class="bg-slate-50 p-4 rounded-xl border border-slate-100">
                        <p class="text-xs text-slate-400 font-medium uppercase">Total de Grupos</p>
                        <h4 class="text-2xl font-bold text-crediamigo-blue mt-1">16 Grupos</h4>
                    </div>
                    <div class="bg-slate-50 p-4 rounded-xl border border-slate-100">
                        <p class="text-xs text-slate-400 font-medium uppercase">Contatos Prévios Realizados</p>
                        <h4 class="text-2xl font-bold text-crediamigo-green mt-1">6 / 16</h4>
                    </div>
                </div>

                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse text-sm">
                        <thead>
                            <tr class="bg-slate-50 text-slate-500 text-xs uppercase tracking-wider font-semibold border-b border-slate-200">
                                <th class="p-3">Grupo / Cliente</th>
                                <th class="p-3">Endereço / Bairro</th>
                                <th class="p-3">Data Vencimento Atual</th>
                                <th class="p-3">Valor Estimado</th>
                                <th class="p-3">Status Contato</th>
                                <th class="p-3 text-center">Ações</th>
                            </tr>
                        </thead>
                        <tbody class="divide-y divide-slate-100 text-slate-700">
                            <tr class="hover:bg-slate-50">
                                <td class="p-3 font-medium text-slate-800">Grupo Amigos do Sol</td>
                                <td class="p-3 text-xs text-slate-500">Rua das Palmeiras, 300 - Centro</td>
                                <td class="p-3 text-slate-600">02/12/2026</td>
                                <td class="p-3 font-semibold text-slate-800">R$ 10.000</td>
                                <td class="p-3"><span class="bg-emerald-50 text-crediamigo-green font-semibold text-xs px-2 py-0.5 rounded">Pré-contato Feito</span></td>
                                <td class="p-3 text-center">
                                    <button onclick="showToast('Abrindo detalhes do Grupo Amigos do Sol...')" class="bg-blue-50 hover:bg-blue-100 text-crediamigo-blue p-2 rounded-xl text-xs font-medium transition">Agendar</button>
                                </td>
                            </tr>
                            <tr class="hover:bg-slate-50">
                                <td class="p-3 font-medium text-slate-800">Grupo Estrela da Manhã</td>
                                <td class="p-3 text-xs text-slate-500">Av. Central, 1200 - Bairro Novo</td>
                                <td class="p-3 text-slate-600">05/12/2026</td>
                                <td class="p-3 font-semibold text-slate-800">R$ 14.500</td>
                                <td class="p-3"><span class="bg-amber-50 text-amber-600 font-semibold text-xs px-2 py-0.5 rounded">Pendente Contato</span></td>
                                <td class="p-3 text-center">
                                    <button onclick="showToast('Registrando contato prévio...')" class="bg-slate-100 hover:bg-slate-200 text-slate-700 p-2 rounded-xl text-xs font-medium transition">Contatar</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- ABA 3: AGENDA E ROTA INTELIGENTE DO DIA -->
        <section id="tab-rota" class="tab-content hidden space-y-6">
            <div class="bg-gradient-to-r from-blue-900 to-crediamigo-blue text-white p-5 rounded-2xl shadow-md relative overflow-hidden">
                <div class="absolute right-0 top-0 translate-x-4 -translate-y-4 w-32 h-32 bg-white/10 rounded-full blur-2xl pointer-events-none"></div>
                <div class="flex flex-col md:flex-row items-start md:items-center justify-between gap-4 relative z-10">
                    <div class="flex items-start space-x-4">
                        <div class="bg-crediamigo-accent text-white p-3 rounded-2xl text-2xl shadow-inner shrink-0">
                            <i class="fa-solid fa-wand-magic-sparkles"></i>
                        </div>
                        <div>
                            <div class="flex items-center space-x-2">
                                <span class="bg-crediamigo-accent/30 text-orange-200 text-xs font-bold px-2 py-0.5 rounded-full uppercase">Inteligência de Campo</span>
                                <span class="text-xs text-blue-200">Hoje, 09:30</span>
                            </div>
                            <h3 class="text-lg font-bold mt-1">Conflito de Rota Detectado na Rua das Flores</h3>
                            <p class="text-sm text-blue-100 mt-1 leading-relaxed">
                                Você tem o <strong>Grupo Renascer (Renovação)</strong> às 10:00 e uma <strong>Visita FNE (Empresa Comercial)</strong> na mesma rua às 10:30.
                            </p>
                        </div>
                    </div>
                    <div class="flex items-center space-x-2 w-full md:w-auto">
                        <button onclick="applySmartSuggestion()" class="flex-1 md:flex-none bg-crediamigo-green hover:bg-emerald-600 text-white font-medium px-4 py-2.5 rounded-xl text-sm transition shadow flex items-center justify-center space-x-2">
                            <i class="fa-solid fa-check"></i>
                            <span>Aplicar Sugestão de Rota</span>
                        </button>
                        <button onclick="dismissSuggestion()" class="bg-white/10 hover:bg-white/20 text-white p-2.5 rounded-xl text-sm transition" title="Dispensar">
                            <i class="fa-solid fa-xmark"></i>
                        </button>
                    </div>
                </div>
            </div>

            <!-- Painel de Rota Otimizada -->
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100 space-y-4">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                    <div>
                        <div class="flex items-center space-x-2">
                            <span class="bg-emerald-50 text-crediamigo-green font-bold text-xs px-2.5 py-1 rounded-full uppercase">Motor de Rota Otimizada</span>
                            <span class="text-xs text-slate-400"><i class="fa-solid fa-route"></i> Sequência sugerida por proximidade</span>
                        </div>
                        <h3 class="text-xl font-bold text-slate-800 mt-2">Sequência Inteligente de Deslocamento de Hoje</h3>
                        <p class="text-sm text-slate-500">O algoritmo reorganizou suas paradas para minimizar o tempo de trânsito e o consumo de combustível.</p>
                    </div>
                    <div class="flex items-center space-x-2 w-full sm:w-auto">
                        <button onclick="recalcularRota()" class="bg-slate-100 hover:bg-slate-200 text-slate-700 px-4 py-2.5 rounded-xl text-sm font-medium transition flex items-center space-x-2">
                            <i class="fa-solid fa-rotate-right"></i>
                            <span>Recalcular Rota</span>
                        </button>
                        <button onclick="abrirRotaCompletaMaps()" class="bg-crediamigo-blue hover:bg-blue-700 text-white px-4 py-2.5 rounded-xl text-sm font-medium transition shadow flex items-center space-x-2">
                            <i class="fa-solid fa-map-location-dot"></i>
                            <span>Abrir Rota Completa no Maps</span>
                        </button>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-4 gap-4 pt-2" id="optimized-route-steps"></div>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                <div class="lg:col-span-7 bg-white rounded-2xl shadow-sm border border-slate-100 flex flex-col overflow-hidden">
                    <div class="p-4 border-b border-slate-100 flex justify-between items-center">
                        <h3 class="font-bold text-slate-800 flex items-center space-x-2">
                            <i class="fa-solid fa-map text-crediamigo-blue"></i>
                            <span>Mapa Interativo de Campo</span>
                        </h3>
                        <span class="text-xs bg-emerald-50 text-crediamigo-green px-2.5 py-1 rounded-full font-medium flex items-center space-x-1">
                            <span class="w-1.5 h-1.5 rounded-full bg-crediamigo-green"></span>
                            <span>GPS Conectado</span>
                        </span>
                    </div>
                    <div class="relative bg-slate-900 h-80 sm:h-96 flex items-center justify-center overflow-hidden">
                        <div class="absolute inset-0 opacity-20 bg-[radial-gradient(#3b82f6_1px,transparent_1px)] [background-size:16px_16px]"></div>
                        
                        <div class="absolute w-full h-12 bg-slate-800/80 top-1/4 -rotate-12 flex items-center px-8 border-y border-slate-700">
                            <span class="text-xs text-slate-400 font-mono">Av. Principal</span>
                        </div>
                        <div class="absolute w-24 h-full bg-slate-800/80 left-1/3 rotate-12 flex flex-col justify-around py-4 border-x border-slate-700">
                            <span class="text-[10px] text-slate-400 font-mono text-center">Rua das Flores</span>
                        </div>

                        <div class="absolute top-[28%] left-[25%] cursor-pointer group transition transform hover:scale-110">
                            <div class="w-10 h-10 bg-crediamigo-green text-white rounded-full flex items-center justify-center font-bold shadow-lg border-2 border-white">1</div>
                            <div class="absolute top-12 left-1/2 -translate-x-1/2 bg-white text-slate-800 text-[11px] font-semibold px-2 py-0.5 rounded shadow whitespace-nowrap border border-slate-200">Grupo Esperança (09:00)</div>
                        </div>

                        <div class="absolute top-[38%] left-[45%] cursor-pointer group transition transform hover:scale-110">
                            <div class="w-10 h-10 bg-purple-600 text-white rounded-full flex items-center justify-center font-bold shadow-lg border-2 border-white animate-bounce">2</div>
                            <div class="absolute top-12 left-1/2 -translate-x-1/2 bg-white text-slate-800 text-[11px] font-semibold px-2 py-0.5 rounded shadow whitespace-nowrap border border-slate-200">Visita FNE - Loja (10:15)</div>
                        </div>

                        <div class="absolute top-[48%] left-[55%] cursor-pointer group transition transform hover:scale-110">
                            <div class="w-10 h-10 bg-crediamigo-blue text-white rounded-full flex items-center justify-center font-bold shadow-lg border-2 border-white">3</div>
                            <div class="absolute top-12 left-1/2 -translate-x-1/2 bg-white text-slate-800 text-[11px] font-semibold px-2 py-0.5 rounded shadow whitespace-nowrap border border-slate-200">Grupo Renascer (11:00)</div>
                        </div>

                        <div class="absolute bottom-[20%] right-[20%] cursor-pointer group transition transform hover:scale-110">
                            <div class="w-10 h-10 bg-slate-400 text-white rounded-full flex items-center justify-center font-bold shadow-lg border-2 border-white">4</div>
                            <div class="absolute top-12 left-1/2 -translate-x-1/2 bg-white text-slate-800 text-[11px] font-semibold px-2 py-0.5 rounded shadow whitespace-nowrap border border-slate-200">Grupo Progresso (14:00)</div>
                        </div>

                        <div class="absolute bottom-3 left-3 bg-slate-900/90 text-white p-2.5 rounded-xl text-xs backdrop-blur border border-slate-700/50 flex items-center space-x-3">
                            <div class="flex items-center space-x-1"><span class="w-3 h-3 rounded-full bg-crediamigo-green"></span><span>Concluído</span></div>
                            <div class="flex items-center space-x-1"><span class="w-3 h-3 rounded-full bg-purple-600"></span><span>FNE</span></div>
                            <div class="flex items-center space-x-1"><span class="w-3 h-3 rounded-full bg-crediamigo-blue"></span><span>Renovação</span></div>
                        </div>
                    </div>
                    <div class="p-4 bg-slate-50 border-t border-slate-100 flex justify-between items-center text-sm">
                        <span class="text-slate-500"><i class="fa-solid fa-route text-crediamigo-blue mr-1"></i> Distância total estimada: <strong>14.2 km</strong></span>
                        <button onclick="abrirRotaCompletaMaps()" class="text-crediamigo-blue font-semibold hover:underline flex items-center space-x-1">
                            <span>Abrir Navegação GPS</span>
                        </button>
                    </div>
                </div>

                <div class="lg:col-span-5 bg-white rounded-2xl shadow-sm border border-slate-100 flex flex-col">
                    <div class="p-4 border-b border-slate-100 flex justify-between items-center">
                        <h3 class="font-bold text-slate-800 flex items-center space-x-2">
                            <i class="fa-solid fa-clipboard-user text-crediamigo-blue"></i>
                            <span>Tarefas do Dia</span>
                        </h3>
                        <span id="task-counter" class="text-xs bg-blue-50 text-crediamigo-blue px-2.5 py-1 rounded-full font-medium">1 / 4 concluídas</span>
                    </div>
                    <div id="daily-task-list" class="divide-y divide-slate-100 overflow-y-auto max-h-[400px] p-2 space-y-2"></div>
                    <div class="p-4 border-t border-slate-100 mt-auto">
                        <button onclick="openNewTaskModal()" class="w-full bg-crediamigo-blue hover:bg-blue-700 text-white font-medium py-2.5 rounded-xl text-sm transition shadow-sm flex items-center justify-center space-x-2">
                            <i class="fa-solid fa-plus"></i>
                            <span>Adicionar Visita / FNE / Cobrança Extra</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- ABA 4: VISITAS FNE -->
        <section id="tab-fne" class="tab-content hidden space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-6">
                    <div>
                        <span class="bg-purple-50 text-purple-700 font-bold text-xs px-2.5 py-1 rounded-full uppercase">Fundo Constitucional de Financiamento do Nordeste</span>
                        <h3 class="text-xl font-bold text-slate-800 mt-2">Painel de Visitas FNE</h3>
                        <p class="text-sm text-slate-500">Acompanhamento pré e pós-desembolso obrigatório para linhas FNE.</p>
                    </div>
                    <button onclick="showToast('Abrindo formulário de nova vistoria FNE...')" class="bg-purple-600 hover:bg-purple-700 text-white px-4 py-2.5 rounded-xl text-sm font-medium transition shadow flex items-center space-x-2">
                        <i class="fa-solid fa-plus"></i>
                        <span>Agendar Vistoria FNE</span>
                    </button>
                </div>

                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse text-sm">
                        <thead>
                            <tr class="bg-slate-50 text-slate-500 text-xs uppercase tracking-wider font-semibold border-b border-slate-200">
                                <th class="p-3">Cliente / Empresa</th>
                                <th class="p-3">Linha FNE</th>
                                <th class="p-3">Endereço</th>
                                <th class="p-3">Data Vistoria</th>
                                <th class="p-3">Status FNE</th>
                                <th class="p-3 text-center">Laudo / Ação</th>
                            </tr>
                        </thead>
                        <tbody class="divide-y divide-slate-100 text-slate-700">
                            <tr class="hover:bg-slate-50">
                                <td class="p-3 font-medium text-slate-800">Comercial Silva ME</td>
                                <td class="p-3"><span class="bg-purple-50 text-purple-700 font-semibold text-xs px-2 py-0.5 rounded">FNE Giro</span></td>
                                <td class="p-3 text-xs text-slate-500">Rua das Flores, 135</td>
                                <td class="p-3 text-slate-600">Hoje, 10:30</td>
                                <td class="p-3"><span class="bg-amber-50 text-amber-600 font-semibold text-xs px-2 py-0.5 rounded">Pendente Vistoria</span></td>
                                <td class="p-3 text-center">
                                    <button onclick="showToast('Abrindo formulário de laudo FNE...')" class="bg-purple-50 hover:bg-purple-100 text-purple-700 p-2 rounded-xl text-xs font-medium transition">Preencher Laudo</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- ABA 5: CONTROLE DE QUILOMETRAGEM -->
        <section id="tab-km" class="tab-content hidden space-y-6">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                <div class="lg:col-span-5 bg-white p-6 rounded-2xl shadow-sm border border-slate-100 space-y-4">
                    <div>
                        <span class="bg-amber-50 text-amber-700 font-bold text-xs px-2.5 py-1 rounded-full uppercase">Prestação de Contas</span>
                        <h3 class="text-xl font-bold text-slate-800 mt-2">Registro de Quilometragem Diária</h3>
                        <p class="text-sm text-slate-500">Informe a quilometragem do veículo ao iniciar e encerrar as rotas de campo.</p>
                    </div>

                    <div class="space-y-4 pt-2">
                        <div>
                            <label class="block text-xs font-bold uppercase text-slate-500 mb-1">Km Inicial</label>
                            <input type="number" id="km-inicial" value="14250" class="w-full px-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm font-semibold text-slate-800">
                        </div>
                        <div>
                            <label class="block text-xs font-bold uppercase text-slate-500 mb-1">Km Final</label>
                            <input type="number" id="km-final" value="14282" oninput="calcularKmRodado()" class="w-full px-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm font-semibold text-slate-800">
                        </div>
                        <div class="p-4 bg-amber-50/60 rounded-2xl border border-amber-200/60 flex items-center justify-between">
                            <div>
                                <p class="text-xs text-amber-800 font-medium uppercase">Total Rodado Hoje</p>
                                <h4 id="km-total-calculado" class="text-3xl font-black text-amber-900 mt-0.5">32 Km</h4>
                            </div>
                        </div>
                        <button onclick="salvarQuilometragem()" class="w-full bg-crediamigo-blue hover:bg-blue-700 text-white font-medium py-3 rounded-xl text-sm transition">Salvar Quilometragem</button>
                    </div>
                </div>

                <div class="lg:col-span-7 bg-white p-6 rounded-2xl shadow-sm border border-slate-100">
                    <h3 class="font-bold text-slate-800 mb-4">Histórico de Deslocamento do Mês</h3>
                    <p class="text-sm text-slate-600">Total acumulado: <strong>340 Km</strong></p>
                </div>
            </div>
        </section>

        <!-- ABA 6: METAS -->
        <section id="tab-metas" class="tab-content hidden space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100">
                <h3 class="font-bold text-slate-800 mb-2">Desempenho Geral</h3>
                <p class="text-sm text-slate-600">Meta de desembolso mensal: <strong>82% Atingido (R$ 246.000 / R$ 300.000)</strong></p>
            </div>
        </section>

    </main>

    <!-- Toast -->
    <div id="toast" class="fixed bottom-6 right-6 bg-slate-900 text-white px-4 py-3 rounded-2xl shadow-2xl z-50 flex items-center space-x-3 transform translate-y-20 opacity-0 transition-all duration-300">
        <span id="toast-message" class="text-sm font-medium">Ação realizada com sucesso!</span>
    </div>

    <script>
        const monthlyData = [
            { id: 1, type: 'Renovação', name: 'Grupo Esperança', address: 'Av. Principal, 450 - Centro', date: '18/11/2026', value: 'R$ 6.500', month: 'atual', status: 'Concluído' },
            { id: 2, type: 'Cobrança', name: 'João Carlos (Atraso 12d)', address: 'Rua das Flores, 120 - Centro', date: '18/11/2026', value: 'R$ 450', month: 'atual', status: 'Pendente' },
            { id: 3, type: 'Visita FNE', name: 'Comercial Silva ME', address: 'Rua das Flores, 135 - Centro', date: '18/11/2026', value: 'FNE Giro', month: 'atual', status: 'Pendente' }
        ];

        let dailyTasks = [
            { id: 1, title: 'Grupo Esperança (Renovação)', address: 'Av. Principal, 450', time: '09:00', type: 'Renovação', completed: true },
            { id: 2, title: 'Comercial Silva ME (Visita FNE)', address: 'Rua das Flores, 135', time: '10:15', type: 'Visita FNE', completed: false }
        ];

        window.onload = function() {
            renderMonthlyTable();
            renderDailyTasks();
            renderOptimizedRouteSteps();
            calcularKmRodado();
        };

        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.tab-btn').forEach(el => {
                el.classList.remove('border-crediamigo-blue', 'text-crediamigo-blue');
                el.classList.add('border-transparent', 'text-slate-500');
            });
            document.getElementById('tab-' + tabId).classList.remove('hidden');
            document.getElementById('btn-' + tabId).classList.add('border-crediamigo-blue', 'text-crediamigo-blue');
        }

        function renderMonthlyTable() {
            const tbody = document.getElementById('monthly-table-body');
            tbody.innerHTML = '';
            monthlyData.forEach(item => {
                const row = document.createElement('tr');
                row.innerHTML = `<td class="p-4">${item.type}</td><td class="p-4">${item.name}</td><td class="p-4">${item.address}</td><td class="p-4">${item.date}</td><td class="p-4">${item.value}</td><td class="p-4 text-center">Ok</td>`;
                tbody.appendChild(row);
            });
        }

        function renderDailyTasks() {
            const container = document.getElementById('daily-task-list');
            container.innerHTML = '';
            dailyTasks.forEach(task => {
                const div = document.createElement('div');
                div.className = 'p-3 rounded-xl border border-slate-100 flex items-center justify-between bg-white';
                div.innerHTML = `<div><h4 class="text-sm font-bold">${task.title}</h4><p class="text-xs text-slate-500">${task.address} • ${task.time}</p></div>`;
                container.appendChild(div);
            });
        }

        function renderOptimizedRouteSteps() {
            const container = document.getElementById('optimized-route-steps');
            if (!container) return;
            container.innerHTML = `<div class="bg-slate-50 p-4 rounded-xl border border-slate-200"><h4 class="font-bold text-sm">1. Grupo Esperança (09:00)</h4></div>`;
        }

        function calcularKmRodado() {
            const inicial = parseFloat(document.getElementById('km-inicial').value) || 0;
            const final = parseFloat(document.getElementById('km-final').value) || 0;
            document.getElementById('km-total-calculado').innerText = (final >= inicial ? final - inicial : 0) + ' Km';
        }

        function salvarQuilometragem() {
            showToast('Quilometragem salva!');
        }

        function applySmartSuggestion() {
            showToast('Sugestão aplicada com sucesso!');
        }

        function dismissSuggestion() {
            showToast('Sugestão dispensada.');
        }

        function recalcularRota() {
            showToast('Rota recalculada!');
        }

        function abrirRotaCompletaMaps() {
            window.open('https://www.google.com/maps', '_blank');
        }

        function showToast(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toast-message').innerText = msg;
            toast.classList.remove('translate-y-20', 'opacity-0');
            setTimeout(() => toast.classList.add('translate-y-20', 'opacity-0'), 3000);
        }
    </script>
</body>
</html>