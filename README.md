<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plataforma Escolar</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2980b9;
            --success: #2ecc71;
            --warning: #f39c12;
            --danger: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --gray: #95a5a6;
            --light-gray: #bdc3c7;
            --admin: #9b59b6;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: var(--dark);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Login Page */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
        }
        
        .login-form {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px;
        }
        
        .login-form h1 {
            text-align: center;
            margin-bottom: 20px;
            color: var(--dark);
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--light-gray);
            border-radius: 5px;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        .btn {
            display: inline-block;
            padding: 12px 24px;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 500;
            transition: background-color 0.3s;
            text-align: center;
        }
        
        .btn:hover {
            background-color: var(--secondary);
        }
        
        .btn-secondary {
            background-color: var(--gray);
        }
        
        .btn-secondary:hover {
            background-color: #7f8c8d;
        }
        
        .btn-small {
            padding: 8px 16px;
            font-size: 14px;
        }
        
        .btn-danger {
            background-color: var(--danger);
        }
        
        .btn-danger:hover {
            background-color: #c0392b;
        }
        
        .btn-admin {
            background-color: var(--admin);
        }
        
        .btn-admin:hover {
            background-color: #8e44ad;
        }
        
        .register-link {
            text-align: center;
            margin-top: 20px;
        }
        
        .register-link a {
            color: var(--primary);
            text-decoration: none;
        }
        
        .register-link a:hover {
            text-decoration: underline;
        }
        
        /* Dashboard */
        .dashboard {
            display: none;
        }
        
        .header {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .admin-badge {
            background-color: var(--admin);
            color: white;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            margin-left: 10px;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .user-name {
            font-weight: 500;
        }
        
        .nav-tabs {
            display: flex;
            background-color: white;
            border-bottom: 1px solid var(--light-gray);
            overflow-x: auto;
        }
        
        .nav-tab {
            padding: 15px 20px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            white-space: nowrap;
            transition: all 0.3s;
        }
        
        .nav-tab.active {
            border-bottom-color: var(--primary);
            color: var(--primary);
            font-weight: 500;
        }
        
        .nav-tab.admin-active {
            border-bottom-color: var(--admin);
            color: var(--admin);
        }
        
        .tab-content {
            padding: 20px 0;
        }
        
        .tab-pane {
            display: none;
        }
        
        .tab-pane.active {
            display: block;
        }
        
        /* Horário */
        .schedule-container {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            overflow-x: auto;
        }
        
        .schedule {
            width: 100%;
            min-width: 800px;
            border-collapse: collapse;
        }
        
        .schedule th, .schedule td {
            padding: 12px 8px;
            text-align: center;
            border: 1px solid var(--light-gray);
        }
        
        .schedule th {
            background-color: var(--primary);
            color: white;
            font-weight: 500;
        }
        
        .schedule td {
            cursor: pointer;
            transition: background-color 0.3s;
            height: 60px;
        }
        
        .schedule td:hover {
            background-color: #f0f7ff;
        }
        
        .schedule td.free {
            background-color: var(--light-gray);
            color: #7f8c8d;
        }
        
        .schedule td.has-content {
            background-color: #e1f5fe;
        }
        
        /* Listas */
        .list-container {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            margin-bottom: 20px;
        }
        
        .list-header {
            padding: 15px 20px;
            background-color: #f8f9fa;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .list-title {
            font-size: 18px;
            font-weight: 600;
        }
        
        .list-actions {
            display: flex;
            gap: 10px;
        }
        
        .list-items {
            max-height: 500px;
            overflow-y: auto;
        }
        
        .list-item {
            padding: 15px 20px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .list-item:last-child {
            border-bottom: none;
        }
        
        .item-actions {
            display: flex;
            gap: 10px;
        }
        
        .action-btn {
            background: none;
            border: none;
            cursor: pointer;
            color: var(--primary);
            font-size: 14px;
            padding: 5px 10px;
            border-radius: 3px;
            transition: background-color 0.3s;
        }
        
        .action-btn:hover {
            background-color: #f0f7ff;
        }
        
        .action-btn.delete {
            color: var(--danger);
        }
        
        .action-btn.delete:hover {
            background-color: #fde8e6;
        }
        
        .action-btn.edit {
            color: var(--warning);
        }
        
        .action-btn.edit:hover {
            background-color: #fef5e7;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 10px;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        .modal-header {
            padding: 20px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-title {
            font-size: 20px;
            font-weight: 600;
        }
        
        .close-modal {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--gray);
        }
        
        .modal-body {
            padding: 20px;
        }
        
        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-col {
            flex: 1;
        }
        
        .students-list {
            margin-top: 20px;
            max-height: 300px;
            overflow-y: auto;
            border: 1px solid var(--light-gray);
            border-radius: 5px;
        }
        
        .student-item {
            padding: 10px 15px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .student-item:last-child {
            border-bottom: none;
        }
        
        .absence-select {
            padding: 5px 10px;
            border-radius: 5px;
            border: 1px solid var(--light-gray);
        }
        
        .modal-footer {
            padding: 20px;
            border-top: 1px solid var(--light-gray);
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }
        
        /* Mensagens */
        .messages-container {
            display: flex;
            gap: 20px;
        }
        
        .messages-sidebar {
            flex: 0 0 300px;
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .messages-list {
            max-height: 600px;
            overflow-y: auto;
        }
        
        .message-item {
            padding: 15px;
            border-bottom: 1px solid var(--light-gray);
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .message-item:hover, .message-item.active {
            background-color: #f0f7ff;
        }
        
        .message-sender {
            font-weight: 500;
            margin-bottom: 5px;
        }
        
        .message-preview {
            color: var(--gray);
            font-size: 14px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .message-date {
            font-size: 12px;
            color: var(--gray);
            margin-top: 5px;
        }
        
        .messages-content {
            flex: 1;
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5x 15px rgba(0, 0, 0, 0.05);
        }
        
        .message-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .message-subject {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .message-meta {
            display: flex;
            justify-content: space-between;
            color: var(--gray);
            font-size: 14px;
        }
        
        .message-body {
            padding: 20px;
            min-height: 300px;
        }
        
        .new-message-btn {
            margin-bottom: 20px;
        }
        
        /* Definições */
        .settings-section {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .settings-section h3 {
            margin-bottom: 15px;
            color: var(--primary);
            border-bottom: 1px solid var(--light-gray);
            padding-bottom: 10px;
        }
        
        /* Admin */
        .admin-section {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            border-left: 4px solid var(--admin);
        }
        
        .admin-section h3 {
            margin-bottom: 15px;
            color: var(--admin);
            border-bottom: 1px solid var(--light-gray);
            padding-bottom: 10px;
        }
        
        .user-type-badge {
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 500;
        }
        
        .badge-professor {
            background-color: var(--primary);
            color: white;
        }
        
        .badge-encarregado {
            background-color: var(--success);
            color: white;
        }
        
        .badge-aluno {
            background-color: var(--warning);
            color: white;
        }
        
        .badge-admin {
            background-color: var(--admin);
            color: white;
        }
        
        /* Responsividade */
        @media (max-width: 768px) {
            .messages-container {
                flex-direction: column;
            }
            
            .messages-sidebar {
                flex: 1;
            }
            
            .form-row {
                flex-direction: column;
                gap: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Página de Login -->
    <div id="loginPage" class="login-container">
        <div class="login-form">
            <h1>Plataforma Escolar</h1>
            <form id="loginForm">
                <div class="form-group">
                    <label for="username">Nome de utilizador</label>
                    <input type="text" id="username" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" class="form-control" required>
                </div>
                <button type="submit" class="btn">Entrar</button>
            </form>
            <div class="register-link">
                <p>Não tem conta? <a href="#" id="showRegister">Registe-se</a></p>
            </div>
        </div>
    </div>

    <!-- Página de Registo -->
    <div id="registerPage" class="login-container" style="display: none;">
        <div class="login-form">
            <h1>Criar Conta</h1>
            <form id="registerForm">
                <div class="form-group">
                    <label for="regType">Tipo de conta</label>
                    <select id="regType" class="form-control" required>
                        <option value="">Selecione...</option>
                        <option value="professor">Professor</option>
                        <option value="encarregado">Encarregado de Educação</option>
                        <option value="aluno">Aluno</option>
                    </select>
                </div>
                <div class="form-group" id="codeField" style="display: none;">
                    <label for="profCode">Código de Professor</label>
                    <input type="text" id="profCode" class="form-control" placeholder="Ex: 33SP">
                </div>
                <div class="form-group">
                    <label for="regUsername">Nome de utilizador</label>
                    <input type="text" id="regUsername" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="regPassword">Password</label>
                    <input type="password" id="regPassword" class="form-control" required>
                </div>
                <div class="form-group" id="studentField" style="display: none;">
                    <label for="studentName">Nome do aluno</label>
                    <input type="text" id="studentName" class="form-control">
                </div>
                <div class="form-group" id="classField" style="display: none;">
                    <label for="studentClass">Turma</label>
                    <select id="studentClass" class="form-control">
                        <option value="">Selecione a turma...</option>
                    </select>
                </div>
                <button type="submit" class="btn">Criar Conta</button>
            </form>
            <div class="register-link">
                <p>Já tem conta? <a href="#" id="showLogin">Faça login</a></p>
            </div>
        </div>
    </div>

    <!-- Dashboard -->
    <div id="dashboard" class="dashboard">
        <header class="header">
            <div class="container header-content">
                <div class="logo">Plataforma Escolar
                    <span id="adminBadge" class="admin-badge" style="display: none;">ADMIN</span>
                </div>
                <div class="user-info">
                    <span class="user-name" id="currentUserName">Utilizador</span>
                    <button id="settingsBtn" class="btn btn-secondary btn-small">Definições</button>
                    <button id="logoutBtn" class="btn btn-secondary">Sair</button>
                </div>
            </div>
        </header>
        
        <div class="nav-tabs">
            <div class="container" style="display: flex; padding: 0;">
                <div class="nav-tab active" data-tab="horario">Horário</div>
                <div class="nav-tab" data-tab="sumarios">Sumários e Faltas</div>
                <div class="nav-tab" data-tab="testes">Testes</div>
                <div class="nav-tab" data-tab="correio">Correio</div>
                <div class="nav-tab" data-tab="turmas" id="turmasTab" style="display: none;">Turmas</div>
                <div class="nav-tab" data-tab="definicoes" id="definicoesTab" style="display: none;">Definições</div>
                <div class="nav-tab" data-tab="admin" id="adminTab" style="display: none;">Administração</div>
            </div>
        </div>
        
        <div class="container tab-content">
            <!-- Horário -->
            <div id="horario" class="tab-pane active">
                <div class="list-actions" id="scheduleActions" style="margin-bottom: 20px; display: none;">
                    <button class="btn btn-admin" id="editScheduleBtn">Editar Horário</button>
                </div>
                <div class="schedule-container">
                    <table class="schedule" id="scheduleTable">
                        <!-- Horário será gerado dinamicamente -->
                    </table>
                </div>
            </div>
            
            <!-- Sumários e Faltas -->
            <div id="sumarios" class="tab-pane">
                <div class="list-container">
                    <div class="list-header">
                        <div class="list-title">Sumários Registados</div>
                        <div class="list-actions" id="sumarioActions" style="display: none;">
                            <button class="btn" id="addSummaryBtn">Adicionar Sumário</button>
                        </div>
                    </div>
                    <div class="list-items" id="summariesList">
                        <!-- Sumários serão carregados dinamicamente -->
                    </div>
                </div>
            </div>
            
            <!-- Testes -->
            <div id="testes" class="tab-pane">
                <div class="list-container">
                    <div class="list-header">
                        <div class="list-title">Testes Marcados</div>
                        <div class="list-actions" id="testActions" style="display: none;">
                            <button class="btn" id="addTestBtn">Adicionar Teste</button>
                        </div>
                    </div>
                    <div class="list-items" id="testsList">
                        <!-- Testes serão carregados dinamicamente -->
                    </div>
                </div>
            </div>
            
            <!-- Correio -->
            <div id="correio" class="tab-pane">
                <button class="btn new-message-btn" id="newMessageBtn">Nova Mensagem</button>
                <div class="messages-container">
                    <div class="messages-sidebar">
                        <div class="messages-list" id="messagesList">
                            <!-- Mensagens serão carregadas dinamicamente -->
                        </div>
                    </div>
                    <div class="messages-content">
                        <div class="message-header">
                            <div class="message-subject" id="messageSubject">Selecione uma mensagem</div>
                            <div class="message-meta">
                                <span id="messageSender">De: -</span>
                                <span id="messageDate">Data: -</span>
                            </div>
                        </div>
                        <div class="message-body" id="messageBody">
                            <p>Selecione uma mensagem da lista para visualizar o seu conteúdo.</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Turmas (apenas para professores e admin) -->
            <div id="turmas" class="tab-pane">
                <div class="list-container">
                    <div class="list-header">
                        <div class="list-title">Turmas</div>
                        <div class="list-actions">
                            <button class="btn" id="addClassBtn">Adicionar Turma</button>
                            <button class="btn" id="addStudentBtn">Adicionar Aluno</button>
                        </div>
                    </div>
                    <div class="list-items" id="classesList">
                        <!-- Turmas serão carregadas dinamicamente -->
                    </div>
                </div>
                
                <div class="list-container" id="studentsContainer" style="display: none;">
                    <div class="list-header">
                        <div class="list-title" id="studentsTitle">Alunos da Turma</div>
                    </div>
                    <div class="list-items" id="studentsList">
                        <!-- Alunos serão carregados dinamicamente -->
                    </div>
                </div>
            </div>
            
            <!-- Definições -->
            <div id="definicoes" class="tab-pane">
                <div class="settings-section">
                    <h3>Alterar Dados Pessoais</h3>
                    <form id="profileForm">
                        <div class="form-group">
                            <label for="profileName">Nome</label>
                            <input type="text" id="profileName" class="form-control" required>
                        </div>
                        <div class="form-group" id="profileStudentNameField" style="display: none;">
                            <label for="profileStudentName">Nome do Aluno</label>
                            <input type="text" id="profileStudentName" class="form-control">
                        </div>
                        <div class="form-group">
                            <label for="profileUsername">Nome de Utilizador</label>
                            <input type="text" id="profileUsername" class="form-control" required>
                        </div>
                        <button type="submit" class="btn">Guardar Alterações</button>
                    </form>
                </div>
                
                <div class="settings-section">
                    <h3>Alterar Password</h3>
                    <form id="passwordForm">
                        <div class="form-group">
                            <label for="currentPassword">Password Atual</label>
                            <input type="password" id="currentPassword" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="newPassword">Nova Password</label>
                            <input type="password" id="newPassword" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="confirmPassword">Confirmar Nova Password</label>
                            <input type="password" id="confirmPassword" class="form-control" required>
                        </div>
                        <button type="submit" class="btn">Alterar Password</button>
                    </form>
                </div>
                
                <div class="settings-section">
                    <h3>Eliminar Conta</h3>
                    <p class="form-group">Esta ação é irreversível. Todos os seus dados serão permanentemente eliminados.</p>
                    <button class="btn btn-danger" id="deleteAccountBtn">Eliminar Minha Conta</button>
                </div>
            </div>
            
            <!-- Administração -->
            <div id="admin" class="tab-pane">
                <div class="admin-section">
                    <h3>Gestão de Utilizadores</h3>
                    <div class="list-container">
                        <div class="list-header">
                            <div class="list-title">Todos os Utilizadores</div>
                        </div>
                        <div class="list-items" id="usersList">
                            <!-- Utilizadores serão carregados dinamicamente -->
                        </div>
                    </div>
                </div>
                
                <div class="admin-section">
                    <h3>Gestão de Turmas</h3>
                    <div class="list-container">
                        <div class="list-header">
                            <div class="list-title">Todas as Turmas</div>
                            <div class="list-actions">
                                <button class="btn btn-admin" id="adminAddClassBtn">Adicionar Turma</button>
                            </div>
                        </div>
                        <div class="list-items" id="adminClassesList">
                            <!-- Turmas serão carregadas dinamicamente -->
                        </div>
                    </div>
                </div>
                
                <div class="admin-section">
                    <h3>Gestão de Encarregados de Educação</h3>
                    <div class="list-container">
                        <div class="list-header">
                            <div class="list-title">Encarregados de Educação</div>
                            <div class="list-actions">
                                <button class="btn btn-admin" id="adminAddGuardianBtn">Adicionar EE</button>
                            </div>
                        </div>
                        <div class="list-items" id="guardiansList">
                            <!-- EE serão carregados dinamicamente -->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal para adicionar/editar sumário -->
    <div id="summaryModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="summaryModalTitle">Registar Sumário</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="summaryForm">
                    <input type="hidden" id="summaryId">
                    <div class="form-group">
                        <label for="summaryDate">Data e Hora</label>
                        <input type="text" id="summaryDate" class="form-control" readonly>
                    </div>
                    <div class="form-group">
                        <label for="summaryClass">Turma</label>
                        <select id="summaryClass" class="form-control" required>
                            <option value="">Selecione a turma...</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="summarySubject">Disciplina</label>
                        <input type="text" id="summarySubject" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="summaryContent">Sumário</label>
                        <textarea id="summaryContent" class="form-control" rows="4" required></textarea>
                    </div>
                    <div class="form-group">
                        <label>Faltas dos Alunos</label>
                        <div class="students-list" id="studentsAbsenceList">
                            <!-- Lista de alunos será carregada dinamicamente -->
                        </div>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="cancelSummaryBtn">Cancelar</button>
                <button class="btn" id="saveSummaryBtn">Guardar</button>
            </div>
        </div>
    </div>

    <!-- Modal para adicionar teste -->
    <div id="testModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Adicionar Teste</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="testForm">
                    <div class="form-group">
                        <label for="testSubject">Disciplina</label>
                        <input type="text" id="testSubject" class="form-control" required>
                    </div>
                    <div class="form-row">
                        <div class="form-col">
                            <div class="form-group">
                                <label for="testDate">Data</label>
                                <input type="date" id="testDate" class="form-control" required>
                            </div>
                        </div>
                        <div class="form-col">
                            <div class="form-group">
                                <label for="testTime">Hora</label>
                                <input type="time" id="testTime" class="form-control" required>
                            </div>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="testClass">Turma</label>
                        <select id="testClass" class="form-control" required>
                            <option value="">Selecione a turma...</option>
                        </select>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="cancelTestBtn">Cancelar</button>
                <button class="btn" id="saveTestBtn">Guardar</button>
            </div>
        </div>
    </div>

    <!-- Modal para nova mensagem -->
    <div id="messageModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Nova Mensagem</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="messageForm">
                    <div class="form-group">
                        <label for="messageTo">Para</label>
                        <select id="messageTo" class="form-control" required>
                            <option value="">Selecione...</option>
                            <!-- Opções serão carregadas dinamicamente -->
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="messageSubjectInput">Assunto</label>
                        <input type="text" id="messageSubjectInput" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="messageContent">Mensagem</label>
                        <textarea id="messageContent" class="form-control" rows="6" required></textarea>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="cancelMessageBtn">Cancelar</button>
                <button class="btn" id="sendMessageBtn">Enviar</button>
            </div>
        </div>
    </div>

    <!-- Modal para adicionar turma -->
    <div id="classModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Adicionar Turma</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="classForm">
                    <div class="form-group">
                        <label for="className">Nome da Turma</label>
                        <input type="text" id="className" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="classYear">Ano</label>
                        <input type="text" id="classYear" class="form-control" required>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="cancelClassBtn">Cancelar</button>
                <button class="btn" id="saveClassBtn">Guardar</button>
            </div>
        </div>
    </div>

    <!-- Modal para adicionar aluno -->
    <div id="studentModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Adicionar Aluno</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="studentForm">
                    <div class="form-group">
                        <label for="studentUsername">Nome de Utilizador</label>
                        <input type="text" id="studentUsername" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="studentPassword">Password</label>
                        <input type="password" id="studentPassword" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="studentFullName">Nome Completo</label>
                        <input type="text" id="studentFullName" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="studentClassSelect">Turma</label>
                        <select id="studentClassSelect" class="form-control" required>
                            <option value="">Selecione a turma...</option>
                        </select>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="cancelStudentBtn">Cancelar</button>
                <button class="btn" id="saveStudentBtn">Guardar</button>
            </div>
        </div>
    </div>

    <!-- Modal para editar horário -->
    <div id="scheduleModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Editar Horário</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="scheduleForm">
                    <div class="form-group">
                        <label for="scheduleDay">Dia da Semana</label>
                        <select id="scheduleDay" class="form-control" required>
                            <option value="">Selecione o dia...</option>
                            <option value="SEGUNDA">Segunda-feira</option>
                            <option value="TERÇA">Terça-feira</option>
                            <option value="QUARTA">Quarta-feira</option>
                            <option value="QUINTA">Quinta-feira</option>
                            <option value="SEXTA">Sexta-feira</option>
                            <option value="SÁBADO">Sábado</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="scheduleTime">Horário</label>
                        <select id="scheduleTime" class="form-control" required>
                            <option value="">Selecione o horário...</option>
                            <option value="7:00h/7:30h">7:00h-7:30h</option>
                            <option value="7:35h/8:25h">7:35h-8:25h</option>
                            <option value="8:30h/9:20h">8:30h-9:20h</option>
                            <option value="9:30h/10:20h">9:30h-10:20h</option>
                            <option value="10:35h/11:25h">10:35h-11:25h</option>
                            <option value="11:30h/12:20h">11:30h-12:20h</option>
                            <option value="12:30h/13:20h">12:30h-13:20h</option>
                            <option value="13:25h/14:15h">13:25h-14:15h</option>
                            <option value="14:20h/15:10h">14:20h-15:10h</option>
                            <option value="15:25h/16:15h">15:25h-16:15h</option>
                            <option value="16:20h/17:10h">16:20h-17:10h</option>
                            <option value="17:25h/18:15h">17:25h-18:15h</option>
                            <option value="18:20h/19:10h">18:20h-19:10h</option>
                            <option value="19:10h/20:00h">19:10h-20:00h</option>
                            <option value="20:00h/20:30h">20:00h-20:30h</option>
                            <option value="20:30h/21:20h">20:30h-21:20h</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="scheduleSubject">Disciplina</label>
                        <input type="text" id="scheduleSubject" class="form-control" placeholder="Deixe vazio para tempo livre">
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="cancelScheduleBtn">Cancelar</button>
                <button class="btn btn-admin" id="saveScheduleBtn">Guardar Alteração</button>
            </div>
        </div>
    </div>

    <!-- Modal para adicionar EE -->
    <div id="guardianModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Adicionar Encarregado de Educação</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="guardianForm">
                    <div class="form-group">
                        <label for="guardianUsername">Nome de Utilizador</label>
                        <input type="text" id="guardianUsername" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="guardianPassword">Password</label>
                        <input type="password" id="guardianPassword" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="guardianName">Nome do Encarregado</label>
                        <input type="text" id="guardianName" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="guardianStudentName">Nome do Aluno</label>
                        <input type="text" id="guardianStudentName" class="form-control" required>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="cancelGuardianBtn">Cancelar</button>
                <button class="btn btn-admin" id="saveGuardianBtn">Guardar</button>
            </div>
        </div>
    </div>

    <script>
        // Dados da aplicação
        const appData = {
            currentUser: null,
            users: JSON.parse(localStorage.getItem('schoolUsers')) || [],
            classes: JSON.parse(localStorage.getItem('schoolClasses')) || [],
            summaries: JSON.parse(localStorage.getItem('schoolSummaries')) || [],
            tests: JSON.parse(localStorage.getItem('schoolTests')) || [],
            messages: JSON.parse(localStorage.getItem('schoolMessages')) || [],
            schedule: JSON.parse(localStorage.getItem('schoolSchedule')) || generateDefaultSchedule()
        };

        // Criar conta de admin se não existir
        if (!appData.users.find(u => u.type === 'admin')) {
            appData.users.push({
                id: 'admin',
                type: 'admin',
                username: 'admin_3EP',
                password: 'ninguem pode admin3',
                name: 'Administrador',
                studentName: null,
                classId: null
            });
            localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
        }

        // Gerar horário padrão baseado na imagem
        function generateDefaultSchedule() {
            const schedule = {
                "SEGUNDA": {
                    "7:00h/7:30h": { subject: "Dúvidas", free: false },
                    "7:35h/8:25h": { free: true },
                    "8:30h/9:20h": { free: true },
                    "9:30h/10:20h": { free: true },
                    "10:35h/11:25h": { free: true },
                    "11:30h/12:20h": { free: true },
                    "12:30h/13:20h": { free: true },
                    "13:25h/14:15h": { free: true },
                    "14:20h/15:10h": { free: true },
                    "15:25h/16:15h": { free: true },
                    "16:20h/17:10h": { free: true },
                    "17:25h/18:15h": { subject: "MAT", free: false },
                    "18:20h/19:10h": { subject: "FRA", free: false },
                    "19:10h/20:00h": { subject: "ING", free: false },
                    "20:00h/20:30h": { free: true },
                    "20:30h/21:20h": { subject: "LIVRE", free: true }
                },
                "TERÇA": {
                    "7:00h/7:30h": { subject: "Dúvidas", free: false },
                    "7:35h/8:25h": { free: true },
                    "8:30h/9:20h": { free: true },
                    "9:30h/10:20h": { free: true },
                    "10:35h/11:25h": { free: true },
                    "11:30h/12:20h": { free: true },
                    "12:30h/13:20h": { free: true },
                    "13:25h/14:15h": { free: true },
                    "14:20h/15:10h": { subject: "HIS", free: false },
                    "15:25h/16:15h": { subject: "HIS", free: false },
                    "16:20h/17:10h": { subject: "CN/FQ", free: false },
                    "17:25h/18:15h": { subject: "POR", free: false },
                    "18:20h/19:10h": { subject: "LIVRE", free: true },
                    "19:10h/20:00h": { subject: "LIVRE", free: true },
                    "20:00h/20:30h": { free: true },
                    "20:30h/21:20h": { subject: "LIVRE", free: true }
                },
                "QUARTA": {
                    "7:00h/7:30h": { subject: "Dúvidas", free: false },
                    "7:35h/8:25h": { free: true },
                    "8:30h/9:20h": { free: true },
                    "9:30h/10:20h": { free: true },
                    "10:35h/11:25h": { free: true },
                    "11:30h/12:20h": { free: true },
                    "12:30h/13:20h": { free: true },
                    "13:25h/14:15h": { free: true },
                    "14:20h/15:10h": { free: true },
                    "15:25h/16:15h": { free: true },
                    "16:20h/17:10h": { free: true },
                    "17:25h/18:15h": { subject: "POR/GEO", free: false },
                    "18:20h/19:10h": { subject: "FRA/ING", free: false },
                    "19:10h/20:00h": { subject: "FQ/CN", free: false },
                    "20:00h/20:30h": { free: true },
                    "20:30h/21:20h": { subject: "MAT", free: false }
                },
                "QUINTA": {
                    "7:00h/7:30h": { subject: "Dúvidas", free: false },
                    "7:35h/8:25h": { subject: "MAT/CN", free: false },
                    "8:30h/9:20h": { subject: "HIS/GEO", free: false },
                    "9:30h/10:20h": { subject: "ING/FRA", free: false },
                    "10:35h/11:25h": { free: true },
                    "11:30h/12:20h": { free: true },
                    "12:30h/13:20h": { free: true },
                    "13:25h/14:15h": { free: true },
                    "14:20h/15:10h": { free: true },
                    "15:25h/16:15h": { free: true },
                    "16:20h/17:10h": { subject: "MAT", free: false },
                    "17:25h/18:15h": { subject: "CN", free: false },
                    "18:20h/19:10h": { subject: "GEO/HIS", free: false },
                    "19:10h/20:00h": { subject: "POR/ING", free: false },
                    "20:00h/20:30h": { free: true },
                    "20:30h/21:20h": { subject: "LIVRE", free: true }
                },
                "SEXTA": {
                    "7:00h/7:30h": { subject: "Dúvidas", free: false },
                    "7:35h/8:25h": { subject: "M.T.", free: false },
                    "8:30h/9:20h": { subject: "M.T.", free: false },
                    "9:30h/10:20h": { subject: "M.T.", free: false },
                    "10:35h/11:25h": { subject: "M.T.", free: false },
                    "11:30h/12:20h": { free: true },
                    "12:30h/13:20h": { free: true },
                    "13:25h/14:15h": { free: true },
                    "14:20h/15:10h": { free: true },
                    "15:25h/16:15h": { free: true },
                    "16:20h/17:10h": { free: true },
                    "17:25h/18:15h": { subject: "HIS/GEO", free: false },
                    "18:20h/19:10h": { subject: "FQ", free: false },
                    "19:10h/20:00h": { subject: "FRA", free: false },
                    "20:00h/20:30h": { free: true },
                    "20:30h/21:20h": { subject: "LIVRE", free: true }
                },
                "SÁBADO": {
                    "7:00h/7:30h": { free: true },
                    "7:35h/8:25h": { free: true },
                    "8:30h/9:20h": { free: true },
                    "9:30h/10:20h": { free: true },
                    "10:35h/11:25h": { free: true },
                    "11:30h/12:20h": { free: true },
                    "12:30h/13:20h": { free: true },
                    "13:25h/14:15h": { free: true },
                    "14:20h/15:10h": { free: true },
                    "15:25h/16:15h": { free: true },
                    "16:20h/17:10h": { free: true },
                    "17:25h/18:15h": { free: true },
                    "18:20h/19:10h": { free: true },
                    "19:10h/20:00h": { free: true },
                    "20:00h/20:30h": { free: true },
                    "20:30h/21:20h": { free: true }
                }
            };
            
            localStorage.setItem('schoolSchedule', JSON.stringify(schedule));
            return schedule;
        }

        // Elementos DOM
        const loginPage = document.getElementById('loginPage');
        const registerPage = document.getElementById('registerPage');
        const dashboard = document.getElementById('dashboard');
        const loginForm = document.getElementById('loginForm');
        const registerForm = document.getElementById('registerForm');
        const regType = document.getElementById('regType');
        const codeField = document.getElementById('codeField');
        const studentField = document.getElementById('studentField');
        const classField = document.getElementById('classField');
        const showRegister = document.getElementById('showRegister');
        const showLogin = document.getElementById('showLogin');
        const logoutBtn = document.getElementById('logoutBtn');
        const settingsBtn = document.getElementById('settingsBtn');
        const currentUserName = document.getElementById('currentUserName');
        const adminBadge = document.getElementById('adminBadge');
        const navTabs = document.querySelectorAll('.nav-tab');
        const tabPanes = document.querySelectorAll('.tab-pane');
        const scheduleTable = document.getElementById('scheduleTable');
        const summariesList = document.getElementById('summariesList');
        const testsList = document.getElementById('testsList');
        const messagesList = document.getElementById('messagesList');
        const classesList = document.getElementById('classesList');
        const studentsList = document.getElementById('studentsList');
        const usersList = document.getElementById('usersList');
        const adminClassesList = document.getElementById('adminClassesList');
        const guardiansList = document.getElementById('guardiansList');
        const studentsContainer = document.getElementById('studentsContainer');
        const studentsTitle = document.getElementById('studentsTitle');
        const sumarioActions = document.getElementById('sumarioActions');
        const testActions = document.getElementById('testActions');
        const scheduleActions = document.getElementById('scheduleActions');
        const turmasTab = document.getElementById('turmasTab');
        const definicoesTab = document.getElementById('definicoesTab');
        const adminTab = document.getElementById('adminTab');
        const addSummaryBtn = document.getElementById('addSummaryBtn');
        const addTestBtn = document.getElementById('addTestBtn');
        const addClassBtn = document.getElementById('addClassBtn');
        const addStudentBtn = document.getElementById('addStudentBtn');
        const adminAddClassBtn = document.getElementById('adminAddClassBtn');
        const adminAddGuardianBtn = document.getElementById('adminAddGuardianBtn');
        const editScheduleBtn = document.getElementById('editScheduleBtn');
        const newMessageBtn = document.getElementById('newMessageBtn');
        const deleteAccountBtn = document.getElementById('deleteAccountBtn');
        const profileForm = document.getElementById('profileForm');
        const passwordForm = document.getElementById('passwordForm');
        const summaryModal = document.getElementById('summaryModal');
        const testModal = document.getElementById('testModal');
        const messageModal = document.getElementById('messageModal');
        const classModal = document.getElementById('classModal');
        const studentModal = document.getElementById('studentModal');
        const scheduleModal = document.getElementById('scheduleModal');
        const guardianModal = document.getElementById('guardianModal');
        const closeModals = document.querySelectorAll('.close-modal');
        const cancelSummaryBtn = document.getElementById('cancelSummaryBtn');
        const cancelTestBtn = document.getElementById('cancelTestBtn');
        const cancelMessageBtn = document.getElementById('cancelMessageBtn');
        const cancelClassBtn = document.getElementById('cancelClassBtn');
        const cancelStudentBtn = document.getElementById('cancelStudentBtn');
        const cancelScheduleBtn = document.getElementById('cancelScheduleBtn');
        const cancelGuardianBtn = document.getElementById('cancelGuardianBtn');
        const saveSummaryBtn = document.getElementById('saveSummaryBtn');
        const saveTestBtn = document.getElementById('saveTestBtn');
        const sendMessageBtn = document.getElementById('sendMessageBtn');
        const saveClassBtn = document.getElementById('saveClassBtn');
        const saveStudentBtn = document.getElementById('saveStudentBtn');
        const saveScheduleBtn = document.getElementById('saveScheduleBtn');
        const saveGuardianBtn = document.getElementById('saveGuardianBtn');
        const summaryForm = document.getElementById('summaryForm');
        const testForm = document.getElementById('testForm');
        const messageForm = document.getElementById('messageForm');
        const classForm = document.getElementById('classForm');
        const studentForm = document.getElementById('studentForm');
        const scheduleForm = document.getElementById('scheduleForm');
        const guardianForm = document.getElementById('guardianForm');
        const summaryClass = document.getElementById('summaryClass');
        const testClass = document.getElementById('testClass');
        const studentClass = document.getElementById('studentClass');
        const studentClassSelect = document.getElementById('studentClassSelect');
        const messageTo = document.getElementById('messageTo');
        const messageSubject = document.getElementById('messageSubject');
        const messageSender = document.getElementById('messageSender');
        const messageDate = document.getElementById('messageDate');
        const messageBody = document.getElementById('messageBody');
        const studentsAbsenceList = document.getElementById('studentsAbsenceList');
        const profileName = document.getElementById('profileName');
        const profileStudentName = document.getElementById('profileStudentName');
        const profileStudentNameField = document.getElementById('profileStudentNameField');
        const profileUsername = document.getElementById('profileUsername');
        const currentPassword = document.getElementById('currentPassword');
        const newPassword = document.getElementById('newPassword');
        const confirmPassword = document.getElementById('confirmPassword');

        // Event Listeners
        document.addEventListener('DOMContentLoaded', initApp);
        loginForm.addEventListener('submit', handleLogin);
        registerForm.addEventListener('submit', handleRegister);
        regType.addEventListener('change', toggleRegisterFields);
        showRegister.addEventListener('click', showRegisterPage);
        showLogin.addEventListener('click', showLoginPage);
        logoutBtn.addEventListener('click', handleLogout);
        settingsBtn.addEventListener('click', () => switchTab('definicoes'));
        deleteAccountBtn.addEventListener('click', deleteAccount);
        profileForm.addEventListener('submit', updateProfile);
        passwordForm.addEventListener('submit', changePassword);
        editScheduleBtn.addEventListener('click', () => openScheduleModal());
        adminAddClassBtn.addEventListener('click', () => openClassModal());
        adminAddGuardianBtn.addEventListener('click', () => openGuardianModal());
        
        navTabs.forEach(tab => {
            tab.addEventListener('click', () => switchTab(tab.dataset.tab));
        });
        
        addSummaryBtn.addEventListener('click', () => openSummaryModal());
        addTestBtn.addEventListener('click', () => openTestModal());
        addClassBtn.addEventListener('click', () => openClassModal());
        addStudentBtn.addEventListener('click', () => openStudentModal());
        newMessageBtn.addEventListener('click', () => openMessageModal());
        
        closeModals.forEach(btn => {
            btn.addEventListener('click', closeAllModals);
        });
        
        cancelSummaryBtn.addEventListener('click', closeAllModals);
        cancelTestBtn.addEventListener('click', closeAllModals);
        cancelMessageBtn.addEventListener('click', closeAllModals);
        cancelClassBtn.addEventListener('click', closeAllModals);
        cancelStudentBtn.addEventListener('click', closeAllModals);
        cancelScheduleBtn.addEventListener('click', closeAllModals);
        cancelGuardianBtn.addEventListener('click', closeAllModals);
        
        saveSummaryBtn.addEventListener('click', saveSummary);
        saveTestBtn.addEventListener('click', saveTest);
        sendMessageBtn.addEventListener('click', sendMessage);
        saveClassBtn.addEventListener('click', saveClass);
        saveStudentBtn.addEventListener('click', saveStudent);
        saveScheduleBtn.addEventListener('click', saveSchedule);
        saveGuardianBtn.addEventListener('click', saveGuardian);

        // Inicialização da aplicação
        function initApp() {
            // Verificar se há um utilizador logado
            const loggedInUser = localStorage.getItem('currentUser');
            if (loggedInUser) {
                appData.currentUser = JSON.parse(loggedInUser);
                showDashboard();
            }
            
            // Popular lista de turmas no registo de alunos
            updateClassSelect(studentClass);
        }

        // Mostrar página de registo
        function showRegisterPage(e) {
            e.preventDefault();
            loginPage.style.display = 'none';
            registerPage.style.display = 'flex';
        }

        // Mostrar página de login
        function showLoginPage(e) {
            e.preventDefault();
            registerPage.style.display = 'none';
            loginPage.style.display = 'flex';
        }

        // Alternar campos de registo
        function toggleRegisterFields() {
            if (regType.value === 'professor') {
                codeField.style.display = 'block';
                studentField.style.display = 'none';
                classField.style.display = 'none';
            } else if (regType.value === 'encarregado') {
                codeField.style.display = 'none';
                studentField.style.display = 'block';
                classField.style.display = 'none';
            } else if (regType.value === 'aluno') {
                codeField.style.display = 'none';
                studentField.style.display = 'none';
                classField.style.display = 'block';
            } else {
                codeField.style.display = 'none';
                studentField.style.display = 'none';
                classField.style.display = 'none';
            }
        }

        // Processar login
        function handleLogin(e) {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            const user = appData.users.find(u => u.username === username && u.password === password);
            
            if (user) {
                appData.currentUser = user;
                localStorage.setItem('currentUser', JSON.stringify(user));
                showDashboard();
            } else {
                alert('Nome de utilizador ou password incorretos!');
            }
        }

        // Processar registo
        function handleRegister(e) {
            e.preventDefault();
            const type = regType.value;
            const username = document.getElementById('regUsername').value;
            const password = document.getElementById('regPassword').value;
            const studentName = document.getElementById('studentName').value;
            const profCode = document.getElementById('profCode').value;
            const studentClassId = document.getElementById('studentClass').value;
            
            // Verificar se o utilizador já existe
            if (appData.users.find(u => u.username === username)) {
                alert('Nome de utilizador já existe!');
                return;
            }
            
            // Verificar código de professor
            if (type === 'professor' && profCode !== '33SP') {
                alert('Código de professor inválido!');
                return;
            }
            
            // Criar novo utilizador
            const newUser = {
                id: Date.now().toString(),
                type: type,
                username: username,
                password: password,
                name: username,
                studentName: type === 'encarregado' ? studentName : null,
                classId: type === 'aluno' ? studentClassId : null
            };
            
            appData.users.push(newUser);
            localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
            
            alert('Conta criada com sucesso!');
            showLoginPage(e);
        }

        // Mostrar dashboard
        function showDashboard() {
            loginPage.style.display = 'none';
            registerPage.style.display = 'none';
            dashboard.style.display = 'block';
            
            currentUserName.textContent = appData.currentUser.name;
            
            // Mostrar/ocultar ações baseadas no tipo de utilizador
            if (appData.currentUser.type === 'professor') {
                sumarioActions.style.display = 'flex';
                testActions.style.display = 'flex';
                turmasTab.style.display = 'block';
                definicoesTab.style.display = 'block';
                scheduleActions.style.display = 'none';
                adminTab.style.display = 'none';
                adminBadge.style.display = 'none';
            } else if (appData.currentUser.type === 'admin') {
                sumarioActions.style.display = 'flex';
                testActions.style.display = 'flex';
                turmasTab.style.display = 'block';
                definicoesTab.style.display = 'block';
                scheduleActions.style.display = 'flex';
                adminTab.style.display = 'block';
                adminBadge.style.display = 'inline';
                
                // Adicionar classe admin às abas
                document.querySelectorAll('.nav-tab').forEach(tab => {
                    if (tab.dataset.tab === 'admin') {
                        tab.classList.add('admin-active');
                    }
                });
            } else {
                sumarioActions.style.display = 'none';
                testActions.style.display = 'none';
                turmasTab.style.display = 'none';
                definicoesTab.style.display = 'block';
                scheduleActions.style.display = 'none';
                adminTab.style.display = 'none';
                adminBadge.style.display = 'none';
            }
            
            // Carregar dados
            loadSchedule();
            loadSummaries();
            loadTests();
            loadMessages();
            loadClasses();
            loadProfileData();
            
            if (appData.currentUser.type === 'admin') {
                loadUsers();
                loadAdminClasses();
                loadGuardians();
            }
            
            // Atualizar selects de turmas
            updateClassSelect(summaryClass);
            updateClassSelect(testClass);
            updateClassSelect(studentClass);
            updateClassSelect(studentClassSelect);
        }

        // Carregar dados do perfil
        function loadProfileData() {
            profileName.value = appData.currentUser.name;
            profileUsername.value = appData.currentUser.username;
            
            if (appData.currentUser.type === 'encarregado') {
                profileStudentNameField.style.display = 'block';
                profileStudentName.value = appData.currentUser.studentName || '';
            } else {
                profileStudentNameField.style.display = 'none';
            }
        }

        // Atualizar perfil
        function updateProfile(e) {
            e.preventDefault();
            
            const newName = profileName.value;
            const newUsername = profileUsername.value;
            const newStudentName = profileStudentName.value;
            
            // Verificar se o username já existe (exceto para o utilizador atual)
            if (newUsername !== appData.currentUser.username) {
                const usernameExists = appData.users.some(u => u.username === newUsername && u.id !== appData.currentUser.id);
                if (usernameExists) {
                    alert('Nome de utilizador já existe!');
                    return;
                }
            }
            
            // Atualizar dados do utilizador
            const userIndex = appData.users.findIndex(u => u.id === appData.currentUser.id);
            if (userIndex !== -1) {
                appData.users[userIndex].name = newName;
                appData.users[userIndex].username = newUsername;
                
                if (appData.currentUser.type === 'encarregado') {
                    appData.users[userIndex].studentName = newStudentName;
                }
                
                localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
                
                // Atualizar utilizador atual
                appData.currentUser = appData.users[userIndex];
                localStorage.setItem('currentUser', JSON.stringify(appData.currentUser));
                
                currentUserName.textContent = appData.currentUser.name;
                
                alert('Dados atualizados com sucesso!');
            }
        }

        // Alterar password
        function changePassword(e) {
            e.preventDefault();
            
            const currentPass = currentPassword.value;
            const newPass = newPassword.value;
            const confirmPass = confirmPassword.value;
            
            if (currentPass !== appData.currentUser.password) {
                alert('Password atual incorreta!');
                return;
            }
            
            if (newPass !== confirmPass) {
                alert('As passwords não coincidem!');
                return;
            }
            
            // Atualizar password
            const userIndex = appData.users.findIndex(u => u.id === appData.currentUser.id);
            if (userIndex !== -1) {
                appData.users[userIndex].password = newPass;
                localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
                
                // Atualizar utilizador atual
                appData.currentUser = appData.users[userIndex];
                localStorage.setItem('currentUser', JSON.stringify(appData.currentUser));
                
                alert('Password alterada com sucesso!');
                passwordForm.reset();
            }
        }

        // Eliminar conta
        function deleteAccount() {
            if (confirm('Tem a certeza que pretende eliminar a sua conta? Esta ação é irreversível!')) {
                // Não permitir que o admin se elimine
                if (appData.currentUser.type === 'admin') {
                    alert('O administrador não pode eliminar a sua própria conta!');
                    return;
                }
                
                // Remover utilizador
                appData.users = appData.users.filter(u => u.id !== appData.currentUser.id);
                localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
                
                // Remover dados associados
                appData.summaries = appData.summaries.filter(s => s.teacher !== appData.currentUser.id);
                localStorage.setItem('schoolSummaries', JSON.stringify(appData.summaries));
                
                appData.tests = appData.tests.filter(t => t.teacher !== appData.currentUser.id);
                localStorage.setItem('schoolTests', JSON.stringify(appData.tests));
                
                appData.messages = appData.messages.filter(m => m.from !== appData.currentUser.id && m.to !== appData.currentUser.id);
                localStorage.setItem('schoolMessages', JSON.stringify(appData.messages));
                
                appData.classes = appData.classes.filter(c => c.teacher !== appData.currentUser.id);
                localStorage.setItem('schoolClasses', JSON.stringify(appData.classes));
                
                alert('Conta eliminada com sucesso!');
                handleLogout();
            }
        }

        // Processar logout
        function handleLogout() {
            appData.currentUser = null;
            localStorage.removeItem('currentUser');
            dashboard.style.display = 'none';
            loginPage.style.display = 'flex';
            
            // Limpar formulários
            loginForm.reset();
            registerForm.reset();
        }

        // Alternar entre abas
        function switchTab(tabName) {
            // Remover classe active de todas as abas
            navTabs.forEach(tab => {
                tab.classList.remove('active');
                tab.classList.remove('admin-active');
            });
            tabPanes.forEach(pane => pane.classList.remove('active'));
            
            // Adicionar classe active à aba selecionada
            const selectedTab = document.querySelector(`.nav-tab[data-tab="${tabName}"]`);
            selectedTab.classList.add('active');
            if (tabName === 'admin') {
                selectedTab.classList.add('admin-active');
            }
            document.getElementById(tabName).classList.add('active');
        }

        // Carregar horário
        function loadSchedule() {
            const days = ['SEGUNDA', 'TERÇA', 'QUARTA', 'QUINTA', 'SEXTA', 'SÁBADO'];
            const times = [
                '7:00h/7:30h', '7:35h/8:25h', '8:30h/9:20h', '9:30h/10:20h',
                '10:35h/11:25h', '11:30h/12:20h', '12:30h/13:20h', '13:25h/14:15h',
                '14:20h/15:10h', '15:25h/16:15h', '16:20h/17:10h', '17:25h/18:15h',
                '18:20h/19:10h', '19:10h/20:00h', '20:00h/20:30h', '20:30h/21:20h'
            ];
            
            let html = '<tr><th>Horários</th>';
            
            // Cabeçalho com dias da semana
            days.forEach(day => {
                html += `<th>${day}</th>`;
            });
            html += '</tr>';
            
            // Linhas com horários
            times.forEach(time => {
                html += `<tr><td>${time}</td>`;
                
                days.forEach(day => {
                    const cellData = appData.schedule[day] && appData.schedule[day][time];
                    let className = '';
                    let content = '';
                    
                    if (cellData && cellData.free) {
                        className = 'free';
                        content = 'LIVRE';
                    } else if (cellData) {
                        className = 'has-content';
                        content = cellData.subject;
                        
                        // Verificar se há sumários para esta aula
                        const hasSummary = appData.summaries.some(summary => 
                            summary.date && summary.date.includes(`${day}, ${time}`));
                        
                        if (hasSummary) {
                            content += '<br><small style="color: green;">✓ Sumário</small>';
                        }
                    }
                    
                    html += `<td class="${className}" data-day="${day}" data-time="${time}">${content}</td>`;
                });
                
                html += '</tr>';
            });
            
            scheduleTable.innerHTML = html;
            
            // Adicionar event listeners às células do horário
            document.querySelectorAll('.schedule td').forEach(cell => {
                cell.addEventListener('click', () => {
                    if (appData.currentUser.type === 'professor' || appData.currentUser.type === 'admin') {
                        const day = cell.dataset.day;
                        const time = cell.dataset.time;
                        openSummaryModal(day, time);
                    }
                });
            });
        }

        // Carregar sumários
        function loadSummaries() {
            let html = '';
            
            if (appData.summaries.length === 0) {
                html = '<div class="list-item">Nenhum sumário registado</div>';
            } else {
                // Filtrar sumários baseado no tipo de utilizador
                let filteredSummaries = appData.summaries;
                
                if (appData.currentUser.type === 'encarregado') {
                    // Encarregados de Educação veem apenas sumários relacionados com o seu aluno
                    filteredSummaries = appData.summaries.filter(summary => {
                        const classStudents = getStudentsInClass(summary.classId);
                        return classStudents.some(student => 
                            student.studentName === appData.currentUser.studentName);
                    });
                } else if (appData.currentUser.type === 'aluno') {
                    // Alunos veem apenas sumários da sua turma
                    filteredSummaries = appData.summaries.filter(summary => 
                        summary.classId === appData.currentUser.classId);
                }
                
                filteredSummaries.forEach(summary => {
                    const classInfo = appData.classes.find(c => c.id === summary.classId);
                    const className = classInfo ? classInfo.name : 'Turma desconhecida';
                    
                    html += `
                        <div class="list-item">
                            <div>
                                <strong>${summary.date} - ${className}</strong><br>
                                <span>${summary.subject}: ${summary.content.substring(0, 100)}...</span>
                                ${summary.absences && summary.absences.length > 0 ? 
                                    `<br><small>Faltas registadas: ${summary.absences.length}</small>` : ''}
                            </div>
                            ${(appData.currentUser.type === 'professor' || appData.currentUser.type === 'admin') ? `
                                <div class="item-actions">
                                    <button class="action-btn edit" data-id="${summary.id}">Editar</button>
                                    <button class="action-btn delete" data-id="${summary.id}">Apagar</button>
                                </div>
                            ` : ''}
                        </div>
                    `;
                });
            }
            
            summariesList.innerHTML = html;
            
            // Adicionar event listeners aos botões de ação
            if (appData.currentUser.type === 'professor' || appData.currentUser.type === 'admin') {
                document.querySelectorAll('.action-btn.edit').forEach(btn => {
                    btn.addEventListener('click', () => {
                        const summaryId = btn.dataset.id;
                        const summary = appData.summaries.find(s => s.id === summaryId);
                        openSummaryModal(null, null, summary);
                    });
                });
                
                document.querySelectorAll('.action-btn.delete').forEach(btn => {
                    btn.addEventListener('click', () => {
                        const summaryId = btn.dataset.id;
                        if (confirm('Tem a certeza que pretende apagar este sumário?')) {
                            appData.summaries = appData.summaries.filter(s => s.id !== summaryId);
                            localStorage.setItem('schoolSummaries', JSON.stringify(appData.summaries));
                            loadSummaries();
                            loadSchedule(); // Atualizar horário para remover o indicador de sumário
                        }
                    });
                });
            }
        }

        // Carregar testes
        function loadTests() {
            let html = '';
            
            if (appData.tests.length === 0) {
                html = '<div class="list-item">Nenhum teste marcado</div>';
            } else {
                // Filtrar testes baseado no tipo de utilizador
                let filteredTests = appData.tests;
                
                if (appData.currentUser.type === 'encarregado') {
                    // Encarregados de Educação veem apenas testes relacionados com o seu aluno
                    filteredTests = appData.tests.filter(test => {
                        const classStudents = getStudentsInClass(test.classId);
                        return classStudents.some(student => 
                            student.studentName === appData.currentUser.studentName);
                    });
                } else if (appData.currentUser.type === 'aluno') {
                    // Alunos veem apenas testes da sua turma
                    filteredTests = appData.tests.filter(test => 
                        test.classId === appData.currentUser.classId);
                }
                
                filteredTests.forEach(test => {
                    const classInfo = appData.classes.find(c => c.id === test.classId);
                    const className = classInfo ? classInfo.name : 'Turma desconhecida';
                    
                    html += `
                        <div class="list-item">
                            <div>
                                <strong>${test.subject}</strong><br>
                                <span>${test.date} às ${test.time} - ${className}</span>
                            </div>
                            ${(appData.currentUser.type === 'professor' || appData.currentUser.type === 'admin') ? `
                                <div class="item-actions">
                                    <button class="action-btn delete" data-id="${test.id}">Apagar</button>
                                </div>
                            ` : ''}
                        </div>
                    `;
                });
            }
            
            testsList.innerHTML = html;
            
            // Adicionar event listeners aos botões de ação
            if (appData.currentUser.type === 'professor' || appData.currentUser.type === 'admin') {
                document.querySelectorAll('.action-btn.delete').forEach(btn => {
                    btn.addEventListener('click', () => {
                        const testId = btn.dataset.id;
                        if (confirm('Tem a certeza que pretende apagar este teste?')) {
                            appData.tests = appData.tests.filter(t => t.id !== testId);
                            localStorage.setItem('schoolTests', JSON.stringify(appData.tests));
                            loadTests();
                        }
                    });
                });
            }
        }

        // Carregar mensagens
        function loadMessages() {
            // Filtrar mensagens para o utilizador atual
            const userMessages = appData.messages.filter(msg => 
                msg.to === appData.currentUser.id || msg.from === appData.currentUser.id);
            
            let html = '';
            
            if (userMessages.length === 0) {
                html = '<div class="message-item">Nenhuma mensagem</div>';
            } else {
                userMessages.forEach(msg => {
                    const sender = appData.users.find(u => u.id === msg.from);
                    html += `
                        <div class="message-item" data-id="${msg.id}">
                            <div class="message-sender">${sender ? sender.name : 'Desconhecido'}</div>
                            <div class="message-preview">${msg.subject}</div>
                            <div class="message-date">${msg.date}</div>
                        </div>
                    `;
                });
            }
            
            messagesList.innerHTML = html;
            
            // Adicionar event listeners às mensagens
            document.querySelectorAll('.message-item').forEach(item => {
                item.addEventListener('click', () => {
                    const messageId = item.dataset.id;
                    const message = appData.messages.find(m => m.id === messageId);
                    
                    if (message) {
                        const sender = appData.users.find(u => u.id === message.from);
                        messageSubject.textContent = message.subject;
                        messageSender.textContent = `De: ${sender ? sender.name : 'Desconhecido'}`;
                        messageDate.textContent = `Data: ${message.date}`;
                        messageBody.innerHTML = `<p>${message.content}</p>`;
                        
                        // Marcar como lida
                        document.querySelectorAll('.message-item').forEach(i => i.classList.remove('active'));
                        item.classList.add('active');
                    }
                });
            });
            
            // Popular lista de destinatários
            messageTo.innerHTML = '<option value="">Selecione...</option>';
            
            if (appData.currentUser.type === 'professor' || appData.currentUser.type === 'admin') {
                // Professores podem enviar para encarregados de educação e alunos
                const guardians = appData.users.filter(u => u.type === 'encarregado');
                const students = appData.users.filter(u => u.type === 'aluno');
                
                guardians.forEach(guardian => {
                    messageTo.innerHTML += `<option value="${guardian.id}">${guardian.name} (EE de ${guardian.studentName})</option>`;
                });
                
                students.forEach(student => {
                    messageTo.innerHTML += `<option value="${student.id}">${student.name} (Aluno)</option>`;
                });
            } else {
                // Encarregados de educação e alunos podem enviar para professores
                const teachers = appData.users.filter(u => u.type === 'professor' || u.type === 'admin');
                teachers.forEach(teacher => {
                    messageTo.innerHTML += `<option value="${teacher.id}">${teacher.name} (${teacher.type === 'admin' ? 'Admin' : 'Professor'})</option>`;
                });
            }
        }

        // Carregar turmas
        function loadClasses() {
            let html = '';
            
            if (appData.classes.length === 0) {
                html = '<div class="list-item">Nenhuma turma criada</div>';
            } else {
                appData.classes.forEach(classItem => {
                    const students = getStudentsInClass(classItem.id);
                    
                    html += `
                        <div class="list-item">
                            <div>
                                <strong>${classItem.name}</strong><br>
                                <span>Ano: ${classItem.year} | Alunos: ${students.length}</span>
                            </div>
                            <div class="item-actions">
                                <button class="action-btn view-students" data-id="${classItem.id}">Ver Alunos</button>
                                ${appData.currentUser.type === 'admin' ? `
                                    <button class="action-btn edit" data-id="${classItem.id}">Editar</button>
                                ` : ''}
                                <button class="action-btn delete" data-id="${classItem.id}">Apagar</button>
                            </div>
                        </div>
                    `;
                });
            }
            
            classesList.innerHTML = html;
            
            // Adicionar event listeners aos botões de ação
            document.querySelectorAll('.action-btn.view-students').forEach(btn => {
                btn.addEventListener('click', () => {
                    const classId = btn.dataset.id;
                    showStudentsInClass(classId);
                });
            });
            
            document.querySelectorAll('.action-btn.edit').forEach(btn => {
                btn.addEventListener('click', () => {
                    const classId = btn.dataset.id;
                    const classItem = appData.classes.find(c => c.id === classId);
                    if (classItem) {
                        openClassModal(classItem);
                    }
                });
            });
            
            document.querySelectorAll('.action-btn.delete').forEach(btn => {
                btn.addEventListener('click', () => {
                    const classId = btn.dataset.id;
                    if (confirm('Tem a certeza que pretende apagar esta turma?')) {
                        appData.classes = appData.classes.filter(c => c.id !== classId);
                        localStorage.setItem('schoolClasses', JSON.stringify(appData.classes));
                        loadClasses();
                        studentsContainer.style.display = 'none';
                        
                        // Atualizar selects de turmas
                        updateClassSelect(summaryClass);
                        updateClassSelect(testClass);
                        updateClassSelect(studentClass);
                        updateClassSelect(studentClassSelect);
                    }
                });
            });
        }

        // Carregar utilizadores (admin)
        function loadUsers() {
            let html = '';
            
            if (appData.users.length === 0) {
                html = '<div class="list-item">Nenhum utilizador registado</div>';
            } else {
                appData.users.forEach(user => {
                    const typeBadge = getUserTypeBadge(user.type);
                    const classInfo = user.classId ? appData.classes.find(c => c.id === user.classId) : null;
                    
                    html += `
                        <div class="list-item">
                            <div>
                                <strong>${user.name}</strong>
                                <span class="user-type-badge ${typeBadge.class}">${typeBadge.text}</span>
                                <br>
                                <span>Username: ${user.username}</span>
                                ${user.studentName ? `<br><span>Aluno: ${user.studentName}</span>` : ''}
                                ${classInfo ? `<br><span>Turma: ${classInfo.name}</span>` : ''}
                            </div>
                            <div class="item-actions">
                                ${user.id !== appData.currentUser.id ? `
                                    <button class="action-btn edit" data-id="${user.id}">Editar</button>
                                    <button class="action-btn delete" data-id="${user.id}">Eliminar</button>
                                ` : '<span style="color: var(--gray);">Utilizador atual</span>'}
                            </div>
                        </div>
                    `;
                });
            }
            
            usersList.innerHTML = html;
            
            // Adicionar event listeners aos botões de ação
            document.querySelectorAll('.action-btn.edit').forEach(btn => {
                btn.addEventListener('click', () => {
                    const userId = btn.dataset.id;
                    const user = appData.users.find(u => u.id === userId);
                    if (user) {
                        editUser(user);
                    }
                });
            });
            
            document.querySelectorAll('.action-btn.delete').forEach(btn => {
                btn.addEventListener('click', () => {
                    const userId = btn.dataset.id;
                    if (confirm('Tem a certeza que pretende eliminar este utilizador?')) {
                        deleteUser(userId);
                    }
                });
            });
        }

        // Carregar turmas (admin)
        function loadAdminClasses() {
            let html = '';
            
            if (appData.classes.length === 0) {
                html = '<div class="list-item">Nenhuma turma criada</div>';
            } else {
                appData.classes.forEach(classItem => {
                    const students = getStudentsInClass(classItem.id);
                    const teacher = appData.users.find(u => u.id === classItem.teacher);
                    
                    html += `
                        <div class="list-item">
                            <div>
                                <strong>${classItem.name}</strong><br>
                                <span>Ano: ${classItem.year} | Alunos: ${students.length} | Professor: ${teacher ? teacher.name : 'Não atribuído'}</span>
                            </div>
                            <div class="item-actions">
                                <button class="action-btn edit" data-id="${classItem.id}">Editar</button>
                                <button class="action-btn delete" data-id="${classItem.id}">Apagar</button>
                            </div>
                        </div>
                    `;
                });
            }
            
            adminClassesList.innerHTML = html;
            
            // Adicionar event listeners aos botões de ação
            document.querySelectorAll('.action-btn.edit').forEach(btn => {
                btn.addEventListener('click', () => {
                    const classId = btn.dataset.id;
                    const classItem = appData.classes.find(c => c.id === classId);
                    if (classItem) {
                        openClassModal(classItem);
                    }
                });
            });
            
            document.querySelectorAll('.action-btn.delete').forEach(btn => {
                btn.addEventListener('click', () => {
                    const classId = btn.dataset.id;
                    if (confirm('Tem a certeza que pretende apagar esta turma?')) {
                        appData.classes = appData.classes.filter(c => c.id !== classId);
                        localStorage.setItem('schoolClasses', JSON.stringify(appData.classes));
                        loadAdminClasses();
                        loadClasses();
                    }
                });
            });
        }

        // Carregar encarregados de educação (admin)
        function loadGuardians() {
            const guardians = appData.users.filter(u => u.type === 'encarregado');
            let html = '';
            
            if (guardians.length === 0) {
                html = '<div class="list-item">Nenhum encarregado de educação registado</div>';
            } else {
                guardians.forEach(guardian => {
                    html += `
                        <div class="list-item">
                            <div>
                                <strong>${guardian.name}</strong><br>
                                <span>Username: ${guardian.username} | Aluno: ${guardian.studentName}</span>
                            </div>
                            <div class="item-actions">
                                <button class="action-btn edit" data-id="${guardian.id}">Editar</button>
                                <button class="action-btn delete" data-id="${guardian.id}">Eliminar</button>
                            </div>
                        </div>
                    `;
                });
            }
            
            guardiansList.innerHTML = html;
            
            // Adicionar event listeners aos botões de ação
            document.querySelectorAll('.action-btn.edit').forEach(btn => {
                btn.addEventListener('click', () => {
                    const guardianId = btn.dataset.id;
                    const guardian = appData.users.find(u => u.id === guardianId);
                    if (guardian) {
                        editGuardian(guardian);
                    }
                });
            });
            
            document.querySelectorAll('.action-btn.delete').forEach(btn => {
                btn.addEventListener('click', () => {
                    const guardianId = btn.dataset.id;
                    if (confirm('Tem a certeza que pretende eliminar este encarregado de educação?')) {
                        deleteUser(guardianId);
                    }
                });
            });
        }

        // Mostrar alunos de uma turma
        function showStudentsInClass(classId) {
            const classItem = appData.classes.find(c => c.id === classId);
            if (!classItem) return;
            
            studentsTitle.textContent = `Alunos da Turma: ${classItem.name}`;
            
            const students = getStudentsInClass(classId);
            let html = '';
            
            if (students.length === 0) {
                html = '<div class="list-item">Nenhum aluno nesta turma</div>';
            } else {
                students.forEach(student => {
                    html += `
                        <div class="list-item">
                            <div>
                                <strong>${student.name}</strong><br>
                                <span>Username: ${student.username}</span>
                            </div>
                            <div class="item-actions">
                                <button class="action-btn delete" data-id="${student.id}">Remover</button>
                            </div>
                        </div>
                    `;
                });
            }
            
            studentsList.innerHTML = html;
            studentsContainer.style.display = 'block';
            
            // Adicionar event listeners aos botões de remover aluno
            document.querySelectorAll('.action-btn.delete').forEach(btn => {
                btn.addEventListener('click', () => {
                    const studentId = btn.dataset.id;
                    if (confirm('Tem a certeza que pretende remover este aluno da turma?')) {
                        const studentIndex = appData.users.findIndex(u => u.id === studentId);
                        if (studentIndex !== -1) {
                            appData.users[studentIndex].classId = null;
                            localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
                            showStudentsInClass(classId);
                        }
                    }
                });
            });
        }

        // Obter alunos de uma turma
        function getStudentsInClass(classId) {
            return appData.users.filter(u => u.type === 'aluno' && u.classId === classId);
        }

        // Obter badge do tipo de utilizador
        function getUserTypeBadge(type) {
            switch(type) {
                case 'professor':
                    return { class: 'badge-professor', text: 'Professor' };
                case 'encarregado':
                    return { class: 'badge-encarregado', text: 'EE' };
                case 'aluno':
                    return { class: 'badge-aluno', text: 'Aluno' };
                case 'admin':
                    return { class: 'badge-admin', text: 'Admin' };
                default:
                    return { class: 'badge-professor', text: 'Utilizador' };
            }
        }

        // Atualizar select de turmas
        function updateClassSelect(selectElement) {
            selectElement.innerHTML = '<option value="">Selecione a turma...</option>';
            appData.classes.forEach(classItem => {
                selectElement.innerHTML += `<option value="${classItem.id}">${classItem.name}</option>`;
            });
        }

        // Abrir modal de sumário
        function openSummaryModal(day = null, time = null, summary = null) {
            const modalTitle = document.getElementById('summaryModalTitle');
            const summaryId = document.getElementById('summaryId');
            const summaryDate = document.getElementById('summaryDate');
            const summarySubject = document.getElementById('summarySubject');
            const summaryContent = document.getElementById('summaryContent');
            
            // Limpar formulário
            summaryForm.reset();
            studentsAbsenceList.innerHTML = '';
            
            if (summary) {
                // Modo edição
                modalTitle.textContent = 'Editar Sumário';
                summaryId.value = summary.id;
                summaryDate.value = summary.date;
                summaryClass.value = summary.classId;
                summarySubject.value = summary.subject;
                summaryContent.value = summary.content;
                
                // Carregar alunos da turma com faltas
                loadStudentsForAbsence(summary.classId, summary.absences || []);
            } else {
                // Modo criação
                modalTitle.textContent = 'Registar Sumário';
                summaryId.value = '';
                
                if (day && time) {
                    summaryDate.value = `${day}, ${time}`;
                    
                    // Preencher com dados do horário, se existirem
                    const cellData = appData.schedule[day] && appData.schedule[day][time];
                    if (cellData && !cellData.free) {
                        summarySubject.value = cellData.subject || '';
                    }
                } else {
                    summaryDate.value = '';
                }
                
                // Carregar alunos da turma selecionada
                summaryClass.addEventListener('change', () => {
                    if (summaryClass.value) {
                        loadStudentsForAbsence(summaryClass.value);
                    } else {
                        studentsAbsenceList.innerHTML = '';
                    }
                });
            }
            
            summaryModal.style.display = 'flex';
        }

        // Carregar alunos para registo de faltas
        function loadStudentsForAbsence(classId, existingAbsences = []) {
            const students = getStudentsInClass(classId);
            studentsAbsenceList.innerHTML = '';
            
            if (students.length === 0) {
                studentsAbsenceList.innerHTML = '<div class="student-item">Nenhum aluno nesta turma</div>';
                return;
            }
            
            students.forEach(student => {
                const existingAbsence = existingAbsences.find(a => a.studentId === student.id);
                
                const studentItem = document.createElement('div');
                studentItem.className = 'student-item';
                studentItem.innerHTML = `
                    <div>${student.name}</div>
                    <select class="absence-select" data-student="${student.id}">
                        <option value="">Sem falta</option>
                        <option value="justificada" ${existingAbsence && existingAbsence.type === 'justificada' ? 'selected' : ''}>Falta Justificada</option>
                        <option value="injustificada" ${existingAbsence && existingAbsence.type === 'injustificada' ? 'selected' : ''}>Falta Injustificada</option>
                        <option value="atraso" ${existingAbsence && existingAbsence.type === 'atraso' ? 'selected' : ''}>Atraso</option>
                        <option value="disciplinar" ${existingAbsence && existingAbsence.type === 'disciplinar' ? 'selected' : ''}>Falta Disciplinar</option>
                        <option value="comportamento" ${existingAbsence && existingAbsence.type === 'comportamento' ? 'selected' : ''}>Falta de Comportamento</option>
                    </select>
                `;
                
                studentsAbsenceList.appendChild(studentItem);
            });
        }

        // Abrir modal de teste
        function openTestModal() {
            testForm.reset();
            testModal.style.display = 'flex';
        }

        // Abrir modal de mensagem
        function openMessageModal() {
            messageForm.reset();
            messageModal.style.display = 'flex';
        }

        // Abrir modal de turma
        function openClassModal(classItem = null) {
            classForm.reset();
            
            if (classItem) {
                // Modo edição
                document.getElementById('className').value = classItem.name;
                document.getElementById('classYear').value = classItem.year;
                // Guardar ID da turma para edição
                classForm.dataset.editId = classItem.id;
            } else {
                // Modo criação
                delete classForm.dataset.editId;
            }
            
            classModal.style.display = 'flex';
        }

        // Abrir modal de aluno
        function openStudentModal() {
            studentForm.reset();
            studentModal.style.display = 'flex';
        }

        // Abrir modal de horário
        function openScheduleModal() {
            scheduleForm.reset();
            scheduleModal.style.display = 'flex';
        }

        // Abrir modal de EE
        function openGuardianModal(guardian = null) {
            guardianForm.reset();
            
            if (guardian) {
                // Modo edição
                document.getElementById('guardianUsername').value = guardian.username;
                document.getElementById('guardianName').value = guardian.name;
                document.getElementById('guardianStudentName').value = guardian.studentName;
                // Guardar ID do EE para edição
                guardianForm.dataset.editId = guardian.id;
            } else {
                // Modo criação
                delete guardianForm.dataset.editId;
            }
            
            guardianModal.style.display = 'flex';
        }

        // Fechar todos os modais
        function closeAllModals() {
            summaryModal.style.display = 'none';
            testModal.style.display = 'none';
            messageModal.style.display = 'none';
            classModal.style.display = 'none';
            studentModal.style.display = 'none';
            scheduleModal.style.display = 'none';
            guardianModal.style.display = 'none';
        }

        // Guardar sumário
        function saveSummary() {
            const summaryId = document.getElementById('summaryId').value;
            const summaryDate = document.getElementById('summaryDate').value;
            const classId = document.getElementById('summaryClass').value;
            const summarySubject = document.getElementById('summarySubject').value;
            const summaryContent = document.getElementById('summaryContent').value;
            
            // Obter faltas dos alunos
            const absences = [];
            document.querySelectorAll('.absence-select').forEach(select => {
                if (select.value) {
                    absences.push({
                        studentId: select.dataset.student,
                        type: select.value
                    });
                }
            });
            
            if (summaryId) {
                // Atualizar sumário existente
                const index = appData.summaries.findIndex(s => s.id === summaryId);
                if (index !== -1) {
                    appData.summaries[index] = {
                        ...appData.summaries[index],
                        classId: classId,
                        subject: summarySubject,
                        content: summaryContent,
                        absences: absences
                    };
                }
            } else {
                // Criar novo sumário
                const newSummary = {
                    id: Date.now().toString(),
                    date: summaryDate,
                    classId: classId,
                    subject: summarySubject,
                    content: summaryContent,
                    absences: absences,
                    teacher: appData.currentUser.id
                };
                
                appData.summaries.push(newSummary);
            }
            
            localStorage.setItem('schoolSummaries', JSON.stringify(appData.summaries));
            closeAllModals();
            loadSummaries();
            loadSchedule(); // Atualizar horário para mostrar o indicador de sumário
        }

        // Guardar teste
        function saveTest() {
            const testSubject = document.getElementById('testSubject').value;
            const testDate = document.getElementById('testDate').value;
            const testTime = document.getElementById('testTime').value;
            const classId = document.getElementById('testClass').value;
            
            const newTest = {
                id: Date.now().toString(),
                subject: testSubject,
                date: testDate,
                time: testTime,
                classId: classId,
                teacher: appData.currentUser.id
            };
            
            appData.tests.push(newTest);
            localStorage.setItem('schoolTests', JSON.stringify(appData.tests));
            closeAllModals();
            loadTests();
        }

        // Enviar mensagem
        function sendMessage() {
            const to = document.getElementById('messageTo').value;
            const subject = document.getElementById('messageSubjectInput').value;
            const content = document.getElementById('messageContent').value;
            
            const newMessage = {
                id: Date.now().toString(),
                from: appData.currentUser.id,
                to: to,
                subject: subject,
                content: content,
                date: new Date().toLocaleDateString('pt-PT'),
                read: false
            };
            
            appData.messages.push(newMessage);
            localStorage.setItem('schoolMessages', JSON.stringify(appData.messages));
            closeAllModals();
            loadMessages();
            
            alert('Mensagem enviada com sucesso!');
        }

        // Guardar turma
        function saveClass() {
            const className = document.getElementById('className').value;
            const classYear = document.getElementById('classYear').value;
            const editId = classForm.dataset.editId;
            
            if (editId) {
                // Modo edição
                const classIndex = appData.classes.findIndex(c => c.id === editId);
                if (classIndex !== -1) {
                    appData.classes[classIndex].name = className;
                    appData.classes[classIndex].year = classYear;
                }
            } else {
                // Modo criação
                const newClass = {
                    id: Date.now().toString(),
                    name: className,
                    year: classYear,
                    teacher: appData.currentUser.id
                };
                
                appData.classes.push(newClass);
            }
            
            localStorage.setItem('schoolClasses', JSON.stringify(appData.classes));
            closeAllModals();
            loadClasses();
            if (appData.currentUser.type === 'admin') {
                loadAdminClasses();
            }
            
            // Atualizar selects de turmas
            updateClassSelect(summaryClass);
            updateClassSelect(testClass);
            updateClassSelect(studentClass);
            updateClassSelect(studentClassSelect);
        }

        // Guardar aluno
        function saveStudent() {
            const username = document.getElementById('studentUsername').value;
            const password = document.getElementById('studentPassword').value;
            const fullName = document.getElementById('studentFullName').value;
            const classId = document.getElementById('studentClassSelect').value;
            
            // Verificar se o utilizador já existe
            if (appData.users.find(u => u.username === username)) {
                alert('Nome de utilizador já existe!');
                return;
            }
            
            const newStudent = {
                id: Date.now().toString(),
                type: 'aluno',
                username: username,
                password: password,
                name: fullName,
                studentName: null,
                classId: classId
            };
            
            appData.users.push(newStudent);
            localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
            closeAllModals();
            
            // Atualizar lista de alunos se estiver a ver uma turma
            if (studentsContainer.style.display !== 'none') {
                const currentClassId = document.querySelector('.action-btn.view-students.active')?.dataset.id;
                if (currentClassId) {
                    showStudentsInClass(currentClassId);
                }
            }
            
            alert('Aluno adicionado com sucesso!');
        }

        // Guardar horário
        function saveSchedule() {
            const day = document.getElementById('scheduleDay').value;
            const time = document.getElementById('scheduleTime').value;
            const subject = document.getElementById('scheduleSubject').value;
            
            if (!day || !time) {
                alert('Por favor, selecione o dia e o horário!');
                return;
            }
            
            // Atualizar o horário
            if (!appData.schedule[day]) {
                appData.schedule[day] = {};
            }
            
            if (subject.trim() === '') {
                appData.schedule[day][time] = { free: true };
            } else {
                appData.schedule[day][time] = { 
                    subject: subject.trim(),
                    free: false
                };
            }
            
            localStorage.setItem('schoolSchedule', JSON.stringify(appData.schedule));
            closeAllModals();
            loadSchedule();
            
            alert('Horário atualizado com sucesso!');
        }

        // Guardar EE
        function saveGuardian() {
            const username = document.getElementById('guardianUsername').value;
            const password = document.getElementById('guardianPassword').value;
            const name = document.getElementById('guardianName').value;
            const studentName = document.getElementById('guardianStudentName').value;
            const editId = guardianForm.dataset.editId;
            
            if (editId) {
                // Modo edição
                const guardianIndex = appData.users.findIndex(u => u.id === editId);
                if (guardianIndex !== -1) {
                    appData.users[guardianIndex].username = username;
                    appData.users[guardianIndex].password = password;
                    appData.users[guardianIndex].name = name;
                    appData.users[guardianIndex].studentName = studentName;
                }
            } else {
                // Verificar se o utilizador já existe
                if (appData.users.find(u => u.username === username)) {
                    alert('Nome de utilizador já existe!');
                    return;
                }
                
                // Modo criação
                const newGuardian = {
                    id: Date.now().toString(),
                    type: 'encarregado',
                    username: username,
                    password: password,
                    name: name,
                    studentName: studentName,
                    classId: null
                };
                
                appData.users.push(newGuardian);
            }
            
            localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
            closeAllModals();
            loadGuardians();
            loadUsers();
            
            alert('Encarregado de Educação guardado com sucesso!');
        }

        // Editar utilizador (admin)
        function editUser(user) {
            const newName = prompt('Novo nome:', user.name);
            if (newName === null) return;
            
            const newUsername = prompt('Novo username:', user.username);
            if (newUsername === null) return;
            
            // Verificar se o username já existe (exceto para o utilizador atual)
            if (newUsername !== user.username) {
                const usernameExists = appData.users.some(u => u.username === newUsername && u.id !== user.id);
                if (usernameExists) {
                    alert('Nome de utilizador já existe!');
                    return;
                }
            }
            
            const userIndex = appData.users.findIndex(u => u.id === user.id);
            if (userIndex !== -1) {
                appData.users[userIndex].name = newName;
                appData.users[userIndex].username = newUsername;
                
                // Se for EE, perguntar pelo nome do aluno
                if (user.type === 'encarregado') {
                    const newStudentName = prompt('Novo nome do aluno:', user.studentName);
                    if (newStudentName !== null) {
                        appData.users[userIndex].studentName = newStudentName;
                    }
                }
                
                // Se for aluno, perguntar pela turma
                if (user.type === 'aluno') {
                    const classNames = appData.classes.map(c => c.name).join(', ');
                    const newClassId = prompt(`Nova turma (turmas disponíveis: ${classNames}):`, user.classId);
                    if (newClassId !== null) {
                        const classItem = appData.classes.find(c => c.name === newClassId);
                        if (classItem) {
                            appData.users[userIndex].classId = classItem.id;
                        } else {
                            alert('Turma não encontrada!');
                        }
                    }
                }
                
                localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
                loadUsers();
                loadGuardians();
                
                alert('Utilizador atualizado com sucesso!');
            }
        }

        // Editar EE (admin)
        function editGuardian(guardian) {
            openGuardianModal(guardian);
        }

        // Eliminar utilizador (admin)
        function deleteUser(userId) {
            // Não permitir que o admin se elimine
            if (userId === appData.currentUser.id) {
                alert('Não pode eliminar a sua própria conta!');
                return;
            }
            
            const user = appData.users.find(u => u.id === userId);
            if (!user) return;
            
            if (confirm(`Tem a certeza que pretende eliminar o utilizador "${user.name}"?`)) {
                // Remover utilizador
                appData.users = appData.users.filter(u => u.id !== userId);
                localStorage.setItem('schoolUsers', JSON.stringify(appData.users));
                
                // Remover dados associados
                if (user.type === 'professor') {
                    appData.summaries = appData.summaries.filter(s => s.teacher !== userId);
                    appData.tests = appData.tests.filter(t => t.teacher !== userId);
                    appData.classes = appData.classes.filter(c => c.teacher !== userId);
                }
                
                appData.messages = appData.messages.filter(m => m.from !== userId && m.to !== userId);
                
                localStorage.setItem('schoolSummaries', JSON.stringify(appData.summaries));
                localStorage.setItem('schoolTests', JSON.stringify(appData.tests));
                localStorage.setItem('schoolMessages', JSON.stringify(appData.messages));
                localStorage.setItem('schoolClasses', JSON.stringify(appData.classes));
                
                loadUsers();
                loadGuardians();
                loadClasses();
                loadAdminClasses();
                
                alert('Utilizador eliminado com sucesso!');
            }
        }
    </script>
</body>
</html>
