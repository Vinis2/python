from abc import ABC, abstractmethod

# Interface da Inspeção
class Inspecao(ABC):
    @abstractmethod
    def realizar_inspecao(self):
        pass

# Classes concretas de inspeção
class InspecaoEletrica(Inspecao):
    def realizar_inspecao(self):
        print("Realizando inspeção elétrica em componentes como circuitos e cabos...")
        print("Inspeção finalizada.")

class InspecaoMecanica(Inspecao):
    def realizar_inspecao(self):
        print("Iniciando o processo de inspeção...")
        print("Criando uma instância de inspeção mecânica.")
        print("Realizando inspeção mecânica em componentes como motores e engrenagens...")
        print("Inspeção finalizada.")

# Classe de Fábrica
class FabricaInspecao(ABC):
    @abstractmethod
    def criar_inspecao(self):
        pass

class FabricaInspecaoEletrica(FabricaInspecao):
    def criar_inspecao(self):
        return InspecaoEletrica()

class FabricaInspecaoMecanica(FabricaInspecao):
    def criar_inspecao(self):
        return InspecaoMecanica()

# Cliente que usa a fábrica para criar inspeções
def cliente(fabrica: FabricaInspecao):
    inspecao = fabrica.criar_inspecao()
    inspecao.realizar_inspecao()

# Exemplo de uso
if __name__ == "_main_":
    print("Iniciando inspeção elétrica:")
    cliente(FabricaInspecaoEletrica())
    
    print("\nIniciando inspeção mecânica:")
    cliente(FabricaInspecaoMecanica())
