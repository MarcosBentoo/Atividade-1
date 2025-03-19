// Classe base Funcionario: Representa um funcionário genérico da empresa
class Funcionario {
    // Atributos: nome do funcionário e seu salário base
    protected String nome;
    protected double salario;

    // Construtor: Criamos um funcionário com nome e salário
    public Funcionario(String nome, double salario) {
        this.nome = nome;
        this.salario = salario;
    }

    // Método para exibir o cargo do funcionário. Nas subclasses, esse método será personalizado
    public void exibirCargo() {
        System.out.println(this.nome + " é um funcionário.");
    }

    // Método para calcular o salário. Aqui, só mostra o salário base, mas nas subclasses ele pode ser alterado
    public void calcularSalario() {
        System.out.println(this.nome + " recebe R$" + this.salario + " de salário base.");
    }

    // Método para calcular o imposto sobre o salário. Exemplo de um cálculo genérico
    public void calcularImposto() {
        double imposto = this.salario * 0.10;  // Imposto de 10%
        System.out.println(this.nome + " pagará R$" + imposto + " de imposto.");
    }

    // Método para exibir o salário líquido (após o imposto)
    public void calcularSalarioLiquido() {
        double imposto = this.salario * 0.10;  // Imposto de 10%
        double salarioLiquido = this.salario - imposto;
        System.out.println(this.nome + " receberá R$" + salarioLiquido + " de salário líquido.");
    }
}

// Subclasse Gerente: Representa um gerente, que herda todas as características de um funcionário
class Gerente extends Funcionario {

    // Construtor: Passa nome e salário do gerente, herdando da classe Funcionario
    public Gerente(String nome, double salario) {
        super(nome, salario);
    }

    // Sobrescreve o método exibirCargo para mostrar que ele é um gerente
    @Override
    public void exibirCargo() {
        System.out.println(this.nome + " é um gerente.");
    }

    // Sobrescreve o método calcularSalario para incluir um bônus específico para gerentes
    @Override
    public void calcularSalario() {
        double salarioComBonus = this.salario + 1000;  // Bônus de R$1000
        System.out.println(this.nome + " recebe R$" + salarioComBonus + " com bônus.");
    }

    // Sobrescreve o método calcularSalarioLiquido, levando em conta o bônus
    @Override
    public void calcularSalarioLiquido() {
        double salarioComBonus = this.salario + 1000;  // Bônus de R$1000
        double imposto = salarioComBonus * 0.10;  // Imposto de 10%
        double salarioLiquido = salarioComBonus - imposto;
        System.out.println(this.nome + " receberá R$" + salarioLiquido + " de salário líquido (com bônus).");
    }
}

// Subclasse Desenvolvedor: Representa um desenvolvedor de software, também herda de Funcionario
class Desenvolvedor extends Funcionario {

    // Construtor: Passa nome e salário do desenvolvedor, herdando da classe Funcionario
    public Desenvolvedor(String nome, double salario) {
        super(nome, salario);
    }

    // Sobrescreve o método exibirCargo para mostrar que ele é um desenvolvedor
    @Override
    public void exibirCargo() {
        System.out.println(this.nome + " é um desenvolvedor.");
    }

    // Sobrescreve o método calcularSalario para incluir um bônus específico para desenvolvedores
    @Override
    public void calcularSalario() {
        double salarioComBonus = this.salario + 500;  // Bônus de R$500
        System.out.println(this.nome + " recebe R$" + salarioComBonus + " com bônus.");
    }

    // Sobrescreve o método calcularSalarioLiquido, levando em conta o bônus
    @Override
    public void calcularSalarioLiquido() {
        double salarioComBonus = this.salario + 500;  // Bônus de R$500
        double imposto = salarioComBonus * 0.10;  // Imposto de 10%
        double salarioLiquido = salarioComBonus - imposto;
        System.out.println(this.nome + " receberá R$" + salarioLiquido + " de salário líquido (com bônus).");
    }
}

// Classe principal com o método main: Aqui é onde vamos executar o programa e ver os resultados
public class Main {
    public static void main(String[] args) {
        // Criando objetos dos tipos Funcionario, Gerente e Desenvolvedor
        Funcionario gerente = new Gerente("Carlos", 5000);  // Gerente com salário de R$5000
        Funcionario desenvolvedor = new Desenvolvedor("Ana", 3000);  // Desenvolvedor com salário de R$3000

        // Chamando os métodos para cada funcionário e exibindo os resultados

        // Exibindo informações sobre o gerente
        System.out.println("---- Gerente ----");
        gerente.exibirCargo();  // Exibe o cargo
        gerente.calcularSalario();  // Exibe o salário com bônus
        gerente.calcularImposto();  // Exibe o imposto
        gerente.calcularSalarioLiquido();  // Exibe o salário líquido

        System.out.println("\n---- Desenvolvedor ----");
        // Exibindo informações sobre o desenvolvedor
        desenvolvedor.exibirCargo();  // Exibe o cargo
        desenvolvedor.calcularSalario();  // Exibe o salário com bônus
        desenvolvedor.calcularImposto();  // Exibe o imposto
        desenvolvedor.calcularSalarioLiquido();  // Exibe o salário líquido
    }
}
