# Linux
Linux, en çok bilinen ve en çok kullanılan açık kaynak kodlu işletim sistemidir. Diğer işletim sistemlerinden farklı olarak Linux açık kaynak kodlu bir yapıya sahiptir. Bu da işletim sistemini kullanan kişinin bilgisayarın arka planında dönen neredeyse her şeyden haberi olabileceği, işletim sistemini kendince düzenleyebileceği ve geliştirebileceği anlamına geliyor.

İşletim sistemi: Processlerimizi koşturur, dosyalarımızı dosya sisteminde tutar istediğimizde geri getirir.

HTTP: yani “Hyper Text Transfer Protocol”, web sayfalarının ağ üzerinden kullanıcıya ne şekilde aktarılacağını gösteren, ortak kullanıma açık bir iletişim protokolüdür. Aynı zamanda HTTP, istemci rolündeki bilgisayar ile sunucu arasındaki alışverişin kurallarını belirler.

pwd: bulunduğumuz directory'i gösterir
ls: dosyalari lsiteler
mkdir: klasör oluşturur
"-" ile başlayan herşey argümandır, komutun parametleridir.
ls -l: long listele
touch: touch komutu var olan dosyanın zaman damgasını değiştirir, dosya yoksa yeni bir boş dosya oluşturur.
dosya: bir çıktıdır.
echo$? : linux'un son yaptığı işlemin sonucnu döndürür. 0 dönerse başarılı 1 dönerse başarısız demektir.
cat örnek-klasör: dosyanın içeriğini gösterir.
more : Ekranda görüntüleme esnasında verilen komutun çıktısını daha dikkatli inceleyebilmek amacıyla sayfa sayfa görüntüleme özelliği sağlayan komuttur.
less: komutu, more komutuna ek özellikler de sağlayan daha gelişmiş bir diğer komuttur.
nano : notepad gibi bir editör sağlar
vi\vim: bir diğer editör 2 modu vardır okuma ve ınput ":W" yazar ":q!" çıkar ":wq" yazıp çıkar.
Ctrl L :ekranı silip başa alır

./my-prog<Input-1.txt my-proga içerğini nerden alacağini gösterir.

Linux'da herşey bir dosyadır memory, paylaşılan memory, klavye gibi

process: çalıştırılabilir birim 3'e ayrılı stdın,stdout,stderr
.\my-prog < Input-1.txt > all-output.txt 2>&1 std errleride stdouta yönlendirdi.

">>" dosya yoksa yarat varsa çıktısına ekle

ps:processleri gösterir
ps aux | grep my-prog  program ismini döker.
ctrl C: interakt sinyalı/çıkış
kill -l: bütün sinyalleri listeler.
kill -INT: 2615 processi öldür.
kill -KILL 2628 uçurur.

cd /proc/ : dosyaların tutulduğu klasör
cwd: current working directory

Ctrl D:end out stream/çıkış

echo $PATH : çalıştırlabilir uygulamalarımız bu klasörde 
pwd
/vargant/program
export PATH=$PATH:/vargant/program

not:path değişkenini mevcut path değişkeninn sonuna ekliyor.

cat etc/envoirment terminal bağımsız env. var. gelir

top:processleri lsiteliyor cpu,memeory gösterir.
htop:cpularu ayrı aurı gösterir.
ls/dev: deviceleri gsöterir.
ls -lrt > dev/null outputu uzay boşluğuna sal
tail outfiles.txt: dosyayı takip edip içini gösterir.
head -n 5 outfiles.txt: ilk 5 satırı döker
tail -n 5 outfiles.txt:son 5 satırı getirir.
tail -f : canlı olarak izler
tail-f /dev/null: bash scriptinin sonuna koyup ayakta kalamsını sağalyabiliriz.
curl:internet kaynağını eşit bir protokölle bir sürü tcp bazlı protöklle almamızı sağlar.
ls -lrt | wc -l kaç dosya var  wc:word count -l : line 
find . -name my-prog*: benim klasörümden baila my-prog la başlayan sonu nolursa olsun göster.
find . | wc -l: kaç dosya var
find . -type d: klasörleri bulur
ctrl K: ekranı sağa doğru hepsini siler
find . -type f: dosyaları bulur.
find .-name *.txt: bütün txt dosyalarını bulur
rm -i: silmeden sor
rm: sil

find . -name *.txt | while read filename ; do echo $filename ; done  : dosyaları bastırdı echo yerine rm koyarsak hepsini siler
curl https://demo.consol.io/v1/catalog/service/web?pretty | grep adress     : adresi çekti
curl https://demo.consol.io/v1/catalog/service/web?pretty | jq '.[0].Adress'  : 0. arrayin adresi
curl https://demo.consol.io/v1/catalog/service/web?pretty | jq -r '.[].Adress'  : hepsinin adresini çekti  "-r" formatlamadan gösterir.
curl https://demo.consol.io/v1/catalog/service/web?pretty | jq -r '.[].Adress' | while read serverAddr ; do curl -s $serverAddr > $serverAddr.txt; done
ls -lrt  çektiğimiz IP'nin içine "cat" diyerek içine bakarsak okuyaiblirz.
dd: blok deviclar arasında dönüşüm yapar.
dd if = /dev/null of zer-file.txt bs = 51"2 count = 2
cat ile zero-file in içine bakarsak boş
hexdump zero-file ile bakarsak 0lari görürürüz.

System over load control: Sisteme çok yüklenildiğinde devreye girer örn: %70 cpu olduğunda devreye gir.
stress: cpu'ya , memory'ye istediğimiz şeylere yük bindirir.
stress -ng -c  1 -l 40 : 1cpuya %40 yüklen.
man wondershape : komut hakkında bilgi
ifconfig: network adreslerini görüntüle
route -n : dış dünyayla ve tüm IP lere erşim
echo "gökhan,sengun,32,netas" | cut -d, f3    : e. elemanı ayırıp gösterir.
echo "gökhan,sengun,32,netas" | awk -F '{print $2, $1, $1 "is at $3 " working in $4 }'       text işleme işlemelri
\ escape eder
tree : folder structure
mv /tmp/mock.data.scv  MOCK_DATA.scv     : ilkini ikincinin üzerine yaz
~/ :ana klasöre koy
mv /users/gengun/downbloıad/ist-codes ~/
chmod 600 "filename" sadece ben okuyup yazabilirim.
nc\netcat :networkde ekrana bişeyler yazdırmak ve döktürmek, tcp sunucusuna bağlanmayı sağlar.
nc -vz www.milliyet.com.tr  : bir yere network bağlantım var mı yok mu test et  "vz" özet bilgi
netcat'in 2 modu var client ve server modu
"netstat -plnt": sunucuda çalışan ve dinlenen bütün portları gösterir.
ALT D: bir sonraki kelimeyi siler
echo "18.01.2017" | grep -E '18.01' 
echo "istanbul codes" | sed 's/istanbulş/malatya/'  textleri değiştirir  sonuna g eklersek hepsini değiştirir.
chmod u+x çalışma izni ver usera

SCP (Secure Copy - Güvenli Kopyalama): bir ağdaki iki bilgisayar arasında dosya kopyalamanızı sağlar. Bağlantı sırasında SSH kullandığı için dosya aktarımı şifreli ve güvenlidir. SCP'yi kullanabilmeniz için SSH Client (SSH istemcisi) bilgisayarınızda kurulu olmalıdır.

zgrep komutu: sıkıştırılmış olsa bile verilen bir dosyadaki ifadeleri aramak için kullanılır. grep komutu için geçerli olan tüm seçenekler zgrep komutu için de geçerlidir.

tar dosyası hazırlamanın çok basit bir mantığı vardır:"tar'lanmak" istenen dosyaları peşpeşe ekleyip tek bir dosya elde etmek. d1,d2,d3,d4,d5 isimli 5 tane dosyamız olsun.Bu dosyaları d.tar dosyasinda birleştirelim.

tar -cvf d.tar d1 d2 d3 d4 d5 

/home dizinini, içindeki dosyalar ve alt klasörleriyle beraber birleştirmek için şu komutu kullanabilirsiniz.

![tar](https://user-images.githubusercontent.com/81867200/189152686-8a107018-8ced-415f-a2d9-be9f773a242d.png)


ZIP Kullanımı
Sunucu içerisinde herhangi bir dosya veya klasörü zip haline getirmek için kullanmamız gereken komut şu şekildedir:

zip -r zipadi.zip ziplenecekdosya.uzanti veya
zip -r zipadi.zip ziplenecekklasor/ sondaki slash(/)‘a dikkat edin

Birden fazla dosya veya klasörü aynı anda zip haline getirmek için yine benzer bir mantık kullanıyoruz:

zip -r zipadi.zip ziplenecekdosya1.uzanti ziplenecekdosya2.uzanti veya
zip -r zipadi.zip klasor1/ klasor2/ veyahut
zip -r zipadi.zip dizin/icindeki/klasor1 dizin/icindeki/klasor2


tar -cvf /tmp/my_home_directory.tar /home/ecoxx 
