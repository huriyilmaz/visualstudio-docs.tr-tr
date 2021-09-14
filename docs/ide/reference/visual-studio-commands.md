---
title: Komutlar
description: Visual Studio'da erişiminiz olan çeşitli komutlar hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 180852e2895318f1ffc2fbf411c3945373b5ab4c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628563"
---
# <a name="visual-studio-commands"></a>Visual Studio komutları

Komut penceresine, Visual Studio **penceresine** veya **Bul/Komut kutusuna** komut satırı komutları **girebilirsiniz.** Her durumda büyüktür işareti ( ) bir komutun, arama veya hata ayıklama işlemi yerine aşağıdaki `>` gibi olduğunu gösterir.

Komutların ve söz dizimlerinin tam listesini Araçlar Seçenekler **Ortamı'nın** Klavye  >  **sayfasında**  >  **bulabilirsiniz.**

IDE'nin yerelleştirilmiş sürümlerinde, komut adları IDE'nin yerel dilinde veya İngilizce olarak girilebilir. Örneğin, aynı komutu yürütmek `File.NewFile` için Fransızca `Fichier.NouveauFichier` IDE'ye veya yazabilirsiniz.

Çoğu komutun diğer adları vardır. Komut diğer adlarının listesi için bkz. [Komut diğer adları.](../../ide/reference/visual-studio-command-aliases.md) Komut klavye kısayolları için [bkz. komutta varsayılan klavye kısayolları Visual Studio.](../default-keyboard-shortcuts-in-visual-studio.md)

## <a name="escape-character"></a>Atlatma karakteri

