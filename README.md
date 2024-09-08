# Desenvolvedor .Net Backend
Repositório criado para compartilhar conhecimentos que adquiri ao longo da minha carreira como Desenvolvedor .Net Backend.

## OO(Orientação a Objetos)
Paradigma de programação que organiza o software em "objetos", que são instâncias de "classes". Cada objeto contém dados (chamados de atributos ou propriedades) e comportamentos (chamados de métodos ou funções). A Orientação a Objetos facilita o desenvolvimento de software modular, reutilizável e escalável, e é amplamente utilizada em linguagens como C#, Java, Python e C++.

Os quatro pilares da OO são:
- Encapsulamento: Agrupa dados e comportamentos relacionados dentro de uma classe, ocultando detalhes internos e expondo apenas o que é necessário para o uso externo.

- Herança: Permite que uma classe herde atributos e métodos de outra classe, facilitando a reutilização e extensão do código.

- Polimorfismo: Permite que objetos de diferentes classes sejam tratados como objetos de uma classe comum, possibilitando a utilização de uma única interface para diferentes tipos de objetos.

- Abstração: Permite que detalhes complexos sejam ocultados, proporcionando uma interface mais simples para interagir com os objetos.

Vamos listar e descrever todos os conceitos e técnicas de Orientação a Objetos (OO) aplicados a um contexto de e-commerce usando C#. Vou fornecer exemplos práticos para cada conceito e técnica, destacando como eles podem ser utilizados no desenvolvimento de um sistema de e-commerce.

### 1. **Classe**

**Descrição:** Define a estrutura dos objetos, incluindo dados (propriedades) e comportamentos (métodos).

```csharp
public class Produto
{
    public string Nome { get; set; }
    public decimal Preco { get; set; }
    
    public Produto(string nome, decimal preco)
    {
        Nome = nome;
        Preco = preco;
    }
}
```

### 2. **Objeto**

**Descrição:** Instância de uma classe. Representa um item específico com seus próprios dados.

```csharp
Produto produto = new Produto("Laptop", 1500.00m);
```

### 3. **Herança**

**Descrição:** Permite que uma classe herde propriedades e métodos de outra classe.

```csharp
// Classe base
public class Categoria
{
    public string Nome { get; set; }
    
    public Categoria(string nome)
    {
        Nome = nome;
    }
}

// Classe derivada
public class Eletronico : Categoria
{
    public Eletronico() : base("Eletrônico") { }
}
```

### 4. **Polimorfismo**

**Descrição:** Permite que métodos tenham diferentes comportamentos com base no tipo de objeto.

```csharp
// Classe base
public abstract class Pagamento
{
    public abstract void ProcessarPagamento();
}

// Subclasses
public class PagamentoCartao : Pagamento
{
    public override void ProcessarPagamento()
    {
        Console.WriteLine("Pagamento com cartão de crédito.");
    }
}

public class PagamentoBoleto : Pagamento
{
    public override void ProcessarPagamento()
    {
        Console.WriteLine("Pagamento com boleto bancário.");
    }
}

// Uso
Pagamento pagamento = new PagamentoCartao();
pagamento.ProcessarPagamento();
```

### 5. **Encapsulamento**

**Descrição:** Protege o estado interno de um objeto e permite acesso controlado.

```csharp
public class Pedido
{
    private decimal valorTotal;
    
    public decimal ValorTotal
    {
        get { return valorTotal; }
        private set { valorTotal = value; }
    }
    
    public void AtualizarValorTotal(decimal valor)
    {
        if (valor >= 0)
        {
            ValorTotal = valor;
        }
    }
}
```

### 6. **Abstração**

**Descrição:** Define a interface de um objeto sem especificar sua implementação.

```csharp
public interface INotificacao
{
    void Enviar(string mensagem);
}

public class NotificacaoEmail : INotificacao
{
    public void Enviar(string mensagem)
    {
        Console.WriteLine($"Email enviado com a mensagem: {mensagem}");
    }
}
```

