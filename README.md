
# Aplikasi Penghitungan Diskon

Tugas 3 Modul Aplikasi Penghitungan Diskon

# Deskripsi
"Aplikasi Hitung Diskon" adalah aplikasi desktop sederhana yang dibangun menggunakan Java Swing untuk menghitung harga akhir produk setelah penerapan diskon awal dan diskon tambahan menggunakan kode kupon. Aplikasi ini memungkinkan pengguna untuk memasukkan harga asli, memilih atau memasukkan persentase diskon, dan menerapkan kode kupon untuk melihat total penghematan dan harga akhir.


# Features

Fitur tambahan dari aplikasi ini meliputi:

1. Input Harga Asli: Pengguna dapat memasukkan harga asli produk yang ingin dihitung.
2. Persentase Diskon: Diskon awal dapat dipilih menggunakan slider atau dropdown (ComboBox) untuk menentukan persentase diskon.
3.  Kode Kupon Diskon: Pengguna dapat memasukkan kode kupon diskon untuk mendapatkan diskon tambahan.
4. Hasil Penghitungan Diskon:
 - Penghematan dari diskon awal.
- Penghematan tambahan dari kode kupon (jika valid).
- Harga akhir setelah penerapan semua diskon.
5. Riwayat Perhitungan: Aplikasi menampilkan riwayat perhitungan diskon dalam JTextArea untuk melihat kembali transaksi sebelumnya.


# Dokumentasi Code

```java
import javax.swing.JOptionPane;
import java.util.Map;
import java.util.HashMap;


public class AplikasiHitungDiskon extends javax.swing.JFrame {
    private Map<String, Integer> kuponDiskonMap; // Deklarasi map untuk kode kupon

    
    public AplikasiHitungDiskon() {
        initComponents();
        initializeKuponDiskon();
    }
    
    private void initializeKuponDiskon() {
    kuponDiskonMap = new HashMap<>();
    kuponDiskonMap.put("DISKON10", 10); // Kode kupon untuk diskon 10%
    kuponDiskonMap.put("DISKON15", 15); // Kode kupon untuk diskon 15%
    kuponDiskonMap.put("DISKON25", 25);
    kuponDiskonMap.put("DISKON50", 50); // Kode kupon untuk diskon 50%
    // Tambahkan variasi kode kupon lainnya di sini jika diperlukan
}

    
private void hitungDiskon() {
    try {
        // Ambil harga asli dari input
        double hargaAsli = Double.parseDouble(txtHargaAsli.getText());

        // Ambil persentase diskon dari slider
        int persentaseDiskonAwal = sliderDiskon.getValue();
        
        // Hitung harga setelah diskon awal
        double penghematanAwal = hargaAsli * persentaseDiskonAwal / 100;
        double hargaSetelahDiskonAwal = hargaAsli - penghematanAwal;

        // Ambil kode kupon dari JTextField untuk diskon tambahan
        String kodeKupon = txtKodeKupon.getText().trim();
        int diskonKupon = 0;
        
        // Validasi kode kupon dan ambil diskon tambahan jika ada
        if (!kodeKupon.isEmpty() && kuponDiskonMap.containsKey(kodeKupon)) {
            diskonKupon = kuponDiskonMap.get(kodeKupon); // Ambil diskon kupon
        } else if (!kodeKupon.isEmpty()) {
            JOptionPane.showMessageDialog(this, "Kode kupon tidak valid.", "Error", JOptionPane.ERROR_MESSAGE);
        }

        // Hitung harga setelah diskon tambahan dari kupon (jika ada)
        double penghematanKupon = hargaSetelahDiskonAwal * diskonKupon / 100;
        double hargaSetelahDiskonTotal = hargaSetelahDiskonAwal - penghematanKupon;

        // Tampilkan hasil di JTextField
        txtPenghematan.setText(String.format("Rp %.2f", penghematanAwal + penghematanKupon));
        txtHargaSetelahDiskon.setText(String.format("Rp %.2f", hargaSetelahDiskonTotal));

        // Tambahkan ke riwayat perhitungan di JTextArea (jika ada)
        txtAreaRiwayat.append("Harga Asli: " + String.format("Rp %.2f", hargaAsli) +
                              ", Diskon Awal: " + persentaseDiskonAwal + "%" +
                              ", Penghematan Awal: " + String.format("Rp %.2f", penghematanAwal) +
                              ", Diskon Kupon: " + diskonKupon + "%" +
                              ", Penghematan Kupon: " + String.format("Rp %.2f", penghematanKupon) +
                              ", Harga Akhir: " + String.format("Rp %.2f", hargaSetelahDiskonTotal) + "\n");
    } catch (NumberFormatException e) {
        JOptionPane.showMessageDialog(this, "Masukkan harga yang valid.", "Error", JOptionPane.ERROR_MESSAGE);
    }
}







    
    



    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {
        java.awt.GridBagConstraints gridBagConstraints;

        jPanel1 = new javax.swing.JPanel();
        jLabel1 = new javax.swing.JLabel();
        jPanel2 = new javax.swing.JPanel();
        jLabel2 = new javax.swing.JLabel();
        jLabel3 = new javax.swing.JLabel();
        jLabel4 = new javax.swing.JLabel();
        jLabel5 = new javax.swing.JLabel();
        btnHitung = new javax.swing.JButton();
        txtPenghematan = new javax.swing.JTextField();
        txtHargaAsli = new javax.swing.JTextField();
        txtKodeKupon = new javax.swing.JTextField();
        txtHargaSetelahDiskon = new javax.swing.JTextField();
        jLabel6 = new javax.swing.JLabel();
        jScrollPane1 = new javax.swing.JScrollPane();
        txtAreaRiwayat = new javax.swing.JTextArea();
        jPanel3 = new javax.swing.JPanel();
        cmbDiskon = new javax.swing.JComboBox<>();
        sliderDiskon = new javax.swing.JSlider();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        jLabel1.setFont(new java.awt.Font("Modern No. 20", 1, 24)); // NOI18N
        jLabel1.setText("Aplikasi Hitung Diskon");
        jPanel1.add(jLabel1);

        jPanel2.setLayout(new java.awt.GridBagLayout());

        jLabel2.setText("Anda Hemat");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 3;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        jPanel2.add(jLabel2, gridBagConstraints);

        jLabel3.setText("Harga Asli");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        jPanel2.add(jLabel3, gridBagConstraints);

        jLabel4.setText("Diskon (%)");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 1;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        jPanel2.add(jLabel4, gridBagConstraints);

        jLabel5.setText("Harga Setelah Diskon");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 2;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        jPanel2.add(jLabel5, gridBagConstraints);

        btnHitung.setText("Hitung");
        btnHitung.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btnHitungActionPerformed(evt);
            }
        });
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 3;
        gridBagConstraints.gridy = 6;
        gridBagConstraints.insets = new java.awt.Insets(18, 240, 5, 253);
        jPanel2.add(btnHitung, gridBagConstraints);
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 3;
        gridBagConstraints.gridwidth = 3;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        gridBagConstraints.ipadx = 63;
        gridBagConstraints.insets = new java.awt.Insets(12, 112, 5, 5);
        jPanel2.add(txtPenghematan, gridBagConstraints);
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.gridwidth = 3;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        gridBagConstraints.ipadx = 63;
        gridBagConstraints.insets = new java.awt.Insets(12, 112, 5, 5);
        jPanel2.add(txtHargaAsli, gridBagConstraints);
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 4;
        gridBagConstraints.gridwidth = 3;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        gridBagConstraints.ipadx = 63;
        gridBagConstraints.insets = new java.awt.Insets(12, 112, 5, 5);
        jPanel2.add(txtKodeKupon, gridBagConstraints);
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 2;
        gridBagConstraints.gridwidth = 3;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        gridBagConstraints.ipadx = 63;
        gridBagConstraints.insets = new java.awt.Insets(12, 112, 5, 5);
        jPanel2.add(txtHargaSetelahDiskon, gridBagConstraints);

        jLabel6.setText("Vouncher Diskon ");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 4;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        jPanel2.add(jLabel6, gridBagConstraints);

        txtAreaRiwayat.setColumns(20);
        txtAreaRiwayat.setRows(5);
        jScrollPane1.setViewportView(txtAreaRiwayat);

        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 3;
        gridBagConstraints.gridy = 7;
        gridBagConstraints.gridheight = 2;
        gridBagConstraints.fill = java.awt.GridBagConstraints.BOTH;
        gridBagConstraints.weighty = 0.1;
        gridBagConstraints.insets = new java.awt.Insets(12, 12, 50, 50);
        jPanel2.add(jScrollPane1, gridBagConstraints);

        javax.swing.GroupLayout jPanel3Layout = new javax.swing.GroupLayout(jPanel3);
        jPanel3.setLayout(jPanel3Layout);
        jPanel3Layout.setHorizontalGroup(
            jPanel3Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGap(0, 0, Short.MAX_VALUE)
        );
        jPanel3Layout.setVerticalGroup(
            jPanel3Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGap(0, 0, Short.MAX_VALUE)
        );

        jPanel2.add(jPanel3, new java.awt.GridBagConstraints());

        cmbDiskon.setModel(new javax.swing.DefaultComboBoxModel<>(new String[] { "0%", "10%", "20%", "30%", "40%", "50%", "60%", "70%", "80%", "90%", "100%" }));
        cmbDiskon.addItemListener(new java.awt.event.ItemListener() {
            public void itemStateChanged(java.awt.event.ItemEvent evt) {
                cmbDiskonItemStateChanged(evt);
            }
        });
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 3;
        gridBagConstraints.gridy = 1;
        gridBagConstraints.gridwidth = 4;
        gridBagConstraints.ipadx = 36;
        gridBagConstraints.ipady = 2;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.WEST;
        gridBagConstraints.insets = new java.awt.Insets(0, 70, 0, 70);
        jPanel2.add(cmbDiskon, gridBagConstraints);

        sliderDiskon.setMajorTickSpacing(10);
        sliderDiskon.setMinorTickSpacing(5);
        sliderDiskon.setPaintTicks(true);
        sliderDiskon.setValue(10);
        sliderDiskon.addChangeListener(new javax.swing.event.ChangeListener() {
            public void stateChanged(javax.swing.event.ChangeEvent evt) {
                sliderDiskonStateChanged(evt);
            }
        });
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 3;
        gridBagConstraints.gridy = 1;
        gridBagConstraints.gridwidth = 6;
        gridBagConstraints.ipadx = 164;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.EAST;
        gridBagConstraints.insets = new java.awt.Insets(12, 0, 0, 0);
        jPanel2.add(sliderDiskon, gridBagConstraints);

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addComponent(jPanel2, javax.swing.GroupLayout.DEFAULT_SIZE, 978, Short.MAX_VALUE)
            .addGroup(layout.createSequentialGroup()
                .addComponent(jPanel1, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                .addContainerGap())
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addComponent(jPanel1, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(31, 31, 31)
                .addComponent(jPanel2, javax.swing.GroupLayout.DEFAULT_SIZE, 686, Short.MAX_VALUE)
                .addContainerGap())
        );

        pack();
    }// </editor-fold>                        

    private void btnHitungActionPerformed(java.awt.event.ActionEvent evt) {                                          
        hitungDiskon();
    }                                         

    private void cmbDiskonItemStateChanged(java.awt.event.ItemEvent evt) {                                           
        hitungDiskon();
    }                                          

    private void sliderDiskonStateChanged(javax.swing.event.ChangeEvent evt) {                                          

    int sliderValue = sliderDiskon.getValue(); // Ambil nilai dari slider

    // Set nilai di JComboBox sesuai dengan nilai slider
    cmbDiskon.setSelectedItem(sliderValue + "%");

    // Panggil metode hitungDiskon untuk memperbarui perhitungan
    hitungDiskon();
    }                                         

    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
        /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(AplikasiHitungDiskon.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(AplikasiHitungDiskon.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(AplikasiHitungDiskon.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(AplikasiHitungDiskon.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new AplikasiHitungDiskon().setVisible(true);
            }
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JButton btnHitung;
    private javax.swing.JComboBox<String> cmbDiskon;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JLabel jLabel4;
    private javax.swing.JLabel jLabel5;
    private javax.swing.JLabel jLabel6;
    private javax.swing.JPanel jPanel1;
    private javax.swing.JPanel jPanel2;
    private javax.swing.JPanel jPanel3;
    private javax.swing.JScrollPane jScrollPane1;
    private javax.swing.JSlider sliderDiskon;
    private javax.swing.JTextArea txtAreaRiwayat;
    private javax.swing.JTextField txtHargaAsli;
    private javax.swing.JTextField txtHargaSetelahDiskon;
    private javax.swing.JTextField txtKodeKupon;
    private javax.swing.JTextField txtPenghematan;
    // End of variables declaration                   
}




```


## Authors

Muhammad Irwan Firmanto
2210010582 5B Reg Pagi Banjarmasin

- [@eternalsugarzy](https://www.github.com/eternalsugarzy)


## Screenshots

![Screenshot 2024-11-02 233801](https://github.com/user-attachments/assets/f98dfd5b-70ab-4a01-ba15-aa69a17b2920)


