import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.sql.*;

public class BarangFrame extends JFrame {
    private JTextField txtNama, txtHarga;
    private JButton btnAdd, btnUpdate, btnDelete, btnRead;
    
    public BarangFrame() {
        setTitle("CRUD Data Barang");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());

        txtNama = new JTextField(20);
        txtHarga = new JTextField(20);
        btnAdd = new JButton("Add");
        btnUpdate = new JButton("Update");
        btnDelete = new JButton("Delete");
        btnRead = new JButton("Read");

        add(new JLabel("Nama:"));
        add(txtNama);
        add(new JLabel("Harga:"));
        add(txtHarga);
        add(btnAdd);
        add(btnUpdate);
        add(btnDelete);
        add(btnRead);

        btnAdd.addActionListener(e -> addBarang());
        btnUpdate.addActionListener(e -> updateBarang());
        btnDelete.addActionListener(e -> deleteBarang());
        btnRead.addActionListener(e -> readBarang());
    }

    private void addBarang() {
        try (Connection conn = DatabaseConnection.getConnection()) {
            String sql = "INSERT INTO data_barang (nama, harga) VALUES (?, ?)";
            PreparedStatement pstmt = conn.prepareStatement(sql);
            pstmt.setString(1, txtNama.getText());
            pstmt.setDouble(2, Double.parseDouble(txtHarga.getText()));
            pstmt.executeUpdate();
            JOptionPane.showMessageDialog(this, "Data barang berhasil ditambahkan.");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private void updateBarang() {
        throw new UnsupportedOperationException("Not supported yet."); // Generated from nbfs://nbhost/SystemFileSystem/Templates/Classes/Code/GeneratedMethodBody
    }

    private void deleteBarang() {
        throw new UnsupportedOperationException("Not supported yet."); // Generated from nbfs://nbhost/SystemFileSystem/Templates/Classes/Code/GeneratedMethodBody
    }

    private void readBarang() {
        throw new UnsupportedOperationException("Not supported yet."); // Generated from nbfs://nbhost/SystemFileSystem/Templates/Classes/Code/GeneratedMethodBody
    }
}
