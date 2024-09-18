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

