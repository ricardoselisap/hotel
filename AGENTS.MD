## Stack principal
- Linguagem de programação: Python 3.14 (venv em `.venv`)
- Frameworks; Agno 3.0, OpenAI (gpt-4o-mini), Supabase, Flask, Flask-Cors
- FrontEnd: HTML, CSS e JS (tudo inline em `static/index.html`)

## Como rodar
- Não existe `requirements.txt`; as dependências já estão instaladas em `.venv`.
- Usar sempre o interpretador do venv: `.venv\Scripts\python.exe app.py`
- O app sobe em `http://localhost:8000` (host `0.0.0.0`, debug=True).
- Credenciais vêm do `.env` via `load_dotenv` (`SUPABASE_URL`, `SUPABASE_KEY`) — nunca ler/expor esse arquivo.

## Arquitetura (app.py)
- Todo o backend está em `app.py`; o frontend inteiro em `static/index.html`.
- `GET /` serve `static/index.html`.
- `POST /perguntar` recebe `{"pergunta": "..."}` e responde `{"mensagem": ...}` via agente Agno (não alterar a `description` do agente).
- `POST /reservas` insere o JSON recebido na tabela `reservas` do Supabase. Atenção: a resposta usa a chave com erro de digitação `"mensagem:"` (com dois-ponto); o frontend lê `dados.mensagem || dados["mensagem:"]`.
- `GET /reservas` retorna todas as reservas do Supabase.

## Railguards
- Não alterar a lógica do projeto.
- Não alterar e criar arquivos sem pedir permissão.
- Não instalar bibliotecas desnecessárias.
- Não expor e não ler arquivos do .env e do .gitignore
- Não alterar a description do agente de hotel.

## Preferências
- Responder sempre em PT-BR
- Colocar comentários nos códigos, facilitando a leitura para um programador iniciante