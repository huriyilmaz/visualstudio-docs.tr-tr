---
title: Komutlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0284ce274791f21c9c0f85d265d92a7097cb09
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596404"
---
# <a name="visual-studio-commands"></a>Visual Studio komutları

**Komut** penceresinde, **anında** pencereye veya **Bul/komut** kutusuna Visual Studio komutlarını girebilirsiniz. Her durumda, büyüktür işareti (`>`), arama veya hata ayıklama işlemi yerine bir komutun aşağıda gösterildiği anlamına gelir.

**Araçlar** > **Seçenekler** > **ortamındaki** **klavye** sayfasında komutların ve sözdiziminin tamamen bir listesini bulabilirsiniz.

IDE yerelleştirilmiş sürümlerinde, komut adları IDE'nin kendi dilinde veya İngilizce girilebilir. Örneğin, yazabilirsiniz `File.NewFile` veya `Fichier.NouveauFichier` aynı komutu yürütmek için Fransızca IDE'de.

Birçok komutun eş adları vardır. Komut diğer adlarının listesi için bkz. [komut diğer adları](../../ide/reference/visual-studio-command-aliases.md). Komut klavye kısayolları için bkz. [Visual Studio 'Da varsayılan klavye kısayolları](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Atlatma karakteri

Visual Studio komutları için kaçış karakteri bir şapka (^). Kaçış karakteri, bir denetim karakteri olarak değil, tam olarak yorumlandığı anlamına gelir. Bu anahtar adları dışında bir parametre veya anahtar değerine düz tırnak ("), boşluk, önde gelen eğik çizgiler, düzeltme işaretleri veya diğer bir hazır bilgi karakterleri katıştırmak için kullanılabilir. Örneğin:

```
>Edit.Find ^^t /regex
```

İç veya dış tırnak işaretleri olup olmadığını şapka işareti aynı şekilde çalışır. Şapka, satırdaki son karakter ise yok sayılır.

## <a name="commands-with-arguments"></a>Bağımsız değişkenlerle komutlar

Aşağıdaki komutlar bağımsız değişkenler veya anahtarlar alır:

| Komut adı | Açıklama |
| - | - |
| [Varolan öğeyi Ekle](../../ide/reference/add-existing-item-command.md) | Geçerli çözüme var olan bir dosya ekler ve onu açar. |
| [Varolan Proje Ekle](../../ide/reference/add-existing-project-command.md) | Mevcut bir projeyi çözüme ekler. |
| [Yeni Öğe Ekle](../../ide/reference/add-new-item-command.md) | Geçerli çözüme .htm, .css, .txt veya frameset gibi yeni bir çözüm öğesi ekler ve onu açar. |
| [Diğer ad](../../ide/reference/alias-command.md) | Tam komut, tam komut ve bağımsız değişkenler için yeni bir diğer ad veya hatta başka bir diğer ad oluşturur. |
| [Deyimi değerlendir](../../ide/reference/evaluate-statement-command.md) | Değerlendirir ve verilen deyimi görüntüler. |
| [Bul](../../ide/reference/find-command.md) | Dosyaları bulunan seçenekler kümesini kullanarak arar **Bul ve Değiştir** denetimi. |
| [Dosyalarda Bul](../../ide/reference/find-in-files-command.md) | Dosyaları bulunan seçenekler kümesini kullanarak arar [dosyalarda Bul](../../ide/find-in-files.md). |
| [Git](../../ide/reference/go-to-command.md) | İmleci belirtilen satıra taşır. |
| [Çağrı yığınını Listele](../../ide/reference/list-call-stack-command.md) | Geçerli çağrı yığınını görüntüler. |
| [Ayrıştırılmış kodu listele](../../ide/reference/list-disassembly-command.md) | Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar. |
| [Belleği Listele](../../ide/reference/list-memory-command.md) | Belirtilen bellek aralığının içeriklerini görüntüler. |
| [Modüllerin listesini](../../ide/reference/list-modules-command.md) | Geçerli işlem için modülleri listeler. |
| [Yazmaçları Listele](../../ide/reference/list-registers-command.md) | Kayıtların listesini görüntüler. |
| [Kaynağı Listele](../../ide/reference/list-source-command.md) | Belirtilen kaynak kodu satırlarını görüntüler. |
| [İş parçacıklarını Listele](../../ide/reference/list-threads-command.md) | Geçerli programdaki iş parçacıklarının listesini görüntüler. |
| [Günlük komut penceresi çıktısı](../../ide/reference/log-command-window-output-command.md) | Kopya, tüm giriş ve çıkışı bir dosyaya komut penceresinden. |
| [Yeni dosya](../../ide/reference/new-file-command.md) | Yeni bir dosya oluşturur ve şu anda seçili olan projeye ekler. |
| [Dosya Aç](../../ide/reference/open-file-command.md) | Varolan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır. |
| [Proje Aç](../../ide/reference/open-project-command.md) | Varolan projeyi açar ve geçerli çözüme projeyi eklemenize olanak sağlar. |
| [Yazdırma](../../ide/reference/print-command.md) | İfadeyi değerlendirir ve sonuçları veya belirtilen metni görüntüler. |
| [Hızlı Bakış Komutu](../../ide/reference/quick-watch-command.md) | Seçilen veya belirtilen metni görüntüler **ifade** alanını **Hızlı Bakış** iletişim kutusu. |
| [Değiştir](../../ide/reference/replace-command.md) | Metin dosyalarında bulunan seçenekler kümesini kullanarak değiştirir **Bul ve Değiştir** denetimi. |
| [Dosyalarda Değiştir](../../ide/reference/replace-in-files-command.md) | Metin dosyalarında bulunan seçenekler kümesini kullanarak değiştirir [dosyalarda Değiştir](../../ide/replace-in-files.md). |
| [Geçerli yığın çerçevesini Ayarla](../../ide/reference/set-current-stack-frame-command.md) | Belirli bir yığın çerçevesini görüntülemenize olanak sağlar. |
| [Geçerli iş parçacığı](../../ide/reference/set-current-thread-command.md) | Belirli bir iş parçacığını görüntülemenize olanak sağlar. |
| [Tabanı Ayarla](../../ide/reference/set-radix-command.md) | Görüntülenecek bayt sayısını belirler. |
| [Kabuk](../../ide/reference/shell-command.md) | İçinden programları başlatır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komutu komut istemi'nden yürüttüğünü artırmadığı. |
| [ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md) | Tümleşik geliştirme ortamı (IDE) veya IDE dışında içindeki bir web tarayıcı penceresinde belirttiğiniz URL'yi görüntüler. |
| [Start](../../ide/reference/start-command.md) | Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar. |
| [Yolu](../../ide/reference/symbol-path-command.md) | Hata ayıklayıcının simge araması dizinler listesini ayarlar. |
| [İki durumlu kesme noktası](../../ide/reference/toggle-breakpoint-command.md) | Dosyadaki geçerli konumda geçerli durumuna bağlı olarak kesme noktasını açar veya devre dışı bırakır. |
| [İzle Komutu](../../ide/reference/watch-command.md) | Oluşturur ve belirtilen bir örneğini açar bir **Watch** penceresi. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
