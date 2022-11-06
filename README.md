# sistemabancariopython
# Criando um sistema bancário básico com Python
# Formação Python Developer

# 03 saques diários limitados a R$500,00, por dia
# Caso o usuário não tenha saldo deverá exibir uma mensagem
# Só poderá ter entradas positivas
# Todos os saques e depósitos deverão aparecer no extrato, formatados no modelo R$xxx.xx

menu = """

[d] DEPOSITAR
[s] SACAR
[e] EXTRATO
[q] SAIR

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUE = 3 #ESTA VARIÁVEL NÃO TEM O SEU VALOR ALTERADO

while True:
#enquanto for verdade
    opcao = input(menu)
    #cria a variável OPCAO e solicite ao usuário que digite uma das opções do menu
    if opcao == "d":
    #se o valor digitado for D    
        valor = float(input("Informe o valor do depósito: "))
        #cria a variável VALOR e coloca um valor fracionário no mesmo
        if valor > 0:
        #se o valor digitado for maior que 0       
            saldo += valor
            #adiciona o valor digitado ao saldo
            extrato += f"Depósito: R$ {valor:.2f}\n"
            #adiciona ao extrato o valor depositado no formato R$ xxx.xx
        else:
        #se não    
            print("Operação falhou! O valor informado é inválido.")
            #imprime a mensagem acima
    elif opcao == "s":
    #mais se OPCAO digitada pelo usuário for S    
        valor = float(input("Informe o valor do saque: "))
        #adiciona a variável VALOR um valor fracionário
        excedeu_saldo = valor > saldo
        #cria a variável EXCEDEU_VALOR. Define que ela é verdadeira quando o VALOR for maior que o SALDO
        excedeu_limite = valor > limite
        #cria a variável EXCEDEU_LIMITE. Define que ela é verdadeira quando o VALOR for maior que o LIMITE
        excedeu_limite_saques = numero_saques >= LIMITE_SAQUE
        #cria a variável EXCEDEU_LIMITE_SAQUES. Define que ela é verdadeira quando o NUMERO_SAQUES for maior ou igual ao LIMITE_SAQUE
        if excedeu_saldo:
        #se o valor solicitado for maior que o saldo
            print("Operação falhou! Você não tem saldo suficiente.")
            #imprime a mensagem acima 
        elif excedeu_limite:
        #se o valor solicitado for maior que o limite por saque    
            print("Operação falhou! O valor do saldo excedeu o limite por saque de R$500.00.")
            #imprime a mensagem acima
        elif excedeu_limite_saques:
        #se a quantidade de saques for maior que o limite do dia    
            print("Operação falhou! Número máximo de saques diários excedido.")
            #imprime a mensagem acima
        elif valor> 0:
        #se nenhuma das condições anteriores for exercdia e se o valor for maior que 0
            saldo -= valor
            #diminua o valor do saldo
            extrato += f"Saque: R$ {vealor:.2f}\n"
            #adiciona ao extrato o valor sacado no formato R$ xxx.xx
            numero_saques += 1
            #contabiliza um saque realizado

        else:
        #se não
            print("Operação falhou! O valor informado é inválido.")
            #imprime a mensagem acima

    elif opcao == "e":
    #e se OPCAO for igual a E
        print("\n============EXTRATO============")
        #imprime a mensagem acima com as demais abaixo
        print("Não foram realizadas movimentações." if not extrato else extrato)
        #imprime a mensagem acima se não houver movimentações
        print(f"\nSaldo: R$ {saldo:.2f}")
        #imprime o saldo no formato R$ xxx.xx
        print("===============================")
        #imprime a mensagem acima

    elif opcao == "q":
    #e se a OPCAO escolhida for Q
        break
        #pare o loop

    else: 
    #se não
        print("Operação inválida, por favor selecione a operação deseja.")
        #imprime a mensagem acima



