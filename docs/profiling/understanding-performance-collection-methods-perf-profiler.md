---
title: Performans toplama yöntemlerini anlama | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 03a49763a682f6b98b02fe40ba957efa8f5483c8
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290637"
---
# <a name="understand-performance-collection-methods"></a>Performans toplama yöntemlerini anlama

Bu belgede, Visual Studio performans Profilcisi içindeki araçların kullandığı veri toplama yöntemleri özetlenmektedir. 

## <a name="sampling"></a>Örnekleme

Profil oluşturma için örnekleme yöntemleri, profil oluşturma çalışması sırasında bir uygulama tarafından gerçekleştirilen iş hakkında istatistiksel verileri toplar. Veri toplama işlemi, uygulama üzerinde her milisaniyenin gibi düzenli bir aralıkta veya örnekleme sıklığındaki bilgiler toplanarak ve ardından bu verileri, uygulamada nerede harcandığına ilişkin bir model oluşturmak üzere çözümleyerek yapılır. Örnekleme yöntemi hafif ve profili oluşturulan uygulamanın yürütülmesi üzerinde çok daha etkilidir. Performans Profilcisi ' nde örnekleme yöntemiyle kullanılan araçlar, [CPU kullanımı](../profiling/cpu-usage.md) aracını içerir.

## <a name="instrumentation"></a>İzleme

İzleme profili oluşturma, bir profil oluşturma işlemi sırasında bir uygulama tarafından gerçekleştirilen iş hakkında ayrıntılı bilgiler toplar. Veri toplama işlemi, bir uygulama çalışırken tam zamanlamayı ve çağrı sayısı bilgilerini toplamak ve yaymak için geri çağırma kancalarını kullanarak veya zamanlama bilgilerini yakalayan bir ikili dosyaya kod ekler. Örnekleme tabanlı yaklaşımlar ile karşılaştırıldığında, izleme yönteminin yüksek bir yükü vardır. Performans profili Oluşturucu kullanan araçlar, [.NET nesne ayırma](../profiling/dotnet-alloc-tool.md) aracı 'nı içerir.