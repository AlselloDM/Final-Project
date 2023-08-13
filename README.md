<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/AlselloDM/Final-Project">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Credit-Risk-Prediction</h3>

  <p align="center">
    Notebook Final project Hacktiv8 HCK-006 Alsello Diveni Manuputty
    <br />
    <a href="https://github.com/AlselloDM/Final-Project"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/AlselloDM/Final-Project">View Demo</a>
    ·
    <a href="https://github.com/AlselloDM/Final-Project/issues">Report Bug</a>
    ·
    <a href="https://github.com/AlselloDM/Final-Project/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## Objective

[![Product Name Screen Shot][product-screenshot]](https://example.com)

Pada notebook ini akan dilakukan pengerjaan Final Project dimana akan dibuat model *Classification* untuk memprediksi `status` resiko hutang menggunakan dataset dari [link](https://www.kaggle.com/datasets/ranadeep/credit-risk-dataset) ini. Pada kasus ini, analis ditugaskan untuk membuatkan sebuah model untuk memprediksi dari data yang berisi informasi umum dari *`debitur`*. Karena resiko salah klasifikasi sangat fatal, maka perlu dilakukan *modelling* dengan berusaha untuk meningkatkan *`accuracy`* model. Namun, dari hasil screening awal ternyata proporsi datanya tidak setara. Hal ini akan menjadi masalah nantinya saat pembuatan model. Dengan model ini, diharapkan bank bisa meringankan kerja tim analisis resiko dalam proses screening dan bisa mengarahkan energi yang tersisa ke pekerjaan lain yang memang butuh seorang manusia untuk melakukannya.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Proses Pengerjaan

Urutan pengerjaannya adalah sebagai berikut

### Prerequisites

Beberapa library yang perlu di-install dahulu.
* pandas
  ```sh
  !pip install pandas
  ```
  * seaborn
  ```sh
  !pip install seaborn
  ```
  * matplotlib
  ```sh
  !pip install matplotlib
  ```
  * numpy
  ```sh
  !pip install numpy
  ```
  * Scikit-learn
  ```sh
  !pip install scikit-learn
  ```
  * feature-engine
  ```sh
  !pip install feature_engine
  ```
### Data Loading
Setelah sudah di-import, langsung saja akan dilakukan loading data. Pada bagian ini juga akan digunakan serangkaian cara untuk mendapatkan overview data.
Pada bagian ini juga digunakan domain knowledge sebagai filter data karena kolom terdiri dari 2 int, 49 float dan 22 object type features.
Sampai akhirnya berikut adalah data-data yang dipilih:
| Column Name      			| Explanation                                                            |
|---------------------------|------------------------------------------------------------------------|
| addr_state				| Area domisili bisa memberi pengaruh kepada pembayaran hutang berdasarkan kondisi ekonomi, lapangan pekerjaan, dsb.       |
| annual_inc       			| Pendapatan debitur adalah faktor penting dalam menilai kemampuan pembayarannya.  |
| application_type 			| Perbedaan tipe aplikasi seperti individual atau joint memiliki kemungkinan berpengaruh terhadap resiko.     |
| delinq_2yrs	   			| Jumlah kategori pembayaran 'delinquent' dalam 2 tahun kebelakang bisa menentukan pola kebiasaan membayar debitur.|
| dti	   					| Rasio Debt-to-Income dapat mengukur kestabilan finansial debitur.													|
| emp_length	   			| Lama bekerja debitur bisa mengukur kestabilan pekerjaan yang berpengaruh kepada kemampuan membayarnya				|
| grade	   					| Penggolongan grade adalah penilaian resiko kredit dari kreditur 
|          					|Grade A: Resiko rendah, diprediksi menguntungkan dan debitur dengan kekuatan finansial yang baik.
|          					|Grade B: Resiko menengah dengan status kredit yang baik.
|          					|Grade C: Resiko menengah hingga tinggi dengan beberapa indikator kredit beresiko.
|          					|Grade D: Resiko tinggi dengan profil kredit yang lebih lemah.
|          					|Grade E: Resiko tinggi dengan riwayat kredit terbatas atau memiliki indikator kredit beresiko dalam jumlah tinggi.
|          					|Grade F: Resiko tinggi dengan riwayat kredit yang buruk seperti jumlah hutang yang tinggi, dan pembayaran yang terlambat
|          					|Grade G: Resiko tertinggi dengan riwayat kredit yang sangat buruk dan masalah kredit lainnya yang lebih berat.
| home_ownership			| Dapat menggambarkan kestabilan situasi finansial debitur.
| inq_last_6mths	   		| Menggambarkan aktivitas kredit debitur belakangan ini.
| int_rate	   				| Dapat berkorelasi dengan tingkat resiko debitur.
| purpose	   				| Dapat memprediksi komitmen membayar debitur.
| revol_util	   			| Menunjukan berapa kredit yang tersedia untuk debitur
| term	   					| Dapat berpengaruh ke kemampuan debitur dalam mengelola pembayaran.
| total_acc	   				| Jumlah total pinjaman dapat memberikan informasi mengenai riwayat kredit debitur.
| acc_now_delinq	   		| Jumlah akun yang saat ini menunggak dapat mengindikasikan masalah kredit yang sedang berlangsung.
| tot_cur_bal	   			| Dapat mencerminkan beban kredit peminjam secara keseluruhan.
| pub_rec					| Jumlah catatan publik seperti bangkrut, repo, pajak dapat mempengaruhi kelayakan kredit.
| mths_since_last_delinq	| Dapat menggambarkan kebiasaan membayar debitur belakangan ini.
| mths_since_last_record	| Dapat menggambarkan resiko kredit
| total_pymnt	 			| Menggambarkan riwayat pembayaran.
| open_acc	   				| Dapat mengindikasikan aktivitas kredit debitur.
| collections_12_mths_ex_med| Dapat menggambarkan masalah kredit belakangan ini.
| loan_amnt	   				| Mungkin berkorelasi dengan resiko itu sendiri.
| recoveries	   			| Mungkin berkorelasi dengan kredit macet(Default)
| verification_status	  	| Dapat mengindikasikan keaslian laporan keuangan debitur.
| loan_status				| Target Prediksi
<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3
    - [ ] Nested Feature

See the [open issues](https://github.com/github_username/repo_name/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Your Name - [@twitter_handle](https://twitter.com/twitter_handle) - email@email_client.com

Project Link: [https://github.com/github_username/repo_name](https://github.com/github_username/repo_name)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* []()
* []()
* []()

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/AlselloDM/Final-Project.svg?style=for-the-badge
[contributors-url]: https://github.com/AlselloDM/Final-Project/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/alsellodm/
[product-screenshot]: images/screenshot.png
