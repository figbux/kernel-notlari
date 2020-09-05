# Linux kernel exploitation notları
Eğer notları okuyorsanız kernel exploitationa yanlış kapıdan giriş yaptınız demektir. Tamamlanmasına vesile olur umuduyla notlar kamuya açıldı.

## Notların son durumu
Karmakarışık ve yarım

## İçindekiler ve daha içeri giremeyenler
```
[*] Amaç
[*] Kaynakları edinin
[*] Lab ortamı kurulumu
[*] Kernel ne işe yarıyor?
    [-] Kernel map
    [-] Kernel 5.8'in codebase'ini biraz incelersek:
[-] Ring goygoyu
[+] Kernel Exploitation Temelleri
    [-] Basit exploitation stratejisi - Büyük resim:
    [-] Kernel'de nasıl zafiyetler var?
    [-] Bu zafiyetleri nasıl sömürülür?
    [-] Bazı kernel güvenlik önlemleri ve aşma yöntemleri
    [-] Debugging
    [-] Nerelerde zafiyetler var?
        [~] LKM (Loadable Kernel Module)
            [o] LKM'lerin kullanım alanları:
            [o] LKM dosya yapısı
            [o] LKM'lerle çalışmak için komutlar
[+] LDD3 - Chapter 15, Memory Mapping and DMA
    [-] List of address types used in Linux
        [o] User virtual addresses
        [o] Physical addresses
        [o] Bus addresses
        [o] Kernel logical addresses
        [o] Kernel virtual addresses
    [-] High and Low Memory
        [o] Low memory
        [o] High memory
    [-] Page Tables
    [-] Virtual Memory Areas
    [-] The mmap Device Operation
[-] Proc cheatsheet
[-] Önemli kernel yapıları, fonksiyonlar vs. kernel v5.8 için sunulmuştur
    [~] task_struct: "işlem"in tanımı
    [~] cred struct: işlemin yetkilerinin tanımı
    [-] "current" makrosu: o anki koşan işleme pointer
    [~] file, fdtable, files_struct: dosyalar
    [~] Virtual function table (vft) yaklaşımı
    [~] socket, sock, skb: ağ
    [~] netlink_sock: IPC için özel soket
    [~] Hepsi bir arada: current, task_struct, files_struct, fdtable,
    [~] Reference counter kavramı
[-] cheatsheet
```
