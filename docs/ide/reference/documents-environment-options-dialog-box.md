---
title: Belgeler, Ortam, Seçenekler İletişim Kutusu
description: IDE'de belgelerin display'ini kontrol etmek ve belge ve dosyalarda yapılan dış değişiklikleri yönetmek için Belgeler bölümündeki Ortamlar sayfasını kullanmayı öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d86d2606d50d3e65adf9a651a143709d89f83650df83fb90322cac7c7b48c434
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121258960"
---
# <a name="options-dialog-box-environment--documents"></a>Seçenekler iletişim kutusu: Ortam \> Belgeleri

Tümleşik geliştirme ortamında  (IDE) belgelerin görüntülenmelerini kontrol etmek ve belge ve dosyalarda yapılan dış değişiklikleri yönetmek için Seçenekler iletişim kutusunun bu sayfasını kullanın. Araçlar menüsünde Seçenekler'e tıklar **ve** ardından Ortam **Belgeleri'ne** tıklayarak bu iletişim **kutusuna**  >  **erişebilirsiniz.**

**Dosyanın ortamın dışında ne zaman değiştirdiğini algılama**

Bu seçenek seçildiğinde, IDE dışındaki bir düzenleyici tarafından yapılan açık bir dosyada yapılan değişiklikler size hemen bir ileti iletir. İleti, dosyayı depolamadan yeniden yüklemenizi sağlar.

**Değiştirilmemiş değişiklikler olmadığı sürece değiştirilmiş dosyaları yeniden yükleyin**

Dosyanın **ortam dışında ne zaman** değiştirdiğini algıla'nın seçili olduğunu ve IDE'de açık bir dosyanın IDE dışında değiştiğini algıla seçeneğine sahip olursanız, varsayılan olarak bir uyarı iletisi oluşturulur. Bu seçenek etkinse bir uyarı görüntülenir ve belge, dış değişiklikleri almak için IDE'ye yeniden yüklenir.

**Salt okunur dosyaların düzenlenmesine izin verme; kaydetmeye çalışırken uyar**

Bu seçenek etkinleştirildiğinde, salt okunur bir dosyayı açabilir ve düzenleyebilirsiniz. Bitirdikten sonra değişikliklerinizin kaydını **kaydetmek** için Farklı Kaydet komutunu kullanarak dosyayı yeni bir adla kaydetmeniz gerekir.

**Şu anda etkin olan belgenin dizinini kullanarak dosyayı açma**

Bu seçenek seçildiğinde, Dosya Aç **iletişim kutusunun** etkin belgenin dizinini görüntüle olduğunu belirtir. Bu seçenek temiz olduğunda, Dosya **Aç iletişim** kutusu bir dosyayı açmak için en son kullanılan dizini görüntüler.

**Yüklemede tutarlı satır sonlarını denetleme**

Düzenleyicinin bir dosyada satır sonlarını taraması ve satır sonlarını biçimlendirme biçiminde tutarsızlıklar algılanırsa bir ileti kutusu görüntülemesi için bu seçeneği belirleyin.

**Genel geri alma işlemi, düzenlenen dosyaları değiştirecek olduğunda uyarı görüntüleme**

Genel Geri Alma komutu, yeniden  düzenleme işlemi sonrasında da değiştirilen dosyalarda yapılan yeniden düzenleme değişikliklerini geri aldıracak bir ileti kutusu görüntülemek için bu seçeneği belirleyin. Bir dosyayı yeniden düzenleme öncesi durumuna döndürerek dosyada yapılan sonraki değişiklikleri atabilirsiniz.

**Dosyalarda Çeşitli dosyaları Çözüm Gezgini**

içinde Çeşitli Dosyalar **düğümünü görüntülemek için bu seçeneği** Çözüm Gezgini.  Çeşitli dosyalar, bir proje veya çözümle ilişkilendirilen dosyalardır, ancak size kolaylık olması **için Çözüm Gezgini** dosyalarda görünebilir.

> [!NOTE]
> Etkin web uygulamasına dahil **edilen** web  belgelerinin Dosya menüsünde Tarayıcıda Görüntüle komutunu etkinleştirmek için bu seçeneği belirleyin.

**Çeşitli dosyalar projesine kaydedilen öğeler**

dosyanın Çeşitli Dosyalar klasöründe kalıcı **olacak dosya** sayısını Çözüm Gezgini.  Bu dosyalar artık bir düzenleyicide açık kalmasalar bile listelenir. 0 ile 256 arasında herhangi bir tam sayı belirtsiniz. Varsayılan sayı 0'dır.

Örneğin, bu seçeneği 5 olarak ayarsanız ve 10 farklı dosyanız açıksa, 10 dosyanın hepsini kapatsanız, ilk 5 dosya Diğer Dosyalar **klasöründe gösterilmeye devam** ediyor.

**Veriler kodsayfaya kaydedilene kadar belgeleri Unicode olarak kaydetme**

Bilgi içeren dosyaların seçilen kod sayfasıyla uyumsuz olması için varsayılan olarak Unicode olarak kaydedilecek şekilde bu seçeneği belirleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Çeşitli Dosyalar](../../ide/reference/miscellaneous-files.md)
- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
