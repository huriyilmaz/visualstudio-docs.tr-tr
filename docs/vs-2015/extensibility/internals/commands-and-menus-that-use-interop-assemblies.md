---
title: Birlikte çalışma derlemelerini kullanan komutlar ve menüler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195042"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Birlikte Çalışma Bütünleştirilmiş Kodları Kullanan Komutlar ve Menüler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Birlikte çalışabilirlik derlemelerini kullanarak menü ve araç çubuğu komutlarını uygulayan VSPackage şunları sağlamalıdır:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Tümleşik geliştirme ortamına (IDE), desteklediği komutlar ve şu anda etkin olup olmadığını bildirin.  
  
- Komutları işlemek için kurallara (sözleşme) bağlı olarak.  
  
- Ya da arabirimini kullanarak komut işlemesini açık bir şekilde uygulayın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .  
  
  Aşağıda bu görevlerin nasıl yapılacağı açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Birlikte Çalışma Bütünleştirilmiş Kodları Kullanarak Komut Durumunu Belirleme](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Bir VSPackage 'ın hangi komutların desteklediği ve şu anda etkin olup olmadıkları hakkında IDE 'ye nasıl bildirim sağladığını açıklar.  
  
 [Birlikte Çalışma Bütünleştirilmiş Kodlarında Komut Sözleşmeleri](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Birlikte çalışma derlemelerini kullanarak tüm VSPackages uygulama komutları tarafından kullanılan temel komut sözleşmesinin tanımını sağlar  
  
 [Uygulama](../../extensibility/internals/command-implementation.md)  
 VSPackage 'ın bir komutu nasıl uyguladığını gösteren bir genel bakış sağlar.  
  
 [Birlikte Çalışma Bütünleştirilmiş Kodu Komut İşleyicilerini Kaydetme](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Bir VSPackage 'ın bir komut işleyicisi sağladığını IDE 'ye bildirmek için gereken kayıt defteri girdilerini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanılabilirlik](../../extensibility/internals/command-availability.md)  
 Hangi VSPackage komutlarının kullanılabilir olduğunu ve hangi nesnenin onları işlediğini belirlemek için IDE tarafından kullanılan kriterleri açıklar.  
  
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Komut desteğini kullanan bir kullanıcı arabirimi oluşturma hakkında ayrıntılı bilgi sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [VSPackage’larda Komut Yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)  
 Doğru komut isteğiyle bir nesneyi ilişkilendirmek için kullanılan işleme genel bakış.
