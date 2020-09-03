---
title: Kaynak denetimi VSPackage oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196959"
---
# <a name="creating-a-source-control-vspackage"></a>Kaynak Denetimi VSPackage’ı Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belge, ile tümleştirilmiş bir kaynak denetimi paketinin mimarisine genel bakış [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , uygulanacak arabirimler tarafından tanımlanan API ve tüketilen hizmetler ve basit bir kaynak denetimi paket uygulamasını gösteren bir örnek içerir.  
  
 Kaynak denetimi VSPackage ile tümleştirilecek kaynak denetimi için derin bir tümleştirme yolu oluşturabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Paketin tarafından barındırılan varsayılan kaynak denetimi kullanıcı arabirimini atlamasına [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , Proje sisteminden gelen kaynak denetim isteklerini yanıtlamasını ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Çözüm Gezgini**gibi bileşenlerle etkileşime geçmesini sağlar. , [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Hizmet modeli kullanarak tümleştirilebilen bir VSPackage oluşturma mekanizmasına sahip iş ortakları sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 ' De kaynak denetimi özelliklerinin uygulanması için kaynak denetim eklentisinin daha gelişmiş bir alternatifi olan kaynak denetimi paketini açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Mimari](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Bir diyagram sunar ve bir kaynak denetimi paketinin bileşenlerini açıklar.  
  
 [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)  
 Bir kaynak denetimi paketinin çeşitli özelliklerini açıklar.  
  
 [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Bir kaynak denetimi paketinin derin tümleştirme için uygulanması gereken VSPackage yapısını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Kaynak denetimi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kullanıcı arabiriminde (UI) kaynak denetimi işlevselliği sağlayan bir kaynak denetimi eklentisinin nasıl oluşturulacağını açıklar.  
  
 [Kaynak Denetimi](../../extensibility/internals/source-control.md)  
 ' Nin tümleşik özelliği olarak kaynak denetimi uygulama seçeneklerini açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
