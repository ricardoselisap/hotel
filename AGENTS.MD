## Execução
- Use o ambiente Python 3.14 existente: `.venv\Scripts\python.exe app.py`.
- O servidor Flask roda em `http://localhost:8000`, com `debug=True` e `host="0.0.0.0"`.
- As dependências estão fixadas em `requirements.txt`; não adicione bibliotecas sem necessidade.
- O `.env` precisa conter `SUPABASE_URL` e `SUPABASE_KEY`; `python-dotenv` os carrega. Nunca leia, exponha ou versione credenciais.
- Não há testes, lint ou typecheck configurados. Verifique sintaxe com `.venv\Scripts\python.exe -m py_compile app.py`.

## Estrutura E Contratos
- `app.py` contém todo o backend; `static/index.html` contém a interface, CSS e JavaScript.
- `GET /` serve `static/index.html`; o frontend usa endpoints relativos, portanto alterações de integração devem ser verificadas com o servidor local em execução.
- `POST /perguntar` recebe `{"pergunta": "..."}` e retorna `{"mensagem": ...}` usando o agente Agno com `gpt-4o-mini`.
- `POST /reservas` insere o JSON recebido na tabela Supabase `reservas` e retorna atualmente a chave literal `"mensagem:"`; se mudar o contrato, ajuste o fallback correspondente no frontend.
- `GET /reservas` retorna diretamente as linhas da tabela `reservas`.
- Não altere a `description` do agente sem solicitação explícita: ela define o comportamento e as informações do chatbot.
