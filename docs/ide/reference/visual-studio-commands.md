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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596404"
---
# <a name="visual-studio-commands"></a>Visual Studio komutları

Visual Studio komutlarını **Komut** penceresinde, **Hemen** penceresine veya **Bul/Komut** kutusuna girebilirsiniz. Her durumda, büyük işareti`>`( ) bir arama veya hata ayıklama işlemi yerine bir komut, aşağıdaki gösterir.

 >  **Araçlar** > **Seçenekleri****Ortamı'nda** **Klavye** sayfasında komutların ve sözdiziminin tam listesini bulabilirsiniz.

IDE'nin yerelleştirilmiş sürümlerinde komut adları IDE'nin ana dilinde veya İngilizce olarak girilebilir. Örneğin, aynı komutu `File.NewFile` `Fichier.NouveauFichier` yürütmek için Fransızca IDE'yi yazabilirsiniz.

Birçok komutun takma adları vardır. Komut diğer adlarının listesi için [Komut takma adlarını](../../ide/reference/visual-studio-command-aliases.md)görün. Komut klavyesi kısayolları için [Visual Studio'daki Varsayılan klavye kısayolları'na](../default-keyboard-shortcuts-in-visual-studio.md)bakın.

## <a name="escape-character"></a>Atlatma karakteri

Visual Studio komutları için kaçış karakteri bir caret (^) olduğunu. Kaçış karakteri, onu hemen izleyen karakterin bir kontrol karakteri olarak değil, kelimenin tam anlamıyla yorumlanması anlamına gelir. Bu, geçiş adları dışında, düz tırnak işaretleri ("), boşluklar, satır başları, bakımlar veya parametre veya anahtar değerindeki diğer tüm gerçek karakterleri katıştırmak için kullanılabilir. Örnek:

```
>Edit.Find ^^t /regex
```

Bir caret, tırnak işaretlerinin içinde veya dışında olsun aynı işlevi görür. Eğer bir gözde, satırdaki son karakterse, yok sayılır.

## <a name="commands-with-arguments"></a>Bağımsız değişkenli komutlar

Aşağıdaki komutlar bağımsız değişkenleri veya anahtarları alır:

| Komut Adı | Açıklama |
| - | - |
| [Varolan Öğe yi Ekle](../../ide/reference/add-existing-item-command.md) | Varolan bir dosyayı geçerli çözüme ekler ve açar. |
| [Varolan Proje ekle](../../ide/reference/add-existing-project-command.md) | Geçerli çözüme varolan bir proje ekler. |
| [Yeni Öğe Ekle](../../ide/reference/add-new-item-command.md) | Geçerli çözüme .htm, .css, .txt veya frameset gibi yeni bir çözüm öğesi ekler ve açar. |
| [Diğer ad](../../ide/reference/alias-command.md) | Tam bir komut, tam komut ve bağımsız değişkenler ve hatta başka bir takma ad için yeni bir takma ad oluşturur. |
| [Bildirimi Değerlendir](../../ide/reference/evaluate-statement-command.md) | Verilen ifadeyi değerlendirir ve görüntüler. |
| [Bul](../../ide/reference/find-command.md) | **Bul ve Değiştir** denetiminde kullanılabilen seçeneklerin bir alt kümesini kullanarak dosyaları arar. |
| [Dosyalarda Bul](../../ide/reference/find-in-files-command.md) | [Dosyaları Bul dosyalarında](../../ide/find-in-files.md)bulunan seçeneklerin bir alt kümesini kullanarak arar. |
| [Git](../../ide/reference/go-to-command.md) | İmleci belirtilen satıra taşır. |
| [Liste Arama Yığını](../../ide/reference/list-call-stack-command.md) | Geçerli çağrı yığınını görüntüler. |
| [Liste Sökme](../../ide/reference/list-disassembly-command.md) | Hata ayıklama işlemini başlatir ve hataların nasıl işleneceğini belirtmenize olanak tanır. |
| [Liste Belleği](../../ide/reference/list-memory-command.md) | Belirtilen bellek aralığının içeriğini görüntüler. |
| [Liste Modülleri](../../ide/reference/list-modules-command.md) | Geçerli işlemin modüllerini listeler. |
| [Liste Kayıtları](../../ide/reference/list-registers-command.md) | Kayıtların listesini görüntüler. |
| [Kaynak Listele](../../ide/reference/list-source-command.md) | Kaynak kodunun belirtilen satırlarını görüntüler. |
| [Liste Konuları](../../ide/reference/list-threads-command.md) | Geçerli programdaki iş parçacıklarının listesini görüntüler. |
| [Günlük Komut Penceresi Çıktısı](../../ide/reference/log-command-window-output-command.md) | Komut penceresinden tüm giriş ve çıktıları bir dosyaya kopyalar. |
| [Yeni Dosya](../../ide/reference/new-file-command.md) | Yeni bir dosya oluşturur ve şu anda seçili projeye ekler. |
| [Dosyayı Aç](../../ide/reference/open-file-command.md) | Varolan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır. |
| [Açık Proje](../../ide/reference/open-project-command.md) | Varolan bir projeyi açar ve projeyi geçerli çözüme eklemenize olanak tanır. |
| [Yazdırma](../../ide/reference/print-command.md) | İfadeyi değerlendirir ve sonuçları veya belirtilen metni görüntüler. |
| [Hızlı Bakış Komutu](../../ide/reference/quick-watch-command.md) | **Hızlı İzleme** iletişim kutusunun **İfade** alanında seçili veya belirtilen metni görüntüler. |
| [Değiştirmek](../../ide/reference/replace-command.md) | **Bul ve Değiştir** denetiminde kullanılabilen seçeneklerin bir alt kümesini kullanarak dosyalardaki metni değiştirir. |
| [Dosyalarda Değiştir](../../ide/reference/replace-in-files-command.md) | [Dosyalarda Değiştir'de](../../ide/replace-in-files.md)bulunan seçeneklerin bir alt kümesini kullanarak dosyalardaki metni değiştirir. |
| [Geçerli Yığın Çerçeveyi Ayarlama](../../ide/reference/set-current-stack-frame-command.md) | Belirli bir yığın çerçevesini görüntülemenizi sağlar. |
| [Geçerli İş Parçacığı Ayarlama](../../ide/reference/set-current-thread-command.md) | Belirli bir iş parçacığı görüntülemenizi sağlar. |
| [Radix'i Ayarla](../../ide/reference/set-radix-command.md) | Görüntülenebilmek için bayt sayısını belirler. |
| [Kabuk](../../ide/reference/shell-command.md) | Komut komut isteminden yürütülmüş gibi içeriden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programları başlatır. |
| [ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md) | Bir web tarayıcısı penceresinde belirttiğiniz URL'yi tümleşik geliştirme ortamında (IDE) veya IDE'nin dışında görüntüler. |
| [Başlangıç](../../ide/reference/start-command.md) | Hata ayıklama işlemini başlatir ve hataların nasıl işleneceğini belirtmenize olanak tanır. |
| [Yol](../../ide/reference/symbol-path-command.md) | Hata ayıklamanın sembolleri aramak için dizinlistesini ayarlar. |
| [Kesme Noktasını Geçiş](../../ide/reference/toggle-breakpoint-command.md) | Kesme noktasını, geçerli durumuna bağlı olarak dosyadaki geçerli konumda açar veya kapatır. |
| [İzle Komutu](../../ide/reference/watch-command.md) | **İzleme** penceresinin belirli bir örneğini oluşturur ve açar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/Komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
