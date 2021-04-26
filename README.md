# GIT KULLANIMI

## Versiyon Kontrol Sistemi (Version Control System)

İki farklı yaklaşım vardır.

![Centralized Version Control](https://homes.cs.washington.edu/~mernst/advice/version-control-fig2.png) ![Distributed Version Control](https://homes.cs.washington.edu/~mernst/advice/version-control-fig3.png)

[KAYNAK](https://homes.cs.washington.edu/~mernst/advice/version-control.html)

## GIT File Workflow
![Git File Workflow](https://csharpcorner.azureedge.net/article/git-and-github-version-control-local-and-remote-repository/Images/Git%20And%20Github%20Version%20Control10.png)

[KAYNAK](https://www.c-sharpcorner.com/article/git-and-github-version-control-local-and-remote-repository/)

## Merge Çeşitleri
1. Fast Forward Merge
2. No Fast Forward Merge
3. 3 Way Merge (Automatic Merge)
## GIT ile ilgili Kısa bilgiler
Git kurulumu için [Git page](https://git-scm.com/)

Git branch oluşturmada proje dosyalarının birer kopyalarını oluşturmayp sadece işaretçi (HEAD) bir kopyası oluşturulduğu için git branch dosyası disk kapasite kullanımı ve branch oluşturma süresi açısından düşük maliyetlidir.

> `git --version`  git versiyon numarasını görüntüler.

> `C:\Program Files<<(x86)>>\Git\etc\gitconfig` ==> `git config --system` komutu ile kullanılan config dosyasının yoludur. git'in install edildiği klasördür. 32 bit install edildi ise `Program Files(x86)` klasörü içerisindedir.

> `C:\Users\<<userame>>\.gitconfig` ==> `git config --global` komutu ile kullanılan config dosyasının yoludur.

> `.git/config` ==> `git config` komutu ile kullanılan config dosyasının yoludur. aktif dizin içerisinde bulunan gizli `.git` klasörü içerisinde yer alır.

> `.gitignore` dosyası oluşturmak için gerekli syntax bilgisi için *[globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming))* <br/> Örnek git `.gitignore` dosyaları için -> [github/gitignore ](https://github.com/github/gitignore).


## CONFIGURASYON

|<div style="width:450px">Komut</div>|İşlevi|
|-|-|
|` git <<command>> --help `|komut hakkında yardım için kullanılır.|
|` git config --global --list `|git ayarlarını listelemek için gerekli komut|
|` git config --global user.name "name" `|kullanıcı adı konfigurasyonu. `commit` komutu ile versiyon bilgilerini kayıt altına alırken bilgi amaçlı olarak kullanılır.|
|` git config --global user.email "email@email.com" `|email konfigurasyonu. `commit` komutu ile versiyon bilgilerini kayıt altına alırken bilgi amaçlı olarak kullanılır.|
|` git config --global --unset user.name `| user.name key bilgisini siler.|
|` git config --global init.defaultBranch master `|Default branch ismi|
|` git config --global core.editor "'path\sublime_text.exe'" `|Editör seçimi|
|` git config --global mergetool.keepBackup false `|git diff aracı çalıştırıldığında bağzı dosyalar oluşturulur. çakışmalar çözülüp merge işlemi bitirilse bile bu dosyalar silinmez. Bu durumu değiştirmek için bu config ayarı kullanılır. git difftool komutu ile çalıştırıalcak 3rd uygulamaların geçici dosyalar bu kapsamda değildir. |
|` git config --global core.excludesFile "path\.gitignore'" `|Global olarak .gitignore dosyasının gösterilmesi|
|` git config --global diff.tool "path\p4merge" `|diff tool olarak p4merge programının belirlenmesi.|
|` git config --global merge.tool "path\p4merge" `|merge tool olarak p4merge programının belirlenmesi.|
|` git config --global alias.his "log --all --oneline --graph --decorate" `|alias verilerek `git his`komutu ile `git log --all --oneline --graph --decorate` komutuna atıfta bulunmak ve kısa komut ile çalıştırılaması|
|` git config --system -e `| --system config dosyasını editör ile açar.|
|` git config --global -e `| --global config dosyasını editör ile açar.|
|` git config -e `| aktif dizin içerisindeki config dosyasını editör ile açar.|


## GIT KOMUTLARI

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|` git init `| Projenizin olduğu klasörü bir git reposu olarak işaretlemek |
|` git add <<file_name>> `| Stageing Area ya dosyaları eklemek |
|` git add -A . `| Stageing Area ya dosyaları toplu olarak eklemek |
|` git rm --cached <<file_name>> `| Staging Area'dan tekrar Untracked files alanına dosyayı geri göndermek |
|` git reset `| Staging Area'dan tekrar Untracked files alanına dosyayı geri göndermek. Commit yapılmadan değişiklik öncesi aktif branch i geri yükler. |
|` git reset --hard <<hash>> `| istenmeyen bir commit yapıldı ise önceki commitin hash bilgisine geri dönülmek istendiğinde kullanılır. |
|` git commit `| Açıklama gitmek için metin editörü çalıştırır. Bir satırdan fazla bir açılama girilecek ise bu şekilde -m parametresiz kullanılmalıdır. GIT 50/72 kuralı unutulmamalıdır. İlk satırda değişikliği özetleyen ve en fazla 50 karakter uzunluğunda bir metin olmalıdır. Ayrıntılarıda ilk satırdan sonra boş bir satır bırakarak ve her biri en fazla 72 karakter uzunluğunda istediğiniz sayıda satır olarak ekleyebilirsiniz.|
|` git commit -m "description" `|  Versiyon ile ilgili açıklama -m seçeneği ile doğrudan komut satırından verilir. |
|` git log -n 2 `|  aktif branchdeki son 2 commit bilgilerini gösterir. |
|` git log -p `| Commit tarihçesinin geniş açıklamalı olarak incelenmesi için kullanılır. |
|` git clone url `| Uzak repoyu locale klonlamak için kullanılır. |
|` git show `| Bu komut son commit için meta verileri ve içerik değişikliklerini gösterir. |

## GIT BRANCH

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|` git branch `| Branch (Dal) ları listeler |
|` git branch --list `| Branch (Dal) ları listeler |
|` git branch -v `| Son commit mesajını gösterecek şekilde branchleri listeler |
|` git branch -a `| local ve remote bütün branchleri listeler |
|` git remote show origin `| Remote olarak aktif olan branchler hakkında detaylı bilgi verir. |
|` git remote update --prune origin `| Remote olarak aktif olan branchlerleri senkronize eder. |
|` git remote update -p `| Remote olarak aktif olan branchlerleri senkronize eder. |
|` git branch -r `| Remote olarak aktif olan branchlerleri gösterir |
|` git help branch `| Branch komutu için açıklamalı yardım görüntüler. |
|` git branch <<new_branch_name>> `| Yeni branch oluşturur. |
|` git checkout <<branch_name>> `| branch_name olarak belirtilen branche geçer. |
|` git checkout -b <<new_branch_name>> `| yeni bir branch yaratır ve o branch aktif branch olarak seçilir. |
|` git push -u origin <<branch_name>> `| yeni oluşturulan branch içerisinde bir değişiklik, bir dosya eklendisi olmasa dahi uzak repository ye entegre etmek için kullanılır. -u parametresi ilk defa senkronizasyon yapılacak ise kullanılmalıdır. Sonrasında -u parametresine gerek yoktur. |
|` git stash `| Stageing Area ya alınmış ve commit edilmemiş değişiklikleri korumak için rafa kaldırır. Stack (yığın) mantığı ile çalışır. |
|` git stash list `| Geçici olarak kayıt altına alınan değişiklikleri listeler. |
|` git stash pop `| En son değişikliğin stash'den silinerek aktif branch'e (dala) geri yükler. |
|` git stash apply stash@{0} `| Belirtilen stash@{0} i Stash'den silmeden aktif branch'e geri yükler |
|` git stash drop stash@{0} `| Belirtilen stash@{0} i aktif branch'e yüklemeden silinmesini sağlar. |
|` git checkout <<hash>> `| Belirtilen hash e ait commite gitmek için kullanılır. HEAD yerine detached HEAD kavramı bulunmaktadır. git in yönettiği pointer. |
|` git checkout master`<br/>`git merge <<mergebranchname>> `| önce birleştirilmek istenen branche geçilir. sonra birleştirilecek branch ismi belirtilerek merge işlemi yapılır. |
|` git branch -d <<branch_name>> `| Silinmek istenen branch ismi girlerek branch silinir. Dikkat edilmesi gereken silinmek istenen branch aktif branch olmamalıdır. |
|` git push origin --delete <<branch_name>> `| Remote branchi silmek. |
|` git init --bare <<repo_name>> `| Yerel github-gitlab gibi dosya paylaşımında uzak bir merkezi depo oluşturmak. |
|` git pull `| Geçerli branch uzak bir branch'i izleyecek şekilde ayarlandıysa bu komutu kullanarak uzak branch'deki değişiklikleri yerel branch ile birleştirmek için kullanabilirsiniz. |
|` git pull --rebase origin master `| origin olarak ayarlanmış uzak sunucuda bulunan master branchini local'e çekerek birleştirme işlemine tabi tutar. Bunun nedeni sizin clone ile local'e çektiğiniz projenizde sizden önce master branch ile birleştirme yapıldı ise bu yapılanları local master branche çekmek için kullanılır. Yani yerel ana dal kopyası uzak ana dal kopyası ile senkronize edilir. (Merge made by the 'recursive' strategy.) - 3 Way Merge |
|` git push `| Localde yapılan değişikliklerin commit sonrasında uzak bir noktadan alınmış projenin uzak sunucu üzerine gönderilerek paylaşılmasını sağlamak için kullanılır. |
|` git push origin master `| Localde yapılan değişikliklerin commit sonrasında uzak bir noktadan alınmış projenin uzak sunucu üzerine gönderilerek paylaşılmasını sağlamak için kullanılır. origin uzak sunucu için belirtilen kısaltmadır. master branchi gösterir. |
|` git remote `| Remote repository'leri (uzak depoları) kısa listesini gösterir. |
|` git remote -v `| Remote repository'leri (uzak depoları) URL bilgisi ile gösterir. |
|` git fetch `| Local Repository veritabanı Remote Repository veritabanı ile senkronize edilir. |
|` git tag "v.1.0.1" `| Etiket ekleme |
|`git rebase -i <<commit_hash>>^ `| sondaki `^` karakterine dikkat edilmelidir. `<<commit_hash>>` olarak belirtilen committen başlamak üzere yukarıya doğru bütün birleştirilebilecek commitlerin açıklamaları ile karşımıza gelir. `pick 4f3782f aciklama` şeklinde birden fazla satır gelecektir. `pick` -> `squash` en alttan üste doğru birleştirme işlemi yapılabilir. Sonrasında metin editörü kaydedip kapatılmalıdır. Tekrar metin editörü açılacak ve commit için açıklama girilecektir. Kapatıldığında da `squash` olarak işaretlenen commitler tekillenecek ve `pick` de belirtilen commite birleştirilecektir. -i interaf (interactive) demektir. Burada config olarak `core.editor` doğru bir şekilde ayarlanmalıdır. |
|` git commit --amend `| Son yapılan commit'in açıklamasını ve içeriğini değiştirir. Son commit sonrasında bir değişiklik yapılarak önceki commit içerisine eklemek isteniyorsa staging area ya dosya aktarılarak bu komut kullanılırsa son yapılan commit içeriğine yeni değişiklik dahil olur. |
|` git config --global merge.conflictStyle diff3 `| Fark(diff) tespit ayarını diff3 olarak ayarlanır. Bu bize bir iki farklı branch de çalışan içeriğin conflict olması durumunda en base halinide gösterecektir. |
|` git config --global rerere.enabled true `| rerere _replay recorded resolution_ kısaltılmasıdır. _kaydedilmiş çözümü tekrar oynat_ . Bu seçenek aktif hale getirildiğinde başka bir dalda da aynı çakışma olursa git çözümü sizin için otomatik olarak uygulayacaktır.|
|` git rerere forget <<pathspec>> `| rerere çözüm olarak kaydedilen çakışma çözümün unutulması (silinmesi) için kullanılır.|
|` rm -rf .git/rr-cache `| rerere çözüm olarak kaydedilen çakışma çözümlerinin tamamanın silinmesi için kullanılır.|
|` git difftool -- index.html `| Working directory ile stage area arasındaki farkı gösterir.|
|` git difftool HEAD `| Working directory ile Repository arasındaki farkı gösterir.|
|` git difftool --staged HEAD `| Stage area ile repository arasındaki farklar|

## EK KOMUTLAR

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|` pwd `| bulunulan klasörün path bilgisini gösterir. |
|` touch <<new_file>> `| <<new_file>> olarak belirtilen boş bir dosya yaratır |
|` git config --global credential.helper wincred `| alabileceği değerler osxkeychain - wincred. Widnows işletim sisteminde `Control Panel > User Accounts > Manage your credentials > Windows Credentials` |
|` git config --global credential.helper "cache --timeout 3600" `| Default olarak 15 dakika burada belirtildiği gibi 3600 saniye boyunca credential sormayacaktır. |

> **ÖNEMLİ NOT 1:** Eğer yerel bulunan klasörü `git init` komutu ile değişiklikleri izlemek için işaretlendi ise bu klasör altında *.git* uzaktılı bir gizli klasör oluşacaktır. Bu git'in kendi mantığı ile değişiklikleri tutuğu db'sidir. Bu klasör başka bir klasöre ve uzak sunucuya kopyalanarak `git clone <<path>>` ile gösterildiğinde bütün commit yapılan değişiklikler ve bütün dosyalar aynı şekilde geri getirilebilir. 

> **ÖNEMLİ NOT 2:** Yukarıdaki gibi bir klon oluşturulup bunun üzerinde değişiklik yapılır sornasında `git commit <<description>>` ile commit edilir. Sonrasında `git push` yapıldında aşağıdaki gibi bir hata alınacaktır. Bu hata başka bir repo açılıp oraya eklenerek sorun giderilebilir. Ancak bu hatayı almamak için `git init --bare` komutu ile uzak repo oluşturulmaktadır. Bu repo kopyalanarak bütün değişklikler aktarılır.

```
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

## KAYNAKÇA
[progit2](https://github.com/progit/progit2)

[progit2-tr](https://github.com/progit/progit2-tr)

[Git Documentation Book](https://git-scm.com/book/en/v2)

[git-tfs](https://github.com/git-tfs/git-tfs) migration tool

[TFS to Git](https://github.com/git-tfs/git-tfs/blob/master/doc/usecases/migrate_tfs_to_git.md) Documentation