
# MODUL 1 DAN 2 Laporan

###### Nama : Abdi bakar djallu
###### Kelas : XII RPL 1
###### No absen : 01

# MODUL 1

![image](https://user-images.githubusercontent.com/109929708/180904293-c176a36d-669e-43e6-a205-d410dc9fd45c.png)


```
composer create-project laravel/laravel penjualan
```


# MODUL 2


# Soal nomor 1


### 1. Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam modul ini.

### Langkah pertama

Pertama kita akan membuat folder model kategori, gunakan perintah artisan pada terminal VS Code
sebagai berikut.

![image](https://user-images.githubusercontent.com/109929708/180910863-73fa24f6-5437-4da1-b669-6b9f7b5e6df7.png)

```
php artisan make:model kategori
```

### Langkah kedua

Isikan kode dibawah ke dalam file anda

```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('produk', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->integer('id_kategori');
            $table->integer('qty');
            $table->integer('harga_beli');
            $table->integer('harga_jual');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('produk');
    }
};

```

Lalu model kategori isi codingan seperti berikut 

![image](https://user-images.githubusercontent.com/109929708/180911279-86060918-13a7-4d11-9dcf-f8eb7b06f8c0.png)

### Langkah ketiga

Selanjutnya kita akan membuat create KategoriTable, dan gunkan perintah artisan di terminal
VS Code seperti dibawah ini :
![image](https://user-images.githubusercontent.com/109929708/180911576-c4db11c5-34bf-4de6-8e1c-8af79167d3a5.png)

### Langkah KeEmpat 

Selanjutnya kita isi CreaeKategoriTable seperti dibawah ini : 

```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};

```
![image](https://user-images.githubusercontent.com/109929708/180912052-4b269ad8-7c56-4849-a9f8-d19a01a42ffb.png)

### Langkah KeLima

Langkah berikutnya membuat KategoriTableSeeder, dengan menggunakan perintah artisan di terminal VS Code seperti berikut :

![image](https://user-images.githubusercontent.com/109929708/180912224-ab247ca2-3b53-4e4b-9ac9-c2e1ebe720c8.png)

### Langkah KeEnam 

Kita Tambahkan use DB; di dalam seeder kategoriTableSeeder.
Dan isi KategoriTableSeeder dengan codingan seperti berikut :
```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
                'nama' => 'Perlengkapan sekolah',
            ],
            [
                'nama' => 'Komputer',
            ],
            [
                'nama' => 'Sabun',
            ],
            [
                'nama' => 'Accesories',
            ],
            [
                'nama' => 'ATK',
            ]
    
        ));
    }
}

```
![image](https://user-images.githubusercontent.com/109929708/180912611-d122fa4c-1da4-4412-9935-522344ad35f0.png)

### Langkah KeTujuh 

Lalu kita akan menambahkan codingan di modulDatabaseSeeder seperti dibawah ini :
```
<?php

namespace Database\Seeders;

 // use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
       $this->call(produkTableSeeder::class);
       $this->call(kategoriTableSeeder::class);
    }
}

```
![image](https://user-images.githubusercontent.com/109929708/180912910-a7ae8187-738e-4b98-978b-886dd2a67e72.png)


# Soal 2

### 2.Berikan data dengan menggunakan seeder yang telah anda pelajari pada modul ini.

Seeder digunakan untuk membuat contoh daya pada database. Fitur ini sangat bermanfaat saat melakukan
pengembangan suatu sistem yang dimana kita memerlukan suatu contoh data. Apalagi ketika membutuhkan contoh data
yang banyak, fitur ini dapat membantu dari pada memasukkan data satu persatu secara manual melali PhpMyAdmin.

Secara pengertian seed dalam bahasa indonesia berarti benih. Maka sebagaimana benih, seeder dapat digunakan untuk membuat sample data atau dummy data dengan command yang sederhana. Maka anda tidak perlu repot untuk melakukan penginputan data secara berulang pada saat proses testing. Hal ini tentunya akan mempercepat proses development yang anda lakukan. Mengapa? Karena anda cukup sekali membuat “benih data” yang dapat digunakan secara berulang kali saat dibutuhkan
