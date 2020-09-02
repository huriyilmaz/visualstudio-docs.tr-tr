---
title: 'DA0004: yüksek işlemci kullanımı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0e14a7400b937c56c2aac49a43d1d59cf96eba0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158704"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Yüksek işlemci kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0004 |  
| Kategori | Profil Oluşturma Araçları kullanımı |  
| Profil oluşturma yöntemleri | İzleme örneklemesi |  
| İleti | İşlemci kullanımınız sürekli olarak %75 üzerinde. CPU 'ya dayalı uygulamalar için örnekleme modunu kullanmayı düşünün. |  
| Kural türü | Bilgi |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="cause"></a>Nedeni  
 İzleme yöntemi kullanılarak toplanmış olan profil oluşturma verilerinde önemli ölçüde yüksek işlemci (CPU) kullanımı. Bir CPU ile bağlantılı uygulamanın profilini oluştururken örnekleme profili oluşturma yöntemini kullanmayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Bu profil oluşturma çalışması sırasında işlemci (veya işlemciler) sürekli olarak çok meşgul. Yüksek CPU kullanımı, CPU 'ya dayalı bir uygulamayı gösterebilir. Belgelenmiş profiller genellikle CPU kullanımı senaryolarını araştırmak için en etkili yoldur. Örnekleme, genellikle işlemcide yönergeler yürüten uygulamaların profilini oluştururken daha etkilidir.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 İşlev zamanlamalarınız gerekmiyorsa veya giriş/çıkış işlemini işlemci performans sorunlarına göre anlamak için daha fazla bilgi edinmek istiyorsanız, izleme yöntemi yerine örnekleme yöntemini kullanarak uygulamanızın profilini oluşturmayı düşünün.
