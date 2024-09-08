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

Claro! Vamos explorar os princípios SOLID com exemplos em C# no contexto de e-commerce. SOLID é um acrônimo para cinco princípios de design de software que ajudam a criar sistemas mais compreensíveis, flexíveis e manuteníveis. Esses princípios são:

1. **S - Single Responsibility Principle (SRP)**
2. **O - Open/Closed Principle (OCP)**
3. **L - Liskov Substitution Principle (LSP)**
4. **I - Interface Segregation Principle (ISP)**
5. **D - Dependency Inversion Principle (DIP)**

## 1. **Single Responsibility Principle (SRP)**

**Descrição:** Uma classe deve ter apenas uma razão para mudar, ou seja, deve ter uma única responsabilidade.

**Exemplo:**

```csharp
// Classe responsável apenas por manipulação de dados do produto
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

// Classe responsável por salvar o produto no banco de dados
public class ProdutoRepositorio
{
    public void Salvar(Produto produto)
    {
        // Código para salvar o produto no banco de dados
    }
}
```

No exemplo acima, `Produto` tem a responsabilidade de representar um produto, enquanto `ProdutoRepositorio` é responsável por persistir dados. Cada classe tem uma responsabilidade clara.

### 2. **Open/Closed Principle (OCP)**

**Descrição:** Entidades de software (classes, módulos, funções, etc.) devem estar abertas para extensão, mas fechadas para modificação.

**Exemplo:**

```csharp
// Interface para cálculo de desconto
public interface IDesconto
{
    decimal AplicarDesconto(decimal preco);
}

// Implementação de desconto percentual
public class DescontoPercentual : IDesconto
{
    private readonly decimal percentual;

    public DescontoPercentual(decimal percentual)
    {
        this.percentual = percentual;
    }

    public decimal AplicarDesconto(decimal preco)
    {
        return preco - (preco * percentual / 100);
    }
}

// Implementação de desconto fixo
public class DescontoFixo : IDesconto
{
    private readonly decimal valorDesconto;

    public DescontoFixo(decimal valorDesconto)
    {
        this.valorDesconto = valorDesconto;
    }

    public decimal AplicarDesconto(decimal preco)
    {
        return preco - valorDesconto;
    }
}

// Classe que usa desconto
public class CarrinhoDeCompras
{
    private readonly IDesconto desconto;

    public CarrinhoDeCompras(IDesconto desconto)
    {
        this.desconto = desconto;
    }

    public decimal CalcularPrecoFinal(decimal precoOriginal)
    {
        return desconto.AplicarDesconto(precoOriginal);
    }
}
```

Aqui, `CarrinhoDeCompras` está fechado para modificações, mas aberto para extensões, pois novos tipos de desconto podem ser adicionados sem alterar o código existente.

### 3. **Liskov Substitution Principle (LSP)**

**Descrição:** Objetos de uma classe base devem poder ser substituídos por objetos de uma classe derivada sem alterar a funcionalidade do programa.

**Exemplo:**

```csharp
// Classe base
public abstract class Pagamento
{
    public abstract void ProcessarPagamento();
}

// Implementação de pagamento com cartão
public class PagamentoCartao : Pagamento
{
    public override void ProcessarPagamento()
    {
        // Código para processar pagamento com cartão
    }
}

// Implementação de pagamento com boleto
public class PagamentoBoleto : Pagamento
{
    public override void ProcessarPagamento()
    {
        // Código para processar pagamento com boleto
    }
}

// Classe que usa pagamentos
public class Pedido
{
    private readonly Pagamento pagamento;

    public Pedido(Pagamento pagamento)
    {
        this.pagamento = pagamento;
    }

    public void Finalizar()
    {
        pagamento.ProcessarPagamento();
        Console.WriteLine("Pedido finalizado.");
    }
}
```

Em `Pedido`, você pode substituir `Pagamento` por `PagamentoCartao` ou `PagamentoBoleto` sem alterar o comportamento da classe `Pedido`.

### 4. **Interface Segregation Principle (ISP)**

**Descrição:** Uma interface não deve obrigar uma classe a implementar métodos que não utiliza. As interfaces devem ser específicas e pequenas.

**Exemplo:**

