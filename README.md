# SGFLOW — Sistema de Gerenciamento de Fluxos Logísticos

Nossa méta,trazer melhor fluxo de transporte aos nossos clientes.

O SGFLOW simula um fluxo logístico com caminhões, cargas e rotas, aplicando **Fila FIFO**, **Pilha LIFO**, **Lista de Rotas**, **Bubble Sort**, **Insertion Sort** e métricas de performance.


## O que o projeto faz

- Controla caminhões no pátio usando **Fila FIFO**.
- Permite atender o primeiro caminhão da fila.
- Controla cargas de cada caminhão usando **Pilha LIFO**.
- Para caminhão de **Carga**, o usuário adiciona itens na pilha e depois finaliza a carga.
- Para caminhão de **Descarga**, o caminhão deve entrar com cargas iniciais e cada clique em Descarga remove o topo da pilha.
- Libera caminhões para uma lista de rotas após finalizar a carga ou esvaziar a descarga.
- Ordena rotas por menor distância usando **Bubble Sort manual**.
- Permite inverter a ordem das rotas por maior distância usando **Insertion Sort manual**.
- Possui **Dashboard de Performance** com tempo, volume e média de memória das operações.
- O dashboard de performance possui barra de rolagem, totais no rodapé, botão para limpar dados e botão para salvar dados em arquivo `.txt`.
- Aceita importação por arquivos **CSV** e **XLSX**.
- Possui interface web simples com Flask.
- Possui testes unitários com `unittest`.

## Como executar

link do site: https://sistema-sgflow.onrender.com

ou

Na pasta do projeto, execute:

```
pip install -r requirements.txt
python src/ui/app.py
```

Depois acesse no navegador:

```
http://127.0.0.1:5000
```

## Como executar os testes

```
python -m unittest discover tests
```

## Formato dos arquivos de importação

O sistema aceita somente arquivos `.csv` e `.xlsx`.

Colunas esperadas:

```
placa,motorista,operacao,destino,distancia,cargas
```

Exemplo:

```
ABC1D23,Carlos Souza,Carga,São Paulo,62,Notebook|Mouse
DEF4G56,Ana Lima,Descarga,Mogi das Cruzes,18,Palete 01|Palete 02
```

As cargas devem ser separadas por `|`.

## Estrutura de diretórios

```
Sistema-SGFLOW/
├── src/
│   ├── core/
│   │   ├── fila.py
│   │   ├── pilha.py
│   │   └── ordenacao.py
│   ├── service/
│   │   └── sgflow_service.py
│   └── ui/
│       ├── app.py
│       ├── templates/
│       │   ├── index.html
│       │   └── performance.html
│       └── static/
│           └── css/
│               └── style.css
├── tests/
│   ├── test_core.py
│   └── test_service.py
├── data/
│   ├── caminhoes_exemplo.csv
│   └── caminhoes_exemplo.xlsx
├── dashbord/
│   ├── index.html
│   └── css/
│       └── style.css
├── doc/
│   └── E2_SGFLOW_Design_Tecnico.md
├── README.md
└── .gitignore
```

## Observações importantes

- Caminhões de **Descarga** precisam ter cargas iniciais.
- Caminhões de **Carga** podem iniciar vazios e receber cargas pela tela.
- A lista de rotas inicia mostrando primeiro o caminhão com menor distância.
- O botão **Inverter Ordem** altera a lista para mostrar primeiro o caminhão com maior distância.
- As notificações aparecem no rodapé, ao lado do nome SGFLOW.
- O consumo de memória é medido com `tracemalloc`, compatível com Windows, Linux e macOS.
- As métricas de performance ficam armazenadas durante a execução do sistema e podem ser limpas ou exportadas em `.txt`.
