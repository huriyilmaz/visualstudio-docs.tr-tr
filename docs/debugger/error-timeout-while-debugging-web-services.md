---
title: Web hizmetlerinde hata ayıklanırken zaman aşımı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 87a2d79fc24bdb433fbb5eb1480dbf5d15520a8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871110"
---
# <a name="error-timeout-while-debugging-web-services"></a>Hata: Web Hizmetlerinde Hata Ayıklarken Zaman Aşımı
Çağıran koddan bir XML Web hizmetine adımlıyorsanız, çağrı bazen zaman aşımına uğrar ve bu da hata ayıklamaya devam edemeyebilirsiniz. Bunun gibi bir hata iletisi görebilirsiniz.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>Çözüm
 Bu sorundan kaçınmak için, XML Web hizmeti çağrısının zaman aşımı değerini, bu örnekte gösterildiği gibi sonsuz olarak ayarlayın:

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
