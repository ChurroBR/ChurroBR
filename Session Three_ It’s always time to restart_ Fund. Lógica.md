# Session Three: It's always time to restart/ Fund. Lógica
 
Autor : Nilton da Silva Moreira
Turma : Info - A
Número : ??

## Exercício 1

Crie uma classe representando a abstração de função
e/ou dados ao lado. Abaixo a especificação das
situações a serem resolvidas:

```csharp=
public class Trigonometria
{
	public double AreaRetangulo(double bas,double alt)
	{
		double area = bas * alt;
		return area;
	}
	
	public double PerimetroRentangulo(double bas, double alt)
	{
		double per = bas + bas+ alt + alt;
		return per;
	}
	
	public bool RetangulosIguais(int b1, int a1, int b2, int a2)
	{
		double area1 = AreaRetangulo(b1, a1);
		double area2 = AreaRetangulo(b2, a2);
	 	bool iguais = area1 == area2;
		return iguais;
	}
}


Trigonometria trig = new Trigonometria();

double x = trig.AreaRetangulo(10, 4);
Console.WriteLine("Area retângulo: " + x);

double y= trig.PerimetroRentangulo(20,5);
Console.WriteLine("Perímetro rentângulo: " + y);

bool z = trig.RetangulosIguais(10, 4, 5, 8);
Console.WriteLine("Retângulo Iguais: " + z);


//Area retângulo: 40
//Perímetro rentângulo: 50
//Retângulo Iguais: True
```

## Exercício 2

Crie uma classe representando a abstração de função
e/ou dados ao lado. Abaixo a especificação das
situações a serem resolvidas:

```csharp=
public class Forma
{
	public double basee;
	public double altura;
	
}

public class Trigonometria
{
	public double AreRretangulo( Forma retangulo)
	{
		double area = retangulo.basee * retangulo.altura;
		return area;
	}
	
	public double AreaTriangulo( Forma triangulo)
	{
		double area = (triangulo.basee * triangulo.altura) /2;
		return area;
	}
	
	public double AreaParalelogramo( Forma paralelogramo)
	{
		double area = paralelogramo.basee * paralelogramo.altura;
		return area;
	}
	
}
	
	
Trigonometria trig = new Trigonometria();
	
Forma ret = new Forma();
ret.basee = 10;
ret.altura = 5;

double x = trig.AreRretangulo(ret);
Console.WriteLine("Area retângulo: " + x);

Forma tri = new Forma();
tri.basee = 8;
tri.altura = 4;

double y = trig.AreaTriangulo(tri);
Console.WriteLine("Area triangulo: " + y);

Forma per = new Forma();
per.basee = 8;
per.altura = 2;

double z = trig.AreaParalelogramo(per);
Console.WriteLine("Area Paralelogramo: " + z);


//Area retângulo: 50
//Area triangulo: 16
//Area Paralelogramo: 16
```

## Exercício 3

Crie uma classe representando a abstração de função e/ou dados ao lado. Abaixo a especificação das situações a serem resolvidas:

```csharp=
public class Pessoa
{
	public string Nome      { get; set; }
	public DateTime Niver   { get; set; }
}



public class Calendario 
{
	public DateTime PrimeiroDia (DateTime data) 
	{
		return data.AddDays(1 - data.Day);
	}
	
	public DateTime UltimoDia (DateTime data)
	{
        return data.AddMonths(1).AddDays(- data.Day);
	}
	
	public bool Possui31Dias (DateTime data)
	{
		 return UltimoDia(data).Day == 31;
	}
	
	public bool SextaFeira13 (DateTime data)
	{
		return data.DayOfWeek == DayOfWeek.Friday && data.Day == 13;
	}
	
	public string SemanasParaNiver (Pessoa pessoa)
	{
		DateTime o = DateTime.Now;
		DateTime s = new DateTime(o.Year, pessoa.Niver.Month, pessoa.Niver.Day);
		TimeSpan a = s - o;
		double f = a.TotalDays/7;
		double h = Math.Round(f);
		string k = pessoa.Nome + ", faltam " + h + " semanas para seu niver!";
		return k;
	}
	
	public bool SouDeLibra (Pessoa pessoa)
	{
		DateTime u = new DateTime(pessoa.Niver.Year,09,23);
		DateTime k = new DateTime(pessoa.Niver.Year,10,22);
		return pessoa.Niver >= u 
                && 
               pessoa.Niver <= k;
	}	

}




Pessoa k = new Pessoa ();
k.Nome = "Laura Oliveira Rocha";
k.Niver = new DateTime(2004,09,29);


Calendario c = new Calendario ();
DateTime a = c.PrimeiroDia(k.Niver);
DateTime b = c.UltimoDia(k.Niver);
bool d = c.Possui31Dias(k.Niver);
bool e = c.SextaFeira13(k.Niver);
string f = c.SemanasParaNiver(k);
bool g = c.SouDeLibra(k);


Console.WriteLine("Primeiro dia do mês: " + a);
Console.WriteLine("Último dia do mês: " + b);
Console.WriteLine("O mês possui 31 dias?: " + d);
Console.WriteLine("A data cai em ua sexta-feira 13?: " + e);
Console.WriteLine(f);
Console.WriteLine("Sou de Libra?: " + g);


//Primeiro dia do mês: 9/1/2004 12:00:00 AM
//Último dia do mês: 9/30/2004 12:00:00 AM
//O mês possui 31 dias?: False
//A data cai em ua sexta-feira 13?: False
//Laura Oliveira Rocha, faltam 20 semanas para seu niver!
//Sou de Libra?: True
```

