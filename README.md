# Habit Tracker Pro

Aplicação web interativa e independente para gerenciamento e acompanhamento de hábitos diários, com métricas visuais via gráficos e um painel completo para personalização dinâmica de temas.

---

## 📌 Sumário

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura de Estilos](#-arquitetura-de-estilos)
- [Como Executar](#-como-executar)
- [Como Funciona](#-como-funciona)

---

## 🚀 Sobre o Projeto

O **Habit Tracker Pro** é uma solução leve projetada para rodar inteiramente no navegador. O sistema permite cadastrar hábitos, registrar o progresso semanal (de segunda a domingo) e visualizar dados analíticos através de gráficos dinâmicos alimentados pela biblioteca **Chart.js**. Todos os dados e configurações de tema são persistidos localmente no navegador (`localStorage`).

---

## ✨ Funcionalidades

- **Gestão de Hábitos (CRUD):** Adicione, acompanhe e remova hábitos facilmente.
- **Grade Semanal Interativa:** Marque ou desmarque a conclusão de cada hábito para cada dia da semana (Segunda a Domingo).
- **Métricas Visuais (Chart.js):**
  - **Gráfico de Barras:** Conclusão individual por hábito (calculado em porcentagem).
  - **Gráfico de Linha:** Progresso geral acumulado por dia da semana.
- **Personalização Dinâmica de Cores:**
  - Seletor de cores em tempo real para a página, cards, botões, textos e estados de sucesso.
  - Recalculagem automática de tonalidades de hover.
  - Opção para **Restaurar Padrão** do tema original.
- **Persistência de Dados:** Salva automaticamente hábitos e preferências de cores no `localStorage`.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5:** Estrutura semântica e acessível.
- **CSS3 / Variáveis CSS (`:root`):** Estilização responsiva e manipulação de propriedades globais.
- **JavaScript (Vanilla JS):** Manipulação do DOM, controle de estado, persistência local e lógica da aplicação.
- **Chart.js (CDN):** Renderização e atualização dinâmica dos gráficos de desempenho.

---

## 🎨 Arquitetura de Estilos

A aplicação utiliza **CSS Custom Properties** no contexto `:root`, permitindo reatividade imediata na interface e nos componentes visuais do Chart.js:

| Variável          | Descrição                             | Valor Padrão |
| :---------------- | :------------------------------------ | :----------- |
| `--bg-color`      | Fundo principal da página             | `#0f172a`    |
| `--card-bg`       | Fundo do container principal          | `#1e293b`    |
| `--inner-bg`      | Fundo dos cards internos e formulário | `#0f172a`    |
| `--primary-color` | Cor de botões e destaques primários   | `#3b82f6`    |
| `--success-color` | Indicador de hábito concluído         | `#22c55e`    |
| `--text-main`     | Cor dos textos principais             | `#f8fafc`    |

---

## ⚡ Como Executar

Por ser uma aplicação contida em um único arquivo HTML, não é necessário instalar gerenciadores de pacotes como `npm` ou `yarn`.

1. Copie o código do arquivo `index.html`.
2. Salve o arquivo em seu computador.
3. Abra-o com duplo clique em qualquer navegador moderno (Chrome, Firefox, Edge, Safari) com acesso à internet (para carregar o CDN do Chart.js).

---

## 🧠 Como Funciona

### 1. Atualização do Tema em Tempo Real

Ao selecionar uma nova cor no painel, a função `updateTheme` atualiza a propriedade no `:root` e recalcula a variante de hover:

```javascript
function updateTheme(key, value) {
  theme[key] = value;
  localStorage.setItem("habit_theme", JSON.stringify(theme));
  applyTheme();
}
```
