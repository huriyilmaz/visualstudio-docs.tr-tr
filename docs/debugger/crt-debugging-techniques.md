---
title: CRT hata ayıklama teknikleri | Microsoft Docs
description: C çalışma zamanı (CRT) kitaplığı kullanan bir programda hata ayıklaması yapmak için kullanabileceğiniz çeşitli teknikler vardır. Bu teknik bilgi edinmek için bu makaleyi ve bağlantılarını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b71c91dbcc420fd4cc89a5e86fb976cca738bdcc
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560531"
---
# <a name="crt-debugging-techniques"></a>CRT Hata Ayıklama Teknikleri
C çalışma zamanı kitaplığını kullanan bir programda hata ayıklaması yapıyorsanız, bu hata ayıklama teknikleri yararlı olabilir.

## <a name="in-this-section"></a>Bu Bölümde
 [CRT hata ayıklama kitaplığı kullanımı](../debugger/crt-debug-library-use.md)

 C Run-Time kitaplığı tarafından sağlanan hata ayıklama desteğini açıklar ve araçlara erişmek için yönergeler sağlar.

 [Raporlama makroları](../debugger/macros-for-reporting.md)

 **_RPTn** ve **_RPTFn** makroları hakkında bilgi sağlar (Crtdbg içinde tanımlanır. H), `printf` hata ayıklama için deyimlerin kullanımını değiştirir.

 [Yığın ayırma Işlevlerinin hata ayıklama sürümleri](../debugger/debug-versions-of-heap-allocation-functions.md)

 Yığın ayırma işlevlerinin özel hata ayıklama sürümlerini açıklar; Örneğin, CRT haritaları nasıl çağırır, bunları açıkça çağırma avantajları, dönüştürme nasıl önlenir, istemci bloklarının içindeki ayrı ayırma türlerini izleme ve _DEBUG tanımlamama sonuçları.

 [CRT hata ayıklama yığın ayrıntıları](../debugger/crt-debug-heap-details.md)

 Bellek yönetimine ve hata ayıklama yığınına, hata ayıklama yığınından blok türlerine, hata ayıklama yığınını, yığın durumu raporlama işlevlerine ve yığın ayırma isteklerini izlemeye yönelik bağlantılar sağlar.

 [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)

 İstemci blok kanca işlevleri, ayırma kanca işlevleri, ayırma kancaları ve CRT bellek ayırmaları ve rapor kanca işlevleri bağlantılarını listeler.

 [CRT Kitaplığını Kullanarak Bellek Sızıntılarını Bulma](../debugger/finding-memory-leaks-using-the-crt-library.md)

 Hata ayıklayıcı ve C Run-Time kitaplığını kullanarak bellek sızıntılarını algılama ve yalıtma tekniklerini ele alır.

## <a name="related-sections"></a>İlgili Bölümler

- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md) -C ve C++ uygulamaları için bazı yaygın hata ayıklama sorunlarını ve tekniklerini açıklar.
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md) -daha güvenli hata ayıklama için öneriler sağlar.