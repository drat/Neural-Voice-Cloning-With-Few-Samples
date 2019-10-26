# Neural-Voice-Cloning-dengan-Beberapa-Sampel


Kami mencoba mengkloning suara untuk speaker yang kontennya independen. Ini berarti bahwa kita harus merangkum identitas pembicara daripada konten yang mereka ucapkan. Kami mencoba melakukan ini dengan membuat ruang yang disematkan speaker untuk speaker yang berbeda.

Embedding speaker mencoba untuk mewakili identitas pembicara (berbagai aspek suara seperti nada, aksen, dll dari pembicara), Anda dapat menganggap ini sebagai sidik jari suara pembicara.


Kami sekarang mengacu pada makalah berikut untuk Implementasi kami: -

- ["Kloning Suara Saraf dengan Beberapa Sampel"] (https://arxiv.org/pdf/1802.06006) oleh Baidu


### Status

Arsitektur untuk Model Multi-Speaker Generatif dan Speaker Encoder telah dibangun.

Model Multi-Speaker Generative telah dilatih untuk adaptasi speaker untuk 84 speaker menggunakan VCTK-dataset telah diselesaikan pada NVIDIA - V100 GPU selama 190000 zaman.


## Adapatation Speaker

Dataset VCTK dibagi untuk pelatihan dan pengujian: 84 pembicara digunakan untuk pelatihan
model multi-speaker, 8 speaker untuk validasi, dan 16 speaker untuk kloning.

#### Pelatihan untuk Adapatasi Pembicara

Berikut ini akan melatih model pada 84 penutur pertama dalam dataset.

`` `
python speaker_adaptation.py --data-root = <path_of_vctk_dataset> --checkpoint-dir = <path> --checkpoint-interval = <int>
`` `

Ini bisa memakan waktu hingga 20 jam menggunakan GPU.

Untuk menyesuaikan model dengan pembicara tertentu setelah pelatihan awal

`` `
python speaker_adaptation.py --data-root = <path_of_vctk_dataset> --restore-parts = <path_of_checkpoint> --checkpoint-dir = <path> --checkpoint-interval = <int>

`` `

Ini akan memakan waktu rata-rata 10 hingga 20 menit.


#### Beberapa Suara Kloning


Sejauh ini beberapa suara kerucut yang kami dapatkan menggunakan adaptasi speaker [LINK] (http://saidl.in/Neural-Voice-Cloning-With-Few-Samples/)
