---
title: Proje Bağlamı | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706595"
---
# <a name="project-context"></a>Proje Bağlamı
Kullanıcı proje ve proje öğeleri ni eklediği veya bunlarla çalıştığı zaman, IDE çeşitli işlemlerin nasıl gerçekleştirileceğini belirlemek için proje bağlamı kavramını kullanır.

 Genellikle dosyalar, **Kullanıcının Yeni Proje** komutunu seçerek açıkça oluşturduğu veya **Dosya** menüsündeki **Projeyi Aç** komutunu seçerek kullanılabilir hale getiren standart proje nesneleridir. Bu gibi durumlarda, dosyalar bir proje bağlamında oluşturulur ve açılır ve proje türü belgeyi düzenlemek için bağlamı tanımlar.

 Bazı projeler çok zengin bir bağlam sağlar. Örneğin, proje, veri bağlama için proje kapsamında, programlı ad alanı veya proje kapsamı yla kaplanmış veritabanı bağlantısını yönetir. Kullanıcı, Solution Explorer'da görüntülenen proje öğesi gibi belirli bir proje nesnesi kullanarak dosyaları veya veritabanı bağlantılarını sık sık doğrudan açabilir.

 Diğer zamanlarda, bir öğenin proje bağlamı açıkça belirtilmemiştir. Örneğin, kullanıcı **Dosya** menüsünde **Varolan Dosyayı Aç** komutunu seçerek, hata ayıklayıcı bir dosya üzerinde çalıştığında veya kullanıcı Bul **ve Değiştir** iletişim kutusunda **Dosyalarda Bul** komutunu tıklattığında bir öğenin bağlamı kullanılamaz. Bu durumları işlemek için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> IDE bir belgeyi açmak için en iyi projeyi bulma işlemini yönetmek için çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Önceliği](../../extensibility/internals/project-priority.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
