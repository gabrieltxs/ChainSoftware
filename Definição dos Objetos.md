# 🧩 Definição de Objetos - Stage 2

Este módulo representa a segunda etapa do experimento, na qual o experimentador define os elementos (ELOs) que serão apresentados ao participante. Cada ELO pode ser representado por uma **imagem** ou uma **palavra**, e os dados são armazenados para uso nas fases posteriores do experimento.

---

## 📁 Estrutura do Projeto

```
├── stage2_objects.html       # Interface para definição dos objetos
├── README.md                 # Este arquivo
└── /objetos_definidos        # (opcional) Pasta para salvar os arquivos JSON
```

---

## 🚀 Como Usar

### 1. Abrir o Arquivo

Abra o arquivo `stage2_objects.html` em qualquer navegador moderno (Chrome, Firefox, Edge). Não é necessário servidor ou instalação.

---

### 2. Interface Dividida

A tela é dividida em duas partes:

#### 🔹 Lado Esquerdo: Formulário de Elos
- Serão gerados automaticamente campos de entrada para a quantidade de elos definida na etapa anterior (Stage 1).
- Para cada elo:
  - Marque **Imagem** ou **Palavra**.
  - Preencha o campo correspondente com o nome da imagem (ex: `Gato.png`) ou com a palavra desejada.
  - Apenas um dos dois pode ser ativado por elo.

#### 🔹 Lado Direito: Grade de Imagens
- Imagens de exemplo são exibidas para auxiliar o experimentador na escolha dos elementos.
- As imagens são:
  - `Bola.png`
  - `Cadeira.png`
  - `Dado.png`
  - `Faca.png`
  - `Gato.png`
  - `Lapis.png`

---

### 3. Rodapé: Ações Disponíveis

- **Nome da Configuração de Objetos**: Campo de identificação da definição atual.
- **Salvar**: Exporta os dados definidos para um arquivo `.json`.
- **Carregar**: Permite importar uma configuração existente.
- **Limpar**: Reinicia todos os campos da tela.
- **Iniciar Experimento**: Avança para a próxima etapa (ex: Stage 3).

---

## 💾 Exemplo de JSON de Objetos

```json
{
  "name_obj": "config_padrao",
  "Elo 1 Palavra": true,
  "Elo 1 Imagem": false,
  "Elo 1 Texto Palavra": "gato",
  "Elo 1 Texto Imagem": "",
  "Elo 2 Palavra": false,
  "Elo 2 Imagem": true,
  "Elo 2 Texto Palavra": "",
  "Elo 2 Texto Imagem": "Faca.png"
}
```

---

## 🛠️ Funcionalidades do Script

- Carrega automaticamente a quantidade de elos definidos na **Stage 1**.
- Cria dinamicamente campos de entrada com controle exclusivo entre imagem e palavra.
- Permite salvar/recuperar as definições de objetos usando arquivos `.json`.
- Armazena os dados no objeto global `datastore_objs`, com visualização opcional via console.
- Integração pronta para uso com próxima etapa (`stage3_test.html`).

---

## 📌 Requisitos

- Navegador moderno com suporte a JavaScript.
- Imagens devem estar disponíveis no mesmo diretório (ou ajustadas via URL no código).

---

## 📤 Sugestão de Organização

Crie uma pasta `objetos_definidos/` para manter as diferentes definições de objetos:

```
objetos_definidos/
├── config_padrao.json
├── objetos_animais.json
└── objetos_cores.json
```

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE). Livre para modificar, adaptar e distribuir conforme necessidade do seu experimento.

---

Se desejar, posso gerar esse arquivo `README.md` diretamente. Deseja o download?
