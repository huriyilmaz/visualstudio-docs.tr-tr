---
description: Kodu çağıran bir XML Web hizmetine adımlarken, hata ayıklamaya devam etmek için devam edelamayabilirsiniz.
title: Web Hizmetleri hata ayıklama sırasında zaman aşımı | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9270a36015c3227b27d3a921370255e7f15d0aa994f69cb7548f82832b1fb885
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419916"
---
# <a name="error-timeout-while-debugging-web-services"></a>Hata: Web Hizmetlerinde Hata Ayıklarken Zaman Aşımı
Kodu çağıran bir XML Web hizmetine adımlarken, hata ayıklamaya devam etmek için devam edelamayabilirsiniz. Bunun gibi bir hata iletisiyle karşınız olabilir.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>Çözüm
 Bu sorunu önlemek için XML Web hizmetine yapılan çağrının zaman aşımı değerini şu örnekte gösterildiği gibi sonsuz olarak ayarlayın:

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
