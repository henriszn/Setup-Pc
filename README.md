# Setup-Pc
Monte o seu Pc ou o Pc do seu sonho 
Vou criar um site interativo para montagem de PCs com verificação de compatibilidade e sugestões personalizadas.
Aqui está um protótipo completo e funcional para o seu site de montagem de PCs:
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MontaPCBR - Monte seu Setup Ideal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f0f4f8;
        }
        .component-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .setup-card {
            transition: all 0.3s ease;
        }
        .setup-card:hover {
            transform: scale(1.02);
        }
        .compatibility-error {
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0% { background-color: rgba(254, 202, 202, 0.7); }
            50% { background-color: rgba(254, 202, 202, 1); }
            100% { background-color: rgba(254, 202, 202, 0.7); }
        }
    </style>
</head>
<body>
    <!-- Navbar -->
    <nav class="bg-gradient-to-r from-blue-600 to-indigo-700 text-white shadow-lg">
        <div class="container mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center space-x-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 3v2m6-2v2M9 19v2m6-2v2M5 9H3m2 6H3m18-6h-2m2 6h-2M7 19h10a2 2 0 002-2V7a2 2 0 00-2-2H7a2 2 0 00-2 2v10a2 2 0 002 2zM9 9h6v6H9V9z" />
                </svg>
                <span class="font-bold text-xl">MontaPCBR</span>
            </div>
            <div class="hidden md:flex space-x-6">
                <a href="#" class="hover:text-blue-200 transition" onclick="showTab('builder')">Montar PC</a>
                <a href="#" class="hover:text-blue-200 transition" onclick="showTab('suggestions')">Sugestões</a>
                <a href="#" class="hover:text-blue-200 transition" onclick="showTab('compare')">Comparar</a>
                <a href="#" class="hover:text-blue-200 transition" onclick="showTab('blog')">Blog</a>
            </div>
            <div class="flex items-center space-x-4">
                <button class="bg-white text-blue-600 px-4 py-2 rounded-lg font-medium hover:bg-blue-50 transition">Entrar</button>
                <button class="md:hidden" id="mobile-menu-button">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>
        <!-- Mobile Menu -->
        <div class="md:hidden hidden bg-blue-700 pb-4 px-4" id="mobile-menu">
            <a href="#" class="block py-2 hover:bg-blue-600 px-2 rounded" onclick="showTab('builder')">Montar PC</a>
            <a href="#" class="block py-2 hover:bg-blue-600 px-2 rounded" onclick="showTab('suggestions')">Sugestões</a>
            <a href="#" class="block py-2 hover:bg-blue-600 px-2 rounded" onclick="showTab('compare')">Comparar</a>
            <a href="#" class="block py-2 hover:bg-blue-600 px-2 rounded" onclick="showTab('blog')">Blog</a>
        </div>
    </nav>

    <!-- Hero Section -->
    <div class="bg-gradient-to-r from-blue-600 to-indigo-700 text-white py-12 md:py-20">
        <div class="container mx-auto px-4 text-center">
            <h1 class="text-3xl md:text-5xl font-bold mb-4">Monte o PC dos seus sonhos</h1>
            <p class="text-lg md:text-xl mb-8 max-w-3xl mx-auto">Escolha os melhores componentes com verificação de compatibilidade em tempo real e sugestões personalizadas para o seu orçamento.</p>
            <button class="bg-white text-blue-600 px-6 py-3 rounded-lg font-medium text-lg hover:bg-blue-50 transition shadow-lg" onclick="showTab('builder')">Começar a montar</button>
        </div>
    </div>

    <!-- Main Content -->
    <div class="container mx-auto px-4 py-8">
        <!-- PC Builder Tab -->
        <div id="builder-tab" class="tab-content">
            <div class="flex flex-col lg:flex-row gap-8">
                <!-- Left Column - Component Selection -->
                <div class="lg:w-2/3 bg-white rounded-xl shadow-md p-6">
                    <h2 class="text-2xl font-bold mb-6 text-gray-800">Monte seu PC</h2>
                    
                    <div class="mb-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-700">Processador (CPU)</h3>
                            <button class="text-blue-600 hover:text-blue-800 flex items-center" onclick="showComponentOptions('cpu')">
                                <span>Escolher</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                                </svg>
                            </button>
                        </div>
                        <div id="selected-cpu" class="border border-gray-200 rounded-lg p-4 bg-gray-50 min-h-[80px] flex items-center justify-center text-gray-500">
                            Nenhum processador selecionado
                        </div>
                    </div>

                    <div class="mb-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-700">Placa-mãe</h3>
                            <button class="text-blue-600 hover:text-blue-800 flex items-center" onclick="showComponentOptions('motherboard')">
                                <span>Escolher</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                                </svg>
                            </button>
                        </div>
                        <div id="selected-motherboard" class="border border-gray-200 rounded-lg p-4 bg-gray-50 min-h-[80px] flex items-center justify-center text-gray-500">
                            Nenhuma placa-mãe selecionada
                        </div>
                    </div>

                    <div class="mb-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-700">Memória RAM</h3>
                            <button class="text-blue-600 hover:text-blue-800 flex items-center" onclick="showComponentOptions('ram')">
                                <span>Escolher</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                                </svg>
                            </button>
                        </div>
                        <div id="selected-ram" class="border border-gray-200 rounded-lg p-4 bg-gray-50 min-h-[80px] flex items-center justify-center text-gray-500">
                            Nenhuma memória RAM selecionada
                        </div>
                    </div>

                    <div class="mb-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-700">Placa de Vídeo (GPU)</h3>
                            <button class="text-blue-600 hover:text-blue-800 flex items-center" onclick="showComponentOptions('gpu')">
                                <span>Escolher</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                                </svg>
                            </button>
                        </div>
                        <div id="selected-gpu" class="border border-gray-200 rounded-lg p-4 bg-gray-50 min-h-[80px] flex items-center justify-center text-gray-500">
                            Nenhuma placa de vídeo selecionada
                        </div>
                    </div>

                    <div class="mb-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-700">Armazenamento</h3>
                            <button class="text-blue-600 hover:text-blue-800 flex items-center" onclick="showComponentOptions('storage')">
                                <span>Escolher</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                                </svg>
                            </button>
                        </div>
                        <div id="selected-storage" class="border border-gray-200 rounded-lg p-4 bg-gray-50 min-h-[80px] flex items-center justify-center text-gray-500">
                            Nenhum armazenamento selecionado
                        </div>
                    </div>

                    <div class="mb-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-700">Fonte de Alimentação</h3>
                            <button class="text-blue-600 hover:text-blue-800 flex items-center" onclick="showComponentOptions('psu')">
                                <span>Escolher</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                                </svg>
                            </button>
                        </div>
                        <div id="selected-psu" class="border border-gray-200 rounded-lg p-4 bg-gray-50 min-h-[80px] flex items-center justify-center text-gray-500">
                            Nenhuma fonte selecionada
                        </div>
                    </div>

                    <div class="mb-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-700">Gabinete</h3>
                            <button class="text-blue-600 hover:text-blue-800 flex items-center" onclick="showComponentOptions('case')">
                                <span>Escolher</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" />
                                </svg>
                            </button>
                        </div>
                        <div id="selected-case" class="border border-gray-200 rounded-lg p-4 bg-gray-50 min-h-[80px] flex items-center justify-center text-gray-500">
                            Nenhum gabinete selecionado
                        </div>
                    </div>

                    <div class="mt-8">
                        <button class="bg-blue-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-blue-700 transition w-full" onclick="saveSetup()">Salvar configuração</button>
                    </div>
                </div>

                <!-- Right Column - Summary and Compatibility -->
                <div class="lg:w-1/3">
                    <div class="bg-white rounded-xl shadow-md p-6 mb-6 sticky top-4">
                        <h2 class="text-2xl font-bold mb-4 text-gray-800">Resumo</h2>
                        
                        <div class="mb-6">
                            <div class="flex justify-between items-center mb-2">
                                <span class="text-gray-600">Valor total:</span>
                                <span class="text-2xl font-bold text-blue-600" id="total-price">R$ 0,00</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-blue-600 h-2.5 rounded-full" id="budget-bar" style="width: 0%"></div>
                            </div>
                            <div class="flex justify-between text-xs text-gray-500 mt-1">
                                <span>Econômico</span>
                                <span>Intermediário</span>
                                <span>Avançado</span>
                            </div>
                        </div>

                        <div class="mb-6">
                            <h3 class="font-semibold text-gray-700 mb-2">Compatibilidade</h3>
                            <div id="compatibility-status" class="p-3 bg-green-100 text-green-800 rounded-lg">
                                <div class="flex items-center">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                        <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                    </svg>
                                    <span>Nenhum problema detectado</span>
                                </div>
                            </div>
                        </div>

                        <div class="mb-6">
                            <h3 class="font-semibold text-gray-700 mb-2">Desempenho estimado</h3>
                            <div class="space-y-3">
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm text-gray-600">Jogos</span>
                                        <span class="text-sm text-gray-600" id="gaming-score">N/A</span>
                                    </div>
                                    <div class="w-full bg-gray-200 rounded-full h-2.5">
                                        <div class="bg-blue-600 h-2.5 rounded-full" id="gaming-bar" style="width: 0%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm text-gray-600">Produtividade</span>
                                        <span class="text-sm text-gray-600" id="productivity-score">N/A</span>
                                    </div>
                                    <div class="w-full bg-gray-200 rounded-full h-2.5">
                                        <div class="bg-blue-600 h-2.5 rounded-full" id="productivity-bar" style="width: 0%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm text-gray-600">Edição de vídeo</span>
                                        <span class="text-sm text-gray-600" id="video-score">N/A</span>
                                    </div>
                                    <div class="w-full bg-gray-200 rounded-full h-2.5">
                                        <div class="bg-blue-600 h-2.5 rounded-full" id="video-bar" style="width: 0%"></div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div>
                            <h3 class="font-semibold text-gray-700 mb-2">Consumo estimado</h3>
                            <div class="flex items-center justify-between bg-gray-100 p-3 rounded-lg">
                                <div class="flex items-center">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-yellow-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                                        <path fill-rule="evenodd" d="M11.3 1.046A1 1 0 0112 2v5h4a1 1 0 01.82 1.573l-7 10A1 1 0 018 18v-5H4a1 1 0 01-.82-1.573l7-10a1 1 0 011.12-.38z" clip-rule="evenodd" />
                                    </svg>
                                    <span class="text-gray-600">Potência</span>
                                </div>
                                <span class="font-semibold" id="power-consumption">0W</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Suggestions Tab -->
        <div id="suggestions-tab" class="tab-content hidden">
            <h2 class="text-2xl font-bold mb-6 text-gray-800">Sugestões de Setups</h2>
            
            <div class="mb-8">
                <div class="flex flex-wrap items-center gap-4 mb-6">
                    <h3 class="text-xl font-semibold text-gray-700">Filtrar por:</h3>
                    <div class="flex flex-wrap gap-2">
                        <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition" onclick="filterSetups('all')">Todos</button>
                        <button class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg hover:bg-gray-300 transition" onclick="filterSetups('gaming')">Games</button>
                        <button class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg hover:bg-gray-300 transition" onclick="filterSetups('productivity')">Produtividade</button>
                        <button class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg hover:bg-gray-300 transition" onclick="filterSetups('video')">Edição de Vídeo</button>
                    </div>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Budget Setup -->
                    <div class="setup-card bg-white rounded-xl shadow-md overflow-hidden">
                        <div class="bg-blue-100 p-4">
                            <h3 class="text-xl font-bold text-blue-800">Setup Econômico</h3>
                            <p class="text-blue-600">Ideal para uso diário e jogos leves</p>
                        </div>
                        <div class="p-6">
                            <ul class="space-y-3 mb-6">
                                <li class="flex justify-between">
                                    <span class="text-gray-600">CPU:</span>
                                    <span class="font-medium">Ryzen 5 5600G</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Placa-mãe:</span>
                                    <span class="font-medium">Gigabyte B450M DS3H</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">RAM:</span>
                                    <span class="font-medium">16GB (2x8GB) DDR4 3200MHz</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">GPU:</span>
                                    <span class="font-medium">Integrada (Vega 7)</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Armazenamento:</span>
                                    <span class="font-medium">SSD 500GB NVMe</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Fonte:</span>
                                    <span class="font-medium">500W 80+ Bronze</span>
                                </li>
                            </ul>
                            <div class="flex justify-between items-center pt-4 border-t border-gray-200">
                                <span class="text-2xl font-bold text-blue-600">R$ 2.899,00</span>
                                <button class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition" onclick="loadPresetSetup('budget')">Selecionar</button>
                            </div>
                        </div>
                    </div>

                    <!-- Mid-range Setup -->
                    <div class="setup-card bg-white rounded-xl shadow-md overflow-hidden">
                        <div class="bg-purple-100 p-4">
                            <h3 class="text-xl font-bold text-purple-800">Setup Intermediário</h3>
                            <p class="text-purple-600">Ótimo custo-benefício para jogos e trabalho</p>
                        </div>
                        <div class="p-6">
                            <ul class="space-y-3 mb-6">
                                <li class="flex justify-between">
                                    <span class="text-gray-600">CPU:</span>
                                    <span class="font-medium">Ryzen 7 5800X</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Placa-mãe:</span>
                                    <span class="font-medium">MSI B550 TOMAHAWK</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">RAM:</span>
                                    <span class="font-medium">32GB (2x16GB) DDR4 3600MHz</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">GPU:</span>
                                    <span class="font-medium">RTX 3060 Ti 8GB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Armazenamento:</span>
                                    <span class="font-medium">SSD 1TB NVMe + HD 2TB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Fonte:</span>
                                    <span class="font-medium">750W 80+ Gold</span>
                                </li>
                            </ul>
                            <div class="flex justify-between items-center pt-4 border-t border-gray-200">
                                <span class="text-2xl font-bold text-purple-600">R$ 6.499,00</span>
                                <button class="bg-purple-600 text-white px-4 py-2 rounded-lg hover:bg-purple-700 transition" onclick="loadPresetSetup('midrange')">Selecionar</button>
                            </div>
                        </div>
                    </div>

                    <!-- High-end Setup -->
                    <div class="setup-card bg-white rounded-xl shadow-md overflow-hidden">
                        <div class="bg-indigo-100 p-4">
                            <h3 class="text-xl font-bold text-indigo-800">Setup Avançado</h3>
                            <p class="text-indigo-600">Máximo desempenho para entusiastas</p>
                        </div>
                        <div class="p-6">
                            <ul class="space-y-3 mb-6">
                                <li class="flex justify-between">
                                    <span class="text-gray-600">CPU:</span>
                                    <span class="font-medium">Intel Core i9-12900K</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Placa-mãe:</span>
                                    <span class="font-medium">ASUS ROG Z690 MAXIMUS</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">RAM:</span>
                                    <span class="font-medium">64GB (4x16GB) DDR5 5200MHz</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">GPU:</span>
                                    <span class="font-medium">RTX 4090 24GB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Armazenamento:</span>
                                    <span class="font-medium">SSD 2TB NVMe PCIe 4.0 + SSD 4TB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Fonte:</span>
                                    <span class="font-medium">1000W 80+ Platinum</span>
                                </li>
                            </ul>
                            <div class="flex justify-between items-center pt-4 border-t border-gray-200">
                                <span class="text-2xl font-bold text-indigo-600">R$ 25.999,00</span>
                                <button class="bg-indigo-600 text-white px-4 py-2 rounded-lg hover:bg-indigo-700 transition" onclick="loadPresetSetup('highend')">Selecionar</button>
                            </div>
                        </div>
                    </div>

                    <!-- Gaming Focused Setup -->
                    <div class="setup-card bg-white rounded-xl shadow-md overflow-hidden setup-type-gaming">
                        <div class="bg-red-100 p-4">
                            <h3 class="text-xl font-bold text-red-800">Setup Gamer</h3>
                            <p class="text-red-600">Otimizado para jogos de alta performance</p>
                        </div>
                        <div class="p-6">
                            <ul class="space-y-3 mb-6">
                                <li class="flex justify-between">
                                    <span class="text-gray-600">CPU:</span>
                                    <span class="font-medium">Intel Core i7-12700K</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Placa-mãe:</span>
                                    <span class="font-medium">MSI MPG Z690 GAMING EDGE</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">RAM:</span>
                                    <span class="font-medium">32GB (2x16GB) DDR4 3600MHz</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">GPU:</span>
                                    <span class="font-medium">RTX 4070 Ti 12GB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Armazenamento:</span>
                                    <span class="font-medium">SSD 2TB NVMe PCIe 4.0</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Fonte:</span>
                                    <span class="font-medium">850W 80+ Gold</span>
                                </li>
                            </ul>
                            <div class="flex justify-between items-center pt-4 border-t border-gray-200">
                                <span class="text-2xl font-bold text-red-600">R$ 13.499,00</span>
                                <button class="bg-red-600 text-white px-4 py-2 rounded-lg hover:bg-red-700 transition" onclick="loadPresetSetup('gaming')">Selecionar</button>
                            </div>
                        </div>
                    </div>

                    <!-- Video Editing Setup -->
                    <div class="setup-card bg-white rounded-xl shadow-md overflow-hidden setup-type-video">
                        <div class="bg-green-100 p-4">
                            <h3 class="text-xl font-bold text-green-800">Setup para Edição de Vídeo</h3>
                            <p class="text-green-600">Ideal para produção de conteúdo</p>
                        </div>
                        <div class="p-6">
                            <ul class="space-y-3 mb-6">
                                <li class="flex justify-between">
                                    <span class="text-gray-600">CPU:</span>
                                    <span class="font-medium">Ryzen 9 7950X</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Placa-mãe:</span>
                                    <span class="font-medium">ASUS ProArt X670E-CREATOR</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">RAM:</span>
                                    <span class="font-medium">64GB (2x32GB) DDR5 5600MHz</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">GPU:</span>
                                    <span class="font-medium">RTX 4080 16GB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Armazenamento:</span>
                                    <span class="font-medium">SSD 2TB NVMe PCIe 4.0 + SSD 4TB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Fonte:</span>
                                    <span class="font-medium">1000W 80+ Platinum</span>
                                </li>
                            </ul>
                            <div class="flex justify-between items-center pt-4 border-t border-gray-200">
                                <span class="text-2xl font-bold text-green-600">R$ 19.999,00</span>
                                <button class="bg-green-600 text-white px-4 py-2 rounded-lg hover:bg-green-700 transition" onclick="loadPresetSetup('video')">Selecionar</button>
                            </div>
                        </div>
                    </div>

                    <!-- Productivity Setup -->
                    <div class="setup-card bg-white rounded-xl shadow-md overflow-hidden setup-type-productivity">
                        <div class="bg-amber-100 p-4">
                            <h3 class="text-xl font-bold text-amber-800">Setup para Produtividade</h3>
                            <p class="text-amber-600">Perfeito para trabalho e multitarefa</p>
                        </div>
                        <div class="p-6">
                            <ul class="space-y-3 mb-6">
                                <li class="flex justify-between">
                                    <span class="text-gray-600">CPU:</span>
                                    <span class="font-medium">Intel Core i7-13700</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Placa-mãe:</span>
                                    <span class="font-medium">ASUS TUF GAMING B760M-PLUS</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">RAM:</span>
                                    <span class="font-medium">32GB (2x16GB) DDR4 3600MHz</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">GPU:</span>
                                    <span class="font-medium">RTX 3060 12GB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Armazenamento:</span>
                                    <span class="font-medium">SSD 1TB NVMe + HD 4TB</span>
                                </li>
                                <li class="flex justify-between">
                                    <span class="text-gray-600">Fonte:</span>
                                    <span class="font-medium">650W 80+ Gold</span>
                                </li>
                            </ul>
                            <div class="flex justify-between items-center pt-4 border-t border-gray-200">
                                <span class="text-2xl font-bold text-amber-600">R$ 8.299,00</span>
                                <button class="bg-amber-600 text-white px-4 py-2 rounded-lg hover:bg-amber-700 transition" onclick="loadPresetSetup('productivity')">Selecionar</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Compare Tab -->
        <div id="compare-tab" class="tab-content hidden">
            <h2 class="text-2xl font-bold mb-6 text-gray-800">Comparar Setups</h2>
            
            <div class="bg-white rounded-xl shadow-md p-6 mb-8">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div>
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">Setup 1</h3>
                        <select class="w-full p-3 border border-gray-300 rounded-lg mb-4" id="setup-select-1">
                            <option value="">Selecione um setup...</option>
                            <option value="current">Setup Atual</option>
                            <option value="budget">Setup Econômico</option>
                            <option value="midrange">Setup Intermediário</option>
                            <option value="highend">Setup Avançado</option>
                            <option value="gaming">Setup Gamer</option>
                            <option value="video">Setup para Edição de Vídeo</option>
                            <option value="productivity">Setup para Produtividade</option>
                        </select>
                        <div id="setup-details-1" class="bg-gray-50 p-4 rounded-lg min-h-[300px]">
                            <p class="text-gray-500 text-center">Selecione um setup para comparar</p>
                        </div>
                    </div>
                    
                    <div>
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">Setup 2</h3>
                        <select class="w-full p-3 border border-gray-300 rounded-lg mb-4" id="setup-select-2">
                            <option value="">Selecione um setup...</option>
                            <option value="current">Setup Atual</option>
                            <option value="budget">Setup Econômico</option>
                            <option value="midrange">Setup Intermediário</option>
                            <option value="highend">Setup Avançado</option>
                            <option value="gaming">Setup Gamer</option>
                            <option value="video">Setup para Edição de Vídeo</option>
                            <option value="productivity">Setup para Produtividade</option>
                        </select>
                        <div id="setup-details-2" class="bg-gray-50 p-4 rounded-lg min-h-[300px]">
                            <p class="text-gray-500 text-center">Selecione um setup para comparar</p>
                        </div>
                    </div>
                    
                    <div>
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">Setup 3</h3>
                        <select class="w-full p-3 border border-gray-300 rounded-lg mb-4" id="setup-select-3">
                            <option value="">Selecione um setup...</option>
                            <option value="current">Setup Atual</option>
                            <option value="budget">Setup Econômico</option>
                            <option value="midrange">Setup Intermediário</option>
                            <option value="highend">Setup Avançado</option>
                            <option value="gaming">Setup Gamer</option>
                            <option value="video">Setup para Edição de Vídeo</option>
                            <option value="productivity">Setup para Produtividade</option>
                        </select>
                        <div id="setup-details-3" class="bg-gray-50 p-4 rounded-lg min-h-[300px]">
                            <p class="text-gray-500 text-center">Selecione um setup para comparar</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="bg-white rounded-xl shadow-md p-6">
                <h3 class="text-xl font-semibold text-gray-800 mb-6">Comparação de Desempenho</h3>
                
                <div class="space-y-8">
                    <div>
                        <h4 class="font-medium text-gray-700 mb-3">Desempenho em Jogos</h4>
                        <div class="flex items-center">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-gaming-1">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-blue-600 h-4 rounded-full" id="compare-gaming-bar-1" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        <div class="flex items-center mt-2">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-gaming-2">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-purple-600 h-4 rounded-full" id="compare-gaming-bar-2" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        <div class="flex items-center mt-2">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-gaming-3">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-green-600 h-4 rounded-full" id="compare-gaming-bar-3" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div>
                        <h4 class="font-medium text-gray-700 mb-3">Desempenho em Produtividade</h4>
                        <div class="flex items-center">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-productivity-1">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-blue-600 h-4 rounded-full" id="compare-productivity-bar-1" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        <div class="flex items-center mt-2">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-productivity-2">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-purple-600 h-4 rounded-full" id="compare-productivity-bar-2" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        <div class="flex items-center mt-2">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-productivity-3">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-green-600 h-4 rounded-full" id="compare-productivity-bar-3" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div>
                        <h4 class="font-medium text-gray-700 mb-3">Desempenho em Edição de Vídeo</h4>
                        <div class="flex items-center">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-video-1">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-blue-600 h-4 rounded-full" id="compare-video-bar-1" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        <div class="flex items-center mt-2">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-video-2">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-purple-600 h-4 rounded-full" id="compare-video-bar-2" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        <div class="flex items-center mt-2">
                            <div class="w-24 text-right mr-4">
                                <span class="text-sm font-medium" id="compare-video-3">-</span>
                            </div>
                            <div class="flex-grow">
                                <div class="w-full bg-gray-200 rounded-full h-4">
                                    <div class="bg-green-600 h-4 rounded-full" id="compare-video-bar-3" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 pt-4 border-t border-gray-200">
                        <div class="bg-gray-50 p-4 rounded-lg">
                            <div class="flex justify-between mb-2">
                                <span class="text-gray-600">Preço Total:</span>
                                <span class="font-bold text-blue-600" id="compare-price-1">-</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Consumo:</span>
                                <span class="font-medium" id="compare-power-1">-</span>
                            </div>
                        </div>
                        
                        <div class="bg-gray-50 p-4 rounded-lg">
                            <div class="flex justify-between mb-2">
                                <span class="text-gray-600">Preço Total:</span>
                                <span class="font-bold text-purple-600" id="compare-price-2">-</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Consumo:</span>
                                <span class="font-medium" id="compare-power-2">-</span>
                            </div>
                        </div>
                        
                        <div class="bg-gray-50 p-4 rounded-lg">
                            <div class="flex justify-between mb-2">
                                <span class="text-gray-600">Preço Total:</span>
                                <span class="font-bold text-green-600" id="compare-price-3">-</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Consumo:</span>
                                <span class="font-medium" id="compare-power-3">-</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Blog Tab -->
        <div id="blog-tab" class="tab-content hidden">
            <h2 class="text-2xl font-bold mb-6 text-gray-800">Blog e Dicas</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
                <div class="bg-white rounded-xl shadow-md overflow-hidden">
                    <div class="h-48 bg-gradient-to-r from-blue-500 to-indigo-600 flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-20 w-20 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 3v2m6-2v2M9 19v2m6-2v2M5 9H3m2 6H3m18-6h-2m2 6h-2M7 19h10a2 2 0 002-2V7a2 2 0 00-2-2H7a2 2 0 00-2 2v10a2 2 0 002 2zM9 9h6v6H9V9z" />
                        </svg>
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold mb-2 text-gray-800">Como escolher o processador ideal</h3>
                        <p class="text-gray-600 mb-4">Entenda as diferenças entre Intel e AMD, e como escolher o melhor CPU para suas necessidades.</p>
                        <a href="#" class="text-blue-600 font-medium hover:text-blue-800 transition">Ler artigo completo →</a>
                    </div>
                </div>
                
                <div class="bg-white rounded-xl shadow-md overflow-hidden">
                    <div class="h-48 bg-gradient-to-r from-purple-500 to-pink-600 flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-20 w-20 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01" />
                        </svg>
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold mb-2 text-gray-800">Guia de placas de vídeo 2023</h3>
                        <p class="text-gray-600 mb-4">Comparativo entre as principais GPUs do mercado e qual oferece o melhor custo-benefício.</p>
                        <a href="#" class="text-blue-600 font-medium hover:text-blue-800 transition">Ler artigo completo →</a>
                    </div>
                </div>
                
                <div class="bg-white rounded-xl shadow-md overflow-hidden">
                    <div class="h-48 bg-gradient-to-r from-green-500 to-teal-600 flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-20 w-20 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
                        </svg>
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold mb-2 text-gray-800">Fontes de alimentação: o que você precisa saber</h3>
                        <p class="text-gray-600 mb-4">Descubra como calcular a potência necessária e a importância da certificação 80+ para seu PC.</p>
                        <a href="#" class="text-blue-600 font-medium hover:text-blue-800 transition">Ler artigo completo →</a>
                    </div>
                </div>
            </div>
            
            <div class="bg-white rounded-xl shadow-md p-6 mb-8">
                <h3 class="text-xl font-bold mb-4 text-gray-800">Últimas Notícias</h3>
                
                <div class="space-y-6">
                    <div class="flex flex-col md:flex-row gap-4">
                        <div class="md:w-1/4 bg-gray-100 rounded-lg h-24 flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 3v2m6-2v2M9 19v2m6-2v2M5 9H3m2 6H3m18-6h-2m2 6h-2M7 19h10a2 2 0 002-2V7a2 2 0 00-2-2H7a2 2 0 00-2 2v10a2 2 0 002 2zM9 9h6v6H9V9z" />
                            </svg>
                        </div>
                        <div class="md:w-3/4">
                            <h4 class="font-bold text-gray-800 mb-1">Nova geração de processadores AMD Ryzen anunciada</h4>
                            <p class="text-gray-600 mb-2">A AMD revelou sua nova linha de processadores com melhorias significativas de desempenho e eficiência energética.</p>
                            <div class="flex justify-between items-center">
                                <span class="text-sm text-gray-500">Publicado há 2 dias</span>
                                <a href="#" class="text-blue-600 font-medium hover:text-blue-800 transition">Ler mais →</a>
                            </div>
                        </div>
                    </div>
                    
                    <div class="flex flex-col md:flex-row gap-4">
                        <div class="md:w-1/4 bg-gray-100 rounded-lg h-24 flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01" />
                            </svg>
                        </div>
                        <div class="md:w-3/4">
                            <h4 class="font-bold text-gray-800 mb-1">Queda nos preços de placas de vídeo prevista para o próximo trimestre</h4>
                            <p class="text-gray-600 mb-2">Analistas de mercado preveem redução nos preços de GPUs devido ao aumento da oferta e diminuição da demanda de mineradores.</p>
                            <div class="flex justify-between items-center">
                                <span class="text-sm text-gray-500">Publicado há 5 dias</span>
                                <a href="#" class="text-blue-600 font-medium hover:text-blue-800 transition">Ler mais →</a>
                            </div>
                        </div>
                    </div>
                    
                    <div class="flex flex-col md:flex-row gap-4">
                        <div class="md:w-1/4 bg-gray-100 rounded-lg h-24 flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                        </div>
                        <div class="md:w-3/4">
                            <h4 class="font-bold text-gray-800 mb-1">DDR5: Vale a pena o investimento agora?</h4>
                            <p class="text-gray-600 mb-2">Analisamos o custo-benefício das novas memórias DDR5 e se já é hora de fazer o upgrade do seu sistema.</p>
                            <div class="flex justify-between items-center">
                                <span class="text-sm text-gray-500">Publicado há 1 semana</span>
                                <a href="#" class="text-blue-600 font-medium hover:text-blue-800 transition">Ler mais →</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="bg-white rounded-xl shadow-md p-6">
                <h3 class="text-xl font-bold mb-4 text-gray-800">Dicas para Iniciantes</h3>
                
                <div class="space-y-4">
                    <div class="p-4 bg-blue-50 border-l-4 border-blue-500 rounded">
                        <h4 class="font-bold text-gray-800 mb-1">Verifique a compatibilidade dos componentes</h4>
                        <p class="text-gray-600">Certifique-se de que o soquete da CPU é compatível com a placa-mãe e que o tipo de memória RAM é suportado.</p>
                    </div>
                    
                    <div class="p-4 bg-purple-50 border-l-4 border-purple-500 rounded">
                        <h4 class="font-bold text-gray-800 mb-1">Não economize na fonte de alimentação</h4>
                        <p class="text-gray-600">Uma fonte de qualidade protege seu investimento e garante estabilidade ao sistema. Opte por modelos com certificação 80+ Gold ou superior.</p>
                    </div>
                    
                    <div class="p-4 bg-green-50 border-l-4 border-green-500 rounded">
                        <h4 class="font-bold text-gray-800 mb-1">Priorize um SSD como armazenamento principal</h4>
                        <p class="text-gray-600">SSDs oferecem velocidades muito superiores aos HDs tradicionais. Um SSD NVMe para o sistema operacional faz toda a diferença na experiência de uso.</p>
                    </div>
                    
                    <div class="p-4 bg-amber-50 border-l-4 border-amber-500 rounded">
                        <h4 class="font-bold text-gray-800 mb-1">Considere a refrigeração do sistema</h4>
                        <p class="text-gray-600">Um bom fluxo de ar é essencial para manter as temperaturas sob controle. Invista em um gabinete com boa ventilação e coolers de qualidade.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Component Selection Modal -->
    <div id="component-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-xl shadow-xl max-w-4xl w-full max-h-[90vh] overflow-hidden">
            <div class="p-6 border-b border-gray-200 flex justify-between items-center">
                <h3 class="text-xl font-bold text-gray-800" id="modal-title">Selecionar Componente</h3>
                <button onclick="closeComponentModal()" class="text-gray-500 hover:text-gray-700">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
            
            <div class="p-6 border-b border-gray-200">
                <div class="flex flex-wrap gap-3 mb-4">
                    <div class="flex items-center">
                        <span class="text-gray-700 mr-2">Filtrar por:</span>
                    </div>
                    <button class="px-3 py-1 bg-blue-600 text-white rounded hover:bg-blue-700 transition" onclick="filterComponents('all')">Todos</button>
                    <button class="px-3 py-1 bg-gray-200 text-gray-700 rounded hover:bg-gray-300 transition" onclick="filterComponents('price-asc')">Menor Preço</button>
                    <button class="px-3 py-1 bg-gray-200 text-gray-700 rounded hover:bg-gray-300 transition" onclick="filterComponents('price-desc')">Maior Preço</button>
                    <button class="px-3 py-1 bg-gray-200 text-gray-700 rounded hover:bg-gray-300 transition" onclick="filterComponents('performance')">Melhor Desempenho</button>
                </div>
                
                <div class="relative">
                    <input type="text" placeholder="Buscar componentes..." class="w-full p-3 pl-10 border border-gray-300 rounded-lg" id="component-search">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-400 absolute left-3 top-3.5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                    </svg>
                </div>
            </div>
            
            <div class="overflow-y-auto max-h-[50vh] p-6" id="component-list">
                <!-- Components will be loaded here dynamically -->
            </div>
            
            <div class="p-6 border-t border-gray-200 flex justify-end">
                <button onclick="closeComponentModal()" class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg hover:bg-gray-300 transition mr-2">Cancelar</button>
                <button onclick="confirmComponentSelection()" class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition">Confirmar</button>
            </div>
        </div>
    </div>

    <!-- Save Setup Modal -->
    <div id="save-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-xl shadow-xl max-w-md w-full">
            <div class="p-6 border-b border-gray-200">
                <h3 class="text-xl font-bold text-gray-800">Salvar Configuração</h3>
            </div>
            
            <div class="p-6">
                <div class="mb-4">
                    <label for="setup-name" class="block text-gray-700 mb-2">Nome da configuração</label>
                    <input type="text" id="setup-name" class="w-full p-3 border border-gray-300 rounded-lg" placeholder="Ex: Meu PC Gamer">
                </div>
                
                <div class="mb-4">
                    <label for="setup-description" class="block text-gray-700 mb-2">Descrição (opcional)</label>
                    <textarea id="setup-description" class="w-full p-3 border border-gray-300 rounded-lg" rows="3" placeholder="Descreva o propósito desta configuração..."></textarea>
                </div>
                
                <div class="flex items-center mb-4">
                    <input type="checkbox" id="setup-public" class="mr-2">
                    <label for="setup-public" class="text-gray-700">Tornar esta configuração pública</label>
                </div>
            </div>
            
            <div class="p-6 border-t border-gray-200 flex justify-end">
                <button onclick="closeSaveModal()" class="px-4 py-2 bg-gray-200 text-gray-700 rounded-lg hover:bg-gray-300 transition mr-2">Cancelar</button>
                <button onclick="confirmSaveSetup()" class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition">Salvar</button>
            </div>
        </div>
    </div>

    <!-- Success Notification -->
    <div id="notification" class="fixed bottom-4 right-4 bg-green-500 text-white px-6 py-3 rounded-lg shadow-lg transform translate-y-20 opacity-0 transition-all duration-300 flex items-center">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
        </svg>
        <span id="notification-message">Configuração salva com sucesso!</span>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-8 mt-12">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                <div>
                    <h4 class="text-lg font-semibold mb-4">MontaPCBR</h4>
                    <p class="text-gray-400">Seu assistente para montar o PC ideal com as melhores peças e compatibilidade garantida.</p>
                </div>
                <div>
                    <h4 class="text-lg font-semibold mb-4">Links Rápidos</h4>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white transition" onclick="showTab('builder')">Montar PC</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition" onclick="showTab('suggestions')">Sugestões</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition" onclick="showTab('compare')">Comparar</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition" onclick="showTab('blog')">Blog</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-lg font-semibold mb-4">Ajuda</h4>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white transition">FAQ</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Guia de Compatibilidade</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Contato</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Sobre Nós</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-lg font-semibold mb-4">Inscreva-se</h4>
                    <p class="text-gray-400 mb-4">Receba novidades e promoções de componentes</p>
                    <div class="flex">
                        <input type="email" placeholder="Seu e-mail" class="px-4 py-2 rounded-l-lg w-full">
                        <button class="bg-blue-600 text-white px-4 py-2 rounded-r-lg hover:bg-blue-700 transition">Enviar</button>
                    </div>
                </div>
            </div>
            <div class="border-t border-gray-700 mt-8 pt-6 flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-400">© 2023 MontaPCBR. Todos os direitos reservados.</p>
                <div class="flex space-x-4 mt-4 md:mt-0">
                    <a href="#" class="text-gray-400 hover:text-white transition">
                        <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24"><path d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z"></path></svg>
                    </a>
                    <a href="#" class="text-gray-400 hover:text-white transition">
                        <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24"><path d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.```
