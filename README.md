# 10exerciciosDTODAOView

# tela 

![telaexer1](https://github.com/user-attachments/assets/e835ac4e-562f-4593-bd3f-fc1d1e6f4b43)

public class ProdutoDTO {
    private String nome;
    private double preco;
    private int quantidade;

    public ProdutoDTO(String nome, double preco, int quantidade) {
        this.nome = nome;
        this.preco = preco;
        this.quantidade = quantidade;
    }

    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public double getPreco() {
        return preco;
    }

    public void setPreco(double preco) {
        this.preco = preco;
    }

    public int getQuantidade() {
        return quantidade;
    }

    public void setQuantidade(int quantidade) {
        this.quantidade = quantidade;
    }
    
    @Override
    public String toString() {
        return "Produto: " + nome + ", Preço: R$" + preco + ", Quantidade: " + quantidade;
    }
}

import java.util.ArrayList;
import javax.swing.JOptionPane;

public class ProdutoDAO {
    private ArrayList<ProdutoDTO> listaProdutos = new ArrayList<>();

    public void adicionarProduto(ProdutoDTO produto) {
        listaProdutos.add(produto);
        JOptionPane.showMessageDialog(null, "Produto cadastrado com sucesso!\n" + produto);
    }

    public void exibirProdutos() {
        StringBuilder produtos = new StringBuilder();
        for (ProdutoDTO produto : listaProdutos) {
            produtos.append(produto.toString()).append("\n");
        }
        JOptionPane.showMessageDialog(null, produtos.toString());
    }
}

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class ProdutoView extends JFrame {
    private JTextField nomeField;
    private JTextField precoField;
    private JTextField quantidadeField;
    private ProdutoDAO produtoDAO;

    public ProdutoView() {
        produtoDAO = new ProdutoDAO();
        setTitle("Cadastro de Produto");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new GridLayout(4, 2));

        JLabel nomeLabel = new JLabel("Nome:");
        nomeField = new JTextField();

        JLabel precoLabel = new JLabel("Preço:");
        precoField = new JTextField();

        JLabel quantidadeLabel = new JLabel("Quantidade:");
        quantidadeField = new JTextField();

        JButton salvarButton = new JButton("Salvar");
        salvarButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String nome = nomeField.getText();
                double preco = Double.parseDouble(precoField.getText());
                int quantidade = Integer.parseInt(quantidadeField.getText());

                ProdutoDTO produto = new ProdutoDTO(nome, preco, quantidade);
                produtoDAO.adicionarProduto(produto);
            }
        });

        add(nomeLabel);
        add(nomeField);
        add(precoLabel);
        add(precoField);
        add(quantidadeLabel);
        add(quantidadeField);
        add(salvarButton);

        setVisible(true);
    }

    public static void main(String[] args) {
        new ProdutoView();
    }
}

# exercicio2 
public class FuncionarioDTO {
    private String nome;
    private String cargo;
    private double salario;

    // Construtor
    public FuncionarioDTO(String nome, String cargo, double salario) {
        this.nome = nome;
        this.cargo = cargo;
        this.salario = salario;
    }

    // Getters e Setters
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getCargo() {
        return cargo;
    }

    public void setCargo(String cargo) {
        this.cargo = cargo;
    }

    public double getSalario() {
        return salario;
    }

    public void setSalario(double salario) {
        this.salario = salario;
    }

    @Override
    public String toString() {
        return "Nome: " + nome + ", Cargo: " + cargo + ", Salário: " + salario;
    }
}

import java.util.ArrayList;
import java.util.List;
import javax.swing.JOptionPane;

public class FuncionarioDAO {
    private List<FuncionarioDTO> listaFuncionarios = new ArrayList<>();

    // Método para adicionar funcionário
    public void adicionarFuncionario(FuncionarioDTO funcionario) {
        listaFuncionarios.add(funcionario);
        JOptionPane.showMessageDialog(null, "Funcionário cadastrado com sucesso!");
    }

