# Tugas_KedaiKopi_Diskon
class Menu:
    def __init__(self, nama, harga):
        self.__nama = nama
        self.__harga = harga
    
    def get_nama(self):
        return self.__nama
    
    def get_harga(self):
        return self.__harga


class Diskon:
    def __init__(self):
        self.__tingkatan_diskon = [
            {"jumlah_pesan": 5, "diskon": 0.2},
            {"jumlah_pesan": 4, "diskon": 0.15},
            {"jumlah_pesan": 3, "diskon": 0.1},
            {"jumlah_pesan": 2, "diskon": 0.05},
            {"jumlah_pesan": 1, "diskon": 0},
        ]

    def get_diskon(self, jumlah_pesan):
        for diskon in self.__tingkatan_diskon:
            if jumlah_pesan >= diskon["jumlah_pesan"]:
                return diskon["diskon"]
        return 0


class AnandaCoffee:
    def __init__(self):
        self.__menu = [
            Menu("ES Kopi Susu", 11000),
            Menu("ES Kopi Coklat", 12000),
            Menu("ES Kopi Hitam", 11000),
            Menu("Ice Americano", 14000)
        ]
        self.__diskon = Diskon()

    def tampilkan_menu(self):
        print("""
        ==============================
        
        Ananda Coffee
        List Menu Minuman Kopi
     
        ==============================
        """)
        for i, menu in enumerate(self.__menu):
            print(f"{chr(65+i)}. {menu.get_nama()} : Rp {menu.get_harga()}")

    def pesan(self):
        while True:
            self.tampilkan_menu()
            pesan = input("masukkan list abjad menu kopi = ")
            if pesan.upper() not in [chr(65+i) for i in range(len(self.__menu))]:
                pilihan = input("menu tidak tersedia, silahkan masukkan abjad menu yang tersedia silahkan ulangi kembali Y/N =")
                if pilihan.upper() == "N":
                    print("Terima kasih atas kunjungan Anda!")
                    break
            else:
                menu = self.__menu[ord(pesan.upper()) - 65]
                jumlah_pesan = int(input("masukkan jumlah pesanan = "))
                harga = menu.get_harga() * jumlah_pesan
                diskon = self.__diskon.get_diskon(jumlah_pesan) * harga
                ppn = int((harga - diskon) * 0.1)
                total_harga = harga - diskon + ppn

                print("--------------------------")
                print("Ananda Coffe")
                print("--------------------------")
                print("Menu :", menu.get_nama())
                print("Jumlah Pesan :", jumlah_pesan)
                print("Harga :", harga)
                print("Diskon :", diskon)
                print("PPN :", ppn)
                print("--------------------------")
                print("Jumlah Bayar :", total_harga)
                print("--------------------------")
                pilihan = input("apakah anda ingin order kembali Y/N =")
                if pilihan.upper() == "N":
                    print("Terima kasih atas kunjungan Anda!")
                    break


ananda_coffee = AnandaCoffee()
ananda_coffee.pesan()

Program di atas adalah program sederhana untuk memesan minuman kopi di Ananda Coffee. Terdapat tiga kelas dalam program tersebut yaitu:

Menu: Kelas ini digunakan untuk membuat objek menu yang memiliki atribut nama dan harga, serta method get_nama() dan get_harga() untuk mengakses atribut tersebut.

Diskon: Kelas ini digunakan untuk membuat objek diskon yang memiliki atribut tingkatan_diskon yang berisi list dictionary yang menyimpan jumlah pesanan dan diskon yang diberikan. Kelas ini juga memiliki method get_diskon(jumlah_pesan) yang akan mengembalikan jumlah diskon yang diberikan berdasarkan jumlah pesanan yang dipesan.

AnandaCoffee: Kelas ini merupakan kelas utama yang digunakan untuk menjalankan program. Kelas ini memiliki dua atribut yaitu menu yang berisi list objek Menu dan diskon yang berisi objek Diskon. Kelas ini juga memiliki tiga method yaitu tampilkan_menu() untuk menampilkan daftar menu, pesan() untuk melakukan pemesanan dan menghitung harga, serta method main() yang digunakan untuk menjalankan program.