```csharp
// Interfaces específicas
public interface IPagamentoComCartao
{
    void ProcessarPagamentoComCartao();
}

public interface IPagamentoComBoleto
{
    void ProcessarPagamentoComBoleto();
}

// Implementações específicas
public class PagamentoCartao : IPagamentoComCartao
{
    public void ProcessarPagamentoComCartao()
    {
        // Código para processar pagamento com cartão
    }
}

public class PagamentoBoleto : IPagamentoComBoleto
{
    public void ProcessarPagamentoComBoleto()
    {
        // Código para processar pagamento com boleto
    }
}

// Classe que usa pagamento
public class Pedido
{
    private readonly IPagamentoComCartao pagamentoCartao;
    private readonly IPagamentoComBoleto pagamentoBoleto;

    public Pedido(IPagamentoComCartao pagamentoCartao, IPagamentoComBoleto pagamentoBoleto)
    {
        this.pagamentoCartao = pagamentoCartao;
        this.pagamentoBoleto = pagamentoBoleto;
    }

    public void FinalizarPagamentoComCartao()
    {
        pagamentoCartao.ProcessarPagamentoComCartao();
    }

    public void FinalizarPagamentoComBoleto()
    {
        pagamentoBoleto.ProcessarPagamentoComBoleto();
    }
}
```

Aqui, `Pedido` não precisa saber de detalhes desnecessários sobre o tipo de pagamento. Ele só interage com as interfaces específicas.

### 5. **Dependency Inversion Principle (DIP)**

**Descrição:** Dependências devem ser de abstrações (interfaces), e não de implementações concretas. O código de alto nível não deve depender do código de baixo nível, ambos devem depender de abstrações.

**Exemplo:**

```csharp
// Abstrações
public interface INotificacao
{
    void Enviar(string mensagem);
}

public interface IPedido
{
    void Finalizar();
}

// Implementações concretas
public class NotificacaoEmail : INotificacao
{
    public void Enviar(string mensagem)
    {
        Console.WriteLine($"Email enviado com a mensagem: {mensagem}");
    }
}

public class Pedido : IPedido
{
    private readonly INotificacao notificacao;

    public Pedido(INotificacao notificacao)
    {
        this.notificacao = notificacao;
    }

    public void Finalizar()
    {
        // Código para finalizar o pedido
        notificacao.Enviar("Seu pedido foi finalizado.");
    }
}
```

Aqui, `Pedido` depende da abstração `INotificacao`, não da implementação concreta `NotificacaoEmail`. Isso permite que diferentes métodos de notificação possam ser utilizados sem alterar a classe `Pedido`.

### Resumo

Os princípios SOLID ajudam a construir sistemas mais flexíveis e manuteníveis. Aqui estão os conceitos aplicados ao contexto de e-commerce:

- **SRP (Single Responsibility Principle):** Separação de responsabilidades, como em `Produto` e `ProdutoRepositorio`.
- **OCP (Open/Closed Principle):** Extensibilidade sem modificação, como em `IDesconto` e suas implementações.
- **LSP (Liskov Substitution Principle):** Substituição de classes derivadas, como em `Pagamento` e suas subclasses.
- **ISP (Interface Segregation Principle):** Interfaces pequenas e específicas, como em `IPagamentoComCartao` e `IPagamentoComBoleto`.
- **DIP (Dependency Inversion Principle):** Dependência de abstrações, como em `INotificacao` e `Pedido`.

Se precisar de mais detalhes sobre algum dos princípios ou tiver dúvidas adicionais, sinta-se à vontade para perguntar!

# Clean Code
É um conceito desenvolvido por Robert C. Martin (também conhecido como Uncle Bob), que promove a escrita de código legível, manutenível e de alta qualidade. No contexto de e-commerce, aplicar princípios de Clean Code ajuda a criar um sistema robusto e fácil de entender.

Aqui está uma lista de práticas e exemplos de como aplicar os princípios de Clean Code em C# no contexto de e-commerce:

### 1. **Nomes Significativos**

**Descrição:** Use nomes claros e descritivos para classes, métodos e variáveis.

**Exemplo:**

```csharp
// Nome da classe é claro sobre o que ela representa
public class CalculadoraDeDesconto
{
    // Nome do método explica claramente o que o método faz
    public decimal CalcularDesconto(decimal precoOriginal, decimal percentualDesconto)
    {
        return precoOriginal - (precoOriginal * percentualDesconto / 100);
    }
}
```

### 2. **Funções Pequenas**

**Descrição:** Mantenha funções pequenas e com uma única responsabilidade.

