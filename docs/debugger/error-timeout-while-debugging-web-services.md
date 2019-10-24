---
title: 'Hata: Web hizmetlerinde hata ayıklanırken zaman aşımı | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aba4fef3e1c787651eb961f80b3507090f250a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736885"
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
