# Fund. Lógica | Session Four: Programs also choose!

Autor: Nilton da Silva Moreira
Turma: Info - A
Número: 51

## Exercício 1 : 

```csharp=
public string AreaRetangulo(double b1, double a1, double b2, double a2)
{
	double area1 = b1 * a1;
	double area2 = b2 * a2;
	return area1 == area2 ?"Os retângulos são iguais" :"Os retângulos são diferentes";
}


string x = 	AreaRetangulo(5, 2, 5, 2);
Console.WriteLine(x);


//Os retângulos são iguais
```

## Exercício 2 : 

```csharp=
public double AreaRetangulo(double bass, double alt)
{
	return bass * alt;
}

public string RetangulosIguais(double b1, double a1, double b2, double a2)
{
	double area1 = AreaRetangulo(b1, a1);
	double area2 = AreaRetangulo(b2, a2);
	bool igual = (area1 == area2);
	if(igual == true)
	{
		return "Os retângulos são iguais";
	}
	else if(area1 > area2)
	{
	   return "O primeiro retângulo é maior.";
	}
	else
    {
		return " O segundo retangulo é maior";
	}
}

string x = RetangulosIguais(10, 2, 5, 2);
Console.WriteLine(x);


//O primeiro retangulo é maior
```

## Exercício 3 : 

```csharp=
public class Retangulo
{
	public double bas{ get; set;}
	public double alt{ get; set;}
}

public double AreaRetangulo(double bas, double alt)
{
	return bas * alt;
}

public string MaiorRetangulo(Retangulo ret1, Retangulo ret2, Retangulo ret3)
{
	double a1 = AreaRetangulo(ret1.bas, ret1.alt);
	double a2 = AreaRetangulo(ret2.bas, ret2.alt);
	double a3 = AreaRetangulo(ret3.bas, ret3.alt);
	bool igual = a1 == a2 && a1 == a3;
	if (igual == true)
	{
		return "Os retângulos são iguais";
	}
	else if (a1 > a2 && a1 > a3)
	{
		return "O primeiro retângulo é maior.";
	}
	else if (a2 > a1 && a2 > a3)
	{
		return "O segundo retângulo é maior.";
	}
	else if (a3 > a1 && a3 > a2)
	{
		return "O terceiro retângulo é maior.";
	}
	else
	{
		return "Existem 2 retângulos maiores" ;
	}
}

Retangulo ret1 = new Retangulo();
ret1.bas = 5;
ret1.alt = 2;

Retangulo ret2 = new Retangulo();
ret2.bas = 5;
ret2.alt = 2;

Retangulo ret3 = new Retangulo();
ret3.bas = 5;
ret3.alt = 2;

string x = MaiorRetangulo(ret1, ret2, ret3);
Console.WriteLine(x);


//Os retângulos são iguais
```

## Exercício 4 : 

```csharp=
public class Ingresso
{
	public bool   Meia  { get; set;}
	public double Preco { get; set;}
	public string Filme { get; set;}
}

public class Cinemark
{
	public double CalcularTotal1 (Ingresso ing)
	{
		if(ing.Meia == true)
		{
			return ing.Preco / 2;
		}
		else
		{
			return ing.Preco;
		}
	}
	
	public string CalcularTotal2 (Ingresso ing)
	{
        double total = CalcularTotal1(ing);
		return "Compra concluída! O ingresso para o filme " + ing.Filme +  " é de R$" + total;
	}
	public double CalcularTotal3 (Ingresso ing1 ,Ingresso ing2)
	{
		double total1 = CalcularTotal1(ing1);
		double total2 = CalcularTotal1(ing2);
		return total1 + total2;
	}
}

Ingresso ing = new Ingresso();
ing.Filme = "Black Widow";
ing.Preco = 20.0;
ing.Meia = true;

Ingresso ing2 = new Ingresso();
ing2.Filme = "Black Widow";
ing2.Preco = 20.0;
ing2.Meia = false;

Cinemark cine = new Cinemark();

double x = cine.CalcularTotal1(ing);
string y = cine.CalcularTotal2(ing);
double z = cine.CalcularTotal3(ing, ing2);

Console.WriteLine(x);
Console.WriteLine(y);
Console.WriteLine(z);



//10
//Compra concluída! O ingresso para o filme Black Widow é de R$10
//30
```

## Exercício 5 : 

```csharp=
public class Ingresso
{
	public int    QtdIngressos { get; set;}
	public bool   Meia { get; set;}
	public double Preco { get; set;}
	public string Filme { get; set;}
}

public class Cinemark
{
	public double CalcularTotal1 (Ingresso ing)
	{
		if(ing.Meia == true)
		{
			return ing.QtdIngressos * (ing.Preco / 2);
		}
		else
		{
			return ing.QtdIngressos * ing.Preco;
		}
	}
	
	public string CalcularTotal2 (Ingresso ing)
	{
        double total = CalcularTotal1(ing);
		if(ing.Meia == true)
		{
			return "Compra concluída! A compra de " + ing.QtdIngressos + " ingressos Meia para o filme " + ing.Filme + " é de R$ " + total;
		}
		else
		{
			return "Compra concluída! A compra de " + ing.QtdIngressos + " ingressos Inteira para o filme " + ing.Filme + " é de R$ " + total;
		}
	}
}

Ingresso ing = new Ingresso();
ing.QtdIngressos = 2;
ing.Filme = "Black Widow";
ing.Preco = 20.0;
ing.Meia = true;


Cinemark cine = new Cinemark();

double x = cine.CalcularTotal1(ing);
string y = cine.CalcularTotal2(ing);

Console.WriteLine(x);
Console.WriteLine(y);


//20
//Compra concluída! A compra de 2 ingressos Meia para o filme Black Widow é de R$ 20
```

## Exercício 6 :

```csharp=
public class Ingresso
{
	public int    QtdIngressos { get; set;}
	public bool   Meia { get; set;}
	public double Preco { get; set;}
	public string Filme { get; set;}
}

public class Cinemark
{
	public double CalcularTotal1 (Ingresso ing, double cupom)
	{
		double total = ing.QtdIngressos * ing.Preco;
		double CupomAplicado = AplicarCupom(total, cupom);
		if(ing.Meia == true)
		{
			total = ing.QtdIngressos * (ing.Preco / 2);
			return CupomAplicado;
		}
		else
		{
			total = ing.QtdIngressos * ing.Preco;
			return CupomAplicado;
		}
	}
	
	private double AplicarCupom (double total, double cupom)
	{
		double desconto = total * (cupom / 100);
		return total - desconto;
	}
}

Ingresso ing = new Ingresso();
ing.QtdIngressos = 2;
ing.Filme = "Black Widow";
ing.Preco = 25;
ing.Meia = false;


Cinemark cine = new Cinemark();

double x = cine.CalcularTotal1(ing, 5);
Console.WriteLine("O total a pagar é de R$ " + x);



//O total a pagar é de R$ 47.5
```

## Exercício 7 :

```csharp=
public class Ingresso
{
	public int    QtdIngressos { get; set;}
	public bool   Meia { get; set;}
	public double Preco { get; set;}
	public string Filme { get; set;}
}

public class Cinemark
{
	public double CalcularTotal1 (Ingresso ing, double cupom)
	{
		double total = ing.QtdIngressos * ing.Preco;
		double CupomAplicado = AplicarCupom(total, cupom);
		if(ing.Meia == true)
		{
			total = ing.QtdIngressos * (ing.Preco / 2);
			return CupomAplicado;
		}
		else if( CupomAplicado > 100)
		{
			double descontoExtra = Math.Round(CupomAplicado * 0.10);
			return CupomAplicado - descontoExtra;
			
		}
		else
		{
			total = ing.QtdIngressos * ing.Preco;
			return CupomAplicado;
		}
	}
	
	private double AplicarCupom (double total, double cupom)
	{
		double desconto = total * (cupom / 100);
		return total - desconto;
	}
}

Ingresso ing = new Ingresso();
ing.QtdIngressos = 5;
ing.Filme = "Black Widow";
ing.Preco = 25;
ing.Meia = false;


Cinemark cine = new Cinemark();

double x = cine.CalcularTotal1(ing, 5);
Console.WriteLine("O total a pagar é de R$ " + x);



//O total a pagar é de R$ 106.75
```

## Exercício 8 : 

```csharp=
public class Ingresso
{
	public int QtdIngressos { get; set; }
	public bool Meia { get; set; }
	public double Preco { get; set; }
	public string Filme { get; set; }
}

public class Cinemark
{
	public double CalcularTotal1 (Ingresso ingresso, double cupom)
	{
		double x = AplicarCupom (ingresso, cupom);
		DateTime hj = new DateTime (2021,5,26);
		
		if (hj.DayOfWeek == DayOfWeek.Wednesday)
		{
			double desconto = x * 0.5;
			x = x - desconto;
			
			if (x > 100)
			{
				double descontoextra = x * 0.1;
				x = x - descontoextra;
			}
		}
		return x;
	}
	
	private double AplicarCupom (Ingresso ingresso, double cupom)
	{
		double total = 0;
		
		if (ingresso.Meia == true)
		{
			total = ingresso.QtdIngressos * (ingresso.Preco/2);
		}
		else
		{
			total = ingresso.QtdIngressos * ingresso.Preco;
		}
		
		double desconto = total * (cupom / 100);
		total = total - desconto;
		return total;
	}
}

Ingresso ing = new Ingresso();
ing.QtdIngressos = 11;
ing.Meia = true;
ing.Filme = "Velozes e Furiosos";
ing.Preco = 25;

Cinemark cine = new Cinemark();

double x = cine.CalcularTotal1(ing, 20);
Console.WriteLine (x);
```

## Exercício 9 :

```csharp=
public class Ingresso
{
	public int QtdIngressos { get; set; }
	public bool Meia { get; set; }
	public double Preco { get; set; }
	public string Filme { get; set; }
	public string Genero { get; set; }
}

public class Cinemark
{
	public double CalcularTotal1 (Ingresso ingresso, double cupom)
	{
		double x = AplicarCupom (ingresso, cupom);
		DateTime hj = new DateTime (2021,5,26);
		
		if (ingresso.Genero.Contains("Nacional"))
		{
			x = 5.50;
		}
		else
			{
			if (hj.DayOfWeek == DayOfWeek.Wednesday)
			{
				double desconto = x * 0.5;
				x = x - desconto;

				if (x > 100)
				{
					double descontoextra = x * 0.1;
					x = x - descontoextra;
				}
			}
		}
		return x;
	}
	
	private double AplicarCupom (Ingresso ingresso, double cupom)
	{
		double total = 0;
		
		if (ingresso.Meia == true)
		{
			total = ingresso.QtdIngressos * (ingresso.Preco/2);
		}
		else
		{
			total = ingresso.QtdIngressos * ingresso.Preco;
		}
		
		double desconto = total * (cupom / 100);
		total = total - desconto;
		return total;
	}
}

Ingresso ing = new Ingresso();
ing.QtdIngressos = 11;
ing.Meia = true;
ing.Filme = "Velozes e Furiosos";
ing.Preco = 25;
ing.Genero= "Nacional";

Cinemark cine = new Cinemark();

double x = cine.CalcularTotal1(ing, 20);
Console.WriteLine (x);
```

## Exercício 10 :

```csharp=
public class jogada
{
	public string Jogada1 {get;set;}
	public string Jogada2 {get;set;}
	public string Nome {get;set;}

}


public string Jokenpo (jogada j1, jogada j2)
{
	string x;
	
	if (j1.Jogada1 == "Pedra" && j2.Jogada2 == "Tesoura" || j1.Jogada1 == "Tesoura" && j2.Jogada2 == "Papel" || j1.Jogada1 == "Papel" && j2.Jogada2 == "Pedra")
	{
		x = "O Jogador " + j1.Nome + " Ganhou!";
	}
	
	else if ( j2.Jogada2 == "Pedra" && j1.Jogada1 == "Tesoura" || j2.Jogada2 == "Tesoura" && j1.Jogada1 == "Papel" || j2.Jogada2 == "Papel" && j1.Jogada1 == "Pedra")
	{
		x =  "O Jogador " + j2.Nome + " Ganhou!";
	}
			
	else
	{
		x = "Empate!";
	}
		
	return x;
}

jogada j1 = new jogada();
j1.Jogada1 = "Tesoura";
j1.Nome = "Letícia";

jogada j2 = new jogada();
j2.Jogada2 = "Pedra";
j2.Nome = "Bruno";

string y = Jokenpo (j1, j2);
y

// O Jogador Bruno Ganhou!
```

## Exercício 11 :

```csharp=
public class Partida
{
	public string Jogador { get; set; }
	public bool Par { get; set; }
	public int Numero { get; set; }
}

public string ImparouPar (Partida j1, Partida j2)
{
	int soma = j1.Numero + j2.Numero;
	string Vencedor = " ";
	
	if (soma % 2 == 0)
	{
		if(j1.Par)
		{
			Vencedor = "Deu Par! O Jogador " + j1.Jogador + " venceu!";
		}
		else
		{
			Vencedor = "Deu Par! O Jogador " + j2.Jogador + " venceu!";
		}
	}
	
	else
	{	
		if(j1.Par == false)
		{
			Vencedor = "Deu Ímpar! O Jogador " + j1.Jogador + " venceu!";
		}
		else
		{
			Vencedor = "Deu Ímpar! O Jogador " + j2.Jogador + " venceu!";
		}
	}
	
	return Vencedor;
}

Partida j1 = new Partida ();
j1.Jogador = "Letícia";
j1.Numero = 2;
j1.Par = false;

Partida j2 = new Partida ();
j2.Jogador = "Bruno";
j2.Numero = 2;
j2.Par = true;

string x = ImparouPar (j1, j2);
x

// Deu Par! O Jogador Bruno venceu!
```