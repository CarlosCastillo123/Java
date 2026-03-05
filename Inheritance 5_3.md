# Inheritance 5.3
## Book
``` java
public class Book {
    private String title;
    private String author;
    private String publisher;
    private String publication;
    Book(String t, String a, String p, String pu){
        title =t;
        author = a;
        publisher = p;
        publication = pu;

    }
    Book(){

    }
    public void setTitle(String s) {
        title = s;
    }

    public void setAuthor(String s) {
        author = s;
    }

    public void setPublisher(String s) {
        publisher = s;
    }

    public void setPublication(String s) {
        publication = s;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public String getPublisher() {
        return publisher;
    }

    public String getPublication() {
        return publication;
    }

    public void printInfo() {
        System.out.println(title);
        System.out.println(author);
        System.out.println(publisher);
        System.out.println(publication);

    }
}
```
## Encyclopedia
```java
public class Encyclopedia extends Book{


    private String edition;
    private int pages;

    Encyclopedia(String t, String a, String p, String pu, String e,int pg) {
        super(t, a, p, pu);
        edition = e;
        pages = pg;
    }
    Encyclopedia(){

    }

    void setEdition(String s){
        edition = s;
    }
    void setPages(int i){
        pages = i;
    }
    public String getEdition(){
        return edition;

    }
    public int getPages(){
        return pages;
    }
    public void printInfo(){
        System.out.println(getTitle());
        System.out.println(getAuthor());
        System.out.println(getPublisher());
        System.out.println(getPublication());
        System.out.println(edition);
        System.out.println(pages);
    }
}

```
## Main 
``` java

public class Main {
    public static void main(String[] args) {
        Book hobbit2 = new Book("The Hobit", "J. R. R. Tolken", "George Allen & Unwin"
        , "21 september 1937");
        Book hobbit = new Book();
        Encyclopedia encyclopedia = new Encyclopedia();
        hobbit.setTitle("The Hobit");
        hobbit.setAuthor("J. R. R. Tolkien");
        hobbit.setPublisher("George Allen & Unwin");
        hobbit.setPublication("21 september 1937");
        encyclopedia.setTitle("The Illustrated Encyclopedia of the Universe");
        encyclopedia.setAuthor("Ian Ridpath");
        encyclopedia.setPublisher("Watson-Guptill");
        encyclopedia.setPublication("2001");
        encyclopedia.setEdition("2nd");
        encyclopedia.setPages(384);
        hobbit.printInfo();
        encyclopedia.printInfo();
        hobbit2.printInfo();
    }
}
```
