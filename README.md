# GIT KULLANIMI

## CONFIGURASYON

|<div style="width:450px">Komut</div>|İşlevi|
|-|-|
|` git config --global --list `|git ayarlarını listelemek için gerekli komut|
|` git config --global init.defaultBranch master `|Default branch ismi|
|` git config --global core.editor "'path\sublime_text.exe'" `|Editör seçimi|

## GIT KOMUTLARI

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|` git init `| Projenizin olduğu klasörü bir git reposu olarak işaretlemek |
|` git add <<file_name>> `| Stageing Area ya dosyaları eklemek |
|` git add -A `| Stageing Area ya dosyaları toplu olarak eklemek |
|` git rm --cached <<file_name>> `| Staging Area'dan tekrar Untracked files alanına dosyayı geri göndermek |
|` git commit `| Açıklama gitmek için metin editörü çalıştırır. Bir satırdan fazla bir açılama girilecek ise bu şekilde -m parametresiz kullanılmalıdır. GIT 50/72 kuralı unutulmamalıdır. İlk satırda değişikliği özetleyen ve en fazla 50 karakter uzunluğunda bir metin olmalıdır. Ayrıntılarıda ilk satırdan sonra boş bir satır bırakarak ve her biri en fazla 72 karakter uzunluğunda istediğiniz sayıda satır olarak ekleyebilirsiniz.|
|` git config --global core.editor "code" `|  Metin editörü ayarlaması |
|` git commit -m "description" `|  Versiyon ile ilgili açıklama -m seçeneği ile doğrudan komut satırından verilir. |
|` git log -n 2 `|  aktif branchdeki son 2 commit bilgilerini gösterir. |

## GIT BRANCH

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|` git branch `| Bracn (Dal) ları listeler |
|` git branch -v `| Son commit mesajını gösterecek şekilde branchleri listeler |
|` git help branch `| Branch komutu için açıklamaları görüntüler. |
|` git branch <<new_branch_name>> `| Yeni branch oluşturur. |
|` git checkout <<branch_name>> `| branch_name olarak belirtilen branche geçer. |
|` git checkout -b <<new_branch_name>> `| yeni bir branch yaratır ve o branch aktif branch olarak seçilir. |
|` git stash `| Stageing Area ya alınmış ve commit edilmemiş değişiklikleri korumak için rafa kaldırır. Stack (yığın) mantığı ile çalışır. |
|` git stash list `| Geçici olarak kayıt altına alınan değişiklikleri listeler. |
|` git stash pop `| En son değişikliğin stash'den silinerek aktif branch'e (dala) geri yükler. |
|` git stash apply stash@{0} `| Belirtilen stash@{0} i Stash'den silmeden aktif branch'e geri yükler |
|` git stash drop stash@{0} `| Belirtilen stash@{0} i aktif branch'e yüklemeden silinmesini sağlar. |
|` git checkout <<hash>> `| Belirtilen hash e ait commite gitmek için kullanılır. HEAD yerine detached HEAD kavramı bulunmaktadır. git in yönettiği pointer. |
|` git checkout master`<br/>`git merge <<mergebranchname>> `| önce birleştirilmek istenen branche geçilir. sonra birleştirilecek branch ismi belirtilerek merge işlemi yapılır. |
|` git branch -d <<branch_name>> `| Silinmek istenen branch ismi girlerek branch silinir. Dikkat edilmesi gereken silinmek istenen branch aktif branch olmamalıdır. |

## EK KOMUTLAR

|<div style="width:300px">Komut</div>|İşlevi|
|-----------|-|
|` touch <<new_file>> `| <<new_file>> olarak belirtilen boş bir dosya yaratır |