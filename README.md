# **Sistema de Fila de Espera no Hospital com Priorização**

Um hospital deseja organizar o atendimento de pacientes em uma **fila de espera** priorizando idosos e classificando os casos em **níveis de urgência**.

## **Objetivo**

1. Criar um sistema que:
   - Classifique os pacientes em **alta urgência**, **média urgência** e **baixa urgência**.
   - Priorize o atendimento de **idosos** (idade ≥ 60 anos).
2. Exibir a ordem de atendimento considerando:
   - A **urgência** (alta → média → baixa).  
   - A **idade** (idosos têm prioridade dentro de cada nível de urgência).

---

## **Regras**

1. Crie uma **classe** `Paciente` com os seguintes atributos:
   - Nome do paciente.
   - Idade.
   - Classificação de urgência (**alta**, **média** ou **baixa**).  

2. Crie uma **classe** `FilaHospital` com os seguintes métodos:
   - `adicionar_paciente`: adiciona um paciente à fila.  
   - `exibir_fila`: exibe a ordem de atendimento no formato:
     ```
     Alta urgência:
     - Nome: Maria | Idade: 72 anos
     - Nome: João | Idade: 65 anos

     Média urgência:
     - Nome: Lucas | Idade: 50 anos

     Baixa urgência:
     - Nome: Ana | Idade: 34 anos
     ```
   - `proximo_paciente`: remove e retorna o próximo paciente na ordem de atendimento.

3. A prioridade de atendimento segue a ordem:
   - **Alta urgência** > **Média urgência** > **Baixa urgência**.
   - Dentro de cada categoria de urgência, **idosos (idade ≥ 60 anos)** têm prioridade.

---

## **Dados de Entrada**

Os dados fornecidos são:  

```python
pacientes = [
    {"nome": "Maria", "idade": 72, "urgencia": "alta"},
    {"nome": "Lucas", "idade": 50, "urgencia": "média"},
    {"nome": "Ana", "idade": 34, "urgencia": "baixa"},
    {"nome": "João", "idade": 65, "urgencia": "alta"},
    {"nome": "Clara", "idade": 28, "urgencia": "média"},
    {"nome": "Pedro", "idade": 80, "urgencia": "alta"},
    {"nome": "Carla", "idade": 59, "urgencia": "baixa"}
]
```
## **Formato de Saída**

A exibição inicial da fila de atendimento deve ser:


Ordem de Atendimento

Alta urgência:
- Nome: Pedro | Idade: 80 anos
- Nome: Maria | Idade: 72 anos
- Nome: João | Idade: 65 anos

Média urgência:
- Nome: Lucas | Idade: 50 anos
- Nome: Clara | Idade: 28 anos

Baixa urgência:
- Nome: Carla | Idade: 59 anos
- Nome: Ana | Idade: 34 anos
```
---

Ao chamar o método `proximo_paciente`, deve exibir:
```
Próximo paciente
- Nome: Pedro | Idade: 80 anos | Urgência: Alta
```

---

Após o atendimento do próximo paciente, a fila deve ser exibida assim:

```
Ordem de Atendimento

Alta urgência:
- Nome: Maria | Idade: 72 anos
- Nome: João | Idade: 65 anos

Média urgência:
- Nome: Lucas | Idade: 50 anos
- Nome: Clara | Idade: 28 anos

Baixa urgência:
- Nome: Carla | Idade: 59 anos
- Nome: Ana | Idade: 34 anos
```
