---
title: Proje Bağlamı | Microsoft Docs
description: IDE'Visual Studio kullanıcı projelere ve proje öğelerine ekleyen veya bu öğelerle birlikte çalışan işlemleri nasıl gerçekleştireceklerini belirlemek için proje bağlamını nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73e3c8a94607e7e0b31bacddac8e7f19b6139328
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899829"
---
# <a name="project-context"></a>Proje Bağlamı
Kullanıcı projelere ve proje öğelerine ekleyen veya bu öğelerle birlikte çalışan IDE, çeşitli işlemlerin nasıl gerçekleştirileceklerini belirlemek için proje bağlamını kullanır.

 Dosyalar genellikle Yeni Proje komutunu seçerek kullanıcının açıkça oluşturduğu standart proje **nesneleridir** veya  Dosya menüsünden Projeyi Aç komutunu seçerek **kullanılabilir hale** getirebilirsiniz. Bu durumlarda dosyalar proje bağlamında oluşturularak açılır ve proje türü belgeyi düzenleme bağlamını tanımlar.

 Bazı projeler çok zengin bir bağlam sağlar. Örneğin, proje veri bağlama için proje kapsamlı, programlı ad alanını veya proje kapsamlı veritabanı bağlantısını yönetir. Kullanıcı, dosyalarda görüntülenen proje öğesi gibi belirli bir proje nesnesini kullanarak dosyaları veya veritabanı bağlantılarını doğrudan Çözüm Gezgini.

 Diğer zamanlarda, bir öğenin proje bağlamı açıkça belirtilmez. Örneğin, bir öğenin bağlamı, kullanıcı Dosya menüsünde Mevcut Dosyayı  Aç komutunu seçerek bir dosyayı açtığında, hata ayıklayıcı bir dosya  üzerinde çalışmadığında veya  kullanıcı Bul ve Değiştir iletişim kutusunda Dosyalarda Bul komutuna tıkladığında kullanılamaz.  Bu durumların üstesinden gelebilir ve IDE, bir belgeyi açmak için en iyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> projeyi bulma sürecini yönetmeye çağrılar.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Önceliği](../../extensibility/internals/project-priority.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
