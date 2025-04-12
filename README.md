# Projeto: Upload e Visualização de Arquivo CSV com Streamlit

Este projeto é uma aplicação **Streamlit** que permite ao usuário fazer upload de arquivos CSV, armazená-los em um banco de dados e visualizar os dados em um gráfico interativo. O foco principal é a simplicidade de uso e a flexibilidade na escolha do banco de dados.

## Funcionalidades Principais

- **Upload de Arquivo CSV**: Faça o upload de um arquivo CSV diretamente pela interface Streamlit.
- **Armazenamento em Banco de Dados**:
  - Suporte para **PostgreSQL**, configurável pela variável de ambiente `DATABASE_URL`.
  - Alternativa para **SQLite**, caso o PostgreSQL não esteja configurado ou esteja apontando para localhost.
- **Visualização Gráfica**:
  - Exibição de uma série temporal utilizando o **Plotly**, com gráficos interativos para fácil análise dos dados.

---

## Fluxo de Funcionamento

1. **Upload do CSV**:
   - O usuário seleciona um arquivo CSV para upload.
   - Os dados são exibidos na interface para pré-visualização.

2. **Conexão com Banco de Dados**:
   - O sistema verifica a variável `DATABASE_URL`:
     - Caso esteja configurada corretamente (e não seja localhost), os dados são armazenados no PostgreSQL.
     - Caso contrário, um banco local SQLite é utilizado como fallback.

3. **Armazenamento de Dados**:
   - Os dados do CSV são enviados para o banco de dados escolhido.

4. **Visualização Interativa**:
   - Um gráfico de linha interativo é gerado para exibir a série temporal com base nos dados armazenados.

---

## Como Executar o Projeto

1. Clone o repositório e navegue até a pasta do projeto:
   ```bash
   git clone [SEU_REPOSITORIO_URL]
   cd nome_do_projeto
   ```

2. Crie e ative um ambiente virtual:
   ```bash
   python -m venv venv
   source venv/bin/activate  # No Windows: venv\Scripts\activate
   ```

3. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure a variável de ambiente para o banco de dados PostgreSQL:
   - Crie um arquivo `.env` na raiz do projeto com o seguinte conteúdo:
     ```
     DATABASE_URL=postgresql://usuario:senha@endereco_do_banco/nome_do_banco
     ```

5. Inicie a aplicação Streamlit:
   ```bash
   streamlit run app.py
   ```

6. Acesse a aplicação:
   - Abra seu navegador e vá para o endereço: `http://localhost:8501`.

---

## Requisitos

- **Python 3.8 ou superior**
- **Bibliotecas**:
  - `streamlit`
  - `pandas`
  - `sqlalchemy`
  - `plotly`
  - `python-dotenv`

---

## Notas Importantes

- Caso a variável de ambiente `DATABASE_URL` esteja apontando para um banco de dados local (localhost) ou não esteja configurada, o sistema irá automaticamente alternar para SQLite.
- Mensagens de aviso e status são exibidas para informar o usuário sobre a escolha do banco de dados.

---

## Exemplo de Gráfico Gerado

Um exemplo do gráfico gerado a partir dos dados carregados:
- Eixo X: Datas (`noted_date`).
- Eixo Y: Temperaturas (`temp`).

> **Dica:** Utilize o cursor para interagir com os pontos do gráfico e visualizar os valores específicos.

---