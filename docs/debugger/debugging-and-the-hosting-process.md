---
title: Hata ayıklama ve barındırma Işlemi | Microsoft Docs
description: 2017 ' dan önceki Visual Studio sürümler için, hata ayıklayıcı performansını geliştirmek ve bazı hata ayıklayıcı özelliklerine erişmek için barındırma sürecini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b54f42b93c9d0be8371a18c422b857d080740c83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080932"
---
# <a name="debugging-and-the-hosting-process"></a>Hata Ayıklama ve Barındırma İşlemi
Visual Studio barındırma işlemi hata ayıklayıcı performansını geliştirir ve kısmi güven hata ayıklama ve tasarım zamanı ifade değerlendirmesi gibi yeni hata ayıklayıcı özelliklerini sağlar. Gerekirse barındırma işlemini devre dışı bırakabilirsiniz. Aşağıdaki bölümlerde, barındırma işlemi olmadan ve ile hata ayıklama arasındaki bazı farklılıklar açıklanır.

> [!NOTE]
> Visual Studio 2017 ' den başlayarak, barındırma işlemini kullanarak hata ayıklama seçeneği artık gerekli değildir ve kaldırılmıştır. daha fazla bilgi için bkz. [hata ayıklama: en az sık kullanılan işinizi hızlandırmak için Visual Studio 2017 aims](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Partial-Trust hata ayıklama ve Click-Once güvenlik
 Kısmi güvenle hata ayıklama barındırma işlemini gerektirir. barındırma işlemini devre dışı bırakırsanız, **Project özelliklerinin** **güvenlik** sayfasında kısmi güven güvenliği etkin olsa bile kısmi güven hata ayıklaması çalışmaz. Daha fazla bilgi için bkz. [nasıl yapılır: kısmi güven uygulamasında hata ayıklama](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Design-Time Ifade değerlendirmesi
 Tasarım zamanı ifadesi her zaman barındırma işlemini kullanır. **Project özelliklerde** barındırma işlemini devre dışı bırakmak, sınıf kitaplığı projeleri için tasarım zamanı ifade değerlendirmesini devre dışı bırakır. Diğer proje türleri için tasarım zamanı ifade değerlendirmesi devre dışı değildir. bunun yerine, Visual Studio gerçek yürütülebiliri başlatır ve barındırma işlemi olmadan tasarım zamanı değerlendirmesi için kullanır. Bu fark farklı sonuçlar üretebilir.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain. CurrentDomain. FriendlyName farkları
 `AppDomain.CurrentDomain.FriendlyName` barındırma işleminin etkin olup olmadığına bağlı olarak farklı sonuçlar döndürür. `AppDomain.CurrentDomain.FriendlyName`Barındırma işlemini etkin olarak çağırırsanız, *app_name* döndürür `.vhost.exe` . Bunu çağırırsanız barındırma işlemi devre dışı bırakılır, *app_name* döndürür `.exe` .

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). FullName farkları
 `Assembly.GetCallingAssembly().FullName` barındırma işleminin etkin olup olmadığına bağlı olarak farklı sonuçlar döndürür. `Assembly.GetCallingAssembly().FullName`Barındırma işlemi etkin olarak çağırırsanız, döndürür `mscorlib` . `Assembly.GetCallingAssembly().FullName`Barındırma işlemi devre dışı olarak çağırırsanız, uygulama adını döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Kısmen Güvenilen Uygulamada Hata Ayıklama](debugger-security.md)