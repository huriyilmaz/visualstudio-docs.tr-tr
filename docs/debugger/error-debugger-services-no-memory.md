---
description: Hata Ayıklama Hizmetleri'nin belleği tükendi ve hata ayıklama oturumunun sonlandırilmesine neden oldu.
title: Hata Ayıklayıcı Hizmetleri Bellek Yetersiz | Microsoft Docs
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
ms.openlocfilehash: fe8ce3949336c9fb323e6477e2aed05b7a5b6365d07f299a84b6203f9c00ba57
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344003"
---
# <a name="debugger-services-running-out-of-memory"></a>Belleği Dolan Hata Ayıklayıcı Hizmetleri
Hata Ayıklama Hizmetleri'nin belleği tükendi ve hata ayıklama oturumunun sonlandırilmesine neden oldu.

## <a name="to-investigate-this-error-on-windows"></a>Bu hatayı Windows
- Hedef uygulamanın bellekte çok büyük **bir** büyüme yaşanmış olup olduğunu görmek için Tanılama Araçları penceresinde işlem belleği grafını kontrol edin. Öyleyse, temel sorunun **ne olduğunu tanılamak** için Bellek Kullanımı aracını kullanın, bkz. [Bellek kullanımını analiz etme.](../profiling/memory-usage.md)

- Hedef uygulama çok fazla bellek tüketmiş gibi görünmüyorsa,  bunun bir hata ayıklayıcısı sorunu olup olmadığını belirlemek için Görev Yöneticisi penceresini kullanarak Visual Studio (devenv.exe), çalışan işleminin (msvsmon.exe) veya VS Code (vsdbg.exe/vsdbg-ui.exe) bellek kullanımını kontrol edin. İşlemde yetersiz bellek varsa devenv.exe uzantı sayısını azaltmayı Visual Studio göz önünde bulundurarak.

## <a name="see-also"></a>Ayrıca bkz.
- [Blog gönderisi: Hata Ayıklama sırasında CPU ve Belleği Analiz Etme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Bellek Yönetimi hakkında](/windows/win32/memory/about-memory-management)
