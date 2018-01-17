# FilesAndFolders
Excercise showing that basic stuff related to creating files and folders 


    package katalogiipliki;

    import java.io.File;
    import java.io.IOException;
    import java.util.Date;
    import java.util.logging.Level;
    import java.util.logging.Logger;

    public class Main {

    public static void main(String[] args) 
    {
        try 
        {
            
            File plik = new File("test.txt");
            File katalog = new File("katalogTestowy"+File.separator+"podkatalogTestowy"+File.separator+"kolejnyPokatalogTestowy");

                katalog.mkdirs();
                System.out.println("Czy to jest katalog? " + katalog.isDirectory());
            
            File plik2 = new File("katalogTestowy"+File.separator+"podkatalogTestowy"+File.separator+"kolejnyPokatalogTestowy", "test2.txt");
            
            if(!plik2.exists())
                plik2.createNewFile();
                
            if (!plik.exists())
                plik.createNewFile();
            
            System.out.println("");
            System.out.println("-------------------------------------------");
            System.out.println(plik.getAbsolutePath());
            System.out.println(plik2.getAbsolutePath());
            System.out.println("-------------------------------------------");
            System.out.println("");
            
            System.out.println("Czy mogę pisać? " + plik.canWrite());
            System.out.println("Czy mogę czytać? " + plik.canRead());
            System.out.println("Czy jest ukryty? " + plik.isHidden());
            System.out.println("Czy jest plikiem? " + plik.isFile());
            System.out.println("Data ostatniej modyfikacji? " + new Date(plik.lastModified()));
            System.out.println("Długość plików w bajtach " + plik.length());
            
            System.out.println("");
            System.out.println("-------------------------------------------");
            System.out.println("");
            
            Main.wypiszWszystkieSciezki(new File(System.getProperty("user.dir")));
            
            plik.delete();
            
        } 
        catch (IOException ex) 
        {
            System.out.println(ex.getMessage());
        }
        
        // System.out.println(System.getProperty("os.version"));
    }
    
    public static void wypiszWszystkieSciezki(File nazwaSciezki)
    {
        String[] nazwyPlikowIKatalogow =  nazwaSciezki.list();
        System.out.println(nazwaSciezki.getPath());
        
        System.out.println("");
        System.out.println("-------------------------------------------");
        System.out.println("");

            for(int i = 0; i < nazwyPlikowIKatalogow.length; i++)
            {
                File p = new File(nazwaSciezki.getPath(), nazwyPlikowIKatalogow[i]);
                System.out.println(p.getPath());
                
                if (p.isDirectory())
                {
                    wypiszWszystkieSciezki(new File(p.getPath()));
                }
            }
    }
}
