# Aligned-Testnet

Gitpod: https://www.gitpod.io/ 

## Memperbarui sistem

Jalankan perintah berikut di terminal Gitpod Anda:

```bash
sudo apt update -y
sudo apt upgrade -y
```

## Menginstal curl

Jalankan perintah berikut di terminal Gitpod Anda:

```bash
sudo apt-get install curl -y
```

## Menginstal OpenSSL 3.0.0

Jalankan perintah berikut di terminal Gitpod Anda:

```bash
sudo apt-get install -y build-essential checkinstall zlib1g-dev
cd /usr/local/src
sudo wget https://www.openssl.org/source/openssl-3.0.0.tar.gz
sudo tar -zxf openssl-3.0.0.tar.gz
cd openssl-3.0.0
sudo ./config
sudo make
sudo make install
sudo ldconfig
```

## Mengunduh dan menginstal AlignedProof

Jalankan perintah berikut di terminal Gitpod Anda:

```bash
curl -L https://raw.githubusercontent.com/yetanotherco/aligned_layer/main/batcher/aligned/install_aligned.sh | bash
```

## Menambahkan direktori bin AlignedProof ke PATH

Jalankan perintah berikut di terminal Gitpod Anda:

```bash
echo "export PATH=\"\$PATH:$HOME/.aligned/bin\"" >> "$HOME/.bashrc"
source "$HOME/.bashrc"
```

Jika perintah `source` tidak berfungsi di Gitpod, Anda mungkin perlu membuka terminal baru atau memulai ulang workspace Anda untuk memperbarui variabel lingkungan.

## Mengunduh file bukti contoh dan mengirimkannya

Jalankan perintah berikut di terminal Gitpod Anda:

```bash
curl -L https://raw.githubusercontent.com/yetanotherco/aligned_layer/main/batcher/aligned/get_proof_test_files.sh | bash
rm -rf ~/aligned_verification_data/
aligned submit \
--proving_system SP1 \
--proof ~/.aligned/test_files/sp1_fibonacci.proof \
--vm_program ~/.aligned/test_files/sp1_fibonacci-elf \
--aligned_verification_data_path ~/aligned_verification_data \
--conn wss://batcher.alignedlayer.com
```

## Memverifikasi bukti di rantai

Jalankan perintah berikut di terminal Gitpod Anda:

```bash
aligned verify-proof-onchain \
--aligned-verification-data ~/aligned_verification_data/*.json \
--rpc https://ethereum-holesky-rpc.publicnode.com \
--chain holesky
```

Harap dicatat bahwa Anda harus memahami apa yang dilakukan skrip ini sebelum menjalankannya, karena menjalankan skrip yang tidak Anda pahami dapat berpotensi merusak sistem Anda atau merusak keamanan Anda.