    // Método para listar funcionários
    public String listarFuncionarios() {
        if (listaFuncionarios.isEmpty()) {
            return "Nenhum funcionário cadastrado.";
        }

        StringBuilder sb = new StringBuilder();
        for (FuncionarioDTO func : listaFuncionarios) {
            sb.append(func.toString()).append("\n");
        }
        return sb.toString();
    }
}

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class FuncionarioView extends JFrame {
    private JTextField nomeField, cargoField, salarioField;
    private JButton cadastrarButton, listarButton;
    private FuncionarioDAO funcionarioDAO;

    public FuncionarioView() {
        funcionarioDAO = new FuncionarioDAO();

        // Configuração da Janela
        setTitle("Sistema de Gerenciamento de Funcionários");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(null);

        // Campo Nome
        JLabel nomeLabel = new JLabel("Nome:");
        nomeLabel.setBounds(30, 30, 100, 30);
        add(nomeLabel);
        nomeField = new JTextField();
        nomeField.setBounds(150, 30, 200, 30);
        add(nomeField);

        // Campo Cargo
        JLabel cargoLabel = new JLabel("Cargo:");
        cargoLabel.setBounds(30, 80, 100, 30);
        add(cargoLabel);
        cargoField = new JTextField();
        cargoField.setBounds(150, 80, 200, 30);
        add(cargoField);

        // Campo Salário
        JLabel salarioLabel = new JLabel("Salário:");
        salarioLabel.setBounds(30, 130, 100, 30);
        add(salarioLabel);
        salarioField = new JTextField();
        salarioField.setBounds(150, 130, 200, 30);
        add(salarioField);

        // Botão Cadastrar
        cadastrarButton = new JButton("Cadastrar");
        cadastrarButton.setBounds(30, 180, 150, 30);
        add(cadastrarButton);

        // Botão Listar
        listarButton = new JButton("Listar Funcionários");
        listarButton.setBounds(200, 180, 150, 30);
        add(listarButton);

        // Ação do botão "Cadastrar"
        cadastrarButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String nome = nomeField.getText();
                String cargo = cargoField.getText();
                double salario = Double.parseDouble(salarioField.getText());

                FuncionarioDTO funcionario = new FuncionarioDTO(nome, cargo, salario);
                funcionarioDAO.adicionarFuncionario(funcionario);

                // Limpar campos
                nomeField.setText("");
                cargoField.setText("");
                salarioField.setText("");
            }
        });

        // Ação do botão "Listar"
        listarButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String funcionarios = funcionarioDAO.listarFuncionarios();
                JOptionPane.showMessageDialog(null, funcionarios);
            }
        });

        setVisible(true);
    }

    public static void main(String[] args) {
        new FuncionarioView();
    }
}

# tela 

