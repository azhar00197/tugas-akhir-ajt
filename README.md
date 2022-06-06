# Tugas Akhir Arsitektur Jaringan Terkini

Repositori ini dibuat dalam rangka memenuhi tugas akhir
mata kuliah Arsitektur Jaringan Komputer di Fakultas Ilmu Komputer
Universitas Brawijaya.

## Daftar Isi

- [Menyiapkan Server](#menyiapkan-server)
- [Tugas 1: Instalasi dan Konfigurasi Mininet dan Ryu](#tugas-1-instalasi-dan-konfigurasi-mininet-dan-ryu)

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

## Tugas 1: Instalasi dan Konfigurasi Mininet dan Ryu
