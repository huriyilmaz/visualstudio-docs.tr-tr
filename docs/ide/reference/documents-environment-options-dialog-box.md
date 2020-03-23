---
title: Belgeler, Ortam, Seçenekler İletişim Kutusu
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7813a2e7686bef5a146e7472bce7f2c24baf9cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570069"
---
# <a name="options-dialog-box-environment--documents"></a>Seçenekler iletişim kutusu: \> Ortam Belgeleri

Tümleşik geliştirme ortamındaki (IDE) belgelerin görüntülenmesini denetlemek ve belgelerde ve dosyalardaki dış değişiklikleri yönetmek için **Seçenekler** iletişim kutusunun bu sayfasını kullanın. **Araçlar** menüsünde **Seçenekler'i** tıklatıp **çevre** > **belgelerini**seçerek bu iletişim kutusuna erişebilirsiniz.

**Dosyanın ortam dışında ne zaman değiştirilmede değiştirilmesini algılama**

Bu seçenek seçildiğinde, bir ileti, IDE dışındaki bir düzenleyici tarafından yapılan açık bir dosyadaki değişiklikleri hemen size iletir. İleti, dosyayı depolama dan yeniden yüklemenize olanak tanır.

**Kaydedilmemiş değişiklikler olmadığı sürece değiştirilen dosyaları yeniden yükleme**

**Dosyaseçilen ortamın dışında ne zaman değiştirildiğini** algılat'a ve IDE'deki açık bir dosya IDE dışında değiştiğinde, varsayılan olarak bir uyarı iletisi oluşturulur. Bu seçenek etkinleştirilirse, hiçbir uyarı görünmez ve belge dış değişiklikleri almak için IDE'de yeniden yüklenir.

**Salt okunur dosyaların düzenlenmesine izin ver; kaydetmeye çalışırken uyar**

Bu seçenek etkinleştirildiğinde, salt okunur dosyasını açıp edinebilirsiniz. İşinizi bitirdiğinizde, değişikliklerinizin kaydını kaydetmek istiyorsanız dosyayı yeni bir ada kaydetmek için Farklı **Kaydet** komutunu kullanmanız gerekir.

**Şu anda etkin olan belgenin dizinini kullanarak dosyayı açma**

Seçildiğinde, bu seçenek Dosya **aç** iletişim kutusunun etkin belgenin dizinini görüntülemesini belirtir. Bu seçenek temizlendiğinde, **Dosyayı Aç** iletişim kutusu, dosyayı açmak için en son kullanılan dizini görüntüler.

**Yükte tutarlı hat sonları olup yok**

Satır sonları biçimlendirilmesinde tutarsızlıklar algılanırsa, düzenleyicinin dosyadaki satır sonlarını taramasını ve ileti kutusunu görüntülemesini sağlamak için bu seçeneği belirleyin.

**Düzenlenen dosyaları değiştireceği genel geri al edildiğinde uyarı görüntüleme**

**Genel Geri Alma** komutu, yeniden düzenleme işleminden sonra değiştirilen dosyalarda yapılan yeniden düzenleme değişikliklerini geri aldığında bir ileti kutusu görüntülemek için bu seçeneği belirleyin. Bir dosyayı ön düzenleme durumuna döndürmek, dosyada yapılan sonraki değişiklikleri atabilir.

**Çözüm Gezgini'nde Çeşitli dosyaları göster**

Çözüm **Gezgini'nde Çeşitli Dosyalar** düğümünü görüntülemek **Solution Explorer**için bu seçeneği seçin. Çeşitli dosyalar, bir proje veya çözümle ilişkili olmayan ancak kolaylık sağlamak için **Solution Explorer'da** görünebilen dosyalardır.

> [!NOTE]
> Etkin web uygulamasında yer almayan web belgeleri için **Dosya** menüsünde **Tarayıcıda Görüntü** komutunu etkinleştirmek için bu seçeneği belirleyin.

**Çeşitli dosyalar projesinde kaydedilen öğeler**

**Çözüm**Gezgini'nin **Çeşitli Dosyalar** klasöründe kalıcı olacak dosya sayısını belirtir. Bu dosyalar, artık bir düzenleyicide açık olmasalar bile listelenir. 0'dan 256'ya kadar herhangi bir tam sayı belirtebilirsiniz. Varsayılan sayı 0'dır.

Örneğin, bu seçeneği 5 olarak ayarlarsanız ve 10 dosyanız açıksa, 10 dosyanın tümünü kapattığınızda, ilk 5 yine de **Çeşitli Dosyalar** klasöründe gösterilir.

**Veriler kod sayfasına kaydedilemiyorsa belgeleri Unicode olarak kaydetme**

Seçili kod sayfasıyla uyumsuz bilgiler içeren dosyaların varsayılan olarak Unicode olarak kaydedilmesine neden olmak için bu seçeneği belirleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Çeşitli Dosyalar](../../ide/reference/miscellaneous-files.md)
- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
