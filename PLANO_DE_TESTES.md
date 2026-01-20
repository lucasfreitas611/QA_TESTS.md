# 🧪 Plano de Testes Funcionais - Gran Backstage

**Projeto:** Gran Backstage - Automação de Estúdio  
**Responsável:** [Seu Nome]  
**Tipo de Teste:** Manual / Funcional / Exploratório  
**Ambiente:** Google Chrome (Latest) / Windows 10/11

---

## 1. Módulo de Autenticação (Login)
*Objetivo: Garantir a segurança e o controle de acesso ao sistema.*

| ID | Cenário de Teste | Passos para Reprodução | Dados de Entrada | Resultado Esperado | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **LOG-01** | Login com Sucesso | 1. Acessar tela de bloqueio.<br>2. Inserir e-mail e senha válidos.<br>3. Clicar em "Iniciar Sessão". | E-mail: `admin@gran.com`<br>Senha: `123456` | O sistema deve remover a tela de bloqueio, exibir o layout principal e carregar o nome do usuário na sidebar. | ✅ Pass |
| **LOG-02** | Login com Senha Inválida | 1. Inserir e-mail válido.<br>2. Inserir senha incorreta.<br>3. Clicar em "Iniciar Sessão". | Senha: `errada` | O sistema deve exibir mensagem de erro "Acesso negado" e manter a tela bloqueada. | ⬜ Pendente |
| **LOG-03** | Validação de Campos Vazios | 1. Deixar campos em branco.<br>2. Clicar em "Iniciar Sessão". | N/A | O sistema deve exibir alerta visual ou mensagem "Preencha e-mail e senha". | ⬜ Pendente |

---

## 2. Módulo Gerador de Mensagens (Core)
*Objetivo: Validar a lógica de negócios, validação de inputs e geração de texto.*

| ID | Cenário de Teste | Passos para Reprodução | Dados de Entrada | Resultado Esperado | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **MSG-01** | Validação de Professor | 1. No campo Grade, colar texto com nome em minúsculo.<br>2. Aguardar verificação automática. | Grade: `joão silva 10h` | O sistema deve reconhecer "João Silva" no banco de dados, ignorar maiúsculas/minúsculas e exibir "✔ Contato: João Silva" em verde. | ⬜ Pendente |
| **MSG-02** | Professor Não Cadastrado | 1. Colar grade com nome inexistente. | Grade: `Professor X 10h` | O sistema deve exibir feedback "Professor não identificado" e não liberar botão de WhatsApp no card final. | ⬜ Pendente |
| **MSG-03** | Validação de Link do Drive | 1. Preencher todos os campos exceto Drive.<br>2. Clicar em "Gerar". | Drive: `(vazio)` | O sistema deve exibir Toast de erro, borda vermelha no campo Drive e **não** gerar a mensagem. | ⬜ Pendente |
| **MSG-04** | Validação de Domínio do Drive | 1. Inserir link que não seja do Google Drive.<br>2. Clicar em "Gerar". | Drive: `youtube.com` | O sistema deve bloquear e avisar "Insira uma URL do Google Drive". | ⬜ Pendente |
| **MSG-05** | Obrigatoriedade de Print | 1. Selecionar aba "Padrão".<br>2. Não selecionar arquivo de imagem.<br>3. Clicar em "Gerar". | Arquivo: `null` | O sistema deve exibir erro "O Print da OS é obrigatório" e destacar o botão de upload em vermelho. | ⬜ Pendente |
| **MSG-06** | Isenção de Print (Pós-Prova) | 1. Selecionar aba "Pós-Prova".<br>2. Verificar se campo de upload sumiu.<br>3. Clicar em "Gerar" sem imagem. | Modo: `PosProva` | O campo de upload deve estar oculto. O sistema deve gerar a mensagem com sucesso sem exigir imagem. | ⬜ Pendente |
| **MSG-07** | Chave de Teste vs Aula | 1. Clicar em "Chave de Teste".<br>2. Gerar mensagem. | Tipo: `Teste` | No texto final gerado, deve aparecer escrito "Chave de teste:" ao invés de "Chave:". | ⬜ Pendente |

---

## 3. Histórico e Banco de Dados (IndexedDB)
*Objetivo: Testar a persistência de dados, CRUD e limites.*

| ID | Cenário de Teste | Passos para Reprodução | Dados de Entrada | Resultado Esperado | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **HIS-01** | Persistência ao Recarregar | 1. Gerar uma mensagem.<br>2. Recarregar a página (F5). | N/A | A mensagem deve permanecer no histórico (carregada via IndexedDB) e não sumir. | ⬜ Pendente |
| **HIS-02** | Edição de Card | 1. Clicar em "Editar" num card.<br>2. Alterar texto e horário.<br>3. Salvar. | Novo Horário: `15:00` | O card deve atualizar as informações na tela e o alarme deve ser reagendado para o novo horário. | ⬜ Pendente |
| **HIS-03** | Exclusão para Lixeira | 1. Clicar em "Lixeira" no card.<br>2. Confirmar. | N/A | O item deve sumir da lista principal e aparecer dentro do Modal de Lixeira. | ⬜ Pendente |
| **HIS-04** | Efeito Neon (Localização) | 1. Disparar um alarme.<br>2. Verificar o card correspondente. | N/A | O card da mensagem específica deve receber borda vermelha e animação pulsante (Neon) por 60 segundos. | ⬜ Pendente |
| **HIS-05** | Paleta de Cores | 1. Clicar no ícone de pincel do card.<br>2. Selecionar cor "Roxo". | Cor: `Roxo` | O fundo do card deve mudar imediatamente para roxo e persistir após F5. | ⬜ Pendente |

---

## 4. Sistema de Alarmes
*Objetivo: Validar a precisão temporal e o disparo duplo de alertas.*

| ID | Cenário de Teste | Passos para Reprodução | Dados de Entrada | Resultado Esperado | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **ALM-01** | Criação de Alarme Duplo | 1. Gerar mensagem para aula das 10:00.<br>2. Verificar sidebar. | Aula: `10:00` | O sistema deve agendar internamente dois alarmes:<br>1. Padrão às 09:00.<br>2. Live às 09:55. | ⬜ Pendente |
| **ALM-02** | Disparo Padrão (1h Antes) | 1. Aguardar horário do alarme padrão. | N/A | Deve exibir Overlay Vermelho, tocar som escolhido e notificar o navegador. | ⬜ Pendente |
| **ALM-03** | Disparo Crítico (5min Antes) | 1. Aguardar horário de "Start Live". | N/A | Deve exibir **Overlay Amarelo/Preto**, tocar som de alerta e mostrar nome do professor em destaque. | ⬜ Pendente |
| **ALM-04** | Limpeza de Alarmes Fantasmas | 1. Apagar uma mensagem que tem alarme.<br>2. Recarregar a página. | N/A | O alarme correspondente deve sumir da sidebar automaticamente (Sync check). | ⬜ Pendente |
