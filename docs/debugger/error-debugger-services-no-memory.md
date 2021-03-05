---
description: Hata ayıklama hizmetlerinin belleği tükendi ve hata ayıklama oturumunun sonlandırmasına neden oldu.
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
ms.openlocfilehash: d881248652d644e9a82725b0d083d095ff72f885
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147048"
---
# <a name="debugger-services-running-out-of-memory"></a>Belleği Dolan Hata Ayıklayıcı Hizmetleri
Hata ayıklama hizmetlerinin belleği tükendi ve hata ayıklama oturumunun sonlandırmasına neden oldu.

## <a name="to-investigate-this-error-on-windows"></a>Windows 'da bu hatayı araştırmak için
- Hedef uygulamanın bellekte çok büyük büyümeye mi karşılaşmadığını görmek için **Tanılama araçları** penceresinde işlem belleği grafiğini kontrol edebilirsiniz. Bu durumda, temel alınan sorunun ne olduğunu tanılamak için **bellek kullanımı** aracını kullanın, bkz. [bellek kullanımını analiz etme](../profiling/memory-usage.md).

- Hedef uygulama çok miktarda bellek tüketmezse, bu bir hata ayıklayıcı sorunu olup olmadığını anlamak için Visual Studio (devenv.exe), çalışan işlemi (msvsmon.exe) veya VS Code (vsdbg.exe/vsdbg-ui.exe) bellek kullanımını denetlemek için **Görev Yöneticisi** penceresini kullanın. Belleğin tükenme işlemi devenv.exe, çalışan Visual Studio uzantılarının sayısını azaltmayı göz önünde bulundurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Blog gönderisi: hata ayıklarken CPU ve belleği çözümleme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Bellek yönetimi hakkında](/windows/win32/memory/about-memory-management)
