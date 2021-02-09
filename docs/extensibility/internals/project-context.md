---
title: Proje bağlamı | Microsoft Docs
description: Visual Studio IDE 'nin proje bağlamını nasıl kullandığını öğrenmek için, Kullanıcı projeleri ve proje öğeleri eklendiğinde veya bunlarla çalışırken nasıl işlem yapılacağını belirleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fdc5550cfde44c71b1b663a30cf1824c6edfcf82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907686"
---
# <a name="project-context"></a>Proje Bağlamı
Kullanıcı, projeleri ve proje öğelerini eklediğinde ya da kullandığında, IDE çeşitli işlemlerin nasıl gerçekleştirileceğini anlamak için proje bağlamı kavramını kullanır.

 Genellikle, dosyalar **Yeni proje** komutunu seçerek veya **Dosya** menüsünde **Proje Aç** komutunu seçerek kullanılabilir hale getirerek kullanıcının açıkça oluşturduğu standart proje nesneleridir. Bu durumlarda dosyalar bir proje bağlamında oluşturulur ve açılır ve proje türü belgeyi düzenlemenin bağlamını tanımlar.

 Bazı projeler çok zengin bir bağlam sağlar. Örneğin, proje, veri bağlama için proje kapsamındaki, programlı bir ad alanını veya proje kapsamlı veritabanı bağlantısını yönetir. Kullanıcı, Çözüm Gezgini ' de bir proje öğesi gibi belirli bir proje nesnesini kullanarak doğrudan dosya ve veritabanı bağlantıları açabilir.

 Diğer zamanlarda, bir öğenin proje bağlamı açıkça belirtilmez. Örneğin, Kullanıcı **Dosya menüsündeki** **var olan dosyayı aç** komutunu seçerek, hata ayıklayıcı bir dosya üzerinde çalıştığında veya Kullanıcı **Bul ve Değiştir** iletişim kutusunda **dosyalarda bul** komutunu tıkladığında bir öğenin bağlamı kullanılamaz. Bu durumları işlemek için IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> bir belgeyi açmak için en iyi projeyi bulma sürecini yönetmek için çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Önceliği](../../extensibility/internals/project-priority.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
