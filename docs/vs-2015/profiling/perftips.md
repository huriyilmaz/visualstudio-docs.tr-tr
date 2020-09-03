---
title: PerfTips | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa56b6731e359db486a111194a710069d41a2f1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295861"
---
# <a name="perftips"></a>PerfTips
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı *PerfTips* ve hata ayıklayıcı ile tümleşik **Tanılama araçları** , hata ayıklarken uygulamanızın performansını izlemenize ve çözümlemenize yardımcı olur.  
  
 Hata ayıklayıcı tümleşik tanılama araçları geliştirilirken performans sorunlarından haberdar olmanın harika bir yoludur, ancak hata ayıklayıcı uygulamanızın performansı üzerinde önemli bir etkiye sahip olabilir. Daha doğru performans verileri toplamak için, hata ayıklayıcının dışında çalışan Visual Studio tanılama araçlarını performans araştırmalarınızın ek bir parçası olarak kullanmayı düşünün. Bkz. [profil oluşturma araçlarını hata ayıklama olmadan çalıştırma](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
## <a name="perftips"></a>PerfTips  
 Hata ayıklayıcı, bir kesme noktası veya Adımlama işleminde yürütmeyi durdurduktan sonra, kesme ve önceki kesme noktası arasındaki geçen süre, düzenleyici penceresinde bir ipucu olarak görüntülenir. Daha fazla bilgi için bkz. [PerfTips: Visual Studio Ile hata ayıklama sırasında bir bakışta performans bilgileri](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Tanılama Araçları penceresi  
 Kesme noktaları ve ilişkili zamanlama verileri zamanlama verileri Tanılama Araçları penceresine kaydedilir  
  
 Aşağıdaki grafikte, Visual Studio 2015 güncelleştirme 1 ' deki Tanılama Araçları penceresi gösterilmektedir:  
  
 ![DiagnosticTools&#45;güncelleştirme 1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-güncelleştirme 1")  
  
- **Olayları kes** zaman çizelgesi, hata ayıklama oturumunda isabet noktalarını işaret ediyor. **Hata ayıklayıcı** ayrıntıları listesini seçmek için bir olaya tıklayın.  
  
- **CPU kullanımı** grafiği, hata ayıklama oturumunda tüm işlemci çekirdekleri genelinde CPU kullanımı değişikliğini gösterir.  
  
- **Hata ayıklayıcı** ayrıntıları bölmesinin **Olaylar** listesi, her bir kesme olayının öğelerini içerir.  
  
- Bir break olayının **Duration** sütunu, olay ve önceki kesme noktası arasındaki geçen süreyi görüntüler.  
  
## <a name="turn-perftips-on-or-off"></a>PerfTips 'ı aç veya kapat  
 PerfTips 'ı etkinleştirmek veya devre dışı bırakmak için:  
  
1. **Hata Ayıkla** menüsünde **Seçenekler**' i seçin.  
  
2. **Hata ayıklama sırasında geçen Perftıp 'Yi göster**veya temizle.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Tanılama Araçları penceresini açma veya kapatma  
 Tanılama Araçları penceresini etkinleştirmek veya devre dışı bırakmak için:  
  
1. **Hata Ayıkla** menüsünde **Seçenekler**' i seçin.  
  
2. **Hata ayıklama sırasında tanılama araçlarını etkinleştir**onay kutusunu işaretleyin veya temizleyin.
