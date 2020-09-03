---
title: Yerel kodda hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61ee852f75737d85604fda106b15e61dc3634899
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196418"
---
# <a name="debugging-native-code"></a>Yerel Kodda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, yerel uygulamalar için bazı yaygın hata ayıklama sorunları ve teknikleri ele alınmaktadır. Bu bölümde ele alınan teknikler, üst düzey tekniklerdir. Visual Studio hata ayıklayıcısını kullanmanın mekanizması için bkz. [hata ayıklayıcı yol haritası](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl Yapılır: İyileştirilmiş Kodda Hata Ayıklama](../debugger/how-to-debug-optimized-code.md)  
 En iyi duruma getirilmiş kodda hata ayıklama için ipuçları, özellikle de programın en iyi duruma getirilmiş bir sürümünde hata ayıklamanızın yanı sıra hata ayıklama ve sürüm yapılandırmalarının varsayılan iyileştirme ayarlarını ve yalnızca iyileştirilmiş kodda (bir hata ayıklama yapı yapılandırmasında en iyi duruma getirmeyi etkinleştirerek) görünen hataları bulmaya yönelik ipuçları verir.  
  
 [DebugBreak ve __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Win32 işlevini açıklar `DebugBreak` ve Platform SDK 'sında başvuru konusuna bir bağlantı sağlar. Ayrıca, iç öğesini açıklar `__debugbreak` .  
  
 [C/C++ Onayları](../debugger/c-cpp-assertions.md)  
 Onaylama deyimlerini, bunların nasıl çalıştığını, bunları kullanmanın avantajlarını (mantık hatalarını yakalama, bir işlemin sonuçlarını kontrol etmeyi ve hata koşullarını test etmeyi), ile etkileşimini `_DEBUG` ve ' de desteklenen onayların türlerini açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Nasıl yapılır: satır Içi derleme kodunda hata ayıklama](../debugger/how-to-debug-inline-assembly-code.md)  
 Kayıt içeriğini görüntülemek ve bu pencereler hakkındaki konuların bağlantılarını sağlamak üzere derleme yönergelerini ve Yazmaçları penceresini görüntülemek için ayrıştırma penceresini kullanma hakkında kısa yönergeler sağlar.  
  
 [MFC Hata Ayıklama Teknikleri](../debugger/mfc-debugging-techniques.md)  
 MFC programları için hata ayıklama tekniklerine bağlantı sağlar: afxDebugBreak, Izleme makrosu, MFC 'de bellek sızıntılarını algılama, MFC onayları ve MFC hata ayıklama derlemeleri boyutunu azaltma.  
  
 [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)  
 CRT hata ayıklama kitaplığı, raporlama için makrolar, malloc ve _malloc_dbg arasındaki farklılıklar, hata ayıklama kanca işlevleri yazma ve CRT hata ayıklama yığını gibi, C çalışma zamanı kitaplığı için hata ayıklama tekniklerine bağlantı sağlar.  
  
 [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)  
 Visual C++ programlarında hata ayıklama hakkında sık sorulan soruların yanıtlarını sağlar  
  
 [COM ve ActiveX Hata Ayıklaması](../debugger/com-and-activex-debugging.md)  
 Com ve ActiveX hata ayıklaması için kullanabileceğiniz araçlar da dahil olmak üzere COM ve ActiveX uygulamalarının hatalarını ayıklama hakkında bilgi sağlar.  
  
 [Nasıl Yapılır: Yerel DLL'lerde Hata Ayıklama](../debugger/how-to-debug-native-dlls.md)  
 Yerel koddan dll 'Ler için hata ayıklamanın nasıl ayarlanacağını açıklar.  
  
 [Nasıl yapılır: eklenen koddaki hataları ayıklama](../debugger/how-to-debug-injected-code.md)  
 Öznitelikleri kullanan hata ayıklama kodu hakkında rehberlik sağlar. Kaynak ek açıklamanın nasıl kullanılacağı, eklenen kodun nasıl görüntüleneceği ve geçerli yürütme noktasındaki ayrıştırılmış kodu nasıl görüntüleneceği hakkında yönergeler içerir.  
  
 [İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Paralel bir uygulamada hata ayıklamak için **paralel görevler** ve **Paralel Yığınlar** araç pencerelerinin nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Visual C++ Proje Türleri](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Visual C++ proje şablonları tarafından oluşturulan yerel proje türlerinde hata ayıklamanın nasıl yapılacağını betimleyen konuların bağlantılarını sağlar.  
  
 [Visual Studio'da Hata Ayıklama](../debugger/debugging-in-visual-studio.md)  
 Hata ayıklama belgelerinin daha büyük bölümlerine bağlantılar sağlar. Bilgiler hata ayıklayıcıdaki yenilikleri, ayarlar ve hazırlık, kesme noktaları, özel durumları işleme, düzenleme ve devam etme, yönetilen kod hatalarını ayıklama, yerel kodda hata ayıklama, SQL hata ayıklama ve Kullanıcı arabirimi başvurularına dahildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Visual Studio'da Hata Ayıklama](../debugger/debugging-in-visual-studio.md)
