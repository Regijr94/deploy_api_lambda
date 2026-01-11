# Deploy API Lambda

Este projeto demonstra como implantar uma API Lambda na AWS usando Chalice e GitHub Actions com CloudFormation.

## Funcionalidades

- API simples construída com Chalice (framework para AWS Lambda).
- Implantação automatizada via GitHub Actions.
- Testes unitários com cobertura mínima de 80%.
- Implantação apenas após criação de uma release no GitHub.

## Pré-requisitos

- Python 3.12
- Conta AWS com permissões para Lambda, API Gateway, IAM e CloudFormation.
- GitHub repository configurado.

## Instalação Local

1. Clone o repositório:
   ```bash
   git clone https://github.com/Regijr94/deploy_api_lambda.git
   cd deploy_api_lambda
   ```

2. Crie um ambiente virtual:
   ```bash
   python -m venv .vev
   source .vev/bin/activate  # No Windows: .vev\Scripts\activate
   ```

3. Instale as dependências:
   ```bash
   cd consumer
   pip install -r requirements.txt
   pip install -r requirements-dev.txt
   ```

4. Execute os testes:
   ```bash
   pytest --cov=. --cov-fail-under=80
   ```

5. Implante localmente (opcional):
   ```bash
   chalice deploy
   ```

## Configuração do GitHub Actions

1. Adicione os segredos no repositório GitHub (Settings > Secrets and variables > Actions):
   - `AWS_ACCESS_KEY_ID`: Sua chave de acesso AWS.
   - `AWS_SECRET_ACCESS_KEY`: Sua chave secreta AWS.

2. Crie uma release no GitHub para acionar a implantação automática.

## Estrutura do Projeto

- `consumer/`: Código da aplicação Chalice.
  - `app.py`: Código principal da API.
  - `tests/`: Testes unitários.
  - `requirements.txt`: Dependências de produção.
  - `requirements-dev.txt`: Dependências de desenvolvimento.
- `.github/workflows/deploy.yml`: Workflow do GitHub Actions.
- `lambda_handler.py`: Handler adicional (se necessário).

## Implantação

A implantação ocorre automaticamente quando uma release é criada no GitHub. O workflow:
- Executa os testes com verificação de cobertura.
- Configura credenciais AWS.
- Implanta a API usando Chalice.

## Contribuição

1. Faça um fork do projeto.
2. Crie uma branch para sua feature: `git checkout -b minha-feature`.
3. Commit suas mudanças: `git commit -m 'Adiciona nova feature'`.
4. Push para a branch: `git push origin minha-feature`.
5. Abra um Pull Request.

## Licença

Este projeto é para fins educacionais. Use sob sua própria responsabilidade.
