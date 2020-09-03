---
title: Proje bağlamı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706595"
---
# <a name="project-context"></a>Proje Bağlamı
Kullanıcı, projeleri ve proje öğelerini eklediğinde ya da kullandığında, IDE çeşitli işlemlerin nasıl gerçekleştirileceğini anlamak için proje bağlamı kavramını kullanır.

 Genellikle, dosyalar **Yeni proje** komutunu seçerek veya **Dosya** menüsünde **Proje Aç** komutunu seçerek kullanılabilir hale getirerek kullanıcının açıkça oluşturduğu standart proje nesneleridir. Bu durumlarda dosyalar bir proje bağlamında oluşturulur ve açılır ve proje türü belgeyi düzenlemenin bağlamını tanımlar.

 Bazı projeler çok zengin bir bağlam sağlar. Örneğin, proje, veri bağlama için proje kapsamındaki, programlı bir ad alanını veya proje kapsamlı veritabanı bağlantısını yönetir. Kullanıcı, Çözüm Gezgini ' de bir proje öğesi gibi belirli bir proje nesnesini kullanarak doğrudan dosya ve veritabanı bağlantıları açabilir.

 Diğer zamanlarda, bir öğenin proje bağlamı açıkça belirtilmez. Örneğin, Kullanıcı **Dosya menüsündeki** **var olan dosyayı aç** komutunu seçerek, hata ayıklayıcı bir dosya üzerinde çalıştığında veya Kullanıcı **Bul ve Değiştir** iletişim kutusunda **dosyalarda bul** komutunu tıkladığında bir öğenin bağlamı kullanılamaz. Bu durumları işlemek için IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> bir belgeyi açmak için en iyi projeyi bulma sürecini yönetmek için çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Önceliği](../../extensibility/internals/project-priority.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
