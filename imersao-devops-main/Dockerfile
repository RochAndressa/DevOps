# Use uma imagem oficial do Python como imagem pai
# A versão 3.10-slim é uma boa escolha por ser leve
FROM python:3.10-slim

# Define o diretório de trabalho no container
WORKDIR /app

# Copia o arquivo de dependências para o diretório de trabalho
# Fazer isso separadamente aproveita o cache de camadas do Docker
COPY requirements.txt .

# Instala as dependências
# --no-cache-dir reduz o tamanho da imagem final
RUN pip install --no-cache-dir -r requirements.txt

# Copia o restante do código da aplicação para o diretório de trabalho
COPY . .

# Expõe a porta em que o app será executado
EXPOSE 8000

# Comando para executar a aplicação com Uvicorn
# --host 0.0.0.0 torna a aplicação acessível de fora do container
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]