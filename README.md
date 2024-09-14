
## **Apresentação do Projeto: Sistema de Busca e Exibição de Dados com Flask**

### **1. Objetivo**

Este projeto visa criar uma aplicação web simples utilizando o Flask, um framework em Python, para facilitar a visualização de dados armazenados em um arquivo CSV. A aplicação disponibiliza uma API que retorna os dados do CSV em formato JSON, permitindo acesso fácil e intuitivo através de um navegador ou ferramentas de teste de API.

### **2. Tecnologias Utilizadas**

- **Flask:** Um microframework para desenvolvimento web em Python, ideal para criar APIs de forma rápida e eficiente.
- **Pandas:** Biblioteca Python que simplifica a leitura e manipulação de dados em arquivos CSV.
- **CSV:** Formato de arquivo que armazena dados tabulares em texto simples, separado por vírgulas.
- **JSON:** Formato de dados leve e popular para troca de informações entre sistemas.

### **3. Estrutura do Projeto**

O projeto é composto pelos seguintes arquivos:

- **`app.py`:** Arquivo principal da aplicação Flask, responsável pela definição da API e leitura dos dados do CSV.
- **`updated_formatted_data.csv`:** Arquivo CSV que contém os dados a serem disponibilizados pela aplicação.

### **4. Código da Aplicação**

#### **4.1. Código do `app.py`**

```python
from flask import Flask, jsonify
import pandas as pd

app = Flask(__name__)

# Função para ler dados do CSV
def read_csv():
    df = pd.read_csv('updated_formatted_data.csv')
    return df.to_dict(orient='records')

@app.route('/find', methods=['GET'])
def find():
    data = read_csv()
    return jsonify(data)

if __name__ == '__main__':
    app.run(debug=True)
```

**Descrição do Código:**

- **Importações:** O código usa Flask para criar a aplicação web e Pandas para ler e manipular o arquivo CSV.
- **Função `read_csv()`:** Lê o arquivo CSV e converte os dados em uma lista de dicionários, onde cada dicionário representa uma linha do CSV.
- **Rota `/find`:** Define um endpoint que retorna os dados do CSV em formato JSON, facilitando a visualização completa dos dados.
- **Execução da Aplicação:** O servidor Flask é iniciado em modo de depuração para auxiliar na identificação e correção de problemas.

### **5. Dados Utilizados**

O arquivo `updated_formatted_data.csv` contém dados fictícios sobre indivíduos com as seguintes informações:

- **_id:** Identificador único da entrada.
- **name:** Nome da pessoa.
- **age:** Idade da pessoa.
- **occupation:** Ocupação.
- **skills:** Habilidades.
- **email:** E-mail.

Exemplo de dados no arquivo CSV:

```
_id,name,age,occupation,skills,email
66de1b0827fa3b22c9400293,Alice,28,Senior Data Scientist,"Python, Machine Learning, SQL",
...
```

### **6. Documentação do Endpoint**

- **Endpoint:** `/find`
- **Método:** GET
- **URL:** `http://127.0.0.1:5000/find`
- **Resposta:**
  ```json
  [
      {
          "_id": "66de1b0827fa3b22c9400293",
          "name": "Alice",
          "age": 28,
          "occupation": "Senior Data Scientist",
          "skills": "Python, Machine Learning, SQL",
          "email": ""
      },
      ...
  ]
  ```

### **7. Passos para Executar o Projeto**

1. **Instalação das Dependências:**
   Instale Flask e Pandas com o comando:
   ```sh
   pip install flask pandas
   ```

2. **Preparação dos Dados:**
   Certifique-se de que o arquivo `updated_formatted_data.csv` está localizado no mesmo diretório que o arquivo `app.py`.

3. **Execução da Aplicação:**
   Inicie o servidor Flask com:
   ```sh
   python app.py
   ```

4. **Acesso ao Endpoint:**
   Abra um navegador ou ferramenta de teste de API (como Postman) e acesse:
   - `http://127.0.0.1:5000/find`

   Você verá todos os dados do CSV exibidos em formato JSON.

### **8. Desafios e Soluções**

- **Desafio:** Garantir que todos os dados sejam lidos e convertidos corretamente.
  - **Solução:** A utilização do Pandas para ler e converter o CSV para JSON garantiu a precisão e eficiência dos dados.

- **Desafio:** Configuração do ambiente Flask e integração com Pandas.
  - **Solução:** A configuração direta do Flask e a integração com Pandas permitiram uma manipulação de dados fluida e eficaz.

### **9. Conclusão**

Este projeto demonstra a capacidade de criar uma aplicação web simples com Flask para disponibilizar dados de um arquivo CSV via API. A visualização dos dados em formato JSON proporciona uma forma prática e acessível para análise e uso dos dados.

---
![image](https://github.com/user-attachments/assets/12e83907-baa7-4ddf-bbd5-decdd2ecac7e)
