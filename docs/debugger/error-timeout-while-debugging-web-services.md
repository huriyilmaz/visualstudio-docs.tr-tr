---
description: Kodu çağıran bir XML Web hizmetine adımlarken, çağrı bazen zaman uzabilir ve sonuç olarak hata ayıklamaya devam amazsiniz.
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
ms.openlocfilehash: f7b31ed5f408f8398cd29615c5848ff8b0153f23
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154388"
---
# <a name="error-timeout-while-debugging-web-services"></a>Hata: Web Hizmetlerinde Hata Ayıklarken Zaman Aşımı
Kodu çağıran bir XML Web hizmetine adımlarken, çağrı bazen zaman uzabilir ve sonuç olarak hata ayıklamaya devam amazsiniz. Bunun gibi bir hata iletisiyle karşınız olabilir.

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
