---
title: Kaynak Denetimi VSPackage Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709187"
---
# <a name="create-a-source-control-vspackage"></a>Bir kaynak denetimi vspackage oluşturma
Bu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dokümantasyon, entegre edilmiş bir kaynak denetim paketinin mimari genel bakışına, uygulanacak arabirimler tarafından tanımlanan API'ye ve tüketilecek hizmetlere ve basit bir kaynak denetim paketi uygulamasını gösteren bir örneğe bağlantılar içerir.

 Bir kaynak denetimi VSPackage ile, kaynak denetimi ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tümleştirmek için derin bir entegrasyon yolu oluşturabilirsiniz. Paketin barındırılan varsayılan kaynak denetimi UI'sini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]atlayabilmesini, proje sisteminden gelen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetim isteklerine yanıt vermesini ve **Solution Explorer**gibi bileşenlerle etkileşimde durmasını sağlar. İş [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ortaklarını, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir hizmet modeli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanarak tümleştirebilen bir VSPackage oluşturmak için bir mekanizmayla güçlendirir.

## <a name="in-this-section"></a>Bu bölümde
- [başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Kaynak denetim özellikleri uygulamak için kaynak denetim eklentisi için daha gelişmiş bir alternatif [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]olan kaynak kontrol paketi, tartışır.

- [Mimari](../../extensibility/internals/source-control-vspackage-architecture.md)

 Bir diyagram sunar ve kaynak denetim paketinin bileşenlerini açıklar.

- [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)

 Kaynak denetim paketinin çeşitli özelliklerini açıklar.

- [Tasarım öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Bir kaynak kontrol paketinin derin tümleştirme için uygulaması gereken VSPackage'ın yapısını açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Kaynak kontrol eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Kaynak denetimi kullanıcı arabiriminde (UI) kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] işlevselliği sağlayan bir kaynak denetimi eklentisinin nasıl oluşturulutur?

- [Kaynak denetimi](../../extensibility/internals/source-control.md)

 Kaynak denetiminin tümleşik bir özelliği olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]uygulanması na yönelik seçenekleri tartışır.
