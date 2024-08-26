class Produto:
    def __init__(self, id, nome, preco):
        self.id = id
        self.nome = nome
        self.preco = preco

    def __str__(self):
        return f"{self.nome} - R${self.preco:.2f}"

# Carrinho de Compras que armazena produtos adicionados
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
        for item in self.itens:
            print(f"{item['produto']} - Quantidade: {item['quantidade']}")
        print(f"Total: R${self.total():.2f}")

    def total(self):
        return sum(item['produto'].preco * item['quantidade'] for item in self.itens)
