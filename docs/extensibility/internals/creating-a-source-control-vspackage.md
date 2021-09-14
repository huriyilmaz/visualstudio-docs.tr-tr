---
title: Kaynak Denetimi VSPackage Paketi | Microsoft Docs
description: Kaynak denetimi ile tümleştirilemesi için kaynak denetimi için derin tümleştirme yolu oluşturan bir kaynak denetimi VSPackage Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e45d798dab342bb50084b467f56f719523ec1df4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626145"
---
# <a name="create-a-source-control-vspackage"></a>VSPackage kaynak denetimi oluşturma
Bu belge, ile tümleştirilmiş bir kaynak denetim paketinin mimarisine genel bakış bağlantılarını, uygulanacak arabirimler tarafından tanımlanan API'yi ve tüketilen hizmetleri ve basit bir kaynak denetim paketi uygulamasını gösteren bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örneği içerir.

 VsPackage kaynak denetimi ile, kaynak denetimi ile tümleştirilemesi için derin bir tümleştirme yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturabilirsiniz. Paketin tarafından barındırılan varsayılan kaynak denetimi kullanıcı arabirimini atlayarak, proje sisteminden gelen kaynak denetimi isteklerine yanıt vermesine ve Çözüm Gezgini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gibi **bileşenlerle etkileşime Çözüm Gezgini.** , [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] iş [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortaklarını bir hizmet modeli kullanarak tümleştirilen bir VSPackage oluşturma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mekanizmasıyla güçlendirmektedir.

## <a name="in-this-section"></a>Bu bölümde
- [Kullanmaya başlama](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 'de kaynak denetimi özelliklerini uygulamak için kaynak denetimi eklentisine daha gelişmiş bir alternatif olan kaynak denetim paketini ele [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] atır.

- [Mimari](../../extensibility/internals/source-control-vspackage-architecture.md)

 Bir diyagram sunar ve kaynak denetim paketinin bileşenlerini açıklar.

- [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)

 Kaynak denetim paketinin çeşitli özelliklerini açıklar.

- [Tasarım öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Bir kaynak denetim paketinin derin tümleştirme için uygulaması gereken VSPackage yapısını açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Kaynak denetimi kullanıcı arabiriminde (UI) kaynak denetimi işlevselliği sağlar bir kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eklentisinin nasıl oluşturulacaklarını açıklar.

- [Kaynak denetimi](../../extensibility/internals/source-control.md)

 Tümleşik bir özelliği olarak kaynak denetimi uygulama seçeneklerini ele [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alan.
