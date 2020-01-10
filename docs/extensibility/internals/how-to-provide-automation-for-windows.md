---
title: 'Nasıl yapılır: Windows için Otomasyon sağlama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848851"
---
# <a name="how-to-provide-automation-for-windows"></a>Nasıl yapılır: Windows için Otomasyon sağlama

Belge ve araç pencereleri için Otomasyon sağlayabilirsiniz. Otomasyon nesnelerini bir pencerede kullanılabilir hale getirmek istediğinizde otomasyon sağlanması önerilir ve ortam, bir görev listesi ile çalıştığı için önceden hazır bir Otomasyon nesnesi sağlamaz.

## <a name="automation-for-tool-windows"></a>Araç pencereleri için Otomasyon

Ortam, aşağıdaki yordamda açıklandığı gibi standart bir <xref:EnvDTE.Window> nesnesi döndürerek bir araç penceresi üzerinde Otomasyon sağlar:

1. __VSFPROPID ortamı aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemi çağırın [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>)`Window` nesnesini almak için `VSFPROPID` parametresi olarak VSFPROPID_ExtWindowObject.

2. Bir çağıran araç pencereniz için <xref:EnvDTE.Window.Object%2A>aracılığıyla VSPackage 'a özgü bir Otomasyon nesnesi istediğinde, ortam `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>veya `IDispatch` arabirimleri için `QueryInterface` çağırır. Hem `IExtensibleObject` hem de `IVsExtensibleObject` bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> yöntemi sağlar.

3. Ortam daha sonra `NULL`geçirme `GetAutomationObject` yöntemi çağırdığında, VSPackage 'a özgü nesneyi geri geçirerek yanıt verin.

4. `IExtensibleObject` için `QueryInterface` çağırıyorsa ve `IVsExtensibleObject` başarısız olursa, ortam `IDispatch`için `QueryInterface` çağırır.

## <a name="automation-for-document-windows"></a>Belge pencereleri için Otomasyon

Bir düzenleyici, `IExtensibleObject` arabirimini uygulayarak ve `GetAutomationObject`yanıt vererek <xref:EnvDTE.Document> nesnenin kendi uygulamasına sahip olmasına rağmen, bir standart <xref:EnvDTE.Document> nesnesi de kullanılabilir.

Ayrıca, bir düzenleyici, `IVsExtensibleObject` veya `IExtensibleObject` arabirimlerini uygulayarak <xref:EnvDTE.Document.Object%2A> yönteminden alınan VSPackage 'a özgü bir Otomasyon nesnesi sağlayabilir. [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) , RTF belgesine özgü bir Otomasyon nesnesine katkıda bulunur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
