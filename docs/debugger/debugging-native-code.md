---
title: Yerel kodda hata ayıklama | Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f98b99a31d9215d661879aa7fa52d4b671024496
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738162"
---
# <a name="debugging-native-code"></a>Yerel Kodda Hata Ayıklama
Bu bölümde, yerel uygulamalar için bazı yaygın hata ayıklama sorunları ve teknikleri ele alınmaktadır. Bu bölümde ele alınan teknikler, üst düzey tekniklerdir. Visual Studio hata ayıklayıcısını kullanmanın mekanizması için bkz. [ilk olarak hata ayıklayıcıya](../debugger/debugger-feature-tour.md)bakın.

## <a name="in-this-section"></a>Bu Bölümde
 [Nasıl yapılır: Iyileştirilmiş kodda hata ayıklama](../debugger/how-to-debug-optimized-code.md) , Özel olarak en iyi duruma getirilmiş kodda hata ayıklama için ipuçları, hata ayıklama ve sürüm yapılandırmalarının varsayılan iyileştirme ayarları ve yalnızca iyileştirilmiş kodda görünen hataları bulmaya yönelik ipuçları sağlar (açılıyor Hata ayıklama yapı yapılandırmasında iyileştirme).

 [DebugBreak ve __debugbreak](../debugger/debugbreak-and-debugbreak.md) Win32 `DebugBreak` işlevini açıklar ve Platform SDK 'sında başvuru konusuna bir bağlantı sağlar. Ayrıca `__debugbreak` iç öğesini açıklar.

 [C/C++ ](../debugger/c-cpp-assertions.md) onaylar Onaylama deyimlerini, bunların nasıl çalıştığını, bunları kullanmanın avantajlarını (mantık hatalarını yakalama, bir işlemin sonuçlarını kontrol etmeyi ve hata koşullarını test etmeyi), `_DEBUG` ile etkileşimini ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desteklenen onayların türlerini açıklar.

 [Nasıl yapılır: satır Içi derleme kodunda hata ayıklama](../debugger/how-to-debug-inline-assembly-code.md) Kayıt içeriğini görüntülemek ve bu pencereler hakkındaki konuların bağlantılarını sağlamak üzere derleme yönergelerini ve Yazmaçları penceresini görüntülemek için ayrıştırma penceresini kullanma hakkında kısa yönergeler sağlar.

 [MFC hata ayıklama teknikleri](../debugger/mfc-debugging-techniques.md) MFC programları için hata ayıklama tekniklerine bağlantı sağlar: afxDebugBreak, Izleme makrosu, MFC 'de bellek sızıntılarını algılama, MFC onayları ve MFC hata ayıklama derlemeleri boyutunu azaltma.

 [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md) CRT hata ayıklama kitaplığı, raporlama makroları, malloc ve _malloc_dbg arasındaki farklılıklar, hata ayıklama kanca işlevleri ve CRT hata ayıklama yığını gibi C çalışma zamanı kitaplığı için hata ayıklama tekniklerine bağlantı sağlar.

 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md) Programlarda hata ayıklama C++ hakkında sık sorulan soruların yanıtlarını sağlar

 [Com ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md) Com ve ActiveX hata ayıklaması için kullanabileceğiniz araçlar da dahil olmak üzere COM ve ActiveX uygulamalarının hatalarını ayıklama hakkında bilgi sağlar.

 [Nasıl yapılır: eklenen koddaki hataları ayıklama](../debugger/how-to-debug-injected-code.md) Öznitelikleri kullanan hata ayıklama kodu hakkında rehberlik sağlar. Kaynak ek açıklamanın nasıl kullanılacağı, eklenen kodun nasıl görüntüleneceği ve geçerli yürütme noktasındaki ayrıştırılmış kodu nasıl görüntüleneceği hakkında yönergeler içerir.

 [Izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) Paralel bir uygulamada hata ayıklamak için **paralel görevler** ve **Paralel Yığınlar** araç pencerelerinin nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [Projeleri hata ayıklamaya C++ hazırlama](../debugger/debugging-preparation-visual-cpp-project-types.md) C++ proje şablonları tarafından oluşturulan yerel proje türlerinde hata ayıklama yapılacağını betimleyen konuların bağlantılarını sağlar.

 [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md) Yerel ve yönetilen DLL 'Lerde hata ayıklama hakkında bilgi sağlar.

 [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md) Hata ayıklama belgelerinin daha büyük bölümlerine bağlantılar sağlar. Bilgiler hata ayıklayıcıdaki yenilikleri, ayarlar ve hazırlık, kesme noktaları, özel durumları işleme, düzenleme ve devam etme, yönetilen kod hatalarını ayıklama, yerel kodda hata ayıklama, SQL hata ayıklama ve Kullanıcı arabirimi başvurularına dahildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Visual Studio’da hata ayıklama](../debugger/index.yml)