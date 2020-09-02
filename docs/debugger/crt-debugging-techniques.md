---
title: CRT hata ayıklama teknikleri | Microsoft Docs
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
ms.openlocfilehash: 88cdc78fd739de412b4cf796d0ca7a42f9174e0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62564042"
---
# <a name="crt-debugging-techniques"></a>CRT Hata Ayıklama Teknikleri
C çalışma zamanı kitaplığını kullanan bir programda hata ayıklaması yapıyorsanız, bu hata ayıklama teknikleri yararlı olabilir.

## <a name="in-this-section"></a>Bu Bölümde
 [CRT Hata Ayıklama Kitaplığı Kullanımı](../debugger/crt-debug-library-use.md)

 C çalışma zamanı kitaplığı tarafından sağlanan hata ayıklama desteğini açıklar ve araçlara erişmek için yönergeler sağlar.

 [Raporlama Makroları](../debugger/macros-for-reporting.md)

 **_RPTn** ve **_RPTFn** makroları hakkında bilgi sağlar (Crtdbg içinde tanımlanır. H), `printf` hata ayıklama için deyimlerin kullanımını değiştirir.

 [Öbek Atama İşlevleri Hata Ayıklama Sürümleri](../debugger/debug-versions-of-heap-allocation-functions.md)

 Yığın ayırma işlevlerinin özel hata ayıklama sürümlerini açıklar; Örneğin, CRT haritaları nasıl çağırır, bunları açıkça çağırma avantajları, dönüştürme nasıl önlenir, istemci bloklarının içindeki ayrı ayırma türlerini izleme ve _DEBUG tanımlamama sonuçları.

 [CRT Hata Ayıklama Öbeği Ayrıntıları](../debugger/crt-debug-heap-details.md)

 Bellek yönetimine ve hata ayıklama yığınına, hata ayıklama yığınından blok türlerine, hata ayıklama yığınını, yığın durumu raporlama işlevlerine ve yığın ayırma isteklerini izlemeye yönelik bağlantılar sağlar.

 [Hata Ayıklama Kanca İşlevi Yazma](../debugger/debug-hook-function-writing.md)

 İstemci blok kanca işlevleri, ayırma kanca işlevleri, ayırma kancaları ve CRT bellek ayırmaları ve rapor kanca işlevleri bağlantılarını listeler.

 [CRT Kitaplığını Kullanarak Bellek Sızıntılarını Bulma](../debugger/finding-memory-leaks-using-the-crt-library.md)

 Hata ayıklayıcı ve C çalışma zamanı kitaplığını kullanarak bellek sızıntılarını algılama ve yalıtma tekniklerini ele alır.

## <a name="related-sections"></a>İlgili Bölümler

- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md) -C ve C++ uygulamaları için bazı yaygın hata ayıklama sorunlarını ve tekniklerini açıklar.
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md) -daha güvenli hata ayıklama için öneriler sağlar.