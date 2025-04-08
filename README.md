<p align="center">
  <img src="https://github.com/user-attachments/assets/9241fa90-74f9-4b50-9d99-e396f96ad56d" alt="logo">
</p>

# 🧪 Chain 1.0 Experimento Interativo em LabJS

Este repositório contém a implementação completa de um experimento **passo a passo** em três etapas, focado em:
1. **Coletar e salvar configurações do participante** (Stage 1)
2. **Definir objetos (imagens/palavras) para cada elo** (Stage 2)
3. **Executar o teste final** com registro de ações, feedback sonoro e dicas dinâmicas (Stage 3)

A seguir, você encontra **instruções detalhadas** de uso e um **exemplo de estrutura de arquivos**.

---

## 📁 Estrutura de Arquivos Sugerida

```
├── main.json                       # Codigo do experimento
├── config_examples/
│   └── config_12_obj.json          # Exemplo de configuração de Stage 1
│   └── set_12_objetos.json         # Exemplo de configuração de objetos do Stage 2
├── images/
│   ├── Bola.png
│   ├── Cadeira.png
│   ├── Dado.png
│   ├── Faca.png
│   ├── Gato.png
│   └── Lapis.png
├── sounds/
│   ├── DING.WAV
│   └── ERRO1.wav
└── README.md                       # Este arquivo
```

> **Observação**: Os arquivos de imagens e sons podem ter nomes diferentes, mas lembre-se de ajustar os caminhos no código, caso use outras mídias.

---

## 🟦 **Stage 1** — Formulário de Configuração

### Descrição
- Coleta informações do participante (nome, idade, sexo).
- Define parâmetros do experimento, como quantidade de elos, sequência de acertos para dicas, instrução geral, **critérios de término** (tempo, acertos, erros, tentativas) e qualquer observação adicional.
- Permite **salvar** e **carregar** arquivos `.json` contendo essas configurações.

### Como Usar
1. **Abrir** `https://labjs.felixhenninger.com/` no navegador e carregar o codigo do experimento, o arquivo `main.json`.
2. Preencha os campos:  
   - **Nome do Participante**, **Idade**, **Sexo**, **Nome do Experimentador**  
   - **Quantidade de Elos** (1 a 20)  
   - **Sequência**: quantos acertos consecutivos até surgir a tela de dicas.  
   - **Clues (Dicas)**: quantas pistas existem e o texto de cada pista (formato livre, mas sugerimos `Resposta;Dica1;Dica2;...`).  
   - **Instrução**: texto que orienta o participante no experimento.  
   - **Término da Sessão por**: Tempo, Acertos, Erros e/ou Tentativas (cada um pode ser habilitado/desabilitado com o checkbox).  
3. Escolha um nome para a configuração no campo **Nome da Configuração** (opcional).
4. Clique em **Salvar** para baixar um arquivo `.json`.  
   - Este arquivo pode ser versionado ou trocado entre pesquisadores.  
5. Clique em **Carregar** e selecione um `.json` previamente salvo para preencher o formulário automaticamente.
6. Clique em **Limpar** caso queira zerar o formulário.
7. Ao finalizar, clique em **Próximo** para avançar ao **Stage 2**.

---

## 🟩 **Stage 2** — Definição de Objetos

### Descrição
- Etapa para **definir** qual conteúdo será exibido em cada elo (palavra ou imagem).
- O formulário gera dinamicamente a quantidade de elos configurada no Stage 1.
- Cada elo pode ser marcado como **Imagem** ou **Palavra** (exclusivo: ao marcar um, o outro desmarca).

### Como Usar
1. **Inicio**.
2. Na **parte direita**, há uma grade de imagens de exemplo (ex: Bola, Cadeira etc.).  
   - Você pode usar essas imagens ou adicionar novas em `/images`.
3. Na **parte esquerda**, cada **Elo** (de 1 até a quantidade definida no Stage 1) terá:
   - Checkbox de **Imagem** e campo de texto.  
   - Checkbox de **Palavra** e campo de texto.  
4. Preencha o que for pertinente (caso escolha **Imagem**, digite o nome do arquivo `Gato.png` por exemplo; se escolher **Palavra**, insira o texto livre).
5. Clique em **Salvar** para baixar um `.json` com as definições dos elos.
6. Clique em **Carregar** para carregar um arquivo `.json` e aplicar as definições existentes.
7. Clique em **Limpar** para remover todos os valores.
8. Para iniciar o teste final, clique em **Iniciar Experimento** e siga para o **Stage 3**.

---

## 🟥 **Stage 3** — Execução do Teste Final

### Descrição
- Mostra os objetos definidos (palavras/imagens) em uma grade embaralhada.
- O participante deve selecionar os objetos na **sequência correta** (ou simplesmente tentar descobrir qual objeto é o certo, dependendo da configuração).
- Quando o participante acerta ou erra, o sistema:
  - Atualiza contadores de acerto e erro.
  - Emite um **som** de feedback (`DING.WAV` para acerto, `ERRO1.wav` para erro).
- Ao atingir **X acertos** consecutivos (definidos pela **Sequência** no Stage 1), surge uma sobreposição de **dicas (Clues)**.  
  - O participante pode ler as dicas e tentar adivinhar a palavra-chave.
- O experimento encerra quando um dos critérios de término (tempo, acertos, erros, tentativas) for atingido ou quando o participante finalizar a sequência completa.

### Como Usar
1. **Inicio**.  
   - Automaticamente, ele buscará os dados salvos no `datastore` interno (etapas anteriores), mas você pode ajustar isso conforme necessidade.
2. **Interaja** na tela:
   - **Parte Superior** (70% da página): Grade com os objetos.  
   - **Parte Inferior** (30% da página):  
     - **Esquerda**: lista de objetos selecionados.  
     - **Direita**: contadores de acertos (verde) e erros (vermelho).
3. Ao selecionar um objeto:
   - Se for o objeto correto no momento, acerto é incrementado.  
   - Se estiver errado, erro é incrementado.
4. Se houver um número de acertos consecutivos definido, surgirá a tela de dicas (caso haja `Clues` configuradas).  
   - Nela, você digita a sua tentativa no campo de texto e clica em **Salvar**.  
   - Se acertar, avança para o próximo conjunto de dicas. Se errar, a tela de dicas fecha e você volta ao tabuleiro.
5. O experimento pode **encerrar automaticamente** ou você pode finalizá-lo clicando no botão **"Obrigado por Participar"** (que aparece no centro após o término).
6. Um **log final** (`final_log.txt`) será gerado para download, contendo todas as ações (seleções, respostas de dicas, hora exata e se foi acerto/erro).

---

## 📄 Exemplo de Arquivo JSON (Configuração Stage 1)

```json
{
  "Nome do Participante": "Maria",
  "Idade": "29",
  "Sexo": "Feminino",
  "Nome do Experimentador": "Dr. Silva",
  "Quantidade de Elos na cadeia": "12",
  "Sequência": "2",
  "Clues": ["Faca;Corta;Afiada", "Gato;Animal;Doméstico"],
  "Instrução": "Selecione os itens em sequência. Após dois acertos, aparecerá uma dica.",
  "Tempo": "180",
  "Tempo_chk": true,
  "Acertos": "10",
  "Acertos_chk": true,
  "Erros": "5",
  "Erros_chk": false,
  "Tentativas": "",
  "Tentativas_chk": false,
  "Nome da Configuração": "config_maria"
}
```

Neste exemplo:
- Após **2 acertos** (`"Sequência": "2"`), uma tela de dica surgirá.  
- O experimento pode terminar se:
  - **Tempo** exceder 180 segundos (**Tempo_chk** = true).
  - **Acertos** chegarem a 10 (**Acertos_chk** = true).
- Há **5 erros** configurados, mas está **Erros_chk** = false, então não encerrará por erros.

---

## 💾 Exemplo de Arquivo JSON (Objetos Stage 2)

```json
{
  "name_obj": "set_12_objetos",
  "Elo 1 Palavra": false,
  "Elo 1 Imagem": true,
  "Elo 1 Texto Palavra": "",
  "Elo 1 Texto Imagem": "Bola.png",
  "Elo 2 Palavra": true,
  "Elo 2 Imagem": false,
  "Elo 2 Texto Palavra": "Cadeira",
  "Elo 2 Texto Imagem": "",
  "...": "... para cada elo até o 12"
}
```

- Para o Elo 1, definimos uma **Imagem** (`Bola.png`).
- Para o Elo 2, definimos **Palavra** (`Cadeira`).
- Cada elo segue esse padrão, alternando conforme necessidade.

---

## 🛠️ Funcionalidades Técnicas & Observações

- **Armazenamento Temporário**: Os dados de cada Stage são guardados em **variáveis globais** (`window.datastore` e `window.datastore_objs`). Por isso, ao abrir cada arquivo HTML em **abas separadas**, pode ser que não haja comunicação adequada. É recomendável que estejam no mesmo fluxo (ex.: abrir `stage1_config.html`, clicar em **Próximo**, que redireciona para o Stage 2, etc.).  
- **Uso de Sonhos**: Em `stage3_test.html`, o experimento tenta carregar `DING.WAV` e `ERRO1.wav` da pasta `/sounds`. Ajuste paths ou nomes conforme necessidade.
- **Importante**: Se você estiver rodando localmente, alguns navegadores podem bloquear certos recursos. Caso encontre problemas, suba os arquivos em um servidor local (por exemplo, via `python -m http.server`) ou outro servidor web simples.

---

## 📌 Dicas de Organização

1. **Configurações**: Mantenha pastas como `config_examples/` com diferentes arquivos `.json`, facilitando a troca de parâmetros.
2. **Objetos**: Use `set_*.json` para descrever grupos de objetos distintos, como `set_animais.json`, `set_instrumentos.json`, etc.
3. **Imagens e Sons**: Organize em pastas separadas (`/images` e `/sounds`) e mantenha nomes padronizados para facilitar a manutenção.

---

## 🧩 Possíveis Extensões

- **Banco de Dados**: Integrar com um backend para salvar resultados de forma centralizada.
- **Estatísticas Detalhadas**: Calcular tempos de reação entre acertos e erros.
- **Exportar em CSV**: Converter o log final em `.csv` ou `.xlsx`.
- **Interface em Diversos Idiomas**: Traduzir para outras línguas.

---

## 📝 Autores

Julio C Abdala, Lorismario Ernesto, Gabriel T. A. Sousa.

---

**Dúvidas ou melhorias?** Abra uma *issue* ou envie um *pull request*!  
Boas coletas e bom experimento! 