![telaexer2](https://github.com/user-attachments/assets/6fd4a486-a077-4942-befb-aad6e6885e20)

# exercicio 3

# tela

![telaBiblioteca](https://github.com/user-attachments/assets/14d787d2-dba7-472a-806f-55aeb08f9a09)

public class LivroDTO {
    private String titulo;
    private String autor;
    private int anoPublicacao;

    public LivroDTO(String titulo, String autor, int anoPublicacao) {
        this.titulo = titulo;
        this.autor = autor;
        this.anoPublicacao = anoPublicacao;
    }

    public String getTitulo() {
        return titulo;
    }

    public void setTitulo(String titulo) {
        this.titulo = titulo;
    }

    public String getAutor() {
        return autor;
    }

    public void setAutor(String autor) {
        this.autor = autor;
    }

    public int getAnoPublicacao() {
        return anoPublicacao;
    }

    public void setAnoPublicacao(int anoPublicacao) {
        this.anoPublicacao = anoPublicacao;
    }

    @Override
    public String toString() {
        return "Título: " + titulo + ", Autor: " + autor + ", Ano: " + anoPublicacao;
    }
}


import java.util.ArrayList;
import java.util.List;
import javax.swing.JOptionPane;

public class LivroDAO {
    private List<LivroDTO> livros = new ArrayList<>();

    // Adicionar livro
    public void adicionarLivro(LivroDTO livro) {
        livros.add(livro);
        JOptionPane.showMessageDialog(null, "Livro adicionado com sucesso!");
    }

    // Remover livro pelo título
    public void removerLivro(String titulo) {
        for (LivroDTO livro : livros) {
            if (livro.getTitulo().equalsIgnoreCase(titulo)) {
                livros.remove(livro);
                JOptionPane.showMessageDialog(null, "Livro removido com sucesso!");
                return;
            }
        }
        JOptionPane.showMessageDialog(null, "Livro não encontrado!");
    }

    // Listar todos os livros
    public void listarLivros() {
        if (livros.isEmpty()) {
            JOptionPane.showMessageDialog(null, "Nenhum livro cadastrado.");
        } else {
            StringBuilder listaLivros = new StringBuilder("Livros cadastrados:\n");
            for (LivroDTO livro : livros) {
                listaLivros.append(livro.toString()).append("\n");
            }
            JOptionPane.showMessageDialog(null, listaLivros.toString());
        }
    }
}


import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class BibliotecaView extends JFrame {
    private JTextField txtTitulo, txtAutor, txtAno;
    private LivroDAO livroDAO;

    public BibliotecaView() {
        livroDAO = new LivroDAO();
        initComponents();
    }

    private void initComponents() {
        setTitle("Gerenciamento de Biblioteca");
        setSize(400, 300);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(null);

        JLabel lblTitulo = new JLabel("Título:");
        lblTitulo.setBounds(10, 10, 100, 25);
        add(lblTitulo);

        txtTitulo = new JTextField();
        txtTitulo.setBounds(120, 10, 200, 25);
        add(txtTitulo);

        JLabel lblAutor = new JLabel("Autor:");
        lblAutor.setBounds(10, 50, 100, 25);
        add(lblAutor);

        txtAutor = new JTextField();
        txtAutor.setBounds(120, 50, 200, 25);
        add(txtAutor);

        JLabel lblAno = new JLabel("Ano de Publicação:");
        lblAno.setBounds(10, 90, 100, 25);
        add(lblAno);

        txtAno = new JTextField();
        txtAno.setBounds(120, 90, 200, 25);
        add(txtAno);

        JButton btnAdicionar = new JButton("Adicionar Livro");
        btnAdicionar.setBounds(10, 130, 150, 30);
        add(btnAdicionar);

        JButton btnRemover = new JButton("Remover Livro");
        btnRemover.setBounds(170, 130, 150, 30);
        add(btnRemover);

        JButton btnListar = new JButton("Listar Livros");
        btnListar.setBounds(10, 170, 150, 30);
        add(btnListar);

        // Adicionar Livro
        btnAdicionar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String titulo = txtTitulo.getText();
                String autor = txtAutor.getText();
                int anoPublicacao;

                try {
                    anoPublicacao = Integer.parseInt(txtAno.getText());
                    LivroDTO livro = new LivroDTO(titulo, autor, anoPublicacao);
                    livroDAO.adicionarLivro(livro);
                } catch (NumberFormatException ex) {
                    JOptionPane.showMessageDialog(null, "Ano de publicação inválido!");
                }
            }
        });

        // Remover Livro
        btnRemover.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String titulo = txtTitulo.getText();
                livroDAO.removerLivro(titulo);
            }
        });

        // Listar Livros
        btnListar.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                livroDAO.listarLivros();
            }
        });
    }

    public static void main(String[] args) {
        new BibliotecaView().setVisible(true);
    }
}

# exercicio 4

# tela 

