<!-- KONFIGURASI KONEKSI, BUAT TABEL DB, TAMBAH, EDIT, DAN HAPUS DATA SCRIPT PHP -->
<?php
// Konfigurasi database
$host = 'localhost';
$username = 'root';
$password = '';
$dbname = 'diskon';

// Koneksi ke database
$conn = new mysqli($host, $username, $password, $dbname);

// Cek koneksi
if ($conn->connect_error) {
    die("Koneksi gagal: " . $conn->connect_error);
}

//deklarasi error pesan 
$error_message = null;

// Buat tabel tasks jika belum ada
$sql_create_table = "
CREATE TABLE IF NOT EXISTS tasks (
    id INT AUTO_INCREMENT PRIMARY KEY,
    kode_barang VARCHAR(20) NOT NULL UNIQUE,
    nama_barang VARCHAR(255) NOT NULL,
    harga_awal DECIMAL(10, 2) NOT NULL,
    diskon_persen DECIMAL(5, 2) NOT NULL,
    harga_akhir DECIMAL(10, 2) NOT NULL
)";
if (!$conn->query($sql_create_table)) {
    die("Gagal membuat tabel: " . $conn->error);
}

// Fungsi untuk membuat kode barang otomatis
function generateKodeBarang($conn) {
    $tanggal = date('Ymd');
    $sql = "SELECT COUNT(*) AS jumlah FROM tasks";
    $result = $conn->query($sql);
    $row = $result->fetch_assoc();
    $jumlah = $row['jumlah'] + 1;
    return "BRG-$tanggal-" . str_pad($jumlah, 4, '0', STR_PAD_LEFT);
}

// Tambahkan atau edit data barang
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $error_message = null;

    // Validasi diskon
    if ($_POST['diskon_persen'] > 100) {
        $error_message = "Diskon tidak boleh lebih dari 100%.";
    } else {
        if ($_POST['action'] === 'add') {
            $kode_barang = generateKodeBarang($conn);
            $nama_barang = $_POST['nama_barang'];
            $harga_awal = $_POST['harga_awal'];
            $diskon_persen = $_POST['diskon_persen'];
            $harga_akhir = $harga_awal - ($harga_awal * $diskon_persen / 100);

            $stmt = $conn->prepare("INSERT INTO tasks (kode_barang, nama_barang, harga_awal, diskon_persen, harga_akhir) VALUES (?, ?, ?, ?, ?)");
            $stmt->bind_param("ssddd", $kode_barang, $nama_barang, $harga_awal, $diskon_persen, $harga_akhir);
            $stmt->execute();
            $stmt->close();
            header("Location: " . $_SERVER['PHP_SELF']);
        } elseif ($_POST['action'] === 'edit') {
            $id = $_POST['id'];
            $nama_barang = $_POST['nama_barang'];
            $harga_awal = $_POST['harga_awal'];
            $diskon_persen = $_POST['diskon_persen'];
            $harga_akhir = $harga_awal - ($harga_awal * $diskon_persen / 100);

            $stmt = $conn->prepare("UPDATE tasks SET nama_barang = ?, harga_awal = ?, diskon_persen = ?, harga_akhir = ? WHERE id = ?");
            $stmt->bind_param("sdddi", $nama_barang, $harga_awal, $diskon_persen, $harga_akhir, $id);
            $stmt->execute();
            $stmt->close();
            header("Location: " . $_SERVER['PHP_SELF']);
        }
    }
}

// Hapus data barang
if (isset($_GET['delete'])) {
    $id = $_GET['delete'];
    $stmt = $conn->prepare("DELETE FROM tasks WHERE id = ?");
    $stmt->bind_param("i", $id);
    $stmt->execute();
    $stmt->close();
    header("Location: " . $_SERVER['PHP_SELF']);
}

// Ambil semua data barang
$sql_select = "SELECT * FROM tasks";
$result = $conn->query($sql_select);

