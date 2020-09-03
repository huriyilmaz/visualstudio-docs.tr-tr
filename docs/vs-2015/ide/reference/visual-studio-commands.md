---
title: Komutlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ad913e418f2f13bd196925b3c085b9d5c7efca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667458"
---
# <a name="visual-studio-commands"></a>Visual Studio Komutları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio **komutları, komut penceresi,** **anlık** pencere veya **Bul/komut** kutusu 'ndan bir komut çağırabilmesini sağlar. Her durumda, bir `>` arama veya hata ayıklama işlemi yerine bir komutun izlenmesi gerektiğini göstermek için büyüktür işareti () kullanılır.

 Komutların ve sözdiziminin tamamen bir listesini **, klavye, ortam seçenekleri** iletişim kutusunda bulabilirsiniz.

 Visual Studio komutları için kaçış karakteri, bir giriş işareti (^) karakteridir. Bu, bir denetim karakteri yerine, hemen sonra gelen karakterin tam olarak yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerindeki düz tırnak işaretlerini ("), boşlukları, baştaki eğik çizgileri, yüzleri veya diğer sabit karakterleri eklemek için kullanılabilir. Örneğin,

```
>Edit.Find ^^t /regex
```

 Bir giriş işareti, tırnak işaretlerinin içinde mi yoksa dışında mı olduğunu görür. Şapka, satırdaki son karakter ise yok sayılır.

 IDE 'nin yerelleştirilmiş sürümlerinde, komut adları IDE 'nin yerel dilinde veya Ingilizce ' de girilebilir. Örneğin, `File.NewFile` `Fichier.NouveauFichier` aynı komutu yürütmek için ya da Fransızca IDE 'de yazabilirsiniz.

 Birçok komutun diğer adları vardır. Komut diğer adlarının listesi için bkz. [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md).

 Aşağıdaki komutlar bağımsız değişkenler ve/veya anahtarlar alır.

|Komut adı|Açıklama|
|------------------|-----------------|
|[Var olan öğeyi Ekle](../../ide/reference/add-existing-item-command.md)|Geçerli çözüme var olan bir dosyayı ekler ve açar.|
|[Mevcut projeyi Ekle](../../ide/reference/add-existing-project-command.md)|Geçerli çözüme mevcut bir projeyi ekler.|
|[Yeni Öğe Ekle](../../ide/reference/add-new-item-command.md)|Geçerli çözüme. htm,. css,. txt veya FRAMESET gibi yeni bir çözüm öğesi ekler ve onu açar.|
|[Ek](../../ide/reference/alias-command.md)|Tüm komut için yeni bir diğer ad oluşturur, komut ve bağımsız değişkenler ya da başka bir diğer ad oluşturur.|
|[Ifadeyi değerlendir](../../ide/reference/evaluate-statement-command.md)|Verilen ifadeyi değerlendirir ve görüntüler.|
|[Bilgi](../../ide/reference/find-command.md)|**Bul ve Değiştir** denetiminde bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar.|
|[Dosyalarda Bul](../../ide/reference/find-in-files-command.md)|Dosyalarında [Bul dosyalarında](../../ide/find-in-files.md)bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar.|
|[Git](../../ide/reference/go-to-command.md)|İmleci belirtilen satıra kaydırır.|
|[Çağrı yığınını Listele](../../ide/reference/list-call-stack-command.md)|Geçerli çağrı yığınını görüntüler.|
|[Ayrıştırılmış kodu Listele](../../ide/reference/list-disassembly-command.md)|Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar.|
|[Belleği listeleme](../../ide/reference/list-memory-command.md)|Belirtilen bellek aralığının içeriğini görüntüler.|
|[Liste modülleri](../../ide/reference/list-modules-command.md)|Geçerli işlem için modülleri listeler.|
|[Kayıt listeleri](../../ide/reference/list-registers-command.md)|Yazmaçların bir listesini görüntüler.|
|[Kaynağı Listele](../../ide/reference/list-source-command.md)|Belirtilen kaynak kodu satırlarını görüntüler.|
|[Iş parçacıklarını Listele](../../ide/reference/list-threads-command.md)|Geçerli programdaki iş parçacıklarının listesini görüntüler.|
|[Günlük komut penceresi çıkışı](../../ide/reference/log-command-window-output-command.md)|Komut penceresi tüm giriş ve çıkışları bir dosyaya kopyalar.|
|[Yeni dosya](../../ide/reference/new-file-command.md)|Yeni bir dosya oluşturur ve onu seçili olan projeye ekler.|
|[Dosya Aç](../../ide/reference/open-file-command.md)|Var olan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır.|
|[Projeyi aç](../../ide/reference/open-project-command.md)|Mevcut bir projeyi açar ve projeyi geçerli çözüme eklemenize olanak sağlar.|
|[Çözümü aç](../../ide/reference/open-solution-command.md)|Varolan bir çözümü açar.|
|[Yazdır](../../ide/reference/print-command.md)|İfadeyi değerlendirir ve sonuçları veya belirtilen metni görüntüler.|
|[Hızlı Izle komutu](../../ide/reference/quick-watch-command.md)|**Hızlı izleme** Iletişim kutusunun **ifade** alanında seçili veya belirtilen metni görüntüler.|
|[Değiştirin](../../ide/reference/replace-command.md)|**Bul ve Değiştir** denetiminde bulunan seçeneklerin bir alt kümesini kullanarak dosyalardaki metni değiştirir.|
|[Dosyalarda Değiştir](../../ide/reference/replace-in-files-command.md)|Dosyalardaki metni [Değiştir dosyalarında](../../ide/replace-in-files.md)bulunan seçeneklerin bir alt kümesini kullanarak değiştirir.|
|[Geçerli yığın çerçevesini ayarla](../../ide/reference/set-current-stack-frame-command.md)|Belirli bir yığın çerçevesini görüntülemenize izin verir.|
|[Geçerli Iş parçacığını ayarla](../../ide/reference/set-current-thread-command.md)|Belirli bir iş parçacığını görüntülemenize izin verir.|
|[Radix ayarla](../../ide/reference/set-radix-command.md)|Görüntülenecek bayt sayısını belirler.|
|[Kabuk](../../ide/reference/shell-command.md)|Komutu komut [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] isteminden yürütülene rağmen, içinden programları başlatır.|
|[ShowWebBrowser komutu](../../ide/reference/showwebbrowser-command.md)|Bir Web tarayıcı penceresinde belirttiğiniz URL 'YI tümleşik geliştirme ortamı (IDE) veya IDE 'nin dışında görüntüler.|
|[Başlangıç](../../ide/reference/start-command.md)|Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar.|
|[Yol](../../ide/reference/symbol-path-command.md)|Hata ayıklayıcının simge araması için dizinlerin listesini ayarlar.|
|[Kesme noktasını aç](../../ide/reference/toggle-breakpoint-command.md)|Dosyadaki geçerli konumda, geçerli durumuna bağlı olarak, kesme noktasını açar veya kapatır.|
|[İzle komutu](../../ide/reference/watch-command.md)|Bir **Gözcü** penceresinin belirtilen bir örneğini oluşturur ve açar.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
