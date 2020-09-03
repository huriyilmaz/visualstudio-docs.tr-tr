---
title: Kaynak denetimi VSPackage oluşturma | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709187"
---
# <a name="create-a-source-control-vspackage"></a>Kaynak denetimi VSPackage oluşturma
Bu belge, ile tümleştirilmiş bir kaynak denetimi paketinin mimarisine genel bakış [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , uygulanacak arabirimler tarafından tanımlanan API ve tüketilen hizmetler ve basit bir kaynak denetimi paket uygulamasını gösteren bir örnek içerir.

 Kaynak denetimi VSPackage ile tümleştirilecek kaynak denetimi için derin bir tümleştirme yolu oluşturabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Paketin tarafından barındırılan varsayılan kaynak denetimi kullanıcı arabirimini atlamasına [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , Proje sisteminden gelen kaynak denetim isteklerini yanıtlamasını ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Çözüm Gezgini**gibi bileşenlerle etkileşime geçmesini sağlar. , [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hizmet modeli kullanarak tümleştirilebilen bir VSPackage oluşturma mekanizmasına sahip iş ortakları sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Bu bölümde
- [Kullanmaya başlama](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 ' De kaynak denetimi özelliklerinin uygulanması için kaynak denetim eklentisinin daha gelişmiş bir alternatifi olan kaynak denetimi paketini açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Mimari](../../extensibility/internals/source-control-vspackage-architecture.md)

 Bir diyagram sunar ve bir kaynak denetimi paketinin bileşenlerini açıklar.

- [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)

 Bir kaynak denetimi paketinin çeşitli özelliklerini açıklar.

- [Tasarım öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Bir kaynak denetimi paketinin derin tümleştirme için uygulanması gereken VSPackage yapısını açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kullanıcı arabiriminde (UI) kaynak denetimi işlevselliği sağlayan bir kaynak denetimi eklentisinin nasıl oluşturulacağını açıklar.

- [Kaynak denetimi](../../extensibility/internals/source-control.md)

 ' Nin tümleşik özelliği olarak kaynak denetimi uygulama seçeneklerini açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