![telaListadeReserva](https://github.com/user-attachments/assets/08bb7948-7b5b-4bee-a2eb-9102f95dce05)


public class ReservaDTO {
    private String cliente;
    private int numeroDoQuarto;
    private String dataEntrada; // Pode usar LocalDate para datas
    private String dataSaida;

    // Construtor
    public ReservaDTO(String cliente, int numeroDoQuarto, String dataEntrada, String dataSaida) {
        this.cliente = cliente;
        this.numeroDoQuarto = numeroDoQuarto;
        this.dataEntrada = dataEntrada;
        this.dataSaida = dataSaida;
    }

    // Getters e Setters
    public String getCliente() {
        return cliente;
    }

    public void setCliente(String cliente) {
        this.cliente = cliente;
    }

    public int getNumeroDoQuarto() {
        return numeroDoQuarto;
    }

    public void setNumeroDoQuarto(int numeroDoQuarto) {
        this.numeroDoQuarto = numeroDoQuarto;
    }

    public String getDataEntrada() {
        return dataEntrada;
    }

    public void setDataEntrada(String dataEntrada) {
        this.dataEntrada = dataEntrada;
    }

    public String getDataSaida() {
        return dataSaida;
    }

    public void setDataSaida(String dataSaida) {
        this.dataSaida = dataSaida;
    }

    @Override
    public String toString() {
        return "Reserva [Cliente: " + cliente + ", Quarto: " + numeroDoQuarto + ", Entrada: " + dataEntrada + ", Saída: " + dataSaida + "]";
    }
}


import java.util.ArrayList;
import java.util.List;

public class ReservaDAO {
    private List<ReservaDTO> reservas;

    public ReservaDAO() {
        reservas = new ArrayList<>();
    }

    // Método para adicionar uma nova reserva
    public void adicionarReserva(ReservaDTO reserva) {
        reservas.add(reserva);
    }

    // Método para buscar reservas por data de entrada
    public List<ReservaDTO> buscarReservasPorData(String data) {
        List<ReservaDTO> resultado = new ArrayList<>();
        for (ReservaDTO reserva : reservas) {
            if (reserva.getDataEntrada().equals(data)) {
                resultado.add(reserva);
            }
        }
        return resultado;
    }

    // Método para listar todas as reservas
    public List<ReservaDTO> listarReservas() {
        return reservas;
    }
}


import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.List;

public class ReservaView extends JFrame {
    private JTextField txtCliente, txtNumeroQuarto, txtDataEntrada, txtDataSaida;
    private JButton btnReservar, btnListarReservas;
    private ReservaDAO reservaDAO;

    public ReservaView() {
        reservaDAO = new ReservaDAO();
        setTitle("Sistema de Reserva de Hotel");
        setSize(400, 300);
        setLayout(new GridLayout(6, 2));

        // Campos de entrada
        add(new JLabel("Cliente:"));
        txtCliente = new JTextField();
        add(txtCliente);

        add(new JLabel("Número do Quarto:"));
        txtNumeroQuarto = new JTextField();
        add(txtNumeroQuarto);

        add(new JLabel("Data de Entrada (dd/mm/aaaa):"));
        txtDataEntrada = new JTextField();
        add(txtDataEntrada);

        add(new JLabel("Data de Saída (dd/mm/aaaa):"));
        txtDataSaida = new JTextField();
        add(txtDataSaida);

        // Botão para adicionar reserva
        btnReservar = new JButton("Reservar");
        btnReservar.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String cliente = txtCliente.getText();
                int numeroQuarto = Integer.parseInt(txtNumeroQuarto.getText());
                String dataEntrada = txtDataEntrada.getText();
                String dataSaida = txtDataSaida.getText();

                ReservaDTO reserva = new ReservaDTO(cliente, numeroQuarto, dataEntrada, dataSaida);
                reservaDAO.adicionarReserva(reserva);

                JOptionPane.showMessageDialog(null, "Reserva adicionada com sucesso!");
                limparCampos();
            }
        });
        add(btnReservar);

        // Botão para listar reservas
        btnListarReservas = new JButton("Listar Reservas");
        btnListarReservas.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                List<ReservaDTO> reservas = reservaDAO.listarReservas();
                StringBuilder sb = new StringBuilder("Reservas:\n");
                for (ReservaDTO reserva : reservas) {
                    sb.append(reserva.toString()).append("\n");
                }
                JOptionPane.showMessageDialog(null, sb.toString());
            }
        });
        add(btnListarReservas);

        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setVisible(true);
    }

    // Método para limpar os campos após a reserva
    private void limparCampos() {
        txtCliente.setText("");
        txtNumeroQuarto.setText("");
        txtDataEntrada.setText("");
        txtDataSaida.setText("");
    }

    public static void main(String[] args) {
        new ReservaView();
    }
}

# exercicio 5 


# tela 

