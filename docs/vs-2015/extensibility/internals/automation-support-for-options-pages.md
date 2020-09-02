---
title: Seçenekler sayfaları için Otomasyon desteği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157248"
---
# <a name="automation-support-for-options-pages"></a>Seçenekler Sayfaları için Otomasyon Desteği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackages, ' de **Araçlar** menüsüne (Araçlar seçenekleri sayfaları) özel **Seçenekler** iletişim kutuları sunabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve bunları otomasyon modeli için kullanılabilir hale getirir.  
  
## <a name="tools-options-pages"></a>Araç seçenekleri sayfaları  
 Bir **araç seçenekleri** sayfası oluşturmak için, bir VSPackage, yöntemin VSPackage 'un uygulamasına <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (veya yönetilen-Code yöntemi) göre, ortama döndürülen bir kullanıcı denetim uygulamasının sağlanması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> .  
  
 Bu yeni sayfaya otomasyon modeli aracılığıyla erişime izin vermek için isteğe bağlıdır, ancak önemle önerilir. Bunu aşağıdaki adımlarla yapabilirsiniz:  
  
1. <xref:EnvDTE._DTE.Properties%2A>Nesneyi IDispatch ile türetilmiş bir nesnenin uygulamasıyla genişletin.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Metodun (veya yönetilen kod için) bir uygulamasını <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> IDispatch 'ten türetilmiş nesneye döndürün.  
  
3. Bir Otomasyon tüketicisi <xref:EnvDTE._DTE.Properties%2A> özel bir **seçenek** özelliği sayfasında yöntemini çağırdığında, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> yöntemini kullanarak özel bir **araç seçenekleri** sayfasının otomasyon uygulamasını elde eder.  
  
4. VSPackage Otomasyon nesnesi, tarafından döndürülen her bir sağlamak için kullanılır <xref:EnvDTE.Property> <xref:EnvDTE._DTE.Properties%2A> .  
  
   Özel bir Araçlar Seçenekler sayfası uygulayan bir örnek için bkz. [VSSDK örnekleri](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Nesnelerini Kullanıma Sunma](../../extensibility/internals/exposing-project-objects.md)