**Exemplo:**

```csharp
public class CarrinhoDeCompras
{
    public decimal CalcularTotal(decimal precoProduto, int quantidade)
    {
        decimal subtotal = CalcularSubtotal(precoProduto, quantidade);
        decimal desconto = CalcularDesconto(subtotal);
        return subtotal - desconto;
    }

    private decimal CalcularSubtotal(decimal precoProduto, int quantidade)
    {
        return precoProduto * quantidade;
    }

    private decimal CalcularDesconto(decimal subtotal)
    {
        // Implementação do cálculo de desconto
        return subtotal * 0.10m; // Exemplo: 10% de desconto
    }
}
```

### 3. **Comentários Úteis**

**Descrição:** Use comentários para explicar o "porquê" do código, não o "como". O código deve ser autoexplicativo sempre que possível.

**Exemplo:**

```csharp
public class Pedido
{
    private readonly INotificacao notificacao;

    // Construtor para injeção de dependência
    public Pedido(INotificacao notificacao)
    {
        this.notificacao = notificacao;
    }

    // Finaliza o pedido e notifica o cliente
    public void Finalizar()
    {
        // Lógica para finalizar o pedido
        notificacao.Enviar("Seu pedido foi finalizado com sucesso.");
    }
}
```

### 4. **Evite Código Duplicado**

**Descrição:** Extraia código repetitivo em métodos ou classes reutilizáveis.

**Exemplo:**

```csharp
public class CalculadoraDeFrete
{
    public decimal CalcularFrete(decimal peso, string endereco)
    {
        return peso * ObterTaxaPorEndereco(endereco);
    }

    private decimal ObterTaxaPorEndereco(string endereco)
    {
        // Código para obter a taxa de frete com base no endereço
        return endereco.Contains("Centro") ? 5.00m : 10.00m;
    }
}
```

### 5. **Tratamento Adequado de Erros**

**Descrição:** Use exceções para tratar erros e não códigos de erro.

**Exemplo:**

```csharp
public class ProcessadorDePagamento
{
    public void ProcessarPagamento(decimal valor)
    {
        if (valor <= 0)
        {
            throw new ArgumentException("O valor do pagamento deve ser positivo.", nameof(valor));
        }

        // Código para processar o pagamento
    }
}
```

### 6. **Formatação Consistente**

**Descrição:** Mantenha um estilo de código consistente para melhorar a legibilidade.

**Exemplo:**

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

    public decimal AplicarDesconto(decimal percentualDesconto)
    {
        return Preco - (Preco * percentualDesconto / 100);
    }
}
```

### 7. **Use Tipos Adequados**

**Descrição:** Escolha tipos que sejam apropriados para o problema em questão.

**Exemplo:**

```csharp
public class CarrinhoDeCompras
{
    public List<Produto> Produtos { get; private set; } = new List<Produto>();

    public void AdicionarProduto(Produto produto)
    {
        Produtos.Add(produto);
    }
    
    public decimal ObterTotal()
    {
        return Produtos.Sum(p => p.Preco);
    }
}
```

### 8. **Siga o Princípio DRY (Don't Repeat Yourself)**

**Descrição:** Evite repetir lógica em diferentes partes do código.

**Exemplo:**

```csharp
public class Pedido
{
    private readonly IDesconto desconto;

    public Pedido(IDesconto desconto)
    {
        this.desconto = desconto;
    }

    public decimal CalcularPrecoFinal(decimal precoOriginal)
    {
        return desconto.AplicarDesconto(precoOriginal);
    }
}
```

### 9. **Princípio de Encapsulamento**

**Descrição:** Mantenha os dados e a lógica dentro das classes, escondendo a complexidade.

**Exemplo:**

```csharp
public class Cliente
{
    private string senha;

    public string Nome { get; set; }

    public void AlterarSenha(string novaSenha)
    {
        // Valida e altera a senha
        if (string.IsNullOrWhiteSpace(novaSenha))
        {
            throw new ArgumentException("A senha não pode ser vazia.");
        }

        senha = novaSenha;
    }
}
```

### 10. **Evite Métodos de Longa Duração**

**Descrição:** Métodos longos devem ser divididos em métodos menores e mais focados.

**Exemplo:**

```csharp
public class Pedido
{
    public void Finalizar()
    {
        ValidarPedido();
        CalcularTotal();
        AtualizarEstoque();
        NotificarCliente();
    }

