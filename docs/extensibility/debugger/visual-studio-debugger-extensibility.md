---
title: Visual Studio Hata Ayıklayıcı Genişletilebilirliği | Microsoft Docs
description: Bu makalede hata Visual Studio genişletilebilirliği açıklanmıştır ve hata ayıklama ile ilgili makalelere Visual Studio sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d79e85eeddd0bcb6aa14aae889df8a17c743cf5f
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439905"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio ayıklayıcı genişletilebilirliği
Visual Studio, programdaki hataları izlemek için güçlü ve kullanımı kolay bir araç sağlayan, tamamen etkileşimli bir kaynak kodu hata ayıklayıcısı içerir. Hata ayıklayıcısı, Visual Basic, C/C++ ve JavaScript için tam destek içerir. Ancak, Microsoft İndirme Merkezi'nden kullanılabilen ile, diğer programlama dilleri aynı zengin özelliklere sahip hata [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ayıklayıcıda [](https://dotnet.microsoft.com/download/visual-studio-sdks)destek olabilir.

 Hata ayıklayıcı, hata ayıklanan dile özgü olan hata ayıklama bileşenlerine yönelik ortak ön [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uçtır (yani kullanıcı arabirimi). Yeni diller için hata ayıklayıcının desteği için tek gereken hata ayıklama altyapısı (DE) gibi gerekli arka uç [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bileşenlerini oluşturmaktır. Bu noktada devreye [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] gelir.

 , [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] yeni bir DE oluşturmak için gereken tüm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] öğelere eksiksiz bir başvuru içerir. Ayrıca, başlamanıza yardımcı olacak örnekler ve öğreticiler de vardır.

 Hata ayıklama desteğine sahip bir dil proje sisteminin tam örneği için [IronPython örneğine bakın.](https://www.microsoft.com/download/details.aspx?id=55984)

 Aşağıdaki bölümlerde, kullanılarak hata ayıklayıcının nasıl genişletildikleri [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] açıklanmaktadır.

## <a name="in-this-section"></a>Bu bölümde
 [Kullanmaya başlayın](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Hata ayıklamanın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neler sunduğu ve SDK'nın nasıl yük devred teklifleri olduğu açıklanmıştır.

 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Programınızı DE için hazırlamadan DE'nin ayrılmaya kadar olan özel DE işlemini belgeler.

 [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) bir ifade değerlendiricisi yazmanız gerekip gerek olmadığını açıklar.

 [Hata ayıklama altyapısı uygulama stratejisi seçme](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) DE'nizin nasıl uygulandığını ele alan.

 [Başvuru](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Hata Ayıklama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API'sini belgeler.

 [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md) Ortak dil çalışma zamanı ifade değerlendirici örneğine ve hata ayıklama altyapısı örneğine bağlantılar içerir.
