"# chityalamounika_MavenHometask1" 




#NewYearGift.java



import java.lang.*;
import java.util.*;
class Chocolate
{
	int weight=0;
	int price=0;
	Chocolate(int weight,int price)
	{
		this.weight=weight;
		this.price=price;
	}
	public int getWeight()
	{
		return this.weight;
	}
	public int getPrice()
	{
		return this.price;
	}
}
class Sweet
{
	int weight=0;
	int price=0;
	Sweet(int weight,int price)
	{
		this.weight=weight;
		this.price=price;
	}
	public int getWeight()
	{
		return this.weight;
	}
	public int getPrice()
	{
		return this.price;
	}
}
 class NewYearGift 
{
	static int sortType;
	static Scanner sc=new Scanner(System.in);
	static ArrayList<Chocolate> chocolates = new ArrayList<Chocolate>();
	static ArrayList<Chocolate> candies = new ArrayList<Chocolate>();
	static ArrayList<Sweet> sweets = new ArrayList<Sweet>();
	static HashMap<String,Integer> nameToWeight = new HashMap<String,Integer>();
	static HashMap<String,Integer> nameToPrice = new HashMap<String,Integer>();
	public static void main(String args[])
	{
		enterChocolates();
		enterSweets();
		System.out.println("Total weight of gift : "+calculateWeight());
		System.out.println("Choose the way to sort : 1.sort by weight\t2.sort by price");
		int sortType=sc.nextInt();
		if(sortType==1)
		{
			Comparator<Chocolate> weightComparision = (Chocolate c1,Chocolate c2) -> ((Integer)c1.getWeight()).compareTo(c2.getWeight());
			Collections.sort(chocolates,weightComparision);
		}
		else
		{
			Comparator<Chocolate> priceComparision = (Chocolate c1,Chocolate c2) -> ((Integer)c1.getPrice()).compareTo(c2.getPrice());
			Collections.sort(chocolates,priceComparision);	
		}
		System.out.println("The sorted results : ");
		for(Chocolate chocolate : chocolates)
		{
			System.out.println(chocolate.getPrice());
		}
		calculateRange(sortType);
	}
	public static void enterChocolates()
	{
                int nchoc;
		
		System.out.println("Enter number of chocolates in the gift : ");
		nchoc=sc.nextInt();
		for(int i=0;i<nchoc;i++)
		{
			System.out.println("Enter chocolate type : 1->candy\t2->wafer");
			int chocType=sc.nextInt();
			System.out.println("Enter chocolate weight : ");
			int chocWeight=sc.nextInt();
			System.out.println("Enter chocolate Price : ");
			int chocPrice=sc.nextInt();
			if(chocType==1)
			{
				System.out.println("Enter the name of the candy : ");
				String candyName=sc.next();
				if(nameToWeight.containsKey(candyName))
				{
					nameToWeight.put(candyName,(int)nameToWeight.get(candyName)+chocWeight);
				}
				else
				{
					nameToWeight.put(candyName,chocWeight);
				}
				if(nameToPrice.containsKey(candyName))
				{
					nameToPrice.put(candyName,(int)nameToPrice.get(candyName)+chocPrice);
				}
				else
				{
					nameToPrice.put(candyName,chocPrice);
				}
			}
			Chocolate choco = new Chocolate(chocWeight,chocPrice);
			chocolates.add(choco);
			if(chocType==1)
			{
				candies.add(choco);
			}
		}
	}
	public static void enterSweets()
	{
		int nsw;
		System.out.println("Enter the number of sweets in the gift : ");
		nsw=sc.nextInt();
		for(int i=0;i<nsw;i++)
		{
			System.out.println("Enter Sweet weight : ");
			int swWeight=sc.nextInt();
			System.out.println("Enter Sweet Price : ");
			int swPrice=sc.nextInt();
			Sweet sweet=new Sweet(swWeight,swPrice);
			sweets.add(sweet);
		}
	}
	public static int calculateWeight()
	{
		int totalWeight=0;
		for(Chocolate chocolate : chocolates)
		{
			totalWeight+=chocolate.getWeight();
		}
		for(Sweet sweet : sweets)
		{
			totalWeight+=sweet.getWeight();
		}
		return totalWeight;
	}
	public static void calculateRange(int sortType)
	{
		int l,h;
		if(sortType==1)
		{
			System.out.println("Enter lower limit : ");
			l=sc.nextInt();
			System.out.println("Enter higher limit : ");
			h=sc.nextInt();
			Set<Map.Entry<String,Integer>> candyset = nameToWeight.entrySet();
			Iterator<Map.Entry<String,Integer>> candyIterator =candyset.iterator();
			while(candyIterator.hasNext())
			{
				Map.Entry candyelement = (Map.Entry)candyIterator.next();
				int currentweight = (int)candyelement.getValue();
				if(currentweight>=l && currentweight<=h)
				{
					System.out.println(candyelement.getKey());
				}
			}
		}
		else
		{
			System.out.println("Enter lower limit : ");
			l=sc.nextInt();
			System.out.println("Enter higher limit : ");
			h=sc.nextInt();
			Set<Map.Entry<String,Integer>> candyset = nameToPrice.entrySet();
			Iterator<Map.Entry<String,Integer>> candyIterator =candyset.iterator();
			while(candyIterator.hasNext())
			{
				Map.Entry candyelement = (Map.Entry)candyIterator.next();
				int currentprice = (int)candyelement.getValue();
				if(currentprice>=l && currentprice<=h)
				{
					System.out.println(candyelement.getKey());
				}
			}
		}
	}
}




