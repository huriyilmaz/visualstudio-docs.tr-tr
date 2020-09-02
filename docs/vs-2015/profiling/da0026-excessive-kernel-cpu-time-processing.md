---
title: 'DA0026: aşırı çekirdek CPU süresi işleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef0a3c42be1057bd1217ec676ae43b220d80345
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152667"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Aşırı çekirdek CPU süresi işlemesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | TODO |  
| Kategori | Profil Oluşturma Araçları kullanımı |  
| Profil oluşturma yöntemi | Örnekleme |  
| İleti | Görece yüksek miktarda çekirdek modu CPU zamanı ölçüldü. SysCall örneklemesi etkin olarak kaynağı araştırın. |  
| Kural türü | Bilgi |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="cause"></a>Nedeni  
 Çekirdek modunda yürütülen oran CPU süresi, kullanıcı modunda harcanan süre miktarını aştı. Profil oluşturmayı yeniden deneyin ve yüksek çekirdek modu yürütme sürelerinin nedenini öğrenmek için sistem çağrılarının sayısını (syscalls) örnekleme.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Uygulamanın çekirdek modu yürütülürken harcadığı sürenin görece yüksek oranı, daha fazla araştırma sağlayabilir. Kullanıcı modu uygulaması, iş parçacığı veya işlem eşitleme temelleri için beklemek veya sistem çağrıları yapmak için g/ç işlemlerini gerçekleştirmek üzere çekirdek moduna geçiş yapar. Uygulama yaptığı sistem çağrılarının türlerini ve Sistem çağrılarına göre örnek çağrı yığınları toplama seçeneğini belirlediğinizde bunlardan sorumlu olan işlevleri araştırabilirsiniz.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Uygulamanızın yaptığı sistem çağrılarının türlerini araştırmak için, profili yeniden çalıştırın ve Sistem çağrılarına göre örnek toplama seçeneğini belirleyin. Daha fazla bilgi için bkz. nasıl yapılır: IDE içinde profil oluşturma araçları çalıştırıyorsanız [örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md) . Profil oluşturma araçlarını komut satırından çalıştırıyorsanız, Profil Oluşturma Araçları komut satırı araçları başvurusu ' nda [VSPerfCmd](../profiling/vsperfcmd.md) konusunun **örnekleme aralığı seçenekleri** bölümüne bakın.
