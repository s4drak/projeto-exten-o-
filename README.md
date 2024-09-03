# projeto-exten-o-
# lixo_coletado.py

from datetime import datetime

class LixoColetado:
    def __init__(self, tipo_lixo, peso, data_coleta=None):
        self.tipo_lixo = tipo_lixo
        self.peso = peso
        self.data_coleta = data_coleta or datetime.now().strftime('%Y-%m-%d %H:%M:%S')

    def __str__(self):
        return f"{self.tipo_lixo} - {self.peso}kg - {self.data_coleta}"

class SistemaColeta:
    def __init__(self):
        self.registros = []

    def registrar_coleta(self, tipo_lixo, peso):
        novo_registro = LixoColetado(tipo_lixo, peso)
        self.registros.append(novo_registro)
        print("Coleta registrada com sucesso!")

    def visualizar_registros(self):
        if not self.registros:
            print("Nenhuma coleta registrada.")
            return
        for registro in self.registros:
            print(registro)

if __name__ == "__main__":
    sistema = SistemaColeta()
    
    while True:
        print("\nSistema de Gerenciamento de Coleta de Lixo")
        print("1. Registrar nova coleta")
        print("2. Visualizar registros")
        print("3. Sair")
        opcao = input("Escolha uma opção: ")

        if opcao == '1':
            tipo_lixo = input("Digite o tipo de lixo: ")
            peso = float(input("Digite o peso do lixo (em kg): "))
            sistema.registrar_coleta(tipo_lixo, peso)
        elif opcao == '2':
            sistema.visualizar_registros()
        elif opcao == '3':
            break
        else:
            print("Opção inválida, tente novamente.")