#gift(case 2)








package newyeargift;
import java.util.*;
public class GiftAnalysis
{
static Scanner input=new Scanner(System.in);
static ArrayList<Chocolate> chocolates=new ArrayList<Chocolate>();
static ArrayList<Chocolate> candies=new ArrayList<Chocolate>();
static ArrayList<Sweet> sweets=new ArrayList<Sweet>();
static HashMap<String,Integer> nameToWeight=new HashMap<String,Integer>();
static HashMap<String,Integer> nameToPrice=new HashMap<String,Integer>();

public static void main(String args[])
{
inputChocolates();
inputSweets();
System.out.println("Total weight of the gift is:"+calcTotalWeight());
System.out.println("Choose the way to sort(enter the number): 1.By Price 2.By Weight");
int sortType=input.nextInt();
if(sortType==1)
{
Comparator<Chocolate> compareByPrice=(chocolate c1,chocolate c2)->((Integer)c1.getPrice()).compareTo(c2.getPrice());
Collections.sort(chocolates,compareByPrice);
}
else
{
Comparator<Chocolate> compareByWeight=(chocolate c1,chocolate c2)->((Integer)c1.getWeight()).compareTo(c2.getWeight());
Collections.sort(chocolates,compareByweight);
}
System.out.println("The sorted result");
for(Chocolate chocolate:chocolates)
{
System.out.println(chocolate.getPrice());
}
calcRange(sortType);
}


public static void inputChocolates()
{
System.out.println("Enter the number of chocolates in gifts:\n");
int numberOfChocolates=input.nextInt();
for(int chocoCount=1;chocoCount=numberOfChocolates;chocoCount++)
{
System.out.println("Enter the chocolate type(Enter the number):1.Candy 2.Bar");
int chocolateType=input.nextInt();
System.out.println("Enter the weight of chocolate");
int chocoWeight=input.nextInt();
System.out.println("Enter the price of chocolate");
int chocoPrice=input.nextInt();
if(chocolateType==1)
{
System.out.println("Enter the name of the candy");
String candyName=input.next();
if(nameToWeight.containsKey(candyName))
{
nameToWeight.put(candyName,(int)nameToWeight.get(candyName)+chocoWeight);
}
else
nameToWeight.put(candyName,chocoWeight);
if(nameToPrice.containsKey(candyName))
{
nameToPrice.put(candyName,(int)nameToPrice.get(candyName)+chocoPrice);
}
else
nameToPrice.put(candyName,chocoPrice);
}
Chocolate choco=new Chocolate(chocoWeight,chocoPrice);
chocolates.add(choco);
if(chocolateType==1)
{
candies.add(choco);
}
}
}


public static void inputSweets()
{
System.out.println("Enter the number of sweets in gifts:\n");
int numberOfSweets=input.nextInt();
for(int sweetCount=1;sweetCount=numberOfSweets;sweetCount++)
{
System.out.println("Enter the sweet type(Enter the number):1.Kova 2.Kalakand");
System.out.println("Enter the weight of sweet");
int sweetWeight=input.nextInt();
System.out.println("Enter the price of sweet");
int sweetPrice=input.nextInt();
Sweet sweet=new Sweet(sweetWeight,sweetPrice);
sweets.add(sweet);
}
}





public static int calcTotalWeight()
{
int totalWeight=0;
for(Chocolate choco:chocolates)
{
totalWeight+=choco.getWeight();
}
for(Sweet sweet:sweets)
{
totalWeight+=sweet.getWeight();
}
return totalWeight;
}












public static void calcRange(int sortType)
{
System.out.println("lets findout the range");
int lowerLimit,higherLimit;
if(sortType==1)
{
System.out.println("Enter the lowerlimit of the price");
lowerLimit=input.nextInt();
System.out.println("Enter the higherlimit of the price");
higherLimit=input.nextInt();
set<Map.Entry<String,Integer>>candyIterator=candySet.iterator();
while(candyIterator.hasNext())
{
Map.Entry candyElement=(Map.Entry)candyIterator.next();
int currentPrice=(int)candyElement.getValue();
if(currentPrice>=lowerLimit && currentPrice<=higherLimit)
System.out.println(candyElement.getKey());
}
}
else
{
System.out.println("Enter the lowerlimit of the weight");
lowerLimit=input.nextInt();
System.out.println("Enter the higherlimit of the weight");
higherLimit=input.nextInt();
set<Map.Entry<String,Integer>>candySet=nameToWeight.entrySet();
Iterator<Map.Entry<String,Integer>> candyIterator=candySet.iterator();
while(candyIterator.hasNext())
{
Map.Entry candyElement=(Map.Entry)candyIterator.next();
int currentWeight=(int)candyElement.getValue();
if(currentWeight>=lowerLimit && currentWeight<=higherLimit)
System.out.println(candyElement.getKey());
}
}
}
} 










