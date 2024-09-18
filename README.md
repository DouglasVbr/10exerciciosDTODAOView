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

