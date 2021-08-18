# Linux kernel exploitation notları
Eğer notları okuyorsanız kernel exploitationa yanlış kapıdan giriş yaptınız demektir. Tamamlanmasına vesile olur umuduyla notlar kamuya açıldı.

## Notların son durumu
Karmakarışık ve yarım

## İçindekiler ve daha içeri giremeyenler
```
------------------------[ Kernel Exploitation Notları ]-------------------------

    1  Önsöz
    2  Amaç
    3  Kaynakları edinin
    4  Lab ortamı kurulumu
    5  CTF'ler
    6  Kernel ne işe yarıyor?
        6.1  Kernel map
        6.2  Kernel 5.8'in codebase'ini biraz incelersek:
    7  Ring goygoyu
    8  Kernel Exploitation Temelleri
        8.1  Basit exploitation stratejisi - Büyük resim:
        8.2  Kernel'de nasıl zafiyetler var?
        8.3  Bu zafiyetleri nasıl sömürülür?
        8.4  Bazı kernel güvenlik önlemleri ve aşma yöntemleri
        8.5  Debugging
        8.6  Nerelerde zafiyetler var?
            8.6.1  LKM (Loadable Kernel Module)
                8.6.1.1  LKM'lerin kullanım alanları:
                8.6.1.2  LKM dosya yapısı
                8.6.1.3  LKM'lerle çalışmak için komutlar
    9  Proc cheatsheet
    10  Önemli kernel yapıları, fonksiyonlar vs. kernel v5.8 için sunulmuştur 
        10.1  task_struct: "işlem"in tanımı
        10.2  cred struct: işlemin yetkilerinin tanımı
            10.2.1  "current" makrosu: o anki koşan işleme pointer
        10.3  file, fdtable, files_struct: dosyalar
        10.4  Virtual function table (vft) yaklaşımı
        10.5  socket, sock, skb: ağ
        10.6  netlink_sock: IPC için özel soket
        10.7  Hepsi bir arada: current, task_struct, files_struct, fdtable,
        10.8  Reference counter kavramı
        10.9  Understanding page fault trace
    11  Kernel'in bellek yönetimi
        11.1  List of address types used in Linux
            11.1.1  User virtual addresses
            11.1.2  Physical addresses
            11.1.3  Bus addresses
            11.1.4  Kernel logical addresses
            11.1.5  Kernel virtual addresses
        11.2  High and Low Memory
            11.2.1  Low memory
            11.2.2  High memory
        11.3  Page Tables
        11.4  Virtual Memory Areas
        11.5  The mmap Device Operation
        11.6  Allocators
            11.6.1  Zoned page frame allocator (buddy allocator)
            11.6.2  Slab allocators
            11.6.3  İsimlendirme
                11.6.3.1  Cache
                11.6.3.2  slab
    12  Kernel'in bellek yönetimi 2 - Tanenbaum: Modern Operating Systems 2014 ch 3
        12.1  Model 1: Memory abstraction yok
        12.2  Model 2: Base ve limit register'ları ile memory abstraction
        12.3  Swapping
        12.4  Boş belleğin yönetimi
            12.4.1  bitmap ile
            12.4.2  linked list ile
        12.5  Sanal bellek (virtual memory)
            12.5.1  Paging
                12.5.1.1  page
                12.5.1.2  page frame
                12.5.1.3  page table
                12.5.1.4  page table entry
                12.5.1.5  TLB (translation lookaside buffer) 
                    12.5.1.5.1  Çalışması
                12.5.1.6  Soft miss
                12.5.1.7  hard miss
                12.5.1.8  page table walk
                12.5.1.9  minor page fault
                12.5.1.10  major page fault
                12.5.1.11  segmentation fault
                12.5.1.12  multilevel page tables
                12.5.1.13  inverted page table
                12.5.1.14  Page replacement algoritmaları
                12.5.1.15  İdeal page size
                12.5.1.16  Instruction ve data space'leri ayrı tutmak
                12.5.1.17  Shared pages ve COW (copy on write)
                12.5.1.18  Shared libraries
                12.5.1.19  Mapped files
            12.5.2  Adım adım paging
            12.5.3  Adım adım page fault handling
            12.5.4  Diske page yedekleme
            12.5.5  Segmentation
                12.5.5.1  x86-64: Segmentation artık yok
                12.5.5.2  x86: Segmentleri page'lemek
                    12.5.5.2.1  LDT (local descriptor table)
                    12.5.5.2.2  GDT (global descriptor table)
                    12.5.5.2.3  segment:offset -> fiziksel adres dönüşümü
    13  Random notes to put somewhere in the note
        13.1  KASLR -> KAISER -> PTI
        13.2  Spinlock
    14  Notes from pwn.college kernel module
        14.1  Rings
        14.2  Different types of OS models
        14.3  How kernel handles syscalls
        14.4  Kernel memory vs userspace memory
        14.5  Possible kernel attack vectors
        14.6  Kernel modules
            14.6.1  Ways to interact w/ kernel modules
            14.6.2  Syscall hooking
            14.6.3  Interrupt hooking
            14.6.4  Interation w/ modules via files
                14.6.4.1  read() and write()
                14.6.4.2  ioctl()
                14.6.4.3  Kernel Race Conditions
                14.6.4.4  On credentials
    15  Kernelde Güvenlik
        15.1  SELinux
            15.1.1  Bypassing SELinux
        15.2  SecComp
    16  Misc
        16.1  UML (user mode linux)
        16.2  Linux insides kalinan yer:
        16.3  rawsploit: libc çok büyük gelince
        16.4  AMD64 Kernel calling conventions
    17  Fuzzing
    18  Android SDK emulator kullanımı
        18.1  Start emulator
        18.2  Start gdb
        18.3  Set cpu cores to 1
    19  Rastgele Exploitation Notları
        19.1  Data-only attacks
        19.2  addr_limit on arm64
        19.3  DiShen's UAF exploitation gadget: "struct iovec"
            19.3.1  How to pwn with this?
        19.4  Always winning the races w/ userfaultfd
        19.5  seq_operations'un ilk pointer'ını ezmenin yeterli oluşu
        19.6  Stack pivot gadget'indeki adresin son 3 byte'ı 0'dan farklı olmalı
        19.7  mov rdi, rax --> mov edi, eax 'a dönüşüyor ve patlatıyor
        19.8  swapgs_restore_regs_and_return_to_usermode yerine kullanılabilecekler
    20  Exploitation cheatsheet
        20.1  Örnek kROP zincirleri
            20.1.1  Dümdüz stackoverflow
            20.1.1  Stack pivoting
```
