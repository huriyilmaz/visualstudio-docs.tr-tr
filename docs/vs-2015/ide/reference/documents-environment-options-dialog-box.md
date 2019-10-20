---
title: Belgeler, ortam, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 705b1a5992d1a3e7931c316c713d46e7e8c7f72e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657778"
---
# <a name="documents-environment-options-dialog-box"></a>Belgeler, Ortam, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tümleşik geliştirme ortamındaki (IDE) belgelerin görüntülenmesini denetlemek ve belge ve dosyalardaki dış değişiklikleri yönetmek için **Seçenekler** iletişim kutusunun bu sayfasını kullanın. Bu iletişim kutusuna, **Araçlar** menüsünden **Seçenekler** ' i ve ardından **ortam** düğümündeki **Belgeler** ' i seçerek erişebilirsiniz. **Belgeler** listede görünmüyorsa, **Seçenekler** Iletişim kutusunda **tüm ayarları göster** ' i seçin.

> [!NOTE]
> İletişim kutularında kullanılabilen seçenekler ve gördüğünüz menü komutlarının adları ve konumları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım altında açıklananlar arasından farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Kaydedilmişse geçerli belge penceresini yeniden kullan** Seçildiğinde, geçerli belgeyi kaydettiyseniz kapatır ve aynı pencerede yeni bir belge açar. Geçerli belgeniz kaydedilmadıysa açık kalır ve yeni belge ayrı bir pencerede açılır. Bu seçenek silinirse, yeni belgeler her zaman ayrı bir pencere olarak açılır.

 Çok bölgeli kesme ve yapıştırma işlemlerini nadiren gerçekleştirir ve çalışma alanınızda açık belge ve pencere sayısını en aza indirmek isterseniz, bu seçeneği deneyin.

 **Dosya ortamın dışında değiştirildiğinde Algıla** Bu seçenek belirlendiğinde, bir ileti, IDE dışında bir düzenleyici tarafından yapılmış olan açık bir dosyadaki değişiklikleri hemen bilgilendirir. İleti, dosyayı depolamadan yeniden yüklemenize olanak sağlar.

 **Kaydedildiğinde, değişiklikleri otomatik yükle** **Dosyanın Seçili ortamın dışında ne zaman değiştirildiğini** ve IDE 'nin IDE dışında değiştiğini tespit ettiğinizde, varsayılan olarak bir uyarı iletisi oluşturulur. Bu seçenek etkinleştirilirse, hiçbir uyarı görünmez ve dış değişikliklerin çekilmesi için belge IDE 'de yeniden yüklenir.

 **Salt okuma dosyalarının düzenlenmesine Izin ver; kaydetme girişiminde uyar** Bu seçenek etkinleştirildiğinde, salt okunurdur bir dosyayı açabilir ve düzenleyebilirsiniz. İşiniz bittiğinde, değişikliklerinizin bir kaydını kaydetmek istiyorsanız dosyayı yeni bir adla kaydetmek için **farklı kaydet**komutunu kullanmanız gerekir.

 **Şu anda etkin olan belgenin dizinini kullanarak dosya aç** Seçildiğinde, bu seçenek **Dosya Aç** iletişim kutusunun etkin belgenin dizinini görüntülediğini belirtir. Bu seçenek temizlenmiş olduğunda **Dosya Aç** iletişim kutusu, bir dosyayı açmak için en son kullanılan dizini görüntüler.

 **Yükün tutarlı satır sonlarını denetle** Düzenleyicinin bir dosyadaki satır sonlarını taramasını sağlamak ve satır sonları nasıl biçimlendirildiğine ilişkin tutarsızlıklar algılanırsa ileti kutusu göstermek için bu seçeneği belirleyin.

 **Genel geri alma, düzenlenen dosyaları değiştirecek olduğunda uyarı görüntüle** **Genel geri alma** komutu yeniden düzenleme işleminden sonra değiştirilen dosyalarda yapılan yeniden düzenleme değişikliklerini geri aldığınızda bir ileti kutusu göstermek için bu seçeneği belirleyin. Ön yeniden düzenleme durumuna bir dosya döndürmek dosyada yapılan sonraki değişiklikleri atabilir.

 **Çözüm Gezgini çeşitli dosyaları göster** **Çözüm Gezgini**Içindeki **çeşitli dosyalar** düğümünü göstermek için bu seçeneği belirleyin. Çeşitli dosyalar bir proje veya çözümle ilişkilendirilmemiş ancak kolaylık olması için **Çözüm Gezgini** içinde görünebilen dosyalardır.

> [!NOTE]
> Etkin Web uygulamasına dahil edilen Web belgelerinin **Dosya** menüsünde **Tarayıcıda görüntüle** komutunu etkinleştirmek için bu seçeneği belirleyin.

 **çeşitli dosyalar projesinde kaydedilen** **\<** *n* > öğeleri, **Çözüm Gezgini** **MiscellaneousFiles** klasöründe kalıcı hale getiriedilecek dosya sayısını belirtir. Bu dosyalar, bir düzenleyicide artık açık olmasalar bile listelenir. 0 ile 256 arasında bir tamsayı belirtebilirsiniz. Varsayılan sayı 0 ' dır.

 Örneğin, bu seçeneği 5 olarak ayarlarsanız ve 10 çeşitli dosyanın açık olması halinde, tüm 10 dosyalarını kapattığınızda, ilk 5, **diğer dosyalar** klasöründe gösterilmeye devam eder.

 **Veriler kod sayfasına kaydedilemediğinde belgeleri Unicode olarak kaydet** Seçili kod sayfasıyla uyumsuz bilgiler içeren dosyaların varsayılan olarak Unicode olarak kaydedilmesini sağlamak için bu seçeneği belirleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Ortam seçenekleri Iletişim kutusu](../../ide/reference/environment-options-dialog-box.md) [çeşitli dosyalar](../../ide/reference/miscellaneous-files.md) [metin bulma ve değiştirme](../../ide/finding-and-replacing-text.md)
