# Fund. Lógica | Session Five: Focused Training Conditions

autor: Nilton da Silva Moreira 
turma: Info-A
número: 51

```csharp=


public class Calculo
{
	public double Valor1 	{ get; set;}
	public double Valor2 	{ get; set;}
	public string Operacao 	{ get; set;}
}

public class Pessoa 
{
	public string nome   	{ get; set;}
	public double Altura 	{ get; set;}
	public double Peso   	{ get; set;}
}

public class Triangulo
{
	public double LadoA 	{ get; set;}
	public double LadoB 	{ get; set;}
	public double LadoC 	{ get; set;}
}

public class Notas 
{
	public double Nota1 	{ get; set;}
	public double Nota2 	{ get; set;}
	public double Nota3 	{ get; set;}
}

public class TreinoFocadoA
{
	public double Calculadora (Calculo calculo)
	{
		double a = 0;
		if(calculo.Operacao == "soma")
		{
			a = calculo.Valor1 + calculo.Valor2;
		}
		else if(calculo.Operacao == "subtração")
		{
			a = calculo.Valor1 - calculo.Valor2;
		}
		else if(calculo.Operacao == "multiplicação")
		{
			a = calculo.Valor1 * calculo.Valor2;
		}
		else if(calculo.Operacao == "divisão")
		{
			a = calculo.Valor1 / calculo.Valor2;
		}
		else if(calculo.Operacao == "Potência")
		{
			a =  Math.Pow(calculo.Valor1, calculo.Valor2);
		}
		
		return a;
	}
	public string Termometro (double grau)
	{
		string t = " ";
		if(grau >= 37.8 && grau <= 39.5)
		{
			t = "Voçê está com febre";
		}
		else if(grau > 39.6)
		{
			t = "Voçê está com febre alta";
		}
		else if(grau < 35)
		{
			t = "Voçê está com hipotermia";
		}
		else if(grau >= 35.1 && grau <= 37.7)
		{
			t =	"Voçê está com a temperatutra normal";
		}
		
		return t;
	}
	public string LucroOuPrejuizo (double gastos, double lucros)
	{
		double a = lucros - gastos;
		string b = "";
		if(a > 0)
		{
			b = "Muito bem! voçê esta R$ " + a + " positivo";
		}
		else
		{
			b = "Poxa! voçê ficou R$ " + Math.Abs(a) + " negativo";
		}
		
		return b;
	}
	public double ArredondarMeioEmMeio (double nota)
	{
		double n = 0;
		if( n 
			
	}
	public string Passou (Notas notas)
	{}
    public string Passou (Notas notas, int faltas)
	{}
	public string TipoTriangulo (Triangulo tri)
	{}
	public string IMC (Pessoa peessoa)
	{}
}
	
```