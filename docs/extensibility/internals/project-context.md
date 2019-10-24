---
title: Proje bağlamı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725765"
---
# <a name="project-context"></a>Proje Bağlamı
Kullanıcı, projeleri ve proje öğelerini eklediğinde ya da kullandığında, IDE çeşitli işlemlerin nasıl gerçekleştirileceğini anlamak için proje bağlamı kavramını kullanır.

 Genellikle, dosyalar **Yeni proje** komutunu seçerek veya **Dosya** menüsünde **Proje Aç** komutunu seçerek kullanılabilir hale getirerek kullanıcının açıkça oluşturduğu standart proje nesneleridir. Bu durumlarda dosyalar bir proje bağlamında oluşturulur ve açılır ve proje türü belgeyi düzenlemenin bağlamını tanımlar.

 Bazı projeler çok zengin bir bağlam sağlar. Örneğin, proje, veri bağlama için proje kapsamındaki, programlı bir ad alanını veya proje kapsamlı veritabanı bağlantısını yönetir. Kullanıcı, Çözüm Gezgini ' de bir proje öğesi gibi belirli bir proje nesnesini kullanarak doğrudan dosya ve veritabanı bağlantıları açabilir.

 Diğer zamanlarda, bir öğenin proje bağlamı açıkça belirtilmez. Örneğin, Kullanıcı Dosya menüsündeki **var olan dosyayı aç** komutunu seçerek, hata ayıklayıcısı **bir dosya üzerinde** çalıştığında veya Kullanıcı içindeki **dosyaları Bul komutunu tıkladığında bir öğenin bağlamı kullanılamaz. Bul ve Değiştir** iletişim kutusu. Bu durumları işlemek için IDE, bir belgeyi açmak için en iyi projeyi bulma işlemini yönetmek üzere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Önceliği](../../extensibility/internals/project-priority.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)