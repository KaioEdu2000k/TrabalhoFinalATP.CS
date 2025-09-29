using System;
using System.IO;

class Programa
{
    static string clinica, dono, veterinario, data;
    static int quantidade;
    static int[] codigos;
    static string[] nomes;
    static string[] especies;
    static int[] idades;
    static decimal[] valores;

    static void Main()
    {
        LerDados();
        GerarRelatorio();
    }

    static void LerDados()
    {
        StreamReader arqEntrada = new StreamReader("clinica_in.txt");

        clinica = arqEntrada.ReadLine();
        dono = arqEntrada.ReadLine();
        veterinario = arqEntrada.ReadLine();
        data = arqEntrada.ReadLine();
        quantidade = int.Parse(arqEntrada.ReadLine());

        codigos = new int[quantidade];
        nomes = new string[quantidade];
        especies = new string[quantidade];
        idades = new int[quantidade];
        valores = new decimal[quantidade];

        for (int i = 0; i < quantidade; i++)
        {
            codigos[i] = int.Parse(arqEntrada.ReadLine());
            nomes[i] = arqEntrada.ReadLine();
            especies[i] = arqEntrada.ReadLine().ToLower();
            idades[i] = int.Parse(arqEntrada.ReadLine());
            valores[i] = decimal.Parse(arqEntrada.ReadLine());
        }

        arqEntrada.Close();
    }

    static void GerarRelatorio()
    {
        StreamWriter arqSaida = new StreamWriter("clinica_out.txt");

        string[] especiesFixas = { "gato", "cachorro", "coelho", "arara", "hamster" };
        string especieAtual, maisVelho;
        int i, j, cont, somaIdade, maiorIdade, somaTotal;
        double media, mediaGeral;
        decimal totalRecebido;

        Console.WriteLine("CLÍNICA VETERINÁRIA: " + clinica);
        arqSaida.WriteLine("CLÍNICA VETERINÁRIA: " + clinica);

        Console.WriteLine("Proprietário: " + dono);
        arqSaida.WriteLine("Proprietário: " + dono);

        Console.WriteLine("Veterinário responsável: " + veterinario);
        arqSaida.WriteLine("Veterinário responsável: " + veterinario);

        Console.WriteLine("Data: " + data);
        arqSaida.WriteLine("Data: " + data);

        Console.WriteLine();
        arqSaida.WriteLine();

        Console.WriteLine("Quantidade de animais atendidos: " + quantidade);
        arqSaida.WriteLine("Quantidade de animais atendidos: " + quantidade);

        Console.WriteLine();
        arqSaida.WriteLine();

        for (i = 0; i < especiesFixas.Length; i++)
        {
            especieAtual = especiesFixas[i];
            cont = 0;
            somaIdade = 0;
            maiorIdade = 0;
            maisVelho = "";

            for (j = 0; j < quantidade; j++)
            {
                if (especies[j] == especieAtual)
                {
                    cont++;
                    somaIdade += idades[j];

                    if (idades[j] > maiorIdade)
                    {
                        maiorIdade = idades[j];
                        maisVelho = nomes[j];
                    }
                }
            }

            if (cont > 0)
            {
                media = somaIdade / cont;

                Console.WriteLine("Espécie: " + especieAtual +
                                  " | Quantidade: " + cont +
                                  " | Média idade: " + media.ToString("F1") + " meses" +
                                  " | Mais velho: " + maisVelho + " (" + maiorIdade + " meses)");

                arqSaida.WriteLine("Espécie: " + especieAtual +
                                   " | Quantidade: " + cont +
                                   " | Média idade: " + media.ToString("F1") + " meses" +
                                   " | Mais velho: " + maisVelho + " (" + maiorIdade + " meses)");
            }
        }

        somaTotal = 0;
        totalRecebido = 0;

        for (i = 0; i < quantidade; i++)
        {
            somaTotal += idades[i];
            totalRecebido += valores[i];
        }

        mediaGeral = somaTotal / quantidade;

        Console.WriteLine();
        arqSaida.WriteLine();

        Console.WriteLine("Média geral de idade: " + mediaGeral.ToString("F1") + " meses");
        arqSaida.WriteLine("Média geral de idade: " + mediaGeral.ToString("F1") + " meses");

        Console.WriteLine("Valor total arrecadado: R$" + totalRecebido.ToString("F2"));
        arqSaida.WriteLine("Valor total arrecadado: R$" + totalRecebido.ToString("F2"));

        arqSaida.Close();
    }
}