![telaPedido](https://github.com/user-attachments/assets/b8d4a4f7-af7c-4292-a404-4ff3f97e71e2)


public class PedidoDTO {
    private int numeroDoPedido;
    private String cliente;
    private String itens;
    private double total;

    public PedidoDTO(int numeroDoPedido, String cliente, String itens, double total) {
        this.numeroDoPedido = numeroDoPedido;
        this.cliente = cliente;
        this.itens = itens;
        this.total = total;
    }

    public int getNumeroDoPedido() {
        return numeroDoPedido;
    }

    public void setNumeroDoPedido(int numeroDoPedido) {
        this.numeroDoPedido = numeroDoPedido;
    }

    public String getCliente() {
        return cliente;
    }

    public void setCliente(String cliente) {
        this.cliente = cliente;
    }

    public String getItens() {
        return itens;
    }

    public void setItens(String itens) {
        this.itens = itens;
    }

    public double getTotal() {
        return total;
    }

    public void setTotal(double total) {
        this.total = total;
    }

    @Override
    public String toString() {
        return "Pedido{" +
                "Numero: " + numeroDoPedido +
                ", Cliente: '" + cliente + '\'' +
                ", Itens: '" + itens + '\'' +
                ", Total: " + total +
                '}';
    }
}


import java.util.ArrayList;
import java.util.List;

public class PedidoDAO {
    private List<PedidoDTO> pedidos;

    public PedidoDAO() {
        this.pedidos = new ArrayList<>();
    }

    public void adicionarPedido(PedidoDTO pedido) {
        pedidos.add(pedido);
    }

    public void removerPedido(PedidoDTO pedido) {
        pedidos.remove(pedido);
    }

    public List<PedidoDTO> listarPedidos() {
        return pedidos;
    }
}


import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class PedidoView extends JFrame {
    private JTextField txtNumeroPedido, txtCliente, txtItens, txtTotal;
    private PedidoDAO pedidoDAO;

    public PedidoView() {
        pedidoDAO = new PedidoDAO();

        setTitle("Sistema de Controle de Pedidos de Restaurantes");
        setSize(400, 300);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(null);

        JLabel lblNumeroPedido = new JLabel("Número do Pedido:");
        lblNumeroPedido.setBounds(10, 10, 150, 25);
        add(lblNumeroPedido);

        txtNumeroPedido = new JTextField();
        txtNumeroPedido.setBounds(160, 10, 200, 25);
        add(txtNumeroPedido);

        JLabel lblCliente = new JLabel("Cliente:");
        lblCliente.setBounds(10, 45, 150, 25);
        add(lblCliente);

        txtCliente = new JTextField();
        txtCliente.setBounds(160, 45, 200, 25);
        add(txtCliente);

        JLabel lblItens = new JLabel("Itens:");
        lblItens.setBounds(10, 80, 150, 25);
        add(lblItens);

        txtItens = new JTextField();
        txtItens.setBounds(160, 80, 200, 25);
        add(txtItens);

        JLabel lblTotal = new JLabel("Total:");
        lblTotal.setBounds(10, 115, 150, 25);
        add(lblTotal);

        txtTotal = new JTextField();
        txtTotal.setBounds(160, 115, 200, 25);
        add(txtTotal);

        JButton btnCadastrar = new JButton("Cadastrar Pedido");
        btnCadastrar.setBounds(10, 150, 170, 30);
        add(btnCadastrar);

        JButton btnListar = new JButton("Listar Pedidos");
        btnListar.setBounds(190, 150, 170, 30);
        add(btnListar);

        // Evento para cadastrar um pedido
        btnCadastrar.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                int numero = Integer.parseInt(txtNumeroPedido.getText());
                String cliente = txtCliente.getText();
                String itens = txtItens.getText();
                double total = Double.parseDouble(txtTotal.getText());

                PedidoDTO pedido = new PedidoDTO(numero, cliente, itens, total);
                pedidoDAO.adicionarPedido(pedido);

                JOptionPane.showMessageDialog(null, "Pedido cadastrado com sucesso!");
            }
        });

        // Evento para listar todos os pedidos
        btnListar.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                StringBuilder pedidosList = new StringBuilder();
                for (PedidoDTO pedido : pedidoDAO.listarPedidos()) {
                    pedidosList.append(pedido.toString()).append("\n");
                }
                JOptionPane.showMessageDialog(null, pedidosList.toString());
            }
        });

        setVisible(true);
    }

    public static void main(String[] args) {
        new PedidoView();
    }
}


# exercicio 6

# tela 







