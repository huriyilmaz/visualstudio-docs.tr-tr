---
title: 'Nasıl yapılsın: Windows için Otomasyon Sağlayın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707960"
---
# <a name="how-to-provide-automation-for-windows"></a>Nasıl yapilir: Pencereler için otomasyon sağlayın

Belge ve takım pencereleri için otomasyon sağlayabilirsiniz. Otomasyon sağlamak, bir pencerede otomasyon nesnelerini kullanılabilir hale getirmek istediğinizde tavsiye edilir ve ortam, görev listesinde olduğu gibi hazır bir otomasyon nesnesi sağlamaz.

## <a name="automation-for-tool-windows"></a>Takım pencereleri için otomasyon

Ortam, aşağıdaki yordamda açıklandığı gibi standart <xref:EnvDTE.Window> bir nesneyi döndürerek bir takım penceresinde otomasyon sağlar:

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Yöntemi çevre üzerinden [__VSFPROPID çağırın. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>)nesneyi `VSFPROPID` almak için parametre olarak VSFPROPID_ExtWindowObject. `Window`

2. Arayan, araç pencereniz için VSPackage'a özgü <xref:EnvDTE.Window.Object%2A>bir otomasyon `QueryInterface` nesnesi `IDispatch` istediğinde, ortam , veya arabirimleri çağırır. `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> Her `IExtensibleObject` `IVsExtensibleObject` ikisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> de ve bir yöntem sağlar.

3. Ortam daha sonra `GetAutomationObject` geçen `NULL`yöntemi aradığında, VSPackage'a özgü nesnenizi geri vererek yanıt verin.

4. Eğer `QueryInterface` çağrı `IExtensibleObject` `IVsExtensibleObject` ve başarısız olursa, `QueryInterface` `IDispatch`o zaman çevre çağırır.

## <a name="automation-for-document-windows"></a>Belge pencereleri için otomasyon

Bir <xref:EnvDTE.Document> düzenleyici arabirimi <xref:EnvDTE.Document> uygulayarak `IExtensibleObject` ve yanıt vererek nesnenin kendi uygulaması olabilir rağmen standart `GetAutomationObject`bir nesne, ortamdan da kullanılabilir.

Buna ek olarak, bir düzenleyici, <xref:EnvDTE.Document.Object%2A> yöntem aracılığıyla alınan VSPackage'a özgü `IVsExtensibleObject` bir `IExtensibleObject` otomasyon nesnesini, arabirimleri uygulayarak sağlayabilir. [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) RTF belgesine özgü bir otomasyon nesnesi sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
