---
title: Hata Ayıklama ve Barındırma Süreci | Microsoft Docs
description: 2017 Visual Studio önceki sürümler için, hata ayıklayıcı performansını geliştirmek ve bazı hata ayıklayıcı özelliklerine erişmek için barındırma işlemini kullanın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626505"
---
# <a name="debugging-and-the-hosting-process"></a>Hata Ayıklama ve Barındırma İşlemi
Bu Visual Studio hata ayıklayıcı performansını artırır ve kısmi güven hata ayıklama ve tasarım zamanı ifadesi değerlendirmesi gibi yeni hata ayıklayıcı özelliklerini sağlar. Gerekirse barındırma işlemini devre dışı 3. Aşağıdaki bölümlerde barındırma işlemiyle ve barındırma olmadan hata ayıklama arasındaki bazı farklar açıklanmaktadır.

> [!NOTE]
> 2017'Visual Studio başlayarak, barındırma işlemini kullanarak hata ayıklama seçeneği artık gerekli değildir ve kaldırılmıştır. Daha fazla bilgi için [bkz. Hata Ayıklama: Visual Studio 2017 En Az Sık Kullanılan İşlerinizi Hızlandırmak için Amaçlar.](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx)

## <a name="partial-trust-debugging-and-click-once-security"></a>Partial-Trust Ayıklama ve Click-Once Güvenlik
 Kısmi güven hata ayıklaması barındırma işlemini gerektirir. Barındırma işlemini devre dışı bıraksanız, Project Özellikleri'nin Güvenlik sayfasında kısmi güven  güvenliği etkinleştirilse bile kısmi güven **hata ayıklaması Project olmaz.** Daha fazla bilgi için, [bkz. How to: Debug a Partial Trust Application](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Design-Time İfade Değerlendirmesi
 Tasarım zamanı ifadesi her zaman barındırma işlemini kullanır. Project Özellikleri'ne barındırma **işlemini devre dışı bırakmak,** Sınıf Kitaplığı projeleri için tasarım zamanı ifadesi değerlendirmesini devre dışı bırakıyor. Diğer proje türleri için tasarım zamanı ifadesi değerlendirmesi devre dışı değildir. Bunun Visual Studio yürütülebilir dosyayı başlatır ve barındırma işlemi olmadan tasarım zamanı değerlendirmesi için kullanır. Bu fark farklı sonuçlar üretebilir.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName Farkları
 `AppDomain.CurrentDomain.FriendlyName` barındırma işleminin etkin olup olmadığına bağlı olarak farklı sonuçlar döndürür. Barındırma işlemi `AppDomain.CurrentDomain.FriendlyName` etkinleştirilmiş olarak çağrısı yapıyorsanız, işlevi `.vhost.exe` app_name. Bunu barındırma işlemi devre dışı olarak çağırsanız, `.exe` app_name.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly() . FullName Farkları
 `Assembly.GetCallingAssembly().FullName` barındırma işleminin etkin olup olmadığına bağlı olarak farklı sonuçlar döndürür. Barındırma işlemi `Assembly.GetCallingAssembly().FullName` etkin olarak çağrısı yapıyorsanız `mscorlib` döndürür. Barındırma işlemi `Assembly.GetCallingAssembly().FullName` devre dışı bırakılmış olarak çağrısı yapıyorsanız, uygulama adını döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Kısmen Güvenilen Uygulamada Hata Ayıklama](debugger-security.md)