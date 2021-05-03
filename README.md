# GIT KULLANIMI

## Versiyon Kontrol Sistemi (Version Control System)

İki farklı yaklaşım vardır.

![Centralized Version Control](/assets/centralizedversioncontrol.jpg) ![Distributed Version Control](/assets/distributedversioncontrol.jpg)

[KAYNAK](https://homes.cs.washington.edu/~mernst/advice/version-control.html)

## GIT File Workflow

![Git File Workflow](/assets/gitfileworkflow.jpg)

[KAYNAK](https://www.c-sharpcorner.com/article/git-and-github-version-control-local-and-remote-repository/)

## Merge ve Merge Çeşitleri

Birleştirilmek istenen iki branch commitlerinin tarihçesi incelendiğinde bu dalların zamanında bir noktada ortak bir commit bilgisine sahip oldukları görülecektir. Bu durum tespit edilir.

Birleştirilmek istenen iki branch içerisindeki son değişiklikleri yansıtan commitler tespit edilir.

Bu bilgilere göre merge işleminin ne çeşit bir yapı içerisinde gerçekleşeceği tespit edilir.

### **1. Fast Forward Merge:**

Birleştirilmek istenen hedef branch üzerinde herhangi bir değişiklik yapılmamıştır. Hedef dalın son commit bilgisi ile kaynak dalın yani birleştirilmek istenen commit'in ilk commit bilgisi aynıdır. Bu ortak commit bilgisi dışında kalan commit bilgilerini kaynak branch üzerinden hedef branch üzerine peşisıra ekler. Bu merge türüne Fast Forward Merge denilir.

![before ff](/assets/ffmergev2.jpg)

### **2. No Fast Forward Merge**

![no-ff](/assets/noffmerge.jpg)

### **3. 3 Way Merge (Automatic Merge)**

![Before Merging](/assets/3waymergev2.jpg)
[Kaynak](https://www.atlassian.com/git/tutorials/using-branches/git-merge)

## REBASE KAVRAMI

![Rebase](/assets/rebase.jpg)

`git rebase <targetbranch>`komutu ile uygulanır.

## GIT ile ilgili Kısa bilgiler

Git kurulumu için [Git page](https://git-scm.com/)

SCI (Software Configuration Items)

SCM (Software Configuration Management)

VCS (Version Control System / Revision Control)

Git branch oluşturmada proje dosyalarının birer kopyalarını oluşturmayp sadece işaretçi (HEAD) bir kopyası oluşturulduğu için git branch dosyası disk kapasite kullanımı ve branch oluşturma süresi açısından düşük maliyetlidir.

>`git --version` git versiyon numarasını görüntüler.

>`C:\Program Files<(x86)>\Git\etc\gitconfig`==>`git config --system`komutu ile kullanılan config dosyasının yoludur. git'in install edildiği klasördür. 32 bit install edildi ise`Program Files(x86)`klasörü içerisindedir.

>`C:\Users\<userame>\.gitconfig`==>`git config --global`komutu ile kullanılan config dosyasının yoludur.

>`.git/config`==>`git config`komutu ile kullanılan config dosyasının yoludur. aktif dizin içerisinde bulunan gizli`.git`klasörü içerisinde yer alır.

>`.gitignore`dosyası oluşturmak için gerekli syntax bilgisi için *[globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming))*<br/>Örnek git`.gitignore`dosyaları için -> [github/gitignore ](https://github.com/github/gitignore).


## CONFIGURASYON

|<div style="width:450px">Komut</div>|İşlevi|
|-|-|
|`git <command> --help`|komut hakkında yardım için kullanılır.|
|`git config --global --list`|git ayarlarını listelemek için gerekli komut|
|`git config --global user.name "name"`|kullanıcı adı konfigurasyonu.`commit`komutu ile versiyon bilgilerini kayıt altına alırken bilgi amaçlı olarak kullanılır.|
|`git config --global user.email "email@email.com"`|email konfigurasyonu.`commit`komutu ile versiyon bilgilerini kayıt altına alırken bilgi amaçlı olarak kullanılır.|
|`git config --global --unset user.name`| user.name key bilgisini siler.|
|`git config --global init.defaultBranch master`|Default branch ismi|
|`git config --global core.editor "'path\sublime_text.exe'"`|Editör seçimi|
|`git config --global mergetool.keepBackup false`|git diff aracı çalıştırıldığında bağzı dosyalar oluşturulur. çakışmalar çözülüp merge işlemi bitirilse bile bu dosyalar silinmez. Bu durumu değiştirmek için bu config ayarı kullanılır. git difftool komutu ile çalıştırıalcak 3rd uygulamaların geçici dosyalar bu kapsamda değildir. |
|`git config --global core.excludesFile "path\.gitignore'"`|Global olarak .gitignore dosyasının gösterilmesi|
|`git config --global diff.tool "path\p4merge"`|difftool olarak p4merge programının belirlenmesi.|
|`git config --global merge.tool "path\p4merge"`|merge tool olarak p4merge programının belirlenmesi.|
|`git config --global alias.his "log --all --oneline --graph --decorate"`|alias verilerek`git his`komutu ile`git log --all --oneline --graph --decorate`komutuna atıfta bulunmak ve kısa komut ile çalıştırılaması|
|`git config --system -e`<br/>`git config --system --edit`| --system config dosyasını editör ile açar.|
|`git config --global -e`| --global config dosyasını editör ile açar.|
|`git config -e`| aktif dizin içerisindeki config dosyasını editör ile açar.|
|`git config gc.pruneExpire "60 days"`| git reset komutu ile silinen commitler default 30 gün daha .git veritabanı içerisinde korunur. Bu süreyi değiştirmek için kullanılan komuttur.|

## GIT KOMUTLARI

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|`git init`| Projenizin olduğu klasörü bir git reposu olarak işaretlemek |
|`git status`| commit edilmemiş yeni veya güncellenen dosyaları listeler. |
|`git add <file_name>`| Stageing Area ya dosyaları eklemek |
|`git add .`<br/>`git add --all`<br/>`git add -A`| Stageing Area ya dosyaları toplu olarak eklemek |
|`git rm --cached <file_name>`| Staging Area'dan tekrar Untracked files alanına dosyayı geri göndermek. Daha önce commit içerisinde varolan ve`.gitignore`dosyasına eklenmesine rağmen izlenen dosyalarda bu komut ile izlenme listesinden çıkarılmalıdır. Ancak ondan sonra .gitignore dosyasındaki ayar aktif olacaktır. |
|`git restore <filename>`| commit yapılmadan önce değişiklikleri iptal etmek için kullanılır. file olarak belirtilen dosyadaki değişiklikleri iptal eder. Bütün değişiklikleri iptal için`.`kullanılabilir. Şart olarak Staging Area`<filename>`eklenmemiş olası gerekir. (destructive - hasar veren komut. bir onay mekanizması yoktur. Geri dönülemez sonuçlar doğurur.) |
|`git checkout <filename>`| Yukarıdaki restore işlemine benzer bir işlem yapar. commit yapılmadan önce değişiklikleri iptal etmek için kullanılır. file olarak belirtilen dosyadaki değişiklikleri iptal eder. Bütün değişiklikleri iptal için`.`kullanılabilir. Şart olarak Staging Area`<filename>`eklenmemiş olası gerekir. (destructive - hasar veren komut. bir onay mekanizması yoktur. Geri dönülemez sonuçlar doğurur.)|
|`git checkout -- <filename>`| Yukarıdaki restore işlemine benzer bir işlem yapar. commit yapılmadan önce değişiklikleri iptal etmek için kullanılır. file olarak belirtilen dosyadaki değişiklikleri iptal eder. Bütün değişiklikleri iptal için`.`kullanılabilir. Şart olarak Staging Area`<filename>`eklenmemiş olası gerekir. (destructive - hasar veren komut. bir onay mekanizması yoktur. Geri dönülemez sonuçlar doğurur.) |
|`git checkout -q <filename>`| Yukarıdaki restor işlemine benzer bir işlem yapar. commit yapılmadan önce değişiklikleri iptal etmek için kullanılır. file olarak belirtilen dosyadaki değişiklikleri iptal eder. Bütün değişiklikleri iptal için`.`kullanılabilir. Şart olarak Staging Area`<filename>`eklenmemiş olası gerekir. (destructive - hasar veren komut. bir onay mekanizması yoktur. Geri dönülemez sonuçlar doğurur.)|
|`git reset`| Staging Area'dan tekrar Untracked files alanına dosyaları geri göndermek için kullanılır. Commit yapılmadan değişiklik öncesi aktif branch'i geri yükler. reset modu yazılı değilse`--mixed`olarak işlem yapacaktır. |
|`git reset <filename>`|`<filename>`olarak belirtilen dosyanın Staging Area'dan tekrar Untracked files alanına dosyayı geri göndermek için kullanılır. (destructive - hasar veren komut. bir onay mekanizması yoktur. Geri dönülemez sonuçlar doğurur.)|
|`git reset --hard`| En son commit bilgilerini (HEAD olarak işaretli commiti) geri yükler. Son commit'e geri döndürmek için kullanılır. (destructive - hasar veren komut. bir onay mekanizması yoktur. Geri dönülemez sonuçlar doğurur.)|
|`git reset --hard <_hash_>`| istenmeyen bir commit yapıldı ise önceki commitin hash bilgisine geri dönülmek istendiğinde kullanılır. (destructive - hasar veren komut. bir onay mekanizması yoktur. Geri dönülemez sonuçlar doğurur.)|
|`git reset --mixed <hash>`|`<hash>`belirtilen commit bilgisine kadar olan commitler değişiklikler korunarak geri dönülür. belirtilen commit bilgisinden sonra yapılan commitler birleştirilir ve tek bir commit haline getirilir. |
|`git config gc.pruneExpire "60 days"`| git reset komutu ile silinen commitler default 30 gün daha .git veritabanı içerisinde korunur. Bu süreyi değiştirmek için kullanılan komuttur.|
|`git fsck --lost-found`| Silinen commitlerin listesini verir. Sahipsiz commitlerde denilebilir. |
|`git merge <deletecommithash>`|`<deletecommithash>`olarak belirtilen silinmiş commit bilgisini geri getirir ve aktif branch ile birleştirir. |
|`git commit`| Açıklama gitmek için metin editörü çalıştırır. Bir satırdan fazla bir açılama girilecek ise bu şekilde -m parametresiz kullanılmalıdır. GIT 50/72 kuralı unutulmamalıdır. İlk satırda değişikliği özetleyen ve en fazla 50 karakter uzunluğunda bir metin olmalıdır. Ayrıntılarıda ilk satırdan sonra boş bir satır bırakarak ve her biri en fazla 72 karakter uzunluğunda istediğiniz sayıda satır olarak ekleyebilirsiniz.|
|`git commit -m "description"`|  Versiyon ile ilgili açıklama -m seçeneği ile doğrudan komut satırından verilir. |
|`git commit -a -m "description"`<br/>`git commit -am "description"`|  Versiyon ile ilgili açıklama -m seçeneği ile doğrudan komut satırından verilir. -a parametresi ile bütün değişiklikler Staging Area alınarak commit işlemi yapılır. |
|`git commit -m "description" --signoff`| Lunix geliştiricileri için kullanılan ve telif hakları ile ilgili bir imzayı açıklamaya ek bir satır`Signed-off-by: <username> <mail>`olarak ekler. |
|`git revert <hash>`|`<hash>`olarak belirtilen commit işlemini geri alır. Geri alıp yeni bir commit olarak gönderir. Bu işlemi yaparken en son committen geriye doğru işlem yapılmalıdır. restore ve reset işleminden farkı commit edilmiş bir değişikliğin geri alınması ve yeni bir commit olarak gönderilmesini sağlar.  |
|`git log`| Commit tarihçesini/geçmişini kısa açıklamaları ile listeler. liste uzun olduğunda boşluk tuşu ile sayfalamalar arasında geçiş yapılır. log sonunda`q`ile çıkılacaktır. |
|`git log -n 2`| Aktif branchdeki son 2 commit bilgilerini gösterir. |
|`git log --oneline`| Commit tarihçesinin her commit tek satır olacak şekilde listeler. |
|`git log --oneline --graph`| Commit tarihçesinin her commit tek satır olacak şekilde grafik olarak listeler. |
|`git log -p`| Commit tarihçesini/geçmişini bir önceki commit'e göre nelerin değiştiğini detaylı bir şekilde görmek için kullanılır. |
|`git show`| Commit tarihçesini/geçmişini geniş açıklamalı olarak detayını göstermek için kullanılır. |
|`git show <hash>`|`<hash>`bilgisi girilmiş commit'in detaylarını gösterir. |
|`git show <tanname>`|`<tanname>`bilgisi girilmiş commit'in detaylarını gösterir. |

## GIT BRANCH

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|`git help branch`<br/>`git branch --help`| Branch komutu için açıklamalı yardım görüntüler. |
|`git branch`| Local (yerel) Branch (Dal) ları listeler |
|`git branch --list`|  Local (yerel) Branch (Dal) ları listeler |
|`git branch -v`| Son commit mesajını gösterecek şekilde branchleri listeler |
|`git branch -a`| local ve remote bütün branchleri listeler |
|`git branch -r`| Remote olarak aktif olan branchlerleri gösterir |
|`git branch --delete <branchname>`<br/>`git branch -d <branchname>`| local ve remote bütün branchleri listeler |
|`git remote show origin`| Remote olarak aktif olan branchler hakkında detaylı bilgi verir. |
|`git remote update --prune origin`| Remote olarak aktif olan branchlerleri senkronize eder. |
|`git remote update -p`| Remote olarak aktif olan branchlerleri senkronize eder. |
|`git branch <new_branch_name>`| Yeni branch oluşturur. |
|`git checkout <branchname>`|`<branchname>`olarak belirtilen branche geçer. |
|`git checkout -b <new_branch_name>`| yeni bir branch yaratır ve o branch aktif branch olarak seçilir. |
|`git branch -d <branch_name>`| Silinmek istenen branch ismi girlerek branch silinir. Dikkat edilmesi gereken silinmek istenen branch aktif branch olmamalıdır. |
|`git push -u origin <branch_name>`| yeni oluşturulan branch içerisinde bir değişiklik, bir dosya eklendisi olmasa dahi uzak repository ye entegre etmek için kullanılır.`-u`parametresi ilk defa senkronizasyon yapılacak ise kullanılmalıdır. Sonrasında`-u`parametresine gerek yoktur. |
|`git stash`| Stageing Area ya alınmış ve commit edilmemiş değişiklikleri korumak için rafa kaldırır. Stack (yığın) mantığı ile çalışır. Son giren ilk çıkar mantığı ile çalışır.|
|`git stash push -u -m "<description>"`| Stageing Area ya alınmış ve commit edilmemiş değişiklikleri korumak için rafa kaldırır. Stack (yığın) mantığı ile çalışır. Untracked files olarak belirtilen ve projeye yeni eklenmiş ama izlenmeyen dosyalarıda rafa kaldırır. Bunu`-u`parametresi ile uygular.`-m`stash e bir açıklama eklemek için kullanılır.`push`komutu yazılmasada olur. |
|`git stash list`| Geçici olarak kayıt altına alınan değişiklikleri listeler. |
|`git stash pop`| En son değişikliğin stash'den silinerek aktif branch'e (dala) geri yükler ve stash listesinden siler. |
|`git stash apply stash@{0}`| Belirtilen stash@{0} i Stash'den silmeden aktif branch'e geri yükler |
|`git stash drop stash@{0}`| Belirtilen stash@{0} i aktif branch'e yüklemeden silinmesini sağlar. |
|`git checkout <hash>`| Belirtilen hash e ait commite gitmek için kullanılır. HEAD yerine detached HEAD kavramı bulunmaktadır. git in yönettiği pointer. |
|`git merge <branchname>`| Bulunulan branch'e`<branchname>`olarak bbelirtilen brench birleştirilir. |
|`git merge --abort`| Çakışma bulunup sorun giderilemez ise branchlerin çakışma öncesi hallerine getirilmesi için kullanılır. |
|`git push origin --delete <branch_name>`| Remote branchi silmek. |
|`git init --bare <repo_name>`| Yerel github-gitlab gibi dosya paylaşımında uzak bir merkezi depo oluşturmak için kullanılır. Working Copy yada Working Directory yani aktif daldaki dosyaların diskimizde normal bir dosya olarak bulunmasını sağlayan yapı mevcut değildir. Sadece`.git`klasörünün yer aldığı özel veritabanı formatına uygun içerik olarak kayıt altında tutulmasını sağlayan sistem oluşturulur.  |
|`git remote`| Remote repository'leri (uzak depoları) kısa listesini gösterir. |
|`git remote -v`| Remote repository'leri (uzak depoları) URL bilgisi ile gösterir. |
|`git tag`| Etiketleri listeler |
|`git tag --list -n`| Etiketleri açıklamaları ile birlite tek satır olarak listeler |
|`git tag --list --format '%(*objectname:short) %(refname:short)'`| Etiketleri belirtilen formatta listeler |
|`git tag v1.0.0"`| Aktif olan commite'e etiket ekleme için kullanılır. |
|`git tag -a v1.0.1 -m "<descriptionversion>"`| Aktif olan commite'e etiket ve açıklama (`<descriptionversion>`) ekleme için kullanılır. |
|`git tag -a v1.0.1 -m "<descriptionversion>" <hash>`|`<hash>`olan belirtilen commite'e etiket ve açıklama (`<descriptionversion>`) ekleme için kullanılır. |
|`git rebase -i <commit_hash>^`| sondaki`^`karakterine dikkat edilmelidir.`<commit_hash>`olarak belirtilen committen başlamak üzere yukarıya doğru bütün birleştirilebilecek commitlerin açıklamaları ile karşımıza gelir.`pick 4f3782f aciklama`şeklinde birden fazla satır gelecektir.`pick`->`squash`en alttan üste doğru birleştirme işlemi yapılabilir. Sonrasında metin editörü kaydedip kapatılmalıdır. Tekrar metin editörü açılacak ve commit için açıklama girilecektir. Kapatıldığında da`squash`olarak işaretlenen commitler tekillenecek ve`pick`de belirtilen commite birleştirilecektir. -i interaf (interactive) demektir. Burada config olarak`core.editor`doğru bir şekilde ayarlanmalıdır. |
|`git commit --amend`| Bu komut yanlızca son commit işlemimizi düzeltmemizi sağlar. Son commit işlemini tekrarlamak için kullanılır. Son yapılan commit'in açıklamasını ve içeriğini değiştirilebilir. Son commit sonrasında bir değişiklik yapılarak önceki commit içerisine eklemek isteniyorsa staging area ya dosya aktarılarak bu komut kullanılırsa son yapılan commit içeriğine yeni değişiklik dahil olur.<br/>NOT:<br/>1. Düzelttiğimiz commit bilgisinin Remote Repository'de **yayınlanmamış** olması gereklidir.<br/>2. Takım çalışmalarında dikkat edilmelidir. Sizin yaptığınız ve düzeltmek istediğiniz committen sonra commit yapılmamış olasına dikkat edilmelidir. |
|`git commit --amend -m "<newdescription>"`| Bu komut yanlızca son commit işlemimizi düzeltmemizi sağlar. Son commit içeriğini değiştirmeden yeni commit açıklamasını değiştirmek için kullanılır.<br/>NOT:<br/>1. Düzelttiğimiz commit bilgisinin Remote Repository'de **yayınlanmamış** olması gereklidir.<br/>2. Takım çalışmalarında dikkat edilmelidir. Sizin yaptığınız ve düzeltmek istediğiniz committen sonra commit yapılmamış olasına dikkat edilmelidir. |
|`git config --global merge.conflictStyle diff3`| Fark(diff) tespit ayarını diff3 olarak ayarlanır. Bu bize bir iki farklı branch de çalışan içeriğin conflict olması durumunda en base halinide gösterecektir. |
|`git config --global rerere.enabled true`| rerere _replay recorded resolution_ kısaltılmasıdır. _kaydedilmiş çözümü tekrar oynat_ . Bu seçenek aktif hale getirildiğinde başka bir dalda da aynı çakışma olursa git çözümü sizin için otomatik olarak uygulayacaktır.|
|`git rerere forget <pathspec>`| rerere çözüm olarak kaydedilen çakışma çözümün unutulması (silinmesi) için kullanılır.|
|`rm -rf .git/rr-cache`| rerere çözüm olarak kaydedilen çakışma çözümlerinin tamamanın silinmesi için kullanılır.|
|`git difftool -- index.html`| Working directory ile stage area arasındaki farkı gösterir.|
|`git difftool HEAD`| Working directory ile Repository arasındaki farkı gösterir.|
|`git difftool --staged HEAD`| Stage area ile repository arasındaki farklar|
|`git difftool --staged`| Stage Area'ya commit edilmek üzere eklenmiş/çıkarılmış dosyaların değişikliklerini difftool ile görüntülemek için kullanılır.`git config --global diff.tool "path\p4merge"`komutu ile belirlenir.|
## REMOTE REPO ILE ÇALIŞMAK

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|`git clone url`| Uzak repoyu locale klonlamak için kullanılır. Git bu işlemi yaparken uzak depo erişim bilgilerini kayıt altına alır. Git uak repo url bilgisini`origin`adı verilen varsayılan bir kısaltma oluşturup erişim için bu veriyi kullanır. |
|`git config --global credential.helper wincred`| alabileceği değerler osxkeychain - wincred. Widnows işletim sisteminde`Control Panel > User Accounts > Manage your credentials > Windows Credentials`alanında bulunur. git uzak sistemine erişim için sağlanan kullanıcı bilgilerinin tutulduğu yeri belirlemek için kullanılır. |
|`git remote`| Local Repository'ler (yerel depolar) ile hangi Remote Repository'ler (uzak depoların) ile ilişkilerinin bulunduğunu kısa liste halinde gösterir.(origin) |
|`git remote -v`| Local Repository'ler (yerel depolar) hangi Remote Repository'ler (uzak depoların) ile ilişkilerinin bulnduğunu görmek için  kısaltma listesinin URL bilgisi ile uzun bir şekilde listesini gösterir.(origin) |
|`git remote add <originname> <giturladdress>`| Yerel depo ile uzak depo arasındaki ilişkiyi kurmak için kuallnılır. Git tarafından biri`fetch`- *yerel depoya uzak depodan veri okuma işlemlerinde* - diğeride`push`- *yerel depodaki değişiklikleri uzak depoya yayınlarken yapılan yazma işlemlerinde* -  kullanır.<br/>- Özel senaryolar için bu adresler farklı olabilir. Örnek olarak okuma işlemleri performans sorunlarını çözmek ve yazma işlemleri güvenlik politikası uygulama ihtiyacı için farklı olabilir.<br/>- Ayrıca projenin bulunduğu sunucunun yedekleme ihtiyacı olarak iki farklı uzak repo sunucusunda da tutmak istenebilir. Böyle bir durumda da fetch ve push remote kaydı oluşturulabilir. |
|`git remote set-url <existorigin> <changeurl>`| Uzak repo adresinin değiştirilmesi-güncellenmesi için kullanılır. Bir servis sağlayıcıdan diğer bir servis sağlayıcıya geçişte kullanılır. |
|`git remote remove <existorigin>`|`<existorigin>`olarak belirtilen uzak repo kısaltmasını siler. |
|`git push`| Localde yapılan değişikliklerin commit sonrasında uzak bir noktadan alınmış projenin uzak sunucu üzerine gönderilerek paylaşılmasını sağlamak için kullanılır. |
|`git push origin master`| Localde yapılan değişikliklerin commit sonrasında uzak bir noktadan alınmış projenin uzak sunucu üzerine gönderilerek paylaşılmasını sağlamak için kullanılır. origin uzak sunucu için belirtilen kısaltmadır. master branchi gösterir. |
|`git push origin --delete <branch_name>`| Remote branchi silmek. |
|`git fetch`| Local Repository veritabanı Remote Repository veritabanı ile senkronize edilir. working directory'e değişiklikleri uygulamaz. Yani dosyalar değiştirilmez. |
|`git pull`| Geçerli branch uzak bir branch'i izleyecek şekilde ayarlandıysa bu komutu kullanarak uzak branch'deki değişiklikleri yerel branch ile birleştirmek için kullanabilirsiniz. working directory'e değişiklikleri uygulanır. Yani bu komutun yaptığı ilk işlem`git fetch`dir. Sonrasında Remote repository'de bulunan dosyaları local repository ile birleştirir.|
|`git checkout master`<br/>`git fetch`<br/>`git merge origin/master`|`git pull`işleminin aynısıdır. git de aslında güncelleme diye bir komut yoktur. Git önce veritabanını uzak repodan alır sonrasında uzak repo ile yerel repo birleştirme işlemine tabi tutulur.|
|`git pull --rebase origin master`| origin olarak ayarlanmış uzak sunucuda bulunan master branchini local'e çekerek birleştirme işlemine tabi tutar. Bunun nedeni sizin clone ile local'e çektiğiniz projenizde sizden önce master branch ile birleştirme yapıldı ise bu yapılanları local master branche çekmek için kullanılır. Yani yerel ana dal kopyası uzak ana dal kopyası ile senkronize edilir. (Merge made by the 'recursive' strategy.) - 3 Way Merge |
|`git diff origin/master master`| yerel dal ile uzak dal arasındaki farkları görüntülemek için kullanılıar. |
|`git diff --staged`| Stage Area'ya commit edilmek üzere eklenmiş/çıkarılmış dosyaların değişikliklerini görüntülemek için kullanılır.|
|`git difftool --staged`| Stage Area'ya commit edilmek üzere eklenmiş/çıkarılmış dosyaların değişikliklerini difftool ile görüntülemek için kullanılır.`git config --global diff.tool "path\p4merge"`komutu ile belirlenir.|

## EK KOMUTLAR

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|`pwd`| bulunulan klasörün path bilgisini gösterir. |
|`touch <new_file>`|`<new_file>`olarak belirtilen boş bir dosya yaratır |
|`echo "<addinfile>" > <new_file>`|`<new_file>`olarak belirtilen  bir dosya yaratır. İçerisine `<addinfile>`yazısını ekler.|
|`git config --global credential.helper wincred`| alabileceği değerler osxkeychain - wincred. Widnows işletim sisteminde`Control Panel > User Accounts > Manage your credentials > Windows Credentials`alanında bulunur. git uzak sistemine erişim için sağlanan kullanıcı bilgilerinin tutulduğu yeri belirlemek için kullanılır. |
|`git config --global credential.helper "cache --timeout 3600"`| Default olarak 15 dakika burada belirtildiği gibi 3600 saniye boyunca credential sormayacaktır. |
|`git log --author="<authorname>" --oneline`|`<authorname>`olarak belirtilen kişiye ait comitleri listeler. |
|`git log --author="<authorname>" --oneline`|`<authorname>`olarak belirtilen kişiye ait comitleri listeler. |
|`git log --author="<authorname>" --oneline -- index.html`| index.html üzerinde`<authorname>`olarak belirtilen kişinin hangi commitlerde değişiklik yaprığının listesini getirir. |

> **ÖNEMLİ NOT 1:** Eğer yerel bulunan klasörü`git init`komutu ile değişiklikleri izlemek için işaretlendi ise bu klasör altında *.git* uzaktılı bir gizli klasör oluşacaktır. Bu git'in kendi mantığı ile değişiklikleri tutuğu db'sidir. Bu klasör başka bir klasöre ve uzak sunucuya kopyalanarak`git clone <path>`ile gösterildiğinde bütün commit yapılan değişiklikler ve bütün dosyalar aynı şekilde geri getirilebilir. 

> **ÖNEMLİ NOT 2:** Yukarıdaki gibi bir klon oluşturulup bunun üzerinde değişiklik yapılır sornasında`git commit <description>`ile commit edilir. Sonrasında`git push`yapıldında aşağıdaki gibi bir hata alınacaktır. Bu hata başka bir repo açılıp oraya eklenerek sorun giderilebilir. Ancak bu hatayı almamak için`git init --bare`komutu ile uzak repo oluşturulmaktadır. Bu repo kopyalanarak bütün değişklikler aktarılır.

```bash
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 235 bytes | 235.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
remote: error: refusing to update checked out branch: refs/heads/master
remote: error: By default, updating the current branch in a non-bare repository
remote: is denied, because it will make the index and work tree inconsistent
remote: with what you pushed, and will require 'git reset --hard' to match
remote: the work tree to HEAD.
remote:
remote: You can set the 'receive.denyCurrentBranch' configuration variable
remote: to 'ignore' or 'warn' in the remote repository to allow pushing into
remote: its current branch; however, this is not recommended unless you
remote: arranged to update its work tree to match what you pushed in some
remote: other way.
remote:
remote: To squelch this message and still keep the default behaviour, set
remote: 'receive.denyCurrentBranch' configuration variable to 'refuse'.
To Z:/ll
 ! [remote rejected] master -> master (branch is currently checked out)
error: failed to push some refs to 'Z:/ll'
```

## MERGE ve DIFF TOOL

[P4merge](https://www.perforce.com/downloads/visual-merge-tool)

[winmerge](https://winmerge.org/)

## KAYNAKÇA

[Git Documentation Book](https://git-scm.com/book/en/v2)

[progit2](https://github.com/progit/progit2)

[progit2-tr](https://github.com/progit/progit2-tr)

[git-tfs](https://github.com/git-tfs/git-tfs) migration tool

[TFS to Git](https://github.com/git-tfs/git-tfs/blob/master/doc/usecases/migrate_tfs_to_git.md) Documentation
