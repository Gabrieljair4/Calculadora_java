# Calculadora_java
O script utiliza Scanner para capturar entradas e um laço while para execuções contínuas. A lógica central é baseada em switch-case, que direciona os números para a operação escolhida (+, -, *, /). O código previne divisões por zero e exibe o resultado formatado, funcionando em um ciclo de entrada, processamento e saída.
import java.util.Scanner;

public class Calculadora {
    public static void main(String[] args) {
        Scanner leitor = new Scanner(System.in);
        boolean rodando = true;

        System.out.println("=== Bem-vindo à Calculadora Java ===");

        while (rodando) {
            System.out.print("\nDigite o primeiro número (ou 0 para sair): ");
            double num1 = leitor.nextDouble();

            // Opção simples de saída
            if (num1 == 0) {
                System.out.println("Encerrando... Até logo!");
                break;
            }

            System.out.print("Escolha a operação (+, -, *, /): ");
            char operacao = leitor.next().charAt(0);

            System.out.print("Digite o segundo número: ");
            double num2 = leitor.nextDouble();

            double resultado = 0;
            boolean operacaoValida = true;

            switch (operacao) {
                case '+':
                    resultado = num1 + num2;
                    break;
                case '-':
                    resultado = num1 - num2;
                    break;
                case '*':
                    resultado = num1 * num2;
                    break;
                case '/':
                    if (num2 != 0) {
                        resultado = num1 / num2;
                    } else {
                        System.out.println("Erro: Não é possível dividir por zero.");
                        operacaoValida = false;
                    }
                    break;
                default:
                    System.out.println("Operação inválida! Tente +, -, * ou /.");
                    operacaoValida = false;
            }

            if (operacaoValida) {
                System.out.printf("Resultado: %.2f %c %.2f = %.2f%n", num1, operacao, num2, resultado);
            }
        }

        leitor.close();
    }
}
