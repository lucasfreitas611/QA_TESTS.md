# 🛡️ Portfólio de QA: Gran Backstage

> "Qualidade não é um ato, é um hábito." – Aristóteles

Bem-vindo ao repositório de documentação e testes do **Gran Backstage**, uma aplicação web desenvolvida para otimizar o fluxo de trabalho de operadores de estúdio.

Este projeto serve como um **Laboratório Prático de QA**, onde aplico conceitos de Teste de Software, validação funcional e gestão de bugs em um cenário real de produção.

---

## 🎯 Sobre o Projeto
O **Gran Backstage** é uma ferramenta de automação desenvolvida para resolver gargalos operacionais no dia a dia de um operador estúdio home office. 

**Principais Funcionalidades da Aplicação:**
* **Gerador de Mensagens:** Padronização de textos para comunicação com professores.
* **Sistema de Alarmes Híbrido:** Alertas visuais e sonoros (Web Workers) para não perder horários de aula.
* **Banco de Dados Local:** Uso de **IndexedDB** para salvar rascunhos e histórico sem depender de conexão constante.
* **Multiview:** Monitoramento de múltiplas lives simultâneas via API do YouTube.

---

## 🧪 Estratégia de Testes

Neste repositório, você encontrará a documentação completa do ciclo de vida de testes (STLC), focada em:

| Tipo de Teste | Descrição | Ferramentas |
| :--- | :--- | :--- |
| **Funcional (Manual)** | Validação de regras de negócio (ex: Login, Geração de Textos). | Chrome DevTools |
| **Exploratório** | Testes livres para identificar comportamentos não previstos e bugs de usabilidade. | Sessões baseadas em roteiro |
| **Banco de Dados** | Validação de CRUD (Create, Read, Update, Delete) no IndexedDB. | Application Tab (DevTools) |
| **UI/UX** | Verificação de responsividade, paleta de cores e feedbacks visuais (Toasts/Modais). | Inspeção Visual |

### 📂 Acesso Rápido
* [📄 **Ver Plano de Testes Completo (Casos de Teste)**](./PLANO_DE_TESTES.md)
* [🐛 **Ver Histórico de Bugs Reportados**](../../issues) *(Aba Issues)*

---

## 🛠️ Tecnologias Envolvidas
Embora o foco deste repositório seja QA, é importante entender a stack da aplicação testada para realizar testes de caixa branca/cinza:

* **Front-end:** HTML5, CSS3 (Moderno), JavaScript (ES6+)
* **Back-end / Auth:** Firebase Authentication & Firestore
* **Armazenamento Local:** IndexedDB & LocalStorage
* **Controle de Versão:** Git & GitHub

---

## 🚀 Próximos Passos (Roadmap de QA)
Meus objetivos de estudo e evolução para este projeto incluem:
- [x] Criação de Casos de Teste Manuais
- [x] Execução de Testes Funcionais (Login, Core, BD)
- [ ] Implementação de Testes Automatizados E2E (**Cypress** ou **Playwright**)
- [ ] Testes de API (Postman)

---

### 👨‍💻 Sobre o Autor
Sou um Operador de Estúdio em transição de carreira para **Quality Assurance (QA)**. Desenvolvi esta ferramenta proativamente para ajudar minha equipe e utilizo este projeto para consolidar meus estudos em testes de software.

---
*Este projeto é mantido por [Seu Nome].*
