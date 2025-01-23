# Fila-do-Hospital-em-Python
estou fazendo uma simulacao de uma fila de urgencia e idade em python
#lista de pacientes do hospital.
pacientes = [
    {"nome": "Maria", "idade": 72, "urgencia": "alta"},
    {"nome": "Lucas", "idade": 50, "urgencia": "média"},
    {"nome": "Ana", "idade": 34, "urgencia": "baixa"},
    {"nome": "João", "idade": 65, "urgencia": "alta"},
    {"nome": "Clara", "idade": 28, "urgencia": "média"},
    {"nome": "Pedro", "idade": 80, "urgencia": "alta"},
    {"nome": "Carla", "idade": 59, "urgencia": "baixa"}
]

#fazendo o codigo para charmar o paciente com nivel de urgencia, alta, media e baixa.
class Paciente:
     def __init__(self, nome, idade, urgencia):#
        self.nome = nome # nome do paciente 
        self.idade = idade # idade do paciente
        self.urgencia = urgencia # grau de urgencia(baixa, media, alta)

     def __repr__(self):
         return f"Nome: {self.nome}, Idade: {self.idade}, Urgencia: {self.urgencia}"
     
     def prioridade_idoso(self):# criando a priorida para pacientes idosos com idade ≥ 60
         """Retornar True se o paciente for idoso (idade ≥ 60), para priorizacao."""
         return self.idade >= 60
     def apresentar(self):
         print(f"Paciente({self.nome}, {self.idade}, {self.urgencia}),")

         #Criando a Fila do Hospital
class FilaHospital:
     def __init__(self):
        #Dicionario para organizar os pacientes com nivel e urgencia
        self.fila = {"alta":[], "média": [], "baixa": []} 

     def adicionar_paciente(self, paciente):
         """adicona um paciente a fila com base na urgencia."""
         if paciente.urgencia in self.fila:
            self.fila[paciente.urgencia].append(paciente)
            # print(f"Adicioando: {paciente.nome} | Idade: {paciente.idade} | Urgenica: {paciente.urgencia}")
         else:
             print(f"Erro: urgencia '{paciente.urgencia}' invalida!")

     def exibir_fila(self): #exibir fila dos pacinetes
         """Exibir a Ordem de atendimento, organizada por nivel de urgencia e prioridade de idade"""         
         print("Ordem de Atendimento\n")

         for urgencia in ["alta", "média", "baixa"]:
             print(f"{urgencia.capitalize()} urgencia")
             # ordena os pacientes por prioridade (idoso > mais velho)
             pacientes_urgencia = sorted(self.fila[urgencia], key=lambda p: (p.prioridade_idoso(), p.idade), reverse=True)
         
             for paciente in pacientes_urgencia:
                 print(f"- Nome: {paciente.nome} | Idade: {paciente.idade}, anos")
             print() #adiciona linha em branco entre os niveis de urgencia

     def proximo_paciente(self):# cahamdno proximo proximo paciente e removendo da fila
         """Remove e retorna o proximo paciente na ordem de atendimente, considerando urgencia e idade."""
         # Prioridade: alta > media > baixa 
         for nivel in ["alta", "média", "baixa"]:
             if self.fila[nivel]:
            #Reorganizar a lista de pacientes a cada chama para garantir a prioridade correta
                self.fila[nivel]= sorted(self.fila[nivel], key=lambda p:(p.prioridade_idoso(), p.idade), reverse=True)     
                paciente = self.fila[nivel].pop(0)#remove o primeiro da fila
                return paciente
         print("A fila esta vazia")
         return None 
     
     # Dados de alguns Pacientes
pacientes = [
     Paciente("Maria", 72, "alta"),
     Paciente("Lucas", 50, "média"),
     Paciente("Ana", 34, "baixa"),
     Paciente("João", 65, "alta"),
     Paciente("Clara", 28, "média"),
     Paciente("Pedro", 80, "alta"),
     Paciente("Carla", 59, "baixa"),
]

# criando a fila do hospital
fila_hospital = FilaHospital()

# Adicionando os pacienes a Fila
for paciente in pacientes:
    fila_hospital.adicionar_paciente(paciente)
    
#Exibindo a fila
fila_hospital.exibir_fila()

# Chamar o proximo paciente
print("Chamando o proximo paciente:")
proximo = fila_hospital.proximo_paciente()
if proximo:
    print(f"Atendimento: Nome: {proximo.nome} | Idade: {proximo.idade} anos | Urgência: {proximo.urgencia}\n") 

#exibir a fila novamente apos o atendimento
# print("Fila atualizada:")
fila_hospital.exibir_fila()