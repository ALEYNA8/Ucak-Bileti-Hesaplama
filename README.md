# Ucak-Bileti-Hesaplama
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Kullanıcıdan girdi al
        System.out.print("Mesafeyi girin (KM) : ");
        int mesafe = scanner.nextInt();

        System.out.print("Yaşınızı girin: ");
        int yas = scanner.nextInt();

        System.out.print("Yolculluk tipi (1 -> Tek Yön, 2 -> Gidiş-Dönüş) : ");
        int yolculukTipi = scanner.nextInt();

        // Girdi Doğrulama
        if (mesafe <= 0 || yas <= 0 || (yolculukTipi != 1 && yolculukTipi != 2)) {
            System.out.println("Hatalı Veri Girdiniz! ");
            return;
        }

        // Mesafe başına ücret
        double birimUcret = 0.10;
        double normalTutar = mesafe * birimUcret;

        // Yaş indirimini hesaplama
        double yasIndirimi = 0;
        if (yas < 12) {
            yasIndirimi = normalTutar * 0.50;
        } else if (yas >= 12 && yas <= 24) {
            yasIndirimi = normalTutar * 0.10;
        } else if (yas > 65) {
            yasIndirimi = normalTutar * 0.30;
        }
        double indirimliTutar = normalTutar - yasIndirimi;

        // Gidiş-Dönüş indirimi uygula
        if (yolculukTipi == 2) {
            indirimliTutar *= 0.80; // %20 indirim
        }

        // Toplam tutarı hesapla
        double toplamTutar = indirimliTutar * (yolculukTipi == 2 ? 2 : 1);

        // Sonucu yazdır
        System.out.println("Toplam Tutar: " + toplamTutar + "TL");
    }
}