// Ambil data untuk diedit jika ada
$editData = null;
if (isset($_GET['edit'])) {
    $id = $_GET['edit'];
    $stmt = $conn->prepare("SELECT * FROM tasks WHERE id = ?");
    $stmt->bind_param("i", $id);
    $stmt->execute();
    $result_edit = $stmt->get_result();
    if ($result_edit->num_rows > 0) {
        $editData = $result_edit->fetch_assoc();
    }
    $stmt->close();
}
?>

<!-- KODING UNTUK MEMBUAT TAMPILAN DESAIN CSS-->
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikasi Perhitungan Diskon UKK RPL</title>
    <script src="https://cdn.jsdelivr.net/npm/jsbarcode@3.11.5/dist/JsBarcode.all.min.js"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" rel="stylesheet">

   <style>
/* Global Styles */
body {
    font-family: 'Roboto', Arial, sans-serif;
    background-color: #f4f4f9;
   	min-height: 100vh;
    margin: 0;
    background: linear-gradient(135deg, #0000ff, #D4A5A5);
    padding-top: 40px;
    color: #333;
    line-height: 1.6;
}

.container {
    max-width: 1200px;
    margin: 30px auto;
    background: #ffffff;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
    padding: 30px;
    border-radius: 12px;
    overflow: hidden;
}

/* Heading Styles */
h1, h2, h3 {
    text-align: center;
    margin-bottom: 20px;
    color: #2c3e50;
    text-transform: uppercase;
}

h1 {
    font-size: 2.5rem;
    letter-spacing: 2px;
}

h3 {
    color: #3498db;
    font-size: 1.5rem;
}

/* Form Styles */
form {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-bottom: 30px;
}

label {
    font-weight: bold;
    margin-bottom: 5px;
    color: #2c3e50;
}

input[type="text"],
input[type="number"],
button {
    padding: 12px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 8px;
    transition: all 0.3s ease;
}

input[type="text"]:focus,
input[type="number"]:focus {
    border-color: #3498db;
    outline: none;
    box-shadow: 0 0 8px rgba(52, 152, 219, 0.3);
}

button {
    background-color: #3498db;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: bold;
    letter-spacing: 1px;
    transition: all 0.3s ease;
}

button:hover {
    background-color: #1d6fa5;
    box-shadow: 0 4px 10px rgba(52, 152, 219, 0.3);
}

/* Table Styles */
table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
    overflow: hidden;
    border-radius: 8px;
}

table th, table td {
    padding: 15px;
    text-align: center;
    border: 1px solid #ddd;
}

table th {
    background-color: #3498db;
    color: white;
    font-size: 16px;
    text-transform: uppercase;
}

table tr:nth-child(even) {
    background-color: #f9f9f9;
}

table tr:hover {
    background-color: #f1f1f1;
    cursor: pointer;
}

.delete {
    color: #e74c3c;
    text-decoration: none;
    font-weight: bold;
    transition: all 0.3s ease;
}

.delete:hover {
    color: #c0392b;
    text-shadow: 0 1px 5px rgba(192, 57, 43, 0.5);
}

a {
    color: #3498db;
    text-decoration: none;
    font-weight: bold;
    transition: all 0.3s ease;
}

a:hover {
    color: #1d6fa5;
}

/* Barcode Style */
svg {
    margin: 0 auto;
    display: block;
}

/* Mobile Styles */
@media (max-width: 768px) {
    .container {
        padding: 20px;
    }

    table {
        font-size: 14px;
    }

    h1 {
        font-size: 2rem;
    }
}
</style>
</head>
<body>
<!-- MEMBUAT TAMPILAN FORM APLIKASI PERHITUNGAN DISKON HTML DAN PHP -->
    <div class="container">
        <h1>Aplikasi Perhitungan Diskon UKK RPL 2025</h1>
        <h1>SMK YAPPRI SUMEDANG</h1>
	
        <!-- Form Input -->
        <?php if ($editData): ?>
            <h3>Edit Porduk</h3>
            <form method="POST" action="">
                <input type="hidden" name="action" value="edit">
                <input type="hidden" name="id" value="<?php echo $editData['id']; ?>">

                <label for="nama_barang">Nama Barang:</label>
                <input type="text" id="nama_barang" name="nama_barang" value="<?php echo $editData['nama_barang']; ?>" required>

                <label for="harga_awal">Harga Awal (Rp):</label>
                <input type="number" step="0.01" id="harga_awal" name="harga_awal" value="<?php echo $editData['harga_awal']; ?>" required>

                <label for="diskon_persen">Diskon (%):</label>
                <input type="number" step="0.01" id="diskon_persen" name="diskon_persen" value="<?php echo $editData['diskon_persen']; ?>" required>

                <button type="submit">Simpan Perubahan</button>
                <a href="<?php echo $_SERVER['PHP_SELF']; ?>"><button>Batal</button></a>
            </form>
        <?php else: ?>
            <h3>Tambah Produk</h3>
            <form method="POST" action="">
                <input type="hidden" name="action" value="add">

                <label for="nama_barang">Nama Produk:</label>
                <input type="text" id="nama_barang" name="nama_barang" required>

                <label for="harga_awal">Harga Awal (Rp):</label>
                <input type="number" step="0.01" id="harga_awal" name="harga_awal" required>

                <label for="diskon_persen">Diskon (%):</label>
                <input type="number" step="0.01" id="diskon_persen" name="diskon_persen" required>

                <button type="submit">Tambah Barang</button>
            </form>
       
  <?php endif; ?>
        <hr>
<!-- MENAMPILKAN DATA PRODUK YANG DIPANGGIL DARI DATABASE DISKON BAHASA HTML DAN PHP -->
        <!-- Tabel Data -->
        <h2>Daftar Produk</h2>
        <div style="overflow-x: auto;">
        <table>
            <tr>
              
                <th>Kode Barcode Barang</th>
                <th>Nama Barang</th>
                <th>Harga</th>
                <th>Diskon (%)</th>
                <th>Total</th>
             
                <th>Aksi</th>
            </tr>
            <?php if ($result->num_rows > 0): ?>
                <?php while ($row = $result->fetch_assoc()): ?>
                    <tr>
                       
                      <td>
                            <svg id="barcode-<?php echo $row['id']; ?>"></svg>
                            <script>
                                JsBarcode("#barcode-<?php echo $row['id']; ?>", "<?php echo $row['kode_barang']; ?>");
                            </script>
                        </td>
                        <td><?php echo $row['nama_barang']; ?></td>
                        <td><?php echo number_format($row['harga_awal'], 2, ',', '.'); ?></td>
                        <td><?php echo $row['diskon_persen']; ?></td>
                        <td><?php echo number_format($row['harga_akhir'], 2, ',', '.'); ?></td>
                        
                        <td>
                            <a href="?edit=<?php echo $row['id']; ?>"><i class="fa fa-edit"></i></a> 
                            <a href="?delete=<?php echo $row['id']; ?>" onclick="return confirm('Yakin ingin menghapus?')"><li class="fa fa-eraser"></li></a>
                        </td>
                    </tr>
                <?php endwhile; ?>
            <?php else: ?>
                <tr>
                    <td colspan="8">Belum ada data barang.</td>
                </tr>
            <?php endif; ?>
            
        </table>
</div>
        <?php if ($error_message): ?>
            <p style="color: red;"><?php echo $error_message; ?></p>
        <?php endif; ?>
        <?php
// Hitung total harga_akhir dari database
$sql_total = "SELECT SUM(harga_akhir) AS total_harga FROM tasks";
$result_total = $conn->query($sql_total);
$row_total = $result_total->fetch_assoc();
$total_harga = $row_total['total_harga'];
?>

<h3 style="text-align: center; margin-top: 20px;">Total Keseluruhan: Rp <?php echo number_format($total_harga, 2, ',', '.'); ?></h3>
    </div>
</body>
</html>
<?php $conn->close(); ?>