    private void ValidarPedido()
    {
        // Valida o pedido
    }

    private void CalcularTotal()
    {
        // Calcula o total
    }

    private void AtualizarEstoque()
    {
        // Atualiza o estoque
    }

    private void NotificarCliente()
    {
        // Notifica o cliente
    }
}
```

### 11. **Separação de Responsabilidades**

**Descrição:** Cada classe deve ter uma responsabilidade clara e bem definida.

**Exemplo:**

```csharp
public class Produto
{
    public string Nome { get; set; }
    public decimal Preco { get; set; }
}

public class Estoque
{
    private readonly List<Produto> produtos = new List<Produto>();

    public void AdicionarProduto(Produto produto)
    {
        produtos.Add(produto);
    }
    
    public bool VerificarDisponibilidade(Produto produto)
    {
        return produtos.Contains(produto);
    }
}

public class Pedido
{
    private readonly Estoque estoque;
    private readonly List<Produto> produtos = new List<Produto>();

    public Pedido(Estoque estoque)
    {
        this.estoque = estoque;
    }

    public void AdicionarProduto(Produto produto)
    {
        if (estoque.VerificarDisponibilidade(produto))
        {
            produtos.Add(produto);
        }
        else
        {
            throw new Exception("Produto não disponível em estoque.");
        }
    }
}
```

### 12. **Testabilidade**

**Descrição:** Escreva código que seja fácil de testar, evitando dependências rígidas e acoplamento excessivo.

**Exemplo:**

```csharp
public interface IRepositorioDePedidos
{
    void Salvar(Pedido pedido);
}

public class PedidoServico
{
    private readonly IRepositorioDePedidos repositorio;

    public PedidoServico(IRepositorioDePedidos repositorio)
    {
        this.repositorio = repositorio;
    }

    public void ProcessarPedido(Pedido pedido)
    {
        // Lógica para processar o pedido
        repositorio.Salvar(pedido);
    }
}
```

### 13. **Uso de Imutabilidade**

**Descrição:** Sempre que possível, use objetos imutáveis para evitar efeitos colaterais inesperados.

**Exemplo:**

```csharp
public class Produto
{
    public string Nome { get; }
    public decimal Preco { get; }

    public Produto(string nome, decimal preco)
    {
        Nome = nome;
        Preco = preco;
    }
}
```

### 14. **Evite Dependências Cíclicas**

**Descrição:** Organize o código para evitar dependências cíclicas entre classes e módulos.

**Exemplo:**

Organize seu código em camadas distintas (por exemplo, repositórios, serviços, e entidades) e use injeção de dependências para evitar acoplamento rígido.

```csharp
// Exemplo de uma estrutura em camadas
public interface IProdutoRepositorio
{
    Produto ObterProdutoPorId(int id);
}

public class ProdutoServico
{
    private readonly IProdutoRepositorio repositorio;

    public ProdutoServico(IProdutoRepositorio repositorio)
    {
        this.repositorio = repositorio;
    }

    public Produto BuscarProduto(int id)
    {
        return repositorio.ObterProdutoPorId(id);
    }
}
```

### 15. **Princípio de Substituição**

**Descrição:** Use herança e interfaces de forma que subclasses possam substituir classes base sem alterar a funcionalidade do sistema.

**Exemplo:**

```csharp
public abstract class Relatorio
{
    public abstract void Gerar();
}

public class RelatorioPDF : Relatorio
{
   

 public override void Gerar()
    {
        // Gera um relatório em PDF
    }
}

public class RelatorioExcel : Relatorio
{
    public override void Gerar()
    {
        // Gera um relatório em Excel
    }
}
```

### 16. **Responsabilidades de Classe**

**Descrição:** Mantenha suas classes focadas em responsabilidades específicas e evite adicionar funcionalidades não relacionadas.

**Exemplo:**

```csharp
public class Produto
{
    public string Nome { get; set; }
    public decimal Preco { get; set; }
}

public class CarrinhoDeCompras
{
    private readonly List<Produto> produtos = new List<Produto>();

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

Aplicar os princípios de Clean Code não só melhora a legibilidade e a manutenção do código, mas também facilita a colaboração em equipe e a escalabilidade do sistema. Se precisar de mais detalhes ou tiver dúvidas adicionais sobre qualquer um desses princípios, sinta-se à vontade para perguntar!


