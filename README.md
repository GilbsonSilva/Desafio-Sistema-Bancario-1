
menu = """
    ========== MENU ==========

    Digite a sua opção!

    [1] Depositar
    [2] Sacar
    [3] Extrato
    [4] Sair

    ==========================

    O Banco @ agradece o uso de seu sistema, volte sempre!!!!
"""

saldo = 0
limite_diario = 500
extrato = ""
numero_saques = 0
LIMITES_SAQUES = 3

while True:
    
    opcao = input(menu)

    if opcao == 1:
        valor_depositado = float(input("Digite o valor a ser depositado: "))
       
        if valor_depositado > 0:
            saldo += valor_depositado
            extrato += f"Depósito: R$ {valor_depositado:.2f}\n"
        else:
            print("Falha na Operação! O valor informado é inválido.")

    elif opcao == 2:
        valor_sacado = float(input("Digite o valor a ser sacado: "))
        excedeu_saldo = valor_sacado > saldo
        excedeu_limite = valor_sacado > limite_diario
        excedeu_saques = numero_saques >= LIMITES_SAQUES

        if excedeu_saldo:
            print("Falha na operação! Saldo insuficiente registrado na conta.")
        elif excedeu_limite:
            print("Falha na operação! Saque excede o valor do limite disponível.")
        elif excedeu_saques:
            print("Falha na operação! Número máximo de saques diário excedido.")

        elif valor_sacado > 0:
            numero_saques += 1
            saldo -= valor_sacado
            extrato += f"Saque: R$ {valor_sacado:.2f}\n"
            print("\n=== Saque realizado com sucesso! ===")

        else:
             print("Falha na operação! Valor informado é inválido.")

    elif opcao == 3:
        print ("\n----------------Extrato----------------")
        print ("Não foram realizadas movimentações." if not extrato else extrato)
        print (f"Saldo autal: R$ {saldo:.2f}")
        print ("----------------------------------------")

    elif opcao == 4:
        break

    else: 
        print("Operação Inválida, por favor selecione novamente a operação desejada.")

