---
title: Hata ayıklayıcı Hizmetleri belleği azalıyor | Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737837"
---
# <a name="debugger-services-running-out-of-memory"></a>Belleği Dolan Hata Ayıklayıcı Hizmetleri
Hata ayıklama hizmetlerinin belleği tükendi ve hata ayıklama oturumunun sonlandırmasına neden oldu.

## <a name="to-investigate-this-error-on-windows"></a>Windows 'da bu hatayı araştırmak için
- Hedef uygulamanın bellekte çok büyük büyümeye mi karşılaşmadığını görmek için **Tanılama araçları** penceresinde işlem belleği grafiğini kontrol edebilirsiniz. Bu durumda, temel alınan sorunun ne olduğunu tanılamak için **bellek kullanımı** aracını kullanın, bkz. [bellek kullanımını analiz etme](../profiling/memory-usage.md).

- Hedef uygulama çok miktarda bellek tüketmezse, Visual Studio 'nun bellek kullanımını (devenv. exe), çalışan işlemini (Msvsmon. exe) veya VS Code (vsdbg. exe/vsdbg-ui. exe) kullanarak bu **görevin** bir şekilde kullanıma hazır olup olmadığını denetleyin. hata ayıklayıcı sorunu. Belleğin tükenme işlemi devenv. exe ise, çalışan Visual Studio uzantılarının sayısını azaltmayı göz önünde bulundurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Blog gönderisi: hata ayıklarken CPU ve belleği çözümleme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Bellek yönetimi hakkında](/windows/win32/memory/about-memory-management)
