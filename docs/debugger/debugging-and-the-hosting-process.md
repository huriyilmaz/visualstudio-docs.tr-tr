---
title: Hata ayıklama ve barındırma Işlemi | Microsoft Docs
ms.date: 08/01/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77df2eae643b658e915662e0f50f6a376141d27
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188463"
---
# <a name="debugging-and-the-hosting-process"></a>Hata Ayıklama ve Barındırma İşlemi
Visual Studio barındırma süreci hata ayıklayıcı performansını geliştirir ve kısmi güven hata ayıklama ve tasarım zamanı ifade değerlendirmesi gibi yeni hata ayıklayıcı özelliklerini sağlar. Gerekirse barındırma işlemini devre dışı bırakabilirsiniz. Aşağıdaki bölümlerde, barındırma işlemi olmadan ve ile hata ayıklama arasındaki bazı farklılıklar açıklanır.

> [!NOTE]
> Visual Studio 2017 ' den başlayarak, barındırma işlemini kullanarak hata ayıklama seçeneği artık gerekli değildir ve kaldırılmıştır. Daha fazla bilgi için bkz. [hata ayıklama: Visual Studio 2017 aims en az sık kullanılan Işinizi hızlandırma](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Kısmi güven hata ayıklama ve bir kez güvenlik
 Kısmi güvenle hata ayıklama barındırma işlemini gerektirir. Barındırma işlemini devre dışı bırakırsanız, **proje özelliklerinin** **güvenlik** sayfasında kısmi güven güvenliği etkin olsa bile kısmi güven hata ayıklaması çalışmaz. Daha fazla bilgi için bkz. [nasıl yapılır: kısmi güven uygulamasında hata ayıklama](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Tasarım zamanı Ifade değerlendirmesi
 Tasarım zamanı ifadesi her zaman barındırma işlemini kullanır. **Proje özelliklerindeki** barındırma işlemini devre dışı bırakmak, sınıf kitaplığı projeleri için tasarım zamanı ifade değerlendirmesini devre dışı bırakır. Diğer proje türleri için tasarım zamanı ifade değerlendirmesi devre dışı değildir. Bunun yerine, Visual Studio gerçek yürütülebiliri başlatır ve barındırma işlemi olmadan tasarım zamanı değerlendirmesi için kullanır. Bu fark farklı sonuçlar üretebilir.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain. CurrentDomain. FriendlyName farkları
 `AppDomain.CurrentDomain.FriendlyName`, barındırma işleminin etkin olmasına bağlı olarak farklı sonuçlar döndürür. Barındırma işlemi etkinken `AppDomain.CurrentDomain.FriendlyName` çağırırsanız, *app_name*`.vhost.exe`döndürür. Bunu çağırdığınızda barındırma işlemi devre dışı bırakılırsa, *app_name*`.exe`döndürür.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). FullName farkları
 `Assembly.GetCallingAssembly().FullName`, barındırma işleminin etkin olmasına bağlı olarak farklı sonuçlar döndürür. Barındırma işlemi etkinken `Assembly.GetCallingAssembly().FullName` çağırırsanız, `mscorlib`döndürür. Barındırma işlemi devre dışı bırakılmışsa `Assembly.GetCallingAssembly().FullName` çağırırsanız, uygulama adını döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Kısmen Güvenilen Uygulamada Hata Ayıklama](debugger-security.md)