Komutlar için kaçış Visual Studio bir karakter (^) olur. Kaçış karakteri, onu takip eden karakterin bir denetim karakteri yerine tam olarak yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerine düz tırnak işaretleri ("), boşluklar, baştaki eğik çizgi, çizgi işareti veya diğer sabit karakterleri eklemek için kullanılabilir. Örnek:

```
>Edit.Find ^^t /regex
```

İster tırnak içinde ister dışında olsun, bir işaret aynı şekilde işlev gösterir. Çizgideki son karakter bir karakterse yoksayılır.

## <a name="commands-with-arguments"></a>Bağımsız değişkenlere sahip komutlar

Aşağıdaki komutlar bağımsız değişkenleri veya anahtarları alır:

| Komut Adı | Description |
| - | - |
| [Var Olan Öğeyi Ekle](../../ide/reference/add-existing-item-command.md) | Mevcut bir dosyayı geçerli çözüme ekler ve açar. |
| [Var Olan Verileri Project](../../ide/reference/add-existing-project-command.md) | Mevcut bir projeyi geçerli çözüme ekler. |
| [Yeni Öğe Ekle](../../ide/reference/add-new-item-command.md) | Geçerli çözüme .htm, .css, .txt veya frameset gibi yeni bir çözüm öğesi ekler ve açar. |
| [Diğer ad](../../ide/reference/alias-command.md) | Tam komut, tam komut ve bağımsız değişkenler, hatta başka bir diğer ad için yeni bir diğer ad oluşturur. |
| [Evaluate Deyimi](../../ide/reference/evaluate-statement-command.md) | Verilen deyimi değerlendirir ve görüntüler. |
| [Bul](../../ide/reference/find-command.md) | Bul ve Değiştir denetiminde kullanılabilen seçeneklerin bir alt kümesini **kullanarak dosyaları** arar. |
| [Dosyalarda Bul](../../ide/reference/find-in-files-command.md) | Dosyalarda Bul seçeneğinde bulunan seçeneklerin bir alt kümesini [kullanarak dosyaları arar.](../../ide/find-in-files.md) |
| [Git](../../ide/reference/go-to-command.md) | İmleci belirtilen satıra taşır. |
| [Çağrı Yığınını Listele](../../ide/reference/list-call-stack-command.md) | Geçerli çağrı yığınını görüntüler. |
| [Disassembly Listesini Ekleme](../../ide/reference/list-disassembly-command.md) | Hata ayıklama işlemini başlar ve hataların nasıl işlen olduğunu belirtmenize olanak sağlar. |
| [Belleği Listele](../../ide/reference/list-memory-command.md) | Belirtilen bellek aralığının içeriğini görüntüler. |
| [Modülleri Listele](../../ide/reference/list-modules-command.md) | Geçerli işlem için modülleri listeler. |
| [Yazmazları Listele](../../ide/reference/list-registers-command.md) | Yazmazların listesini görüntüler. |
| [Liste Kaynağı](../../ide/reference/list-source-command.md) | Kaynak kodun belirtilen satırlarını görüntüler. |
| [İş Parçacıklarını Listele](../../ide/reference/list-threads-command.md) | Geçerli programda iş parçacıklarının listesini görüntüler. |
| [Günlük Komutu Penceresi Çıkışı](../../ide/reference/log-command-window-output-command.md) | Dosyanın tüm giriş ve çıkışlarını Komut penceresi dosyasına kopyalar. |
| [Yeni Dosya](../../ide/reference/new-file-command.md) | Yeni bir dosya oluşturur ve bu dosyayı seçili olan projeye ekler. |
| [Dosya Aç](../../ide/reference/open-file-command.md) | Mevcut bir dosyayı açar ve bir düzenleyici belirtmenize olanak sağlar. |
| [Açık Project](../../ide/reference/open-project-command.md) | Mevcut bir projeyi açar ve projeyi geçerli çözüme eklemenize olanak sağlar. |
| [Yazdır](../../ide/reference/print-command.md) | İfadeyi değerlendirir ve sonuçları veya belirtilen metni görüntüler. |
| [Hızlı İzleme Komutu](../../ide/reference/quick-watch-command.md) | Hızlı İzleme iletişim kutusunun İfade **alanında** seçili veya belirtilen **metni** görüntüler. |
| [Değiştirmek](../../ide/reference/replace-command.md) | Bul ve Değiştir denetiminde kullanılabilen seçeneklerin bir alt kümesini kullanarak **dosyalarda bulunan metni** değiştirir. |
| [Dosyalarda Değiştir](../../ide/reference/replace-in-files-command.md) | Dosyalarda yer alan metni, Dosyalarda Değiştir'te bulunan seçeneklerin bir alt [kümesini kullanarak değiştirir.](../../ide/replace-in-files.md) |
| [Geçerli Yığın Çerçevesini Ayarlama](../../ide/reference/set-current-stack-frame-command.md) | Belirli bir yığın çerçevesini görüntülemeye olanak sağlar. |
| [Geçerli İş Parçacığını Ayarla](../../ide/reference/set-current-thread-command.md) | Belirli bir iş parçacığını görüntülemeye olanak sağlar. |
| [Radix'i ayarlama](../../ide/reference/set-radix-command.md) | Görüntülenecek bayt sayısını belirler. |
| [Kabuk](../../ide/reference/shell-command.md) | Komut isteminden yürütülür gibi içindeki programları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlatıyor. |
| [ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md) | Web tarayıcısı penceresinde belirttiğiniz URL'yi tümleşik geliştirme ortamında (IDE) veya IDE'nin dışında görüntüler. |
| [Başlangıç](../../ide/reference/start-command.md) | Hata ayıklama işlemini başlar ve hataların nasıl işlen olduğunu belirtmenize olanak sağlar. |
| [Yol](../../ide/reference/symbol-path-command.md) | Hata ayıklayıcısının sembol araması için dizin listesini ayarlar. |
| [Kesme Noktası'nın GeçişIni Değiştir](../../ide/reference/toggle-breakpoint-command.md) | Kesme noktası, geçerli durumuna bağlı olarak dosyasındaki geçerli konumda açık veya kapalı olur. |
| [İzleme Komutu](../../ide/reference/watch-command.md) | İzleme penceresinin belirtilen bir örneğini oluşturur **ve** açar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/Komut kutusu](../../ide/find-command-box.md)
- [Visual Studio diğer adları](../../ide/reference/visual-studio-command-aliases.md)