## Exercício 4

Crie uma classe representando a abstração de função
e/ou dados ao lado. Abaixo a especificação das
situações a serem resolvidas:

```csharp=
public class RegistroBRValidador
{
	public bool ValidarCadastro(string email, string senha)
	{
		bool v1 = email.Length >= 8;
		bool v2 = email.Contains("!") || email.Contains("@") || email.Contains("#") || email.Contains("%");
		bool v3 = email.Contains("a") || email.Contains("e") || email.Contains("i") || email.Contains("o") || email.Contains("u");
		bool v4 = email.Contains("@");
		bool v5 = email.Contains("@") 
				 && 
				  email.Substring(0, email.IndexOf("@")).Length > 2 
				 &&
				  email.Substring(email.IndexOf("@")).Length > 2;
		return v1 && v2 && v3 && v4 && v5;
	}
	
	public bool ValidarDominio(string dominio)
	{
		bool v1 = dominio.EndsWith(".com.br");
		bool v2 = dominio[0] != '1' && dominio[0] != '2' && dominio[0] != '3' &&
				dominio[0] != '4' &&  dominio[0] != '5' &&  dominio[0] != '6' &&
				dominio[0] != '7' &&  dominio[0] != '8' &&  dominio[0] != '9' &&
			    dominio[0] != '0';
		bool v3 = dominio.Substring(0, dominio.IndexOf(".com.br")).Length >= 5;
		
		return v1 && v2 && v3;
	}
}

RegistroBRValidador registroBR = new RegistroBRValidador();
bool x = registroBR.ValidarCadastro("nmoreira407@gmail.com", "9181");
Console.WriteLine("Cadastro Ok? " + x);


//Cadastro Ok? True
```

## Exercício 5

Crie uma classe representando a abstração de função
e/ou dados ao lado. Abaixo a especificação das
situações a serem resolvidas:

```csharp=
public class Retangulo 
{
	public double alt  { get; set; }
	public double bas  { get; set; }
}

public class Cilindro
{
	public double raio { get; set; }
	public double alt  { get; set; }
}

public class Trigonometria
{
	public bool AreasIguais(Retangulo ret1, Retangulo ret2)
	{
		double area1 = AreaRetangulo(ret1);
		double area2 = AreaRetangulo(ret2);
		return area1 == area2;
	}
	
	public double AreaRetangulo(Retangulo ret)
	{
		return ret.bas * ret.alt;
	}
	
	public bool TransferenciaPossivel(Cilindro ci1, Cilindro ci2)
	{
		double cilindro1 = VolumeCilindro(ci1);
		double cilindro2 = VolumeCilindro(ci2);
		return cilindro1 == cilindro2;
	}
	
	public double VolumeCilindro(Cilindro cil)
	{
	 return Math.Pow(cil.raio, 2) * cil.alt;
	}
}

Retangulo ret = new Retangulo();
ret.bas = 5;
ret.alt = 2;

Retangulo ret2 = new Retangulo();
ret2.bas = 5;
ret2.alt = 2;


Cilindro cil = new Cilindro();
cil.raio = 10;
cil.alt = 20;

Cilindro cil2 = new Cilindro();
cil2.raio = 10;
cil2.alt = 20;


Trigonometria tri = new Trigonometria();
bool a = tri.AreasIguais(ret, ret2);
Console.WriteLine("Areas iguais: " + a);

double b = tri.AreaRetangulo(ret);
Console.WriteLine("A Area do Retangulo é: " + b);

bool c = tri.TransferenciaPossivel(cil, cil2);
Console.WriteLine("A Transferencia é possível: " + c);

double d = tri.VolumeCilindro(cil);
Console.WriteLine("O Volume do Cilindro é: " + d);
 
 
//Areas iguais: True
//A Area do Retangulo é: 10
//A Transferencia é possível: True
//O Volume do Cilindro é: 2000
```

## Exercício 6

Crie uma classe representando a abstração de função
e/ou dados ao lado. Abaixo a especificação das
situações a serem resolvidas:

```csharp=
public class Compra
{
	public int qtdCalca     { get; set;}
	public int qtdCamiseta  { get; set;}
	public int qtdBlusa     { get; set;}
	public int qtdCalcados  { get; set;}
}
					

public class Brecho
{
	public double CalcularTotal(Compra masculino, Compra feminino, Compra infantil)
	{
		return TotalMasculino(masculino) + TotalInfantil(infantil) + TotalFeminino(feminino) + TotalCalcados(feminino.qtdCalcados,  masculino.qtdCalcados, infantil.qtdCalcados);
	}
	
	private double TotalMasculino (Compra pecaMasculina)
	{
		return (pecaMasculina.qtdBlusa * 30) + (pecaMasculina.qtdCamiseta * 30) + (pecaMasculina.qtdCalca);
	}

    private double TotalFeminino (Compra pecaFeminino)
	{
		return (pecaFeminino.qtdBlusa * 40) + (pecaFeminino.qtdCamiseta * 40) + (pecaFeminino.qtdCalca * 40);
	}

	private double TotalInfantil (Compra pecaInfantil)
	{
		return (pecaInfantil.qtdBlusa * 20 ) + (pecaInfantil.qtdCalca * 20) + (pecaInfantil.qtdCamiseta * 20);
	}
	
	private double TotalCalcados (int qtdCalcadoFeminino, int qtdCalcadoMasculino, int qtdCalcadoInfantil)
	{
		return ((qtdCalcadoFeminino * 35) + (qtdCalcadoInfantil * 35) + (qtdCalcadoMasculino * 35));
	}
}

Compra compraMasculina = new Compra ();
compraMasculina.qtdBlusa = 3;
compraMasculina.qtdCalca = 2;
compraMasculina.qtdCalcados = 3;
compraMasculina.qtdCamiseta = 5;

Compra compraFeminina = new Compra ();
compraFeminina.qtdBlusa = 1;
compraFeminina.qtdCalca = 4;
compraFeminina.qtdCalcados = 6;
compraFeminina.qtdCamiseta = 3;

Compra compraInfantil = new Compra ();
compraInfantil.qtdBlusa = 3;
compraInfantil.qtdCalca = 2;
compraInfantil.qtdCalcados = 3;
compraInfantil.qtdCamiseta = 5;

Brecho compra = new Brecho();
double totalFinal = compra.CalcularTotal(compraFeminina, compraMasculina, compraInfantil);
Console.WriteLine("O total da sua comprar foi: R$ " + totalFinal);


//O total da sua comprar foi: R$ 1144
```

## Exercício 7

Crie uma classe representando a abstração de função e/ou dados ao lado. Abaixo a especificação das situações a serem resolvidas:

```csharp=
class MainClass {
  
  public static void Main (string[] args) {
    
    Console.WriteLine ("Exercício 7 | Abstração de Funções");

    Pedido p = new Pedido();
    p.Valor = 1000;
    p.AnosGarantia = 2;
    p.DistanciaEntregaKm = 50;
    p.Parcelas = 18;
    
    double cupom = 10;

    LojaMoveis loja = new LojaMoveis();
    Nota n = loja.CalcularCompra(p, cupom);

    Console.WriteLine("Valor final é: " + n.ValorFinal);
    Console.WriteLine("Nota Fiscal é: " + n.NotaFiscal);


  }

}


public class Pedido
{
  public double Valor           {get; set;}
  public int AnosGarantia       {get; set;}  
  public int DistanciaEntregaKm {get; set;}
  public int Parcelas           {get; set;}
}

public class Nota 
{
  public double ValorFinal  { get; set; }
  public string NotaFiscal  { get; set; }
}


public class LojaMoveis
{

    public Nota CalcularCompra (Pedido pedido, double cupom)
    {
        double desconto = ValorDesconto(pedido.Valor, cupom);
        double garantia = ValorGarantia(pedido.Valor, pedido.AnosGarantia);
        double frete = ValorFrete(pedido.DistanciaEntregaKm);

        double valor = pedido.Valor - desconto + garantia + frete;
        
        double valorFinal = ValorJuros(valor, pedido.Parcelas);
        valorFinal = Math.Round(valorFinal, 2);

        Nota notafiscal = new Nota();
        notafiscal.ValorFinal = valorFinal;
        notafiscal.NotaFiscal = "NF" + DateTime.Now.ToString("yyyyMMddHHmmss");

        return notafiscal;
    }

    private double ValorDesconto(double valorCompra, double cupom)
    {
        return valorCompra * (cupom/100);
    }

    private double ValorGarantia(double valorCompra, int anos)
    {
        return valorCompra * (15.0 / 100.0) * anos;
    }

    private double ValorFrete(int distancia)
    {
        return distancia / 10 * 3;
    }

    private double ValorJuros(double valorCompra, int parcelas)
    {
        return valorCompra * Math.Pow(1 + 0.03, parcelas);
    }
}


//Exercício 7 | Abstração de Funções
//Valor final é: 2068.46
```