<h2> GIT KOMUTLARI </h2>

Git bir sürüm kontrol sistemidir. Üzerinde çalıştığımız kodun eski ve yeni versiyonlarına ulaşmamızı sağlar. Projede hangi değişikliklerin yapıldığını ve kimler tarafından yapıldığını kontrol etmemizi sağlar. 
Şimdi git versiyonlama sisteminde kullanılan yaygın komutları inceleyelim.

Git sisteminde işlem yapmaya başlamadan önce e-posta ve kullanıcı adı yapılandırması yapılmalıdır.

```ini
  git config --global user.name "hediyeorhan"
  git config --global user.email hediyeorhan2015@gmail.com # kullanıcı adınızı ve e-posta adresinizi buraya ekleyin.
  ```

Öncelikle yerel dizinimizde üzerinde çalışacağımız projede aşağıda verilen komut ile bir git klasörü oluşturuyoruz.

```ini
  git init # başlatma
  ```

Daha sonra projeye dosya eklemek istersek ***touch*** komutu ile dosya ekleyebiliriz.

```ini
  touch add_file # dosya oluşturma.
  mkdir folder # klasör oluşturma.
  ```

Bu ve benzeri değişiklikleri projede kalıcı hale getirmek için git add komutunu kullanıyoruz. Add komutu tüm dosyaları geçiş bölgesine yükler.

```ini
  git add . # tüm dosyaları ekler.
  git add add_file # özellikle belirttiğimiz dosyayı ekler.
  ```

Dosyaları ekledikten sonra, bu dosyalara bir commit mesajı yazılmalıdır.

```ini
  git commit -m "commit message"
  ```

add ve commit komutlarını tek bir satırda çalıştırmak için :

```ini
  git commit -am "commit message"
  ```

***rm*** komutu dizindeki dosyaları siler, ***mv*** komutu dosya adını değiştirir. Dosyaları taşımak için kullanılır.

Eğer dosyaları git add komutu ile ekledikten sonra geri almak istiyorsak:

```ini
  git reset HEAD filename
  git checkout --filename
  ```

Git'te ***status*** komutu, projede işlenmemiş bir değişiklik olup olmadığını kontrol etmek için kullanılır.

```ini
  git status # Shows current git status. It shows if the current directory is linked to any git.
  ```

Log komutu, commit mesajlarının kim tarafından ve ne zaman yapıldığını görmek için kullanılır.

```ini
  git log
  ```

Eski commit sürümüne dönmek için log komutu ile commitleri listeleyebilir ve ardından commit hash kodunu alarak o commit'e dönebilirsiniz.

Hash kodu: Her commit'in kendi numarası vardır.

```ini
  git log
  git checkout version_hash_code
  git commit -m "old version copied"
  ```

Yerel dizinimizde bulunan ve github'a yüklemek istemediğimiz dosyaları gizlemek için bir .gitignore dosyası oluşturulmalıdır. Daha sonra gizlemek istediğimiz dosyaları .gitignore içine yazıyoruz.

```ini
  touch .gitignore # kullandığınız teknolojiye göre .gitignore şablonlarını Google'da bulabilirsiniz.
  ```

Eğer .gitignore dosyamıza eklediğimiz dosyalar gizli değilse ve github'a yükleniyorsa, : 

```ini
  git rm --cached file_name
  git commit -m "cache cleared"
  ```

***"Branch"*** projenin farklı geliştirme yollarını temsil eden bağımsız çalışma alanlarıdır. Branch'ler, projenin farklı özelliklerini veya geliştirmelerini izlemek ve test etmek veya farklı ekiplerin farklı görevler üzerinde çalışmasına izin vermek için kullanılır.

Head, hangi branch'te ve hangi commit üzerinde olduğumuzu gösterir / işaret eder.

Yeni bir branch oluşturma :

```ini
  git branch new_branch_name
  ```

Bulunulan branch'i değiştirme :

```ini
  git switch branch_name
  ```

İki branch'i birleştirme

```ini
  git switch branch1  # branch1'e girdik ve branch2 ile birleştirdik.
  git merge branch2
  ```

Mevcut branch'leri listeleme : 

```ini
  git branch # hangi branch içerisinde olduğumuz '*' ile belirtir.
  ```

Her branch'te oluşturulan dosyalar/klasörler o branch'e aittir. Birleştirilmediği takdirde diğer branch'ler tarafından erişilemezler. 
Farklı branch'lerdeki commitler de birbirlerine görünmezler.

Fast forwarding: Ana branch'ten türetilen/oluşturulan bir branch'ta yapılan değişikliklerin ana branch'a merge edilmesi işlemidir.

***Her iki branch'te çakışan kodlar olduğunda: master branch'te iken diğer branch merge edildiğinde, diğer branch'teki değişiklikler master branch'teki dosyaya yazılır.***

Master'da silinen bir dosya diğer branch'te değiştirilip merge yapılmak istendiğinde master'da dosya olmadığı için ***merge conflic*** durumu ortaya çıkıyor.

***!!! Herhangi iki branch'i birleştirmek için çakışma olmaması gerekir.***

Dosyayı son işlemden geri yüklemek için :

```ini
  git restore filename
  ```

Git, kendi üzerine eklenmeyen ve commit edilmeyen değişiklikleri ***stash*** ile saklayabilir. Bu şekilde yapıldığında değişiklikler ***git status*** komutu ile görünmez.
Git bunu kendi içinde saklar ve biz istediğimiz zaman geri alabiliriz.

```ini
  git stash 
  ```

Git stash'ta saklanan bilgileri projemizdeki dosyalara geri almak için :

```ini
  git stash pop  # geri getirir ve listeden siler.
  ```

Bir satırda farklı değişiklikler yapıldığında, tüm stash'ler listelenir ve id'lerde tutulur.

```ini
  git stash list  # stash listesini gösterir.
  ```

Stash'leri tek tek eklemek istersek :

```ini
  git stash apply stash_id  # listeden silmez.
  ```

Tüm stash'leri temizleme : 

```ini
  git stash clear
  ```

<h3> Geçmiş commit'lere geri dönme </h3>

Eski bir commit'e geri dönmek için : 

```ini
  git log # buradan, istenen commit'in hash kodu elde edilebilir.
  git checkout commit_hash_code
  ```

Eski bir işleme geri dönüldüğünde, master branch yerine ***'HEAD detached'*** branch'ına geçilir.
***git switch*** komutu ile master branch'e geri dönebilirsiniz. Ya da yeni bir branch oluşturulabilir ve eski commit'in düzenlemeleri burada tutulabilir.

Sadece bir adım önceki commit'e dönmek için :

```ini
  git reset HEAD~1
  ```

Belirtilen commit'ten sonraki tüm commit'leri ***git log*** geçmişinden silmek için ***reset*** komutu kullanılabilir. Ancak bu komut sadece commit geçmişinden commitleri siler ve projede silinen commitler üzerinde yapılan değişiklikleri silmez.

```ini
  git reset commit_hash_code
  ```

Projede ***hard*** parametresi ile silinen commitler tarafından yapılan değişiklikler de silinebilir.

```ini
  git reset --hard commit_hash_code
  ```

***revert*** komutu commitleri commit geçmişinde tutmak ve değişiklikleri projeden silmek için kullanılır. Değişiklikleri geri alır ve yeni bir commit oluşturur. Bu komut ***git log*** geçmişindeki commitleri silmez.

```ini
  git revert commit_hash_code  # proje bu commit'i geri alır.
  ```

İki işlem arasındaki veya bir projedeki değişiklikleri/farklılıkları görmek için :

```ini
  git diff HEAD # son commit'e göre farkı gösterir.

  git diff commit1_hash_code commit2_hash_code # iki commit arasındaki farkı gösterir.

  git diff commit1_hash_code : commit2_hash_code # bu şekilde de kullanılabilir.
  ```

İki branch arasındaki farkı görmek için : 

```ini
  git diff branch1_name branch2_name

  git diff branch1_name : branch2_name
  ```

Logları temizlemek, tarihi yeniden yazmak ve aradaki merge commit'lerden kurtulmak için :

```ini
  git switch branch1_name
  git rebase branch2_name  # önce branch2'deki commitler sıralanır, ardından branch1'deki commitler sıralanır.
  ```

<h3> Projenin Github'a yüklenmesi </h3>

Local projemizi Github'a yüklemek için öncelikle bir github reposu oluşturulmalıdır. Sonrasında git status ile projede yaptığımız ekleme ve commitlerin güncelliğini kontrol edebiliriz. 
Oluşturduğumuz repoya uzaktan bağlanmak için ***remote*** komutu kullanılmalıdır.

```ini
  git remote add origin github_repo_url.git # "origin" terimi, daha sonraki komutlarda daha kolay kullanım için repo url'sini temsil eder. 
  ```

Uzak bağlantı kurulduktan sonra local dosyalarımızı github'a yüklemek için ***push*** komutu kullanılır.

```ini
  git push -u origin main # branch adınız farklıysa değiştirilebilir. Örneğin: master, feat ...
  ```

Burada ***push*** komutu çalıştırıldığında terminal ekranından veya tarayıcıdan github hesabınıza giriş yapmanız istenir.

Eğer main/master branch push edilecekse sadece ***git push*** komutu yeterli olacaktır. Eğer farklı bir branch push edilecekse ***git push origin branch_name*** komutu kullanılmalıdır.

***PULL REQUEST***

Başkasına ait bir repoyu değiştirme isteğidir. Ya da başkasının bana ait olan bir repoyu değiştirme isteğidir.

Github üzerindeki projede yaptığımız değişiklikleri local üzerinde görebilmek için projeyi local'e çekmemiz gerekiyor. 
Github üzerindeki branch'ler remote branch olarak kabul edilir. Bu branch'leri listelemek için :

```ini
  git branch -r 
  ```

Projenin son sürümünü github'dan local'e çekmek için :

```ini
  git fetch # merge istenmediğinde kullanılabilir.
  ```

Remote branch'ler arasında gezinmek için :

```ini
  git checkout origin/branch_name
  ```

Github'dan lokalleştirdiğimiz projenin güncel versiyonunu birleştirmek için :

```ini
  git pull 
  ```

***git pull = git fetch + git merge***

***push -> Github'a gönderme.***

***pull -> Github'dan çekme.***

Başkasına ait bir repoyu çekip üzerinde değişiklik yapmak için Github üzerinde o repoyu ***fork*** etmemiz gerekiyor ki kendi repolarımız arasında listelensin. Daha sonra kendi repolarımız arasından url adresini alarak local repomuza klonlamalıyız.

```ini
  git clone repo_url.git # repo'yu local'e çekme.
  ```

***Repoyu bu şekilde push ve pull edebiliriz.***