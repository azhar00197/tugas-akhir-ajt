# Tugas Akhir Arsitektur Jaringan Terkini

Repositori ini dibuat dalam rangka memenuhi tugas akhir
mata kuliah Arsitektur Jaringan Komputer di Fakultas Ilmu Komputer
Universitas Brawijaya.

## Daftar Isi

- [Menyiapkan Server](#menyiapkan-server)
- [Tugas 1: Instalasi dan Konfigurasi Mininet, Ryu, dan Flow Manager](#tugas-1-instalasi-dan-konfigurasi-mininet-ryu-dan-flow-manager)
  - [Instalasi Mininet](#instalasi-mininet-dan-openflow)
  - [Instalasi Ryu](#instalasi-ryu)
  - [Instalasi Flow Manager](#instalasi-flow-manager)
- [Tugas 2: Membuat Custom Topology Mininet](#tugas-2-membuat-custom-topology-mininet)
  - [Topology 2 Host dan 2 Switch](#topology-2-host-dan-2-switch)

## Menyiapkan Server

Server dibuat menggunakan layanan <abbr title="Elastic Compute Cloud">EC2</abbr> pada [<abbr title="Amazon Web Service">AWS</abbr>](https://aws.amazon.com).

1. Memilih layanan <abbr title="Elastic Compute Cloud">EC2</abbr> pada AWS.

   ![Memilih layanan EC2](https://fikrimus35.github.io/tugas-akhir-ajt/images/001-select-ec2-service.webp)

2. Launch instance

   ![Launch instance](https://fikrimus35.github.io/tugas-akhir-ajt/images/002-launch-instance.webp)

3. Memberi nama instance **Tugas Akhir**

   ![Nama instance](https://fikrimus35.github.io/tugas-akhir-ajt/images/003-give-instance-name.webp)

4. Memilih Sistem Operasi **Ubuntu 22.04 64-bit**

   ![Memilih OS Ubuntu](https://fikrimus35.github.io/tugas-akhir-ajt/images/004-select-ubuntu-os.webp)

5. Memilih instance type **t2.medium**

   ![Memilih t2.medium](https://fikrimus35.github.io/tugas-akhir-ajt/images/005-select-t2-medium.webp)

6. Memilih pair key **vockey** yang nantinya digunakan untuk otentikasi SSH

   ![Memilih pair key](https://fikrimus35.github.io/tugas-akhir-ajt/images/006-select-vockey-key-pair.webp)

7. Mengizinkan paket SSH, HTTP, dan HTTPS agar dapat masuk ke server.

   ![Izinkan ssh, http, dan https](https://fikrimus35.github.io/tugas-akhir-ajt/images/007-grant-ssh-http-https.webp)

8. Mengkonfigurasi storage berjenis **gp3** dengan ukuran **30 GB**

   ![Konfigurasi storage](https://fikrimus35.github.io/tugas-akhir-ajt/images/008-configure-storage.webp)

9. Launching instance

   ![Launching instance](https://fikrimus35.github.io/tugas-akhir-ajt/images/009-launching-instance.webp)

10. Server **Tugas Akhir** berhasil dibuat.

    ![Server berhasil dibuat](https://fikrimus35.github.io/tugas-akhir-ajt/images/010-server-created.webp)

11. Buka konfigurasi Security Groups untuk mengizinkan input melalui port lainnya

    ![Konfigurasi Security Groups](https://fikrimus35.github.io/tugas-akhir-ajt/images/011-security-groups.webp)

12. Memilih **launch-wizard-3**, Security Group yang dipakai oleh server **Tugas Akhir**

    ![Konfigurasi launch-wizard-3](https://fikrimus35.github.io/tugas-akhir-ajt/images/012-select-security-group.webp)

13. Membuka daftar **Inbound Rules**

    ![Edit Inbound Rules](https://fikrimus35.github.io/tugas-akhir-ajt/images/013-select-inbound-rules.webp)

14. Izinkan input pada port TCP 8000 hingga 8001 dari 0.0.0.0/0

    ![Izinkan TCP 8000-8001](https://fikrimus35.github.io/tugas-akhir-ajt/images/014-grant-tcp-8000-8001.webp)

## Tugas 1: Instalasi dan Konfigurasi Mininet, Ryu, dan Flow Manager

### Instalasi Mininet dan OpenFlow

1. Clone repositori Mininet

   ![Clone mininet](https://fikrimus35.github.io/tugas-akhir-ajt/images/101-clone-mininet-repository.webp)

2. Install Mininet dan OpenFlow dengan menjalankan **install.sh** pada direktori util repositori Mininet.

   ![Install Mininet dan OpenFlow](https://fikrimus35.github.io/tugas-akhir-ajt/images/102-install-mininet.webp)

### Instalasi Ryu

1. Clone repository Ryu

   ![Clone ryu](https://fikrimus35.github.io/tugas-akhir-ajt/images/103-clone-ryu.webp)

2. Install ryu menggunakan `pip install`.

   ![Install ryu](https://fikrimus35.github.io/tugas-akhir-ajt/images/104-install-ryu.webp)

### Instalasi Flow Manager

1. Clone repository Flow Manager

   ![Clone flow manager](https://fikrimus35.github.io/tugas-akhir-ajt/images/105-clone-flow-manager.webp)

## Tugas 2: Membuat Custom Topology Mininet

### Topology 2 Host dan 2 Switch

Topologi jaringan ini terdiri atas 2 host dan 2 switch yang disusun seperti gambar berikut.

![Topology](https://fikrimus35.github.io/tugas-akhir-ajt/images/201-topology-2-host-2-switch.webp)

1. Membuat topology dengan framework mininet

   **Kode Lengkap**

   ```python
   from mininet.topo import Topo
   from mininet.log import info

   class MyTopo( Topo ):
      def addSwitch(self, name, **opts ):
         kwargs = { 'protocols' : 'OpenFlow13'}
         kwargs.update( opts )
         return super(MyTopo, self).addSwitch( name, **kwargs )
      
      def __init__( self ):
         # Inisialisasi Topology
         Topo.__init__( self )
         # Tambahkan node, switch, dan host
         info( '*** Add switches\n')
         s1 = self.addSwitch('s1')
         s2 = self.addSwitch('s2')
         # ....
         info( '*** Add hosts\n')
         h1 = self.addHost('h1', ip='10.1.0.1/24')
         h2 = self.addHost('h2', ip='10.1.0.2/24')
         # ...
         info( '*** Add links\n')
         self.addLink(s1, h1, port1=1, port2=1)
         self.addLink(s1, s2, port1=2, port2=1)
         self.addLink(s2, h2, port1=2, port2=1)
         # ....
   topos = { 'mytopo': ( lambda: MyTopo() ) }
   ```

   **Penjelasan Kode**

   ```python
   from mininet.topo import Topo
   from mininet.log import info
   ```

   Mengimport library mininet yang dibutuhkan.

   ```python
   class MyTopo( Topo ):
   ```

   Membuat class `MyTopo` dan inherit ke class `Topo`.

   ```python
   def addSwitch(self, name, **opts ):
         kwargs = { 'protocols' : 'OpenFlow13'}
         kwargs.update( opts )
         return super(MyTopo, self).addSwitch( name, **kwargs )
   ```

   Membuat fungsi `addSwitch` untuk menambahkan switch. Pada fungsi tersebut juga terdapat konfigurasi protocol yang digunakan switch, yakni OpenFlow 1.3.

   ```python
   def __init__( self ):
         # Inisialisasi Topology
         Topo.__init__( self )
         # Tambahkan node, switch, dan host
         info( '*** Add switches\n')
         s1 = self.addSwitch('s1')
         s2 = self.addSwitch('s2')
         # ....
         info( '*** Add hosts\n')
         h1 = self.addHost('h1', ip='10.1.0.1/24')
         h2 = self.addHost('h2', ip='10.1.0.2/24')
         # ...
         info( '*** Add links\n')
         self.addLink(s1, h1, port1=1, port2=1)
         self.addLink(s1, s2, port1=2, port2=1)
         self.addLink(s2, h2, port1=2, port2=1)
   ```

   Kode ini adalah constructor dari class `Mytopo`. Di dalamnya terdapat pembuatan 2 buah switch: `s1` dan `s2`, 2 host: `h1` dan `h2`, dan beberapa koneksi antar node:

   ```text
   h1(1) <--> (1)s1(2) <--> (1)s2(2) <--> (1)h2
   ```

   ```python
   topos = { 'mytopo': ( lambda: MyTopo() ) }
   ```

   Kode ini mendeklarasikan topologi yang digunakan bernama `mytopo` dan dibuat dengan menginstansiasi class `MyTopo`.

2. Menjalankan topologi

   ![Menjalankan topologi](https://fikrimus35.github.io/tugas-akhir-ajt/images/202-run-topo.webp)

3. Memasukkan flow ke masing-masing switch

   - Pada switch 1:

     - Teruskan paket dari port `1` ke port `2`

       ![Port 1 to Port 2](https://fikrimus35.github.io/tugas-akhir-ajt/images/203-flow-s1-in-1-out-2.webp)

     - Teruskan paket dari port `2` ke port `1`

       ![Port 2 to Port 1](https://fikrimus35.github.io/tugas-akhir-ajt/images/204-flow-s1-in-2-out-1.webp)

   - Pada switch 2:

     - Teruskan paket dari port `1` ke port `2`

       ![Port 1 to Port 2](https://fikrimus35.github.io/tugas-akhir-ajt/images/205-flow-s2-in-1-out-2.webp)

     - Teruskan paket dari port `2` ke port `1`

       ![Port 2 to Port 1](https://fikrimus35.github.io/tugas-akhir-ajt/images/206-flow-s2-in-2-out-1.webp)

4. Uji koneksi

   - pingall

     ![pingall](https://fikrimus35.github.io/tugas-akhir-ajt/images/207-pingall.webp)

     Semua host berhasil terkoneksi dengan bukti `0% packet dropped`

   - traceroute h1 ke h2

     ![traceroute h1 ke h2](https://fikrimus35.github.io/tugas-akhir-ajt/images/208-traceroute-h1-to-h2.webp)

     Latency `h1` ke `h2` sangat sedikit dengan nilai kurang dari 1 millisecond.
