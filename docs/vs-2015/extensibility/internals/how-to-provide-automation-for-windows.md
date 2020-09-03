---
title: 'Nasıl yapılır: Windows için Otomasyon sağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191840"
---
# <a name="how-to-provide-automation-for-windows"></a>Nasıl Yapılır: Windows için Otomasyon Sağlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belge ve araç pencereleri için Otomasyon sağlayabilirsiniz. Otomasyon nesnelerini bir pencerede kullanılabilir hale getirmek istediğinizde otomasyon sağlanması önerilir ve ortam, bir görev listesi ile çalıştığı için önceden hazır bir Otomasyon nesnesi sağlamaz.  
  
## <a name="automation-for-tool-windows"></a>Araç pencereleri için Otomasyon  
 Ortam, <xref:EnvDTE.Window> Aşağıdaki yordamda açıklandığı gibi standart bir nesne döndürerek bir araç penceresi üzerinde Otomasyon sağlar:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Araç pencereleri için Otomasyon sağlamak üzere  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> `VSFPROPID` Nesneyi almak için yöntemi parametresi ile ortam aracılığıyla çağırın `Window` .  
  
2. Bir çağıran araç pencerenizin aracılığıyla VSPackage 'a özgü bir Otomasyon nesnesi istediğinde, ortam, <xref:EnvDTE.Window.Object%2A> `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> veya `IDispatch` arabirimlerini çağırır. Her ikisi de `IExtensibleObject` `IVsExtensibleObject` bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> yöntemi sağlar.  
  
3. Ortam daha sonra `GetAutomationObject` yöntemi geçirerek `NULL` , VSPackage 'a özgü nesneyi geri geçirerek yanıtlayın.  
  
4. `QueryInterface`Ve için arama `IExtensibleObject` `IVsExtensibleObject` başarısız olursa, ortam öğesine çağrı yapılır `QueryInterface` `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Belge pencereleri için Otomasyon  
 Standart bir <xref:EnvDTE.Document> nesne, ortamda da kullanılabilir, ancak bir düzenleyici, `T:EnvDTE.Document` arabirimini uygulayarak ve yanıt vererek nesnenin kendi uygulamasına sahip olabilir `IExtensibleObject` `GetAutomationObject` .  
  
 Ayrıca, bir düzenleyici, <xref:EnvDTE.Document.Object%2A> veya arabirimlerini uygulayarak yöntemi aracılığıyla alınan VSPackage 'a özgü bir Otomasyon nesnesi sağlayabilir `IVsExtensibleObject` `IExtensibleObject` . [VSSDK örnekleri](../../misc/vssdk-samples.md) , RTF belgesine özgü bir Otomasyon nesnesine katkıda bulunur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
