---
title: Proje Öğelerinin Açılması ve Kaydedilmesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706965"
---
# <a name="opening-and-saving-project-items"></a>Proje Öğelerini Açma ve Kaydetme
Yeni bir proje türü eklediğinizde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamında (IDE) proje dosyalarınızın açılmasını ve kaydedilmesi durumunda yönetmeniz gerekir. Aşağıdaki konular, dosyaların açılması ve kaydedilmesi için farklı yaklaşımları tartışır.

## <a name="in-this-section"></a>Bu Bölümde
- [Dosya Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 **IDE'nin Açık Dosya** komutunu nasıl işlediğine ve projelerin bu komuta yanıt vermedeki rolüne ilişkin adım adım bir açıklama sağlar.

- [Birlikte Aç Komutunu Kullanarak Dosyaları Görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 IDE'nin Açık Komutu'nu nasıl işlediğine ilişkin **Open With** ayrıntılı, adım adım bir açıklama sağlayarak, bazı standart düzenleyici seçenekleri olan bir dosyanın açılmasını ister.

- [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)

 Projenizde belirli bir türdeki dosyaların projeye özel bir düzenleyici kullanılarak açılması gerektiğini belirtmek için adım adım yönergeler sağlar.

- [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)

 IDE'nin proje türündeki dosyalar için standart bir düzenleyici yi nasıl açacağını belirtmek için adım adım yönergeler sağlar.

- [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)

 Açık bir dosya için projeye özgü bir düzenleyiciyi açmak için adım adım yönergeler sağlar.

- [Standart Belge Kaydetme](../../extensibility/internals/saving-a-standard-document.md)

 IDE'nin **Kaydet,** **Farklı Kaydet**ve Standart bir düzenleyicide açılan bir belge için Tüm komutları **kaydet** işlemlerini nasıl yaptığına ilişkin ayrıntılı bir açıklama sağlar.

- [Özel Belge Kaydetme](../../extensibility/internals/saving-a-custom-document.md)

 IDE'nin **Kaydet,** **Farklı Kaydet**ve Özel bir düzenleyicide açılan belgeler için Tüm komutları **kaydet** işlemlerini nasıl yaptığına ilişkin bir diyagram ve ayrıntılı açıklama sağlar.

- [Projedeki Bir Dosyayı Hangi Düzenleyicinin Açacağını Belirleme](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Bir dosya için uygun düzenleyiciyi veya tasarımcıyı seçmek için IDE'nin izlediği işlemi tartışır.

## <a name="related-sections"></a>İlgili Bölümler
- [Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../../extensibility/creating-custom-editors-and-designers.md)

 IDE'nin barındırabileceği dört editör türünü listeler ve her editörün açıklamalarını verir.

- [Proje Türleri](../../extensibility/internals/project-types.md)

 Projelerin kodun derlenme ve oluşturulme biçimini, düzenleyicilerin nasıl açıldığını ve proje öğelerinin nasıl biçimlendirilip biçimlendirilebildiğini tartışır.
