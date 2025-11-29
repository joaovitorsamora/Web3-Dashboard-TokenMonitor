# 🌐 Web3-Dashboard-TokenMonitor

Um painel de monitoramento *frontend* e minimalista, desenvolvido para rastrear o estado de um *Smart Contract* específico (SRC Token) e fornecer visualização de dados em tempo real da *blockchain*. Este projeto demonstra a integração entre desenvolvimento web tradicional e o ecossistema Web3.

## 🚀 Tecnologias e Ferramentas

| Categoria | Tecnologia | Detalhes |
| :--- | :--- | :--- |
| **Integração Web3** | **Ethers.js** (v6+) | Biblioteca essencial para interagir com a Ethereum Virtual Machine (EVM), facilitando a leitura de dados de contratos e a gestão de provedores (MetaMask). |
| **Visualização de Dados** | **Chart.js** | Utilizado para criar gráficos dinâmicos e intuitivos, prontos para exibir histórico de preços, *Total Supply* ou outras métricas on-chain. |
| **UX/UI** | HTML5, CSS | Estrutura de código leve, design Dark Mode (`#0d0d0d` background) e estilização com foco na clareza dos dados. |
| **Notificações** | **SweetAlert2** | Usado para exibir alertas modernos e interativos, dando feedback claro ao usuário sobre status de login, sucesso ou erros de transação. |
| **Segurança/Sessão** | `localStorage` | Gerenciamento de tokens JWT (Autorização Bearer) para endpoints *off-chain* e manutenção do estado de login do usuário. |

## ✨ Principais Funcionalidades

* **Conexão Segura:** Implementação da lógica de conexão com carteiras compatíveis com EVM (como MetaMask) através do Ethers.js.
* **Monitoramento de Contrato:** Leitura direta de funções *view* do Smart Contract (via ABI e Endereço) para buscar métricas como:
    * *Total Supply* do Token.
    * *Balance* do token para o usuário conectado.
    * Status do usuário logado (usando endpoint *off-chain* protegido por Token JWT).
* **Autenticação Híbrida:** Demonstração de um sistema onde a API *off-chain* utiliza tokens JWT e o *frontend* interage com a carteira do usuário.
* **Feedback de Usuário:** Uso de SweetAlert2 para notificar o usuário sobre eventos críticos, como "Credenciais inválidas", "Erro de conexão" ou "Usuário deslogado", elevando a qualidade da experiência.
* **Dashboard Interativo:** Exibição dinâmica de dados do token e gráficos para análise rápida.

## 💡 Estrutura e Implementação

O projeto utiliza uma estrutura leve de *Vanilla JavaScript* + HTML/CSS, ideal para PoCs e dashboards de monitoramento.

* **Lógica Principal:** Contida em um único arquivo `index.html` para simplificar o deploy.
* **Comunicação:** Funções assíncronas em JavaScript gerenciam a busca de dados da blockchain (Ethers.js) e de APIs externas (Fetch API/Axios).
* **Estado:** Uso de `localStorage` para persistir o token de autenticação e manter o usuário logado entre sessões.

## ⚙️ Como Rodar Localmente

Este projeto roda no navegador, mas exige a execução em um servidor local para garantir o funcionamento correto das dependências e evitar problemas de CORS.

1.  **Clone o Repositório:**
    ```bash
    git clone https://github.com/joaovitorsamora/Web3-Dashboard-TokenMonitor.git
    cd Web3-Dashboard-TokenMonitor
    ```

2.  **Configuração:**
    * No arquivo `index.html`, **ajuste o `ABI` e o `CONTRACT_ADDRESS`** para o Smart Contract que você deseja monitorar.
    * Verifique se as URLs dos endpoints (ex: `loginURL`, `userLoggedURL`) estão configuradas corretamente para apontar para sua API *off-chain*.

3.  **Execução (Servidor Local):**
    Use um servidor simples (como *Live Server* do VS Code ou o módulo Python):
   
4.  Acesse `http://localhost:8000` em seu navegador.

* **Requisito:** É necessário ter uma extensão de carteira Web3 (como **MetaMask**) instalada e conectada para interagir com o Ethers.js.
