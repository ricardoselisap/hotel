## Execução
- Use Python 3.14 pelo ambiente existente: `.venv\Scripts\python.exe app.py`.
- O servidor Flask escuta em `http://localhost:8000` com `debug=True` e `host="0.0.0.0"`.
- Dependências fixadas estão em `requirements.txt`; não adicione bibliotecas sem necessidade.
- A aplicação exige `SUPABASE_URL` e `SUPABASE_KEY` no `.env`, carregados por `python-dotenv`; nunca leia, exponha ou versiona credenciais.
- Não há suíte de testes, lint ou typecheck configurados. Para uma verificação rápida de sintaxe, use `.venv\Scripts\python.exe -m py_compile app.py`.

## Estrutura E Contratos
- O backend inteiro está em `app.py`; a interface, CSS e JavaScript estão em `static/index.html`.
- `GET /` serve `static/index.html`; o JavaScript usa endpoints relativos, então valide alterações iniciando o servidor local.
- `POST /perguntar` recebe `{"pergunta": "..."}` e retorna `{"mensagem": ...}` após chamar o agente Agno com `gpt-4o-mini`.
- `POST /reservas` insere o JSON recebido na tabela Supabase `reservas` e atualmente retorna a chave literal `"mensagem:"`; preserve esse contrato ou atualize também o fallback correspondente no frontend.
- `GET /reservas` retorna todas as linhas de `reservas` diretamente como JSON.
- Não altere a `description` do agente de hotel sem uma solicitação explícita, pois ela define o comportamento e os dados apresentados pelo chatbot.
