class Produto:
    def __init__(self, id, nome, preco):
        self.id = id
        self.nome = nome
        self.preco = preco

    def __str__(self):
        return f"{self.nome} - R${self.preco:.2f}"

class Carrinho:
    def __init__(self):
        self.itens = []

    def adicionar(self, produto, quantidade):
        for item in self.itens:
            if item['produto'].id == produto.id:
                item['quantidade'] += quantidade
                return
        self.itens.append({'produto': produto, 'quantidade': quantidade})

    def remover(self, produto_id):
        self.itens = [item for item in self.itens if item['produto'].id != produto_id]

    def visualizar(self):
        if not self.itens:
            print("O carrinho está vazio.")
        else:
            for item in self.itens:
                print(f"{item['produto']} - Quantidade: {item['quantidade']}")
            print(f"Total: R${self.total():.2f}")

    def total(self):
        return sum(item['produto'].preco * item['quantidade'] for item in self.itens)

        def menu():
    print("\nMenu:")
    print("1 - Adicionar produto ao carrinho")
    print("2 - Remover produto do carrinho")
    print("3 - Visualizar carrinho")
    print("4 - Sair")

def adicionar_produto(carrinho, produtos):
    print("\nProdutos disponíveis:")
    for produto in produtos:
        print(f"{produto.id} - {produto.nome} - R${produto.preco:.2f}")

    produto_id = int(input("\nDigite o ID do produto para adicionar: "))
    quantidade = int(input("Digite a quantidade: "))

    produto = next((p for p in produtos if p.id == produto_id), None)
    if produto:
        carrinho.adicionar(produto, quantidade)
        print(f"{produto.nome} adicionado ao carrinho.")
    else:
        print("Produto não encontrado.")

def remover_produto(carrinho):
    produto_id = int(input("\nDigite o ID do produto para remover: "))
    carrinho.remover(produto_id)
    print("Produto removido do carrinho.")

def main():
    # Produtos disponíveis
    produtos = [
        Produto(1, "Produto A", 10.00),
        Produto(2, "Produto B", 20.00),
        Produto(3, "Produto C", 30.00)
    ]
    
    carrinho = Carrinho()
    
    while True:
        menu()
        opcao = int(input("\nEscolha uma opção: "))
        
        if opcao == 1:
            adicionar_produto(carrinho, produtos)
        elif opcao == 2:
            remover_produto(carrinho)
        elif opcao == 3:
            carrinho.visualizar()
        elif opcao == 4:
            print("Saindo...")
            break
        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    main()

    python carrinho_compras.py
