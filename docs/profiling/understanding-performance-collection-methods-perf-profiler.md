---
title: Profil oluşturma performansı toplama yöntemlerini anlama
description: Veri toplama yöntemleri hakkında bilgi edinmek için veri toplama Visual Studio Performans Profili Oluşturucu öğrenin.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 8ca31215b5b9d27725f6feaa5ba65f91ebc119ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156961"
---
# <a name="understand-profiler-performance-collection-methods"></a>Profil oluşturma performansı toplama yöntemlerini anlama

Bu belgede, veri toplama yöntemlerinin içindeki araçların Visual Studio Performans Profili Oluşturucu özetler. 

## <a name="sampling"></a>Örnekleme

Profil oluşturma için örnekleme yöntemleri, profil oluşturma çalıştırması sırasında bir uygulama tarafından gerçekleştirilen çalışma hakkında istatistiksel veriler toplar. Veri toplama, uygulamayla ilgili bilgileri düzenli aralıklarla veya her milisaniye gibi örnekleme sıklığında toplayarak ve ardından uygulamada zaman harcanarak bir model oluşturmak için bu verileri analiz ederek yapılır. Örnekleme yöntemi hafiftir ve profili yapılan uygulamanın yürütülmesi üzerinde çok az etkisi vardır. Örnek Performans Profili Oluşturucu kullanan araçlar CPU Kullanımı [aracını](../profiling/cpu-usage.md) içerir.

## <a name="instrumentation"></a>İzleme

Ölçüm aracı profili oluşturma, profil oluşturma çalıştırması sırasında bir uygulama tarafından gerçekleştirilen iş hakkında ayrıntılı bilgi toplar. Veri toplama, zamanlama bilgilerini yakalayan bir ikili dosyaya kod eklayan araçlarla veya uygulama çalışırken tam zamanlama ve çağrı sayısı bilgilerini toplamak ve yalıtmak için geri çağırma kancaları kullanılarak yapılır. Ölçüm yöntemi, örnekleme tabanlı yaklaşımlara kıyasla yüksek ek yüke sahiptir. [.NET](../profiling/dotnet-alloc-tool.md) nesne Performans Profili Oluşturucu kullanan araçlar.