---
title: Birlikte çalışma derlemelerini kullanan komutlar ve menüler | Microsoft Docs
description: Birlikte çalışma derlemelerini kullanarak bir VSPackage içinde menü ve araç çubuğu komutları uygularken tamamlanması gereken görevler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5a487c2fe6f97e338924a0b8c682f9dd9798571
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057240"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Birlikte çalışma derlemelerini kullanan komutlar ve menüler
Birlikte çalışabilirlik derlemelerini kullanarak menü ve araç çubuğu komutlarını uygulayan VSPackage şunları sağlamalıdır:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamına (IDE), desteklediği komutlar ve şu anda etkin olup olmadığını bildirin.

- Komutları işlemek için kurallara (sözleşme) bağlı olarak.

- Ya da arabirimini kullanarak komut işlemesini açık bir şekilde uygulayın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

  Aşağıdaki bölümde bu görevlerin nasıl yapılacağı açıklanmaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [Birlikte çalışabilirlik derlemelerini kullanarak komut durumunu belirleme](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Bir VSPackage 'ın hangi komutların desteklediği ve şu anda etkin olup olmadıkları hakkında IDE 'ye nasıl bildirim sağladığını açıklar.

- [Birlikte çalışma derlemelerindeki komut sözleşmeleri](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Birlikte çalışma derlemelerini kullanarak tüm VSPackages uygulayan komutları tarafından kullanılan temel komut sözleşmesinin tanımını sağlar.

- [Komut uygulama](../../extensibility/internals/command-implementation.md)

 VSPackage 'ın bir komutu nasıl uyguladığını gösteren bir genel bakış sağlar.

- [Birlikte çalışma bütünleştirilmiş kodu komut işleyicilerini Kaydet](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Bir VSPackage 'ın bir komut işleyicisi sağladığını IDE 'ye bildirmek için gereken kayıt defteri girdilerini açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)

 Hangi VSPackage komutlarının kullanılabilir olduğunu ve hangi nesnenin onları işlediğini belirlemek için IDE tarafından kullanılan kriterleri açıklar.

- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut desteğini kullanan bir kullanıcı arabirimi oluşturma hakkında ayrıntılı bilgi sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [VSPackages 'de komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)

 Doğru komut isteğiyle bir nesneyi ilişkilendirmek için kullanılan işleme genel bakış.
