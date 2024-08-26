print("Bem vindo ao carrinho de compras")

carrinho = []
precos = []
total = []
preco_total = []

while True:
    print()
    print('Escolha sua opção: ')
    print("1.Adicionar item ")
    print("2.Ver carrinho ")
    print("3.Remover Item ")
    print("4.calcular total ")

    digitado = int(input('Digite um número para continuar: '))

    item = ""

    if digitado == 1:

        while item != "ok":

            item = input('O que você gostaria de adicionar? ')
            preco = float(input('digite o preço '))
            precos.append(preco)

            ok = input('digite ok quando terminar. ')

            if item != 'ok':
                carrinho.append(item)

                print(f"'{item}' Foi adicionado ao seu carrinho. ")
                print(f" O preço é R${preco}")
                break

    if digitado == 2:

        print('Isto é o que está no seu carrinho de compras: ')

        for i, item_carrinho in enumerate(carrinho):
            preco = precos[i]

            print(f"{i + 1}. {item_carrinho} - R${preco}")

        # ok = input('pressione ok quando terminar ')
        if not carrinho:
            print('Seu carrinho está vazio.')

        input("Pressione enter para continuar...")
        continue

    if digitado == 3:
        retirar = input('Digite o que você gostaria de remover? ')

        if retirar in carrinho:
            index = carrinho.index(retirar)
            carrinho.remove(retirar)
            preco = precos.pop(index)
            print(f"{retirar} removido do carrinho. Preço: R${preco}")

        else:
            print('Item não encontrado no carrinho.')

        continue

    if digitado == 4:

        preco_total = sum(precos)
        print(f"O total é R$ {preco_total}")

        if item != 'ok':
            break

    if digitado == 5:
        print('volte sempre.')
        break
