---
title: Koleksiyon yöntemlerini seçin | Microsoft Docs
description: Visual Studio Profil Oluşturma Araçları performans verisi toplamanın üç yöntemini destekler. Uygulamanız için ihtiyacınız olan birini nasıl seçebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a304006a778dc4766e6b4be9ceb133450c0dfb52
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876920"
---
# <a name="how-to-choose-collection-methods"></a>Nasıl yapılır: koleksiyon yöntemleri seçme

Visual Studio Profil Oluşturma Araçları performans verilerini toplamak için üç yöntem destekler: örnekleme, izleme ve eşzamanlılık. .NET bellek ayırma ve yaşam süresi verilerini toplamak için örnekleme veya izleme yöntemini de kullanabilirsiniz.

Uygulamanız için en uygun koleksiyon yöntemini belirtmek üzere performans oturumu **yöntemi** özelliğini kullanabilirsiniz. Bir performans oturumunun Özellik sayfalarından, Performans Gezgini veya performans sihirbazından koleksiyon yöntemini ayarlayabilirsiniz. Komut satırı araçları kullanıyorsanız daha fazla bilgi için bkz. [komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md) .

## <a name="performance-wizard"></a>Performans Sihirbazı

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Performans sihirbazını kullanarak bir koleksiyon yöntemi seçmek için

- Sihirbazın ilk sayfasında, aşağıdaki seçeneklerden birini seçin:

| Seçenek | Açıklama |
|----------------------------| - |
| **CPU örnekleme** | İlk analizler ve CPU kullanımı sorunlarını analiz etmek için yararlı olan uygulama istatistiklerini toplar. |
| **Yapısı** | Odaklanmış analizler ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verilerini toplar. |
| **.NET bellek ayırma** | Örnekleme profili oluşturma yöntemini kullanarak .NET Framework bellek ayırma verilerini toplar. |
| **Eşzamanlılık** | Sayısal kaynak çekişmesini verilerini toplar. |

## <a name="performance-explorer"></a>Performans Gezgini

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Performans Gezgini kullanarak bir koleksiyon yöntemi seçmek için

1. **Performans Gezgini** araç çubuğunda, **Yöntem** açılır listesinin yanındaki oka tıklayın.

2. Tercih ettiğiniz koleksiyon yöntemine tıklayın.

## <a name="performance-session-property-pages"></a>Performans oturumu Özellik sayfaları

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak örnekleme veya izleme yöntemini seçmek için

1. **Performans Gezgini**' de, performans oturumu ' nu seçin.

     Bir performans oturumu dosya adı öğesine sahiptir. *psess* uzantısı.

2. Performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Özellik sayfalarında**, **genel**' e tıklayın.

4. Tercih ettiğiniz koleksiyon yöntemine tıklayın.

    - Örnekleme verilerini toplarken kullanılabilir diğer seçenekler hakkında daha fazla bilgi için bkz. [örnekleme kullanarak performans Istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Örnekleme verilerini toplarken kullanılabilir diğer seçenekler hakkında daha fazla bilgi için bkz. [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak .NET bellek verileri toplamayı seçmek için

1. **Performans Gezgini**' de, performans oturumu ' nu seçin.

     Bir performans oturumu dosya adının. psess uzantısı vardır.

2. Performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Özellik sayfalarında**, **genel**' e tıklayın.

4. **Örnekleme** veya **izleme**' ye tıklayın.

5. .NET Framework nesne ayırmalarının boyutunu ve sayısını toplamak için **.NET nesne ayırma bilgilerini topla** ' ya tıklayın.

6. Seçim Ayrıca, nesne belleğinin geri alındığı çöp toplama nesilleri hakkında veri toplamak için **.NET nesne yaşam süresi bilgilerini toplayın** .

     .NET bellek verileri topladığınızda kullanılabilen diğer seçenekler hakkında bilgi için bkz. [.net bellek ayırma ve ömür verileri toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak eşzamanlılık veri toplamayı seçme

1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellik sayfalarında**, **genel**' e tıklayın.

3. **Eşzamanlılık**' e tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md) 
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
