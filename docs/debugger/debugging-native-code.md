---
title: Yerel Kod Hata Ayıklama | Microsoft Docs
description: Sık karşılaşılan hata ayıklama sorunları ve yerel uygulamalar için yerel uygulamalar için üst düzey teknikler hakkında Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 68b671aecd885cbd5b317c71c0a5962752a86001f8c9567e73b855b7060867d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264070"
---
# <a name="debugging-native-code"></a>Yerel Kodda Hata Ayıklama
Bölümünde yerel uygulamalar için bazı yaygın hata ayıklama sorunları ve teknikleri yer almaktadır. Bu bölümde ele alan teknikler üst düzey tekniklerdir. Hata ayıklayıcısını kullanma Visual Studio için bkz. İlk olarak [hata ayıklayıcıya bakın).](../debugger/debugger-feature-tour.md)

## <a name="in-this-section"></a>Bu Bölümde
 [Nasıl olur: İyileştirilmiş Kodda Hata Ayıklama](../debugger/how-to-debug-optimized-code.md) En iyi duruma getirilmiş kodda hata ayıklamaya yönelik ipuçları verir. Özellikle, programınız için en iyi duruma getirilmiş bir sürümde neden hata ayıklamanız gerektiği, Hata Ayıklama ve Yayın yapılandırmaları için varsayılan iyileştirme ayarları ve yalnızca iyileştirilmiş kodda görünen hataları bulmaya yönelik ipuçları verir (Hata ayıklama derleme yapılandırmasında iyileştirmeyi açma).

 [DebugBreak ve __debugbreak](../debugger/debugbreak-and-debugbreak.md) Win32 işlevini `DebugBreak` açıklar ve Platform SDK'sı içinde başvuru konusuna bir bağlantı sağlar. Ayrıca iç `__debugbreak` ifadeleri de açıklar.

 [C/C++ Onaylamaları](../debugger/c-cpp-assertions.md) Onay deyimlerini, nasıl çalışırlarını, bunları kullanmanın avantajlarını (mantık hatalarını yakalama, bir işlem sonuçlarını denetleme ve hata koşullarını test etme), ile etkileşimlerini ve içinde desteklenen onay türlerini `_DEBUG` ele [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] alır.

 [Nasıl kurulur: Satır Içi Derleme Kodunda Hata Ayıklama](../debugger/how-to-debug-inline-assembly-code.md) Derleme yönergelerini görüntülemek için Disassembly penceresini kullanma hakkında kısa yönergeler ve yazmaca yönelik içerikleri görüntülemek için Yazmanlar penceresini sağlar ve bu pencerelerle ilgili konuların bağlantılarını sağlar.

 [MFC Hata Ayıklama Teknikleri](../debugger/mfc-debugging-techniques.md) MFC programları için şu hata ayıklama tekniklerine bağlantı sağlar: afxDebugBreak, TRACE makrosu, MFC'de bellek sızıntılarını algılama, MFC onayları ve MFC Hata Ayıklama derlemelerinin boyutunu azaltma.

 [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md) CRT Hata Ayıklama Kitaplığı'nın kullanımı, raporlama makroları, malloc ile _malloc_dbg arasındaki farklar, hata ayıklama kancası işlevleri yazma ve CRT hata ayıklama yığını dahil olmak üzere C Run-Time Kitaplığı için hata ayıklama tekniklerine bağlantı sağlar.

 [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md) C++ programlarında hata ayıklama hakkında sık sorulan soruların yanıtlarını sağlar

 [COM ve ActiveX Hata Ayıklama](../debugger/com-and-activex-debugging.md) COM ve ActiveX için kullanabileceğiniz araçlar dahil olmak üzere COM ve ActiveX hata ayıklama hakkında bilgi sağlar.

 [Nasıl edilir: KodDa Hata Ayıklama](../debugger/how-to-debug-injected-code.md) Öznitelikleri kullanan kodlarda hata ayıklama konusunda rehberlik sağlar. Yönergeler arasında Kaynak Ek Açıklamasını açma, ekli kodu görüntüleme ve geçerli yürütme noktasındaki ayrık kodu görüntüleme yer alan yönergeler yer alan yönergelerdir.

 [Adım adım kılavuz: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) Paralel uygulamada hata ayıklamak **için Paralel Görevler** ve Paralel **Yığınlar** araç pencerelerini kullanmayı açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [C++ projelerinde hata ayıklamaya hazırlanma](../debugger/debugging-preparation-visual-cpp-project-types.md) C++ proje şablonları tarafından oluşturulan yerel proje türlerinde hata ayıklamayı açıklayan konulara bağlantılar sağlar.

 [DLL Projelerinde Hata Ayıklama](../debugger/debugging-dll-projects.md) Yerel ve yönetilen URL'lerde hata ayıklama hakkında bilgi sağlar.

 [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md) Hata ayıklama belgelerinin daha büyük bölümlerine bağlantılar sağlar. Hata ayıklayıcısındaki yeni bilgiler, ayarlar ve hazırlık, kesme noktaları, özel durumları işleme, düzenleme ve devam, yönetilen kodda hata ayıklama, yerel kodda hata ayıklama, hata ayıklama SQL ve kullanıcı arabirimi başvurularını içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)