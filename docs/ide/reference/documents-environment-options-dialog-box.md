---
title: Belgeler, Ortam, Seçenekler İletişim Kutusu
description: Belgeler bölümündeki ortamlar sayfasını kullanarak IDE 'deki belgelerin görüntülenmesini denetleyebilir ve belge ve dosyalardaki dış değişiklikleri yönetebilir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9ed6833bd60854cf2e3bcfbab76d57c7010f7863
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882140"
---
# <a name="options-dialog-box-environment--documents"></a>Seçenekler iletişim kutusu: ortam \> belgeleri

Tümleşik geliştirme ortamındaki (IDE) belgelerin görüntülenmesini denetlemek ve belge ve dosyalardaki dış değişiklikleri yönetmek için **Seçenekler** iletişim kutusunun bu sayfasını kullanın. Bu iletişim kutusuna, **Araçlar** menüsünde **Seçenekler** ' i ve ardından **ortam** belgeleri ' ni seçerek erişebilirsiniz  >  .

**Dosya ortamın dışında değiştirildiğinde Algıla**

Bu seçenek belirlendiğinde, bir ileti, IDE dışında bir düzenleyici tarafından yapılmış olan açık bir dosyadaki değişiklikleri hemen bilgilendirir. İleti, dosyayı depolamadan yeniden yüklemenize olanak sağlar.

**Kaydedilmemiş değişiklikler olmadıkça değiştirilen dosyaları yeniden yükle**

**Dosyanın Seçili ortamın dışında ne zaman değiştirildiğini** ve IDE 'nin IDE dışında değiştiğini tespit ettiğinizde, varsayılan olarak bir uyarı iletisi oluşturulur. Bu seçenek etkinleştirilirse, hiçbir uyarı görünmez ve dış değişikliklerin çekilmesi için belge IDE 'de yeniden yüklenir.

**Salt okuma dosyalarının düzenlenmesine izin ver; kaydetme denemesi sırasında uyar**

Bu seçenek etkinleştirildiğinde, salt okunurdur bir dosyayı açabilir ve düzenleyebilirsiniz. İşiniz bittiğinde, değişikliklerinizin bir kaydını kaydetmek istiyorsanız dosyayı yeni bir adla kaydetmek için **farklı kaydet** komutunu kullanmanız gerekir.

**Şu anda etkin olan belgenin dizinini kullanarak dosya aç**

Seçildiğinde, bu seçenek **Dosya Aç** iletişim kutusunun etkin belgenin dizinini görüntülediğini belirtir. Bu seçenek temizlenmiş olduğunda **Dosya Aç** iletişim kutusu, bir dosyayı açmak için en son kullanılan dizini görüntüler.

**Yükün tutarlı satır sonlarını denetle**

Düzenleyicinin bir dosyadaki satır sonlarını taramasını sağlamak ve satır sonları nasıl biçimlendirildiğine ilişkin tutarsızlıklar algılanırsa ileti kutusu göstermek için bu seçeneği belirleyin.

**Genel geri alma, düzenlenen dosyaları değiştirecek olduğunda uyarı görüntüle**

**Genel geri alma** komutu yeniden düzenleme işleminden sonra değiştirilen dosyalarda yapılan yeniden düzenleme değişikliklerini geri aldığınızda bir ileti kutusu göstermek için bu seçeneği belirleyin. Ön yeniden düzenleme durumuna bir dosya döndürmek dosyada yapılan sonraki değişiklikleri atabilir.

**Çözüm Gezgini çeşitli dosyaları göster**

**Çözüm Gezgini** Içindeki **çeşitli dosyalar** düğümünü göstermek için bu seçeneği belirleyin. Çeşitli dosyalar bir proje veya çözümle ilişkilendirilmemiş ancak kolaylık olması için **Çözüm Gezgini** içinde görünebilen dosyalardır.

> [!NOTE]
> Etkin Web uygulamasına dahil edilen Web belgelerinin **Dosya** menüsünde **Tarayıcıda görüntüle** komutunu etkinleştirmek için bu seçeneği belirleyin.

**Çeşitli dosyalar projesinde kaydedilen öğeler**

**Çözüm Gezgini** **çeşitli dosyalar** klasöründe kalıcı hale getirmek için dosya sayısını belirtir. Bu dosyalar, bir düzenleyicide artık açık olmasalar bile listelenir. 0 ile 256 arasında bir tamsayı belirtebilirsiniz. Varsayılan sayı 0 ' dır.

Örneğin, bu seçeneği 5 olarak ayarlarsanız ve 10 çeşitli dosyanın açık olması halinde, tüm 10 dosyalarını kapattığınızda, ilk 5, **diğer dosyalar** klasöründe gösterilmeye devam eder.

**Veriler kod sayfasına kaydedilemediğinde belgeleri Unicode olarak kaydet**

Seçili kod sayfasıyla uyumsuz bilgiler içeren dosyaların varsayılan olarak Unicode olarak kaydedilmesini sağlamak için bu seçeneği belirleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Çeşitli dosyalar](../../ide/reference/miscellaneous-files.md)
- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
