<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meu Portfólio GitHub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #0d1117;
            color: #c9d1d9;
        }
        
        .github-btn {
            background-color: #238636;
            transition: background-color 0.3s;
        }
        
        .github-btn:hover {
            background-color: #2ea043;
        }
        
        .github-card {
            background-color: #161b22;
            border: 1px solid #30363d;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .github-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }
        
        .language-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
            margin-right: 5px;
        }
        
        .edit-mode {
            border: 2px dashed #58a6ff;
            padding: 10px;
        }
        
        [contenteditable]:focus {
            outline: none;
            background-color: rgba(56, 139, 253, 0.1);
        }
    </style>
</head>
<body>
    <div class="container mx-auto px-4 py-8 max-w-5xl">
        <!-- Cabeçalho -->
        <header class="flex flex-col md:flex-row items-center justify-between mb-10 p-6 github-card rounded-lg">
            <div class="flex flex-col md:flex-row items-center">
                <div class="relative group">
                    <div id="profile-pic" class="w-32 h-32 rounded-full bg-gray-700 overflow-hidden mb-4 md:mb-0 md:mr-6 flex items-center justify-center text-4xl">
                        <i class="fas fa-user"></i>
                    </div>
                    <div class="hidden group-hover:flex absolute inset-0 bg-black bg-opacity-50 rounded-full items-center justify-center cursor-pointer" onclick="document.getElementById('profile-upload').click()">
                        <i class="fas fa-camera text-white"></i>
                    </div>
                    <input type="file" id="profile-upload" class="hidden" accept="image/*" onchange="updateProfilePic(this)">
                </div>
                <div>
                    <h1 id="user-name" class="text-3xl font-bold text-white" contenteditable="true">Seu Nome</h1>
                    <p id="user-username" class="text-xl text-gray-400" contenteditable="true">@seu_username</p>
                    <p id="user-bio" class="mt-2 text-gray-300" contenteditable="true">Desenvolvedor Full Stack apaixonado por criar soluções inovadoras</p>
                </div>
            </div>
            <div class="mt-4 md:mt-0">
                <button class="github-btn text-white px-4 py-2 rounded-md font-medium" onclick="toggleEditMode()">
                    <i class="fas fa-edit mr-2"></i>
                    <span id="edit-btn-text">Modo Edição</span>
                </button>
            </div>
        </header>

        <!-- Estatísticas -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-10">
            <div class="github-card rounded-lg p-6 flex items-center">
                <div class="bg-purple-500 bg-opacity-20 p-3 rounded-lg mr-4">
                    <i class="fas fa-code-branch text-purple-400 text-xl"></i>
                </div>
                <div>
                    <h3 class="text-gray-400 text-sm">Repositórios</h3>
                    <p id="repo-count" class="text-2xl font-bold text-white" contenteditable="true">24</p>
                </div>
            </div>
            <div class="github-card rounded-lg p-6 flex items-center">
                <div class="bg-green-500 bg-opacity-20 p-3 rounded-lg mr-4">
                    <i class="fas fa-users text-green-400 text-xl"></i>
                </div>
                <div>
                    <h3 class="text-gray-400 text-sm">Seguidores</h3>
                    <p id="followers-count" class="text-2xl font-bold text-white" contenteditable="true">142</p>
                </div>
            </div>
            <div class="github-card rounded-lg p-6 flex items-center">
                <div class="bg-blue-500 bg-opacity-20 p-3 rounded-lg mr-4">
                    <i class="fas fa-star text-blue-400 text-xl"></i>
                </div>
                <div>
                    <h3 class="text-gray-400 text-sm">Estrelas</h3>
                    <p id="stars-count" class="text-2xl font-bold text-white" contenteditable="true">78</p>
                </div>
            </div>
        </div>

        <!-- Sobre -->
        <div class="github-card rounded-lg p-6 mb-10">
            <h2 class="text-xl font-bold text-white mb-4 flex items-center">
                <i class="fas fa-user-circle mr-2 text-gray-400"></i>
                Sobre
            </h2>
            <div id="about-content" class="text-gray-300" contenteditable="true">
                <p>Olá! Sou um desenvolvedor apaixonado por tecnologia e inovação. Tenho experiência em desenvolvimento web, mobile e aplicações backend.</p>
                <p class="mt-2">Atualmente trabalho com React, Node.js e TypeScript, mas estou sempre aberto a aprender novas tecnologias.</p>
            </div>
        </div>

        <!-- Habilidades -->
        <div class="github-card rounded-lg p-6 mb-10">
            <h2 class="text-xl font-bold text-white mb-4 flex items-center">
                <i class="fas fa-code mr-2 text-gray-400"></i>
                Habilidades
            </h2>
            <div id="skills-container" class="flex flex-wrap gap-2">
                <span class="bg-blue-900 bg-opacity-40 text-blue-300 px-3 py-1 rounded-full">JavaScript</span>
                <span class="bg-blue-900 bg-opacity-40 text-blue-300 px-3 py-1 rounded-full">React</span>
                <span class="bg-green-900 bg-opacity-40 text-green-300 px-3 py-1 rounded-full">Node.js</span>
                <span class="bg-blue-900 bg-opacity-40 text-blue-300 px-3 py-1 rounded-full">TypeScript</span>
                <span class="bg-purple-900 bg-opacity-40 text-purple-300 px-3 py-1 rounded-full">CSS</span>
                <span class="bg-orange-900 bg-opacity-40 text-orange-300 px-3 py-1 rounded-full">HTML</span>
                <span class="bg-red-900 bg-opacity-40 text-red-300 px-3 py-1 rounded-full">Git</span>
                <span class="bg-green-900 bg-opacity-40 text-green-300 px-3 py-1 rounded-full">MongoDB</span>
            </div>
            <div class="mt-4 hidden" id="add-skill-container">
                <div class="flex">
                    <input type="text" id="new-skill" placeholder="Nova habilidade" class="bg-gray-800 text-white px-3 py-2 rounded-md mr-2 flex-grow">
                    <select id="skill-color" class="bg-gray-800 text-white px-3 py-2 rounded-md mr-2">
                        <option value="blue">Azul</option>
                        <option value="green">Verde</option>
                        <option value="red">Vermelho</option>
                        <option value="purple">Roxo</option>
                        <option value="orange">Laranja</option>
                        <option value="pink">Rosa</option>
                    </select>
                    <button onclick="addSkill()" class="github-btn text-white px-4 py-2 rounded-md">Adicionar</button>
                </div>
            </div>
        </div>

        <!-- Projetos -->
        <div class="mb-10">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-xl font-bold text-white flex items-center">
                    <i class="fas fa-project-diagram mr-2 text-gray-400"></i>
                    Projetos em Destaque
                </h2>
                <button id="add-project-btn" class="hidden github-btn text-white px-4 py-2 rounded-md text-sm">
                    <i class="fas fa-plus mr-2"></i>
                    Adicionar Projeto
                </button>
            </div>
            
            <div id="projects-container" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Projeto 1 -->
                <div class="github-card rounded-lg p-6 project-card">
                    <div class="flex justify-between">
                        <h3 class="text-lg font-semibold text-white project-title" contenteditable="true">Awesome App</h3>
                        <div class="project-actions hidden">
                            <button class="text-gray-400 hover:text-white" onclick="removeProject(this)">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    </div>
                    <p class="text-gray-400 mt-2 project-description" contenteditable="true">Um aplicativo incrível construído com React e Node.js que resolve problemas do mundo real.</p>
                    <div class="mt-4 flex items-center">
                        <span class="language-dot bg-yellow-500"></span>
                        <span class="text-gray-400 project-language" contenteditable="true">JavaScript</span>
                    </div>
                    <div class="mt-4 flex justify-between">
                        <div class="flex items-center">
                            <i class="fas fa-star mr-1 text-gray-400"></i>
                            <span class="text-gray-400 project-stars" contenteditable="true">45</span>
                            <i class="fas fa-code-branch ml-3 mr-1 text-gray-400"></i>
                            <span class="text-gray-400 project-forks" contenteditable="true">12</span>
                        </div>
                        <a href="#" class="text-blue-400 hover:underline project-link" contenteditable="true">github.com/user/awesome-app</a>
                    </div>
                </div>
                
                <!-- Projeto 2 -->
                <div class="github-card rounded-lg p-6 project-card">
                    <div class="flex justify-between">
                        <h3 class="text-lg font-semibold text-white project-title" contenteditable="true">Data Visualizer</h3>
                        <div class="project-actions hidden">
                            <button class="text-gray-400 hover:text-white" onclick="removeProject(this)">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    </div>
                    <p class="text-gray-400 mt-2 project-description" contenteditable="true">Uma ferramenta de visualização de dados poderosa que transforma dados complexos em gráficos interativos.</p>
                    <div class="mt-4 flex items-center">
                        <span class="language-dot bg-blue-500"></span>
                        <span class="text-gray-400 project-language" contenteditable="true">TypeScript</span>
                    </div>
                    <div class="mt-4 flex justify-between">
                        <div class="flex items-center">
                            <i class="fas fa-star mr-1 text-gray-400"></i>
                            <span class="text-gray-400 project-stars" contenteditable="true">32</span>
                            <i class="fas fa-code-branch ml-3 mr-1 text-gray-400"></i>
                            <span class="text-gray-400 project-forks" contenteditable="true">8</span>
                        </div>
                        <a href="#" class="text-blue-400 hover:underline project-link" contenteditable="true">github.com/user/data-visualizer</a>
                    </div>
                </div>
            </div>
        </div>

        <!-- Contato -->
        <div class="github-card rounded-lg p-6">
            <h2 class="text-xl font-bold text-white mb-4 flex items-center">
                <i class="fas fa-envelope mr-2 text-gray-400"></i>
                Contato
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="flex items-center">
                    <div class="bg-gray-800 p-3 rounded-lg mr-3">
                        <i class="fas fa-envelope text-blue-400"></i>
                    </div>
                    <span id="contact-email" class="text-gray-300" contenteditable="true">seuemail@exemplo.com</span>
                </div>
                <div class="flex items-center">
                    <div class="bg-gray-800 p-3 rounded-lg mr-3">
                        <i class="fab fa-linkedin text-blue-400"></i>
                    </div>
                    <span id="contact-linkedin" class="text-gray-300" contenteditable="true">linkedin.com/in/seuperfil</span>
                </div>
                <div class="flex items-center">
                    <div class="bg-gray-800 p-3 rounded-lg mr-3">
                        <i class="fab fa-twitter text-blue-400"></i>
                    </div>
                    <span id="contact-twitter" class="text-gray-300" contenteditable="true">@seutwitter</span>
                </div>
                <div class="flex items-center">
                    <div class="bg-gray-800 p-3 rounded-lg mr-3">
                        <i class="fas fa-globe text-blue-400"></i>
                    </div>
                    <span id="contact-website" class="text-gray-300" contenteditable="true">seusite.com</span>
                </div>
            </div>
        </div>

        <!-- Modal para adicionar projeto -->
        <div id="add-project-modal" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center z-50 hidden">
            <div class="bg-gray-800 rounded-lg p-6 w-full max-w-md">
                <h3 class="text-xl font-bold text-white mb-4">Adicionar Novo Projeto</h3>
                <div class="mb-4">
                    <label class="block text-gray-400 mb-2">Título do Projeto</label>
                    <input type="text" id="new-project-title" class="w-full bg-gray-700 text-white px-3 py-2 rounded-md">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-400 mb-2">Descrição</label>
                    <textarea id="new-project-description" class="w-full bg-gray-700 text-white px-3 py-2 rounded-md" rows="3"></textarea>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-400 mb-2">Linguagem</label>
                    <input type="text" id="new-project-language" class="w-full bg-gray-700 text-white px-3 py-2 rounded-md">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-400 mb-2">Cor da Linguagem</label>
                    <select id="new-project-color" class="w-full bg-gray-700 text-white px-3 py-2 rounded-md">
                        <option value="yellow">Amarelo</option>
                        <option value="blue">Azul</option>
                        <option value="green">Verde</option>
                        <option value="red">Vermelho</option>
                        <option value="purple">Roxo</option>
                    </select>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-400 mb-2">Estrelas</label>
                    <input type="number" id="new-project-stars" class="w-full bg-gray-700 text-white px-3 py-2 rounded-md">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-400 mb-2">Forks</label>
                    <input type="number" id="new-project-forks" class="w-full bg-gray-700 text-white px-3 py-2 rounded-md">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-400 mb-2">Link</label>
                    <input type="text" id="new-project-link" class="w-full bg-gray-700 text-white px-3 py-2 rounded-md">
                </div>
                <div class="flex justify-end">
                    <button class="bg-gray-600 text-white px-4 py-2 rounded-md mr-2" onclick="closeProjectModal()">Cancelar</button>
                    <button class="github-btn text-white px-4 py-2 rounded-md" onclick="saveNewProject()">Salvar</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        let editMode = false;
        
        function toggleEditMode() {
            editMode = !editMode;
            
            const editBtnText = document.getElementById('edit-btn-text');
            const addProjectBtn = document.getElementById('add-project-btn');
            const addSkillContainer = document.getElementById('add-skill-container');
            const projectActions = document.querySelectorAll('.project-actions');
            
            if (editMode) {
                editBtnText.textContent = 'Salvar Alterações';
                addProjectBtn.classList.remove('hidden');
                addSkillContainer.classList.remove('hidden');
                projectActions.forEach(action => action.classList.remove('hidden'));
            } else {
                editBtnText.textContent = 'Modo Edição';
                addProjectBtn.classList.add('hidden');
                addSkillContainer.classList.add('hidden');
                projectActions.forEach(action => action.classList.add('hidden'));
                
                // Aqui você poderia adicionar código para salvar as alterações em um backend
                alert('Alterações salvas com sucesso!');
            }
        }
        
        function updateProfilePic(input) {
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    const profilePic = document.getElementById('profile-pic');
                    profilePic.innerHTML = '';
                    profilePic.style.backgroundImage = `url('${e.target.result}')`;
                    profilePic.style.backgroundSize = 'cover';
                    profilePic.style.backgroundPosition = 'center';
                };
                
                reader.readAsDataURL(input.files[0]);
            }
        }
        
        function addSkill() {
            const skillName = document.getElementById('new-skill').value.trim();
            const skillColor = document.getElementById('skill-color').value;
            
            if (skillName) {
                const skillsContainer = document.getElementById('skills-container');
                
                const colorClasses = {
                    blue: 'bg-blue-900 bg-opacity-40 text-blue-300',
                    green: 'bg-green-900 bg-opacity-40 text-green-300',
                    red: 'bg-red-900 bg-opacity-40 text-red-300',
                    purple: 'bg-purple-900 bg-opacity-40 text-purple-300',
                    orange: 'bg-orange-900 bg-opacity-40 text-orange-300',
                    pink: 'bg-pink-900 bg-opacity-40 text-pink-300'
                };
                
                const skillSpan = document.createElement('span');
                skillSpan.className = `${colorClasses[skillColor]} px-3 py-1 rounded-full`;
                skillSpan.textContent = skillName;
                
                skillsContainer.appendChild(skillSpan);
                document.getElementById('new-skill').value = '';
            }
        }
        
        function openProjectModal() {
            document.getElementById('add-project-modal').classList.remove('hidden');
        }
        
        function closeProjectModal() {
            document.getElementById('add-project-modal').classList.add('hidden');
        }
        
        function saveNewProject() {
            const title = document.getElementById('new-project-title').value.trim();
            const description = document.getElementById('new-project-description').value.trim();
            const language = document.getElementById('new-project-language').value.trim();
            const color = document.getElementById('new-project-color').value;
            const stars = document.getElementById('new-project-stars').value || '0';
            const forks = document.getElementById('new-project-forks').value || '0';
            const link = document.getElementById('new-project-link').value.trim() || '#';
            
            if (title && description) {
                const projectsContainer = document.getElementById('projects-container');
                
                const projectHTML = `
                    <div class="github-card rounded-lg p-6 project-card">
                        <div class="flex justify-between">
                            <h3 class="text-lg font-semibold text-white project-title" contenteditable="true">${title}</h3>
                            <div class="project-actions">
                                <button class="text-gray-400 hover:text-white" onclick="removeProject(this)">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </div>
                        </div>
                        <p class="text-gray-400 mt-2 project-description" contenteditable="true">${description}</p>
                        <div class="mt-4 flex items-center">
                            <span class="language-dot bg-${color}-500"></span>
                            <span class="text-gray-400 project-language" contenteditable="true">${language}</span>
                        </div>
                        <div class="mt-4 flex justify-between">
                            <div class="flex items-center">
                                <i class="fas fa-star mr-1 text-gray-400"></i>
                                <span class="text-gray-400 project-stars" contenteditable="true">${stars}</span>
                                <i class="fas fa-code-branch ml-3 mr-1 text-gray-400"></i>
                                <span class="text-gray-400 project-forks" contenteditable="true">${forks}</span>
                            </div>
                            <a href="#" class="text-blue-400 hover:underline project-link" contenteditable="true">${link}</a>
                        </div>
                    </div>
                `;
                
                projectsContainer.innerHTML += projectHTML;
                closeProjectModal();
                
                // Limpar campos
                document.getElementById('new-project-title').value = '';
                document.getElementById('new-project-description').value = '';
                document.getElementById('new-project-language').value = '';
                document.getElementById('new-project-stars').value = '';
                document.getElementById('new-project-forks').value = '';
                document.getElementById('new-project-link').value = '';
            }
        }
        
        function removeProject(button) {
            const projectCard = button.closest('.project-card');
            projectCard.remove();
        }
        
        // Inicializar
        document.getElementById('add-project-btn').addEventListener('click', openProjectModal);
    </script>
</body>
</html>
