---
title: Proje sistemlerine Web Hizmetleri ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002657"
---
# <a name="adding-web-services-to-project-systems"></a>Proje sistemlerine Web Hizmetleri ekleme
XML Web Hizmetleri, genel olarak, SOAP (basit nesne erişim Protokolü) protokolü kullanılarak proje sistemine programlı bilgiler döndüren, URL adreslenebilir kaynaklardır. Arabirimini kullanarak, Web hizmetlerini VSPackage proje sisteminizle tümleştirebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> .  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Proje sisteminize bir Web hizmeti eklemek için  
  
1. `QueryService`Arabirim için <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> hizmet aracılığıyla çağrı <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> .  
  
2. Yöntemini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> . `pDiscoverySession`Parametresi olarak geçirirseniz `NULL` , sizin için bir bulma oturumu oluşturulur ve oturum önbelleğe alınır ve bu sayede arabirim tarafından daha sonra kullanılmak üzere kullanılabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> Yöntem için bir işaretçi döndürür <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Yöntemini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> . Web hizmeti başvuruları klasörü için Otomasyon nesnesini parametresi olarak geçirin `pUnkWebReferenceFolder` . Daha sonra Visual Studio ortamı, Web hizmetinin zaten mevcut olup olmadığını denetler. Web hizmeti yoksa, ortam indirir ve Web hizmetini bir klasöre ve ek dosyalara (. wsdl dosyaları gibi) klasörün alt düğümlerine ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>