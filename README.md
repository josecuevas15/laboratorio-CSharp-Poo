# laboratorio-CSharp-Poo
## 1 - Read Books
Crea una función isBookRead que reciba una lista de libros y un título y devuelva si se ha leído o no dicho libro. Un libro es un objeto con title como string y isRead como booleano. En caso de no existir el libro devolver false.

### Solucion:
```csharp
public class Book
{
    public string title {  get; set; }
    public bool isRead { get; set; }
    public Book(string title, bool isRead ) { 
        this.title = title;
        this.isRead = isRead;
    } 
}
public static bool IsBookRead(Book[] books, string titleToSearch)
{
    foreach (Book book in books)
    {
        if( book.title == titleToSearch) { return book.isRead; }
    }
    return false;
}

static void Main(string[] args)
{
    var books = new Book[] {
        new Book
        (
            "Harry Potter y la piedra filosofal",
            true
        ),
        new Book
        (
            "Cancion de hielo y fuego",
            false
        ),
        new Book
        (
            "Devastacion",
            true
        )
    };

    Console.WriteLine(IsBookRead(books, "Devastacion")); // true
    Console.WriteLine(IsBookRead(books, "Cancion de hielo y fuego")); // false
    Console.WriteLine(IsBookRead(books, "Los Pilares de la Tierra")); // false 
}
```
## 2 - Slot Machine

El objetivo de este ejercicio es crear una máquina tragaperras utilizando clases donde cada vez que juguemos insertemos una moneda. Cada máquina tragaperras (instancia) tendrá un contador de monedas que automáticamente se irá incrementando conforme vayamos jugando.

Cuando se llame al método play el número de monedas se debe incrementar de forma automática y debe generar tres booleanos aleatorios que representarán el estado de las 3 ruletas. El usuario habrá ganado en caso de que los tres booleanos sean true, y por tanto deberá mostrarse por consola el mensaje:

```"Congratulations!!!. You won <número de monedas> coins!!";```

y reiniciar las monedas almacenadas, ya que las hemos conseguido y han salido de la máquina. En caso contrario deberá mostrar otro mensaje:

```"Good luck next time!!".```

### Solucion:

```csharp
public class Maquina
{
    int monedas {  get; set; }
    public Maquina()
    {
        this.monedas = 0;
    }
    public void jugar()
    {
        this.monedas++;
        Random random = new Random();
        bool ruleta1 = random.Next(0, 2) == 1;
        bool ruleta2 = random.Next(0, 2) == 1;
        bool ruleta3 = random.Next(0, 2) == 1;
        if ( ruleta1 && ruleta2 && ruleta3 )
        {
            Console.WriteLine($"Enhorabuena!! Has ganado {monedas} monedas!!");
            this.monedas = 0;
        } else {
            Console.WriteLine("Suerte para la proxima!");
        }

    }

}
static void Main(string[] args)
{
    Maquina maquina = new Maquina();
    Console.WriteLine("Introduzca el caracter p para jugar \nIntroduzca otro caracter para salir.");
    char c = Convert.ToChar(Console.ReadLine().ToLower());
    while(c == 'p')
    {
        maquina.jugar();
        c = Convert.ToChar(Console.ReadLine().ToLower());
    }
    
}
```

