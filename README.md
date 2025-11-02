# TUGAS-MATEMATIKA-DISKRIT-PERT-7
# NAMA : DIVA OKTIANA PANCA RAMADANI <br>
# NIM : 312510313 <br>
# Simulasi Tabel Kebenaran (Truth Table)
import itertools
# Definisi fungsi implikasi
def implies(p, q):
 return (not p) or q
# Header tabel
print(f"{'p':<5}{'q':<5}{'p and q':<10}{'p or q':<10}{'¬p':<5}{'p → q':<8}")
# Iterasi semua kombinasi p dan q (True/False)
for p, q in itertools.product([True, False], repeat=2):
 print(f"{p!s:<5}{q!s:<5}{(p and q)!s:<10}{(p or q)!s:<10}{(not p)!s:<5}{implies(p, q)!s:<8}")
# Pembuktian Kontradiksi Sederhana (Logika Matematis)
#Jika n² ganjil, maka n juga ganjil.
#Kita buktikan secara logika bahwa kebalikannya menghasilkan kontradiksi.

def is_odd(n):
    return n % 2 != 0  # Lebih akurat: ganjil jika sisa bagi 2 bukan 0

def proof_by_contradiction():
    """
    Membuktikan pernyataan: "Jika n² ganjil, maka n juga ganjil."
    Dengan proof by contradiction: Asumsikan kebalikannya benar, yaitu ada n genap dengan n² ganjil.
    Jika tidak ditemukan kontradiksi, maka pernyataan asli benar.
    """
    for n in range(1, 101):  # Periksa hingga n=100 untuk lebih komprehensif
        if is_odd(n**2) and not is_odd(n):  # Jika n² ganjil tapi n genap
            print(f"Kontradiksi ditemukan pada n={n}!")
            return False
    print("Tidak ada kontradiksi ditemukan → pernyataan benar (jika n² ganjil maka n ganjil).")
    return True
# Uji Tautologi (dengan Table Kebenaran)
def check_tautology():
    tautology = True
    print("Memeriksa apakah (p ∧ q) → p adalah tautologi:")
    for p, q in itertools.product([True, False], repeat=2):
        result = implies(p and q, p)
        print(f"p={p}, q={q}, (p ∧ q) → p = {result}")
        if not result:
            tautology = False
    print("\nKesimpulan:", "TAUTOLOGI" if tautology else "BUKAN tautologi")

check_tautology()
