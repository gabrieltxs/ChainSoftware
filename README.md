# 🧪 Formulário de Configuração de Experimento - Stage 1

Este projeto contém a interface de configuração inicial de um experimento, permitindo ao experimentador definir parâmetros básicos antes de iniciar a tarefa experimental (Stage 2). O formulário coleta informações do participante, define os parâmetros da tarefa, critérios de encerramento da sessão, além de permitir salvar e carregar configurações personalizadas em arquivos JSON.

---

## 📁 Estrutura do Projeto

```
├── index.html               # Interface do formulário (Stage 1)
├── README.md                # Este arquivo
└── /configuracoes           # (opcional) Pasta sugerida para armazenar configs JSON
```

---

## 🚀 Como Usar

### 1. Abertura do Formulário

Basta abrir o arquivo `index.html` em qualquer navegador moderno. Não é necessário servidor ou instalação adicional.

---

### 2. Preenchimento dos Campos

#### 🔹 Informações Pessoais
- **Nome do Participante**: Nome do voluntário.
- **Idade**: Idade numérica.
- **Sexo**: Masculino, Feminino ou Outro.
- **Nome do Experimentador**: Nome da pessoa conduzindo o experimento.

#### 🔹 Parâmetros
- **Quantidade de Elos na cadeia**: Número de elementos ou etapas na tarefa (1 a 20).
- **Sequência**: Código/texto que representa a ordem das etapas.
- **Clues**: Quantidade de pistas a serem usadas. Após selecionar a quantidade, campos adicionais aparecerão para preenchimento.
- **Instrução**: Texto com as instruções que serão dadas ao participante.

#### 🔹 Critérios de Término da Sessão
Você pode configurar a sessão para encerrar com base em:
- **Tempo** (em segundos)
- **Número de acertos**
- **Número de erros**
- **Número de tentativas**

Basta marcar o checkbox correspondente para ativar o campo e preencher o valor.

#### 🔹 Configurações
- **Nome da Configuração**: Nome para identificação do arquivo JSON da configuração.
- **Salvar**: Gera e baixa um arquivo `.json` com as configurações atuais.
- **Carregar**: Permite carregar um arquivo `.json` previamente salvo.
- **Limpar**: Reinicia todos os campos do formulário.

---

### 3. Salvamento de Configuração

Após preencher os campos, clique em **Salvar**. Um arquivo `.json` será baixado com os dados inseridos. Esse arquivo pode ser reutilizado posteriormente.

---

### 4. Carregamento de Configuração

Para carregar uma configuração existente:
1. Clique no botão **Escolher Arquivo**.
2. Selecione o arquivo `.json` salvo anteriormente.
3. Os campos do formulário serão preenchidos automaticamente.

---

### 5. Início do Experimento

Clique em **Próximo** para continuar para a próxima etapa (ex: `stage2_objects.html`, que deve ser implementado).

---

## 💾 Exemplo de Configuração

```json
{
  "Nome do Participante": "João Silva",
  "Idade": "25",
  "Sexo": "Masculino",
  "Nome do Experimentador": "Dr. Lucas",
  "Quantidade de Elos na cadeia": "5",
  "Sequência": "A-B-C-D-E",
  "Clues": ["Resposta1;Dica1;Dica2"],
  "Instrução": "Por favor, siga as instruções na tela...",
  "Tempo": "180",
  "Tempo_chk": true,
  "Acertos": "",
  "Acertos_chk": false,
  "Erros": "",
  "Erros_chk": false,
  "Tentativas": "",
  "Tentativas_chk": false,
  "Nome da Configuração": "config_joao"
}
```

---

## 🛠️ Personalização

O código pode ser expandido facilmente para incluir:
- Novos critérios de término.
- Novos tipos de instruções.
- Integração com outras fases do experimento (como Lab.js ou custom HTML/JS).

---

## 📌 Requisitos

- Apenas um navegador moderno (Chrome, Firefox, Edge, etc).
- Nenhuma dependência externa ou backend é necessário.

---

## 📤 Sugestão de Uso com Git

Recomenda-se salvar os arquivos de configuração na pasta `configuracoes/`, com nomes descritivos, como:

```
configuracoes/
├── config_piloto1.json
├── config_joana_revisao.json
└── config_padrao.json
```

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE), sinta-se livre para utilizar e adaptar.