### 7. **Composição**

**Descrição:** Modela objetos compostos a partir de outros objetos, indicando uma relação "tem um".

```csharp
public class CarrinhoDeCompras
{
    private List<Produto> produtos = new List<Produto>();
    
    public void AdicionarProduto(Produto produto)
    {
        produtos.Add(produto);
    }

    public decimal CalcularTotal()
    {
        return produtos.Sum(p => p.Preco);
    }
}
```

### 8. **Interface**

**Descrição:** Define um contrato que as classes podem implementar.

```csharp
public interface IAvaliar
{
    void Avaliar(string comentario, int estrelas);
}

public class AvaliacaoProduto : IAvaliar
{
    public void Avaliar(string comentario, int estrelas)
    {
        Console.WriteLine($"Comentário: {comentario}, Estrelas: {estrelas}");
    }
}
```

### 9. **Sobrecarga de Métodos**

**Descrição:** Permite que métodos com o mesmo nome realizem diferentes tarefas com base em seus parâmetros.

```csharp
public class Desconto
{
    public decimal AplicarDesconto(decimal preco, decimal percentual)
    {
        return preco - (preco * percentual / 100);
    }
    
    public decimal AplicarDesconto(decimal preco, decimal valorDesconto, bool emValor)
    {
        return emValor ? preco - valorDesconto : AplicarDesconto(preco, valorDesconto);
    }
}
```

### 10. **Sobreposição (Override)**

**Descrição:** Permite que uma classe derivada forneça uma implementação específica para um método que já foi definido na classe base.

```csharp
public class Produto
{
    public virtual void ExibirDetalhes()
    {
        Console.WriteLine("Detalhes do produto.");
    }
}

public class ProdutoEletronico : Produto
{
    public override void ExibirDetalhes()
    {
        Console.WriteLine("Detalhes do produto eletrônico.");
    }
}
```

### 11. **Classe Abstrata**

**Descrição:** Classe que não pode ser instanciada e pode conter métodos abstratos que devem ser implementados pelas subclasses.

```csharp
public abstract class Entidade
{
    public abstract void Validar();
}

public class Produto : Entidade
{
    public override void Validar()
    {
        // Implementação da validação do produto
    }
}
```

### 12. **Método Abstrato**

**Descrição:** Método que deve ser implementado pelas classes derivadas.

```csharp
public abstract class Pagamento
{
    public abstract void ProcessarPagamento();
}
```

### 13. **Construtor**

**Descrição:** Método especial chamado quando um objeto é criado, usado para inicializar o estado do objeto.

```csharp
public class Produto
{
    public string Nome { get; set; }
    public decimal Preco { get; set; }

    public Produto(string nome, decimal preco)
    {
        Nome = nome;
        Preco = preco;
    }
}
```

### 14. **Destruidor**

**Descrição:** Método especial chamado quando um objeto é destruído, usado para liberar recursos.

```csharp
public class Pedido
{
    ~Pedido()
    {
        // Código para liberar recursos
    }
}
```

### 15. **Modificadores de Acesso**

**Descrição:** Controlam a visibilidade dos membros de uma classe (e.g., `public`, `private`, `protected`).

```csharp
public class Cliente
{
    private string nome;

    public string Nome
    {
        get { return nome; }
        set { nome = value; }
    }
}
```

### 16. **Dependência**

**Descrição:** Relação onde uma classe depende de outra para funcionar.

```csharp
public class Pedido
{
    private readonly INotificacao notificacao;

    public Pedido(INotificacao notificacao)
    {
        this.notificacao = notificacao;
    }

    public void Finalizar()
    {
        notificacao.Enviar("Pedido finalizado.");
    }
}
```

### 17. **Injeção de Dependência**

**Descrição:** Técnica para fornecer dependências a uma classe de fora, ao invés de a classe criar suas próprias instâncias.

