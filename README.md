# Desafio Dio - Criando Projeto para Consultar a Previsão do Tempo via API



### **Projeto: Consulta de Previsão do Tempo via API**

**Objetivo:** 

Desenvolver um projeto que permita consultar a previsão do tempo para uma determinada localidade usando uma API.



**Requisitos:**

- API de previsão do tempo (por exemplo, OpenWeatherMap)
- Linguagem de programação (por exemplo, Python)
- Conhecimento básico de programação e APIs



### **Passos:**

#### **1. Obtenha uma chave de API:**

- Crie uma conta no site da API de previsão do tempo.
- Obtenha uma chave de API que permitirá que você faça chamadas à API.



#### **2. Instale as bibliotecas necessárias:**

- Instale a biblioteca Requests para fazer chamadas HTTP.
- Instale a biblioteca JSON para analisar os dados JSON retornados pela API.



#### **3. Escreva o código:**

python

```python
import requests
import json

# Chave da API
api_key = 'SUA_CHAVE_DE_API'

# Localidade
cidade = 'São Paulo'

# URL da API
url = f'https://api.openweathermap.org/data/2.5/weather?q={cidade}&appid={api_key}'

# Faz a chamada à API
response = requests.get(url)

# Verifica se a chamada foi bem-sucedida
if response.status_code == 200:
    # Converte os dados JSON para um dicionário
    dados = json.loads(response.text)

    # Extrai as informações desejadas
    temperatura = dados['main']['temp'] - 273.15
    sensacao_termica = dados['main']['feels_like'] - 273.15
    descricao = dados['weather'][0]['description']

    # Exibe as informações
    print(f'Temperatura: {temperatura:.2f} °C')
    print(f'Sensação térmica: {sensacao_termica:.2f} °C')
    print(f'Descrição: {descricao}')
else:
    print('Erro ao consultar a API.')
```



#### **4. Execute o código:**

- Salve o código em um arquivo com extensão `.py`.
- Execute o arquivo usando o interpretador Python.



**Resultado:** O código exibirá as informações de previsão do tempo para a localidade especificada, incluindo temperatura, sensação térmica e descrição do tempo.



#### **Exemplo mais completo com tratamento de erros e saída formatada:**

python

```python
import requests
import json

# Chave da API
api_key = 'SUA_CHAVE_DE_API'

# Localidade
cidade = 'São Paulo'

# URL da API
url = f'https://api.openweathermap.org/data/2.5/weather?q={cidade}&appid={api_key}'

try:
    # Faz a chamada à API
    response = requests.get(url)

    # Verifica se a chamada foi bem-sucedida
    if response.status_code == 200:
        # Converte os dados JSON para um dicionário
        dados = json.loads(response.text)

        # Extrai as informações desejadas
        temperatura = dados['main']['temp'] - 273.15
        sensacao_termica = dados['main']['feels_like'] - 273.15
        descricao = dados['weather'][0]['description']

        # Exibe as informações formatadas
        print('**Previsão do Tempo para {}**'.format(cidade))
        print('Temperatura: {:.2f} °C'.format(temperatura))
        print('Sensação térmica: {:.2f} °C'.format(sensacao_termica))
        print('Descrição: {}'.format(descricao))
    else:
        print('Erro ao consultar a API. Código de status: {}'.format(response.status_code))

except Exception as e:
    print('Ocorreu um erro ao consultar a API: {}'.format(e))
```



#### **Este código inclui:**

- Tratamento de erros para lidar com possíveis problemas na chamada à API.
- Saída formatada para tornar as informações mais fáceis de ler.
- Mensagens de erro mais descritivas para ajudar na depuração.



#### **Para executar o código:**

1. Salve o código em um arquivo com extensão `.py`.
2. Substitua `SUA_CHAVE_DE_API` pela sua chave de API da OpenWeatherMap.
3. Execute o arquivo usando o interpretador Python.



### **Resultado:**

O código exibirá as informações de previsão do tempo para a localidade especificada em um formato mais amigável, como:

```plaintext
**Previsão do Tempo para São Paulo**
Temperatura: 25.45 °C
Sensação térmica: 27.23 °C
Descrição: Céu limpo
```
