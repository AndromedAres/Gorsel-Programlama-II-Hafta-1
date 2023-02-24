# Gorsel-Programlama-II
Görsel Programlama II Hafta 1
//Lütfen tamamını kopyalayıp yapıştırmaktansa Form ekranını oluşturduktan sonra grup grup taşıyınız!!!
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Görsel_programlama_II_Hafta_1
{
    public partial class Form1 : Form
    {
        Color orijinalRenk = new Color();
        //form çalıştığı sürece timerı sayacak bir sayaç
        int sayac;
        public Form1()
        {
            InitializeComponent();
        }

        private void comboBox1_SelectedIndexChanged(object sender, EventArgs e)
        {
            textBox1.Text = comboBox1.SelectedIndex.ToString()
                + " "
                + comboBox1.SelectedItem.ToString()
                + " " + comboBox1.Text;
            // seçilmiş öğrenin yazısını anahtarlıyalım 
            switch (comboBox1.Text)
            {
                case "orijinal":
                    textBox1.Text = "Arkaplan orijinale dönmüştür.";
                    this.BackColor = orijinalRenk;
                    break;
                case "Kırmızı":
                    textBox1.Text = "Arkaplan Kırmızı yapılmıştır";
                    this.BackColor = Color.Red;
                    break;
                case "Yeşil":
                    textBox1.Text = "Arkaplan Yeşil yapılmıştır";
                    this.BackColor = Color.Green;
                    break;
                case "Mavi":
                    textBox1.Text = "Arkaplan Mavi yapılmıştır";
                    this.BackColor = Color.Blue;
                    break;
                case "Turuncu":
                    textBox1.Text = "Arkaplan Turuncu yapılmıştır";
                    this.BackColor = Color.Orange;
                    break;
                //diğer durumlar için
                default:
                    textBox1.Text = "Arkaplan orijinale dönmüştür.";
                    this.BackColor = orijinalRenk;
                    break;
                    
            }
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            //orjinal rengi not alalım
            orijinalRenk = this.BackColor;
            pictureBox1.Image= Resource1.anakart;
            // Görüntüyü uzatmak
            // pictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;
            // Görüntüyü Tam boyutunda büyütmek, form için kaydırma gerekbilir. Fromun AutoScroll özelliğini açabilirsiniz
            // pictureBox1.SizeMode = PictureBoxSizeMode.AutoSize;
            // Görüntünün ebatları aynı kalır ama ortasını gösterir
            // pictureBox1.SizeMode = PictureBoxSizeMode.CenterImage;
            // Görüntüyü PictureBox a boyutlar. Ölçüsünü değiştirir
            //pictureBox1.SizeMode = PictureBoxSizeMode.Zoom;
            pictureBox1.SizeMode = PictureBoxSizeMode.Zoom;
            //sayacı sıfırla
            sayac = 0;
            // timer başlat
            timer1.Start();
        }

        private void comboBox2_SelectedIndexChanged(object sender, EventArgs e)
        {
            // seçilmiş indeks değişti, seçilen PC Bileşen resmi göster
            switch (comboBox2.SelectedItem.ToString())//comboBox2.Text
            {
                case "İşlemci":
                    textBox1.Text = " İntel Core ";
                    //bu uzun hali bunun yerine kısa halini Resource'u kullanıcaz  pictureBox1.ImageLocation = "C:\\Users\\win7\\source\\repos\\Görsel programlama II Hafta 1\\Görsel programlama II Hafta 1\\Images\\islemci.jpg";
                    pictureBox1.Image = Resource1.islemci; //Location dosya konumunu verirken, Resource İmage'in kendisini verir !!!
                    break;
                case "RAM":
                    textBox1.Text = "DDR 4";
                    pictureBox1.Image = Resource1.ddr4;
                    break;
                case "Ekran Kartı":
                    textBox1.Text = "GEFORCE RTX 3090";
                    pictureBox1.Image = Resource1.geforce_rtx_3090;
                    break;
                case "Anakart":
                    textBox1.Text = "Ryzen AMD";
                    pictureBox1.Image = Resource1.anakart;
                    break;
                case "Kasa":
                    textBox1.Text = "Kasa ATX";
                    pictureBox1.Image = Resource1.kasa;
                    break;
                case "Klavye":
                    textBox1.Text = "Razer Cynosa V2";
                    pictureBox1.Image =  Resource1.klavye;
                    break;
                case "Fare":
                    textBox1.Text = "Razer Viper";
                    pictureBox1.Image = Resource1.mouse;
                    break;
                default:
                    textBox1.Text = " Ürün Bulunamadı ! ";
                    pictureBox1.Image = Resource1.yok;
                    break;
                    
            }
            sayac = 0;
           
            
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            // timer tick olduğunda sayacı arttır, yeni resim göster
            sayac++;
            // resim sayısı 7, 7. resimden sonra başa dön 0
            int resim_indisi = sayac % 7;
            //resimleri göster
            switch (resim_indisi)
            {
                case 0:
                    pictureBox1.Image = Resource1.islemci;
                    break;
                case 1:
                    pictureBox1.Image = Resource1.ddr4;
                    break;
                case 2:
                    pictureBox1.Image = Resource1.geforce_rtx_3090;
                    break;
                case 3:
                    pictureBox1.Image = Resource1.anakart;
                    break;
                case 4:
                    pictureBox1.Image = Resource1.kasa;
                    break;
                case 5:
                    pictureBox1.Image = Resource1.klavye;
                    break;
                case 6:
                    pictureBox1.Image = Resource1.mouse;
                    break;

            }
            timer1.Stop();
        }
    }

}