```csharp
public class Pedido
{
    private readonly INotificacao notificacao;

    public Pedido(INotificacao notificacao)
    {
        this.notificacao = notificacao;
    }
}
```

### 18. **Delegado**

**Descrição:** Tipo que representa métodos e pode ser usado para implementar callbacks e eventos.

```csharp
public delegate void Notificacao(string mensagem);

public class Pedido
{
    public event Notificacao OnPedidoFinalizado;

    public void Finalizar()
    {
        OnPedidoFinalizado?.Invoke("Pedido finalizado.");
    }
}
```

### 19. **Eventos**

**Descrição:** Mecanismo para notificar outros objetos sobre mudanças de estado ou ações.

```csharp
public class Pedido
{
    public event EventHandler PedidoFinalizado;

    protected virtual void OnPedidoFinalizado()
    {
        PedidoFinalizado?.Invoke(this, EventArgs.Empty);
    }

    public void Finalizar()
    {
        OnPedidoFinalizado();
    }
}
```

### 20. **Propriedades**

**Descrição:** Mecanismo para acessar e modificar o estado de um objeto com encapsulamento.

```csharp
public class Produto
{
    private decimal preco;

    public decimal Preco
    {
        get { return preco; }
        set
        {
            if (value >= 0)
            {
                preco = value;
            }
        }
    }
}
```

### 21. **Métodos Estáticos**

**Descrição:** Métodos que pertencem à classe em vez de a uma instância específica.

```csharp
public class Calculadora
{
    public static decimal Somar(decimal a, decimal b)
    {
        return a + b;
    }
}
```

### 22. **Classe Estática**

**Descrição:** Classe que não pode ser instanciada e só pode conter membros estáticos.

```csharp
public static class Utilitarios
{
    public static void ImprimirRelatorio(string relatorio)
    {
        Console.WriteLine(relatorio);
    }
}
```

### Aplicação Prática no Contexto de E-commerce

Esses conceitos e técnicas ajudam a modelar e implementar diferentes aspectos de um sistema de e-commerce:

- **Classe:** `Produto`, `Cliente`, `Pedido`.
- **Herança:** `ProdutoEletronico` herda de `Produto`.
- **Polimorfismo:** Implementar diferentes tipos de pagamento.
- **Encapsulamento:** Protege detalhes internos de um `Pedido`.
- **Abstração:** Define uma interface para `INotificacao

`.
- **Composição:** `CarrinhoDeCompras` contém múltiplos `Produto`.
- **Interface:** `IAvaliar` para avaliações de produtos.
- **Sobrecarga de Métodos:** Métodos para aplicar descontos.
- **Sobreposição (Override):** Substitui métodos em subclasses.
- **Classe Abstrata:** `Entidade` com método `Validar`.
- **Método Abstrato:** Implementação de validação de pagamento.
- **Construtor:** Inicializa objetos `Produto` e `Pedido`.
- **Destruidor:** Libera recursos em `Pedido`.
- **Modificadores de Acesso:** Controla acesso a dados de `Cliente`.
- **Dependência e Injeção de Dependência:** `Pedido` que usa `INotificacao`.
- **Delegado e Eventos:** Notifica sobre a finalização de pedidos.
- **Propriedades:** Controle de acesso a dados em `Produto`.
- **Métodos e Classe Estática:** `Calculadora` para cálculos de desconto.

Esses exemplos cobrem uma ampla gama de técnicas e conceitos OO aplicados em um sistema de e-commerce, e são fundamentais para criar um sistema robusto e bem estruturado. Se precisar de mais detalhes ou exemplos específicos, estou à disposição para ajudar!

# Clean Code
Clean Code refere-se a um conjunto de práticas e princípios para escrever código que seja fácil de entender, manter e expandir. O conceito foi popularizado pelo livro Clean Code: A Handbook of Agile Software Craftsmanship de Robert C. Martin, também conhecido como "Uncle Bob".
