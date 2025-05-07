import java.util.ArrayList;

// Classe Autor
class Autor {
    private String nome;
    private String abreviatura;
    private ArrayList<String> contatos;

    // Construtor
    public Autor(String nome, String abreviatura) {
        this.nome = nome;
        this.abreviatura = abreviatura;
        this.contatos = new ArrayList<>();
    }

    // Método para adicionar contato
    public void adicionarContato(String tipo, String contato) {
        this.contatos.add(tipo + ": " + contato);
    }

    // Getters
    public String getNome() {
        return nome;
    }

    public String getAbreviatura() {
        return abreviatura;
    }

    public ArrayList<String> getContatos() {
        return contatos;
    }
}

// Classe Editora
class Editora {
    private String nome;
    private String email;

    // Construtor
    public Editora(String nome, String email) {
        this.nome = nome;
        this.email = email;
    }

    // Getters
    public String getNome() {
        return nome;
    }

    public String getEmail() {
        return email;
    }
}

// Classe Livro
class Livro {
    private String titulo;
    private int anoPublicacao;
    private Editora editora;
    private ArrayList<Autor> autores;

    // Construtor
    public Livro(String titulo, int anoPublicacao, Editora editora) {
        this.titulo = titulo;
        this.anoPublicacao = anoPublicacao;
        this.editora = editora;
        this.autores = new ArrayList<>();
    }

    // Método para adicionar autor
    public void adicionarAutor(Autor autor) {
        this.autores.add(autor);
    }

    // Getters
    public String getTitulo() {
        return titulo;
    }

    public int getAnoPublicacao() {
        return anoPublicacao;
    }

    public Editora getEditora() {
        return editora;
    }

    public ArrayList<Autor> getAutores() {
        return autores;
    }
}

// Classe principal para demonstração
public class SistemaLivros {
    public static void main(String[] args) {
        // Criando editoras
        Editora editora1 = new Editora("Companhia das Letras", "contato@companhiadasletras.com.br");
        Editora editora2 = new Editora("Editora Abril", "contato@abril.com.br");
        
        // Criando autores
        Autor autor1 = new Autor("Machado de Assis", "M. Assis");
        autor1.adicionarContato("Email", "machado@email.com");
        autor1.adicionarContato("Telefone", "(21) 9999-9999");
        
        Autor autor2 = new Autor("Clarice Lispector", "C. Lispector");
        autor2.adicionarContato("Email", "clarice@email.com");
        
        Autor autor3 = new Autor("Jorge Amado", "J. Amado");
        autor3.adicionarContato("Site", "www.jorgeamado.com.br");
        
        // Criando livros
        Livro livro1 = new Livro("Dom Casmurro", 1899, editora1);
        livro1.adicionarAutor(autor1);
        
        Livro livro2 = new Livro("A Hora da Estrela", 1977, editora1);
        livro2.adicionarAutor(autor2);
        
        Livro livro3 = new Livro("Capitães da Areia", 1937, editora2);
        livro3.adicionarAutor(autor3);
        
        // Demonstrando os registros criados
        System.out.println("=== SISTEMA DE LIVROS ===");
        System.out.println("\nLivro 1:");
        System.out.println("Título: " + livro1.getTitulo());
        System.out.println("Ano: " + livro1.getAnoPublicacao());
        System.out.println("Editora: " + livro1.getEditora().getNome());
        System.out.println("Autores:");
        for (Autor a : livro1.getAutores()) {
            System.out.println("- " + a.getNome() + " (" + a.getAbreviatura() + ")");
        }
        
        System.out.println("\nLivro 2:");
        System.out.println("Título: " + livro2.getTitulo());
        System.out.println("Ano: " + livro2.getAnoPublicacao());
        System.out.println("Editora: " + livro2.getEditora().getNome());
        System.out.println("Autores:");
        for (Autor a : livro2.getAutores()) {
            System.out.println("- " + a.getNome() + " (" + a.getAbreviatura() + ")");
            System.out.println("  Contatos:");
            for (String c : a.getContatos()) {
                System.out.println("  " + c);
            }
        }
    }
}
