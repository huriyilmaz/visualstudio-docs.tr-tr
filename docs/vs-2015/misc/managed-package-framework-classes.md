---
title: Yönetilen paket çerçevesi sınıfları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297699"
---
# <a name="managed-package-framework-classes"></a>Yönetilen paket çerçevesi sınıfları
Yönetilen paket çerçevesi (MPF) sınıfları, yönetilen kod kullanılarak VSPackages oluşturmak için kullanılabilir. Birçok VSPackage arabirimi için varsayılan uygulamalar sağlarlar. MPF, uygulama ayrıntılarını ve karmaşıklıkları gizleyerek, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en az miktarda kodla tümleştirme ürünleri oluşturmanıza olanak sağlar.  
  
> [!WARNING]
> Yönetilen paket çerçevesi sınıfları içeren derlemelerin çoğu Visual Studio SDK ile birlikte gönderilir. Projeler için yönetilen [paket çerçevesindeki](https://archive.codeplex.com/?p=mpfproj11)projeler Için yönetilen paketlenmiş Framework kaynak kodunu indirebilirsiniz.  
  
## <a name="mpf-namespaces"></a>MPF ad alanları  
 Aşağıdaki tabloda tarafından sunulan MPF ad alanları listelenmektedir [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
|Ad alanı|İçindekiler|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|COM hatalarının, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sabitlerin ve Win32 pencerelerinin işlenmesine yönelik yararlı sınıflar içerir.|  
|<xref:Microsoft.VisualStudio.Package>|Projeler, düzenleyiciler ve MSBuild için yönetilen kod sarmalayıcıları içerir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell>|Birçok yaygın Visual Studio nesnesinin bir uygulamasını türetiytebilmeniz için MPF temel sınıfları içerir.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Tasarımcı uzantılarını içerir.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Serileştirme tasarımcı uzantılarını içerir.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]CodeDOM tasarımcı uzantılarını içerir.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Proje alt türlerini destekler ("türler" olarak da bilinir).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages ve yönetilen paket çerçevesi](../misc/vspackages-and-the-managed-package-framework.md)   
 [Visual Studio birlikte çalışma derlemelerini kullanma](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages ve yönetilen paket çerçevesi](../misc/vspackages-and-the-managed-package-framework.md)