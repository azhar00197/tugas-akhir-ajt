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
