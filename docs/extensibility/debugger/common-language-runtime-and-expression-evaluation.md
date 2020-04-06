---
title: Ortak Dil Çalışma Süresi ve İfade Değerlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739117"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Ortak dil çalışma süresi ve ifade değerlendirmesi
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR ifade değerlendiricilerve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneğine](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Ortak Dil Çalışma Zamanı'nı (CLR) hedefleyen Visual Basic ve C# (C-sharp olarak okunur) gibi derleyiciler, daha sonra yerel kodla derlenen Microsoft Ara Dili (MSIL) üretir. CLR, ortaya çıkan kodu hata ayıklamak için hata ayıklama altyapısı (DE) sağlar. Özel programlama dilinizi Visual Studio IDE'ye entegre etmeyi planlıyorsanız, MSIL'e derlemeyi seçebilirsiniz ve bu nedenle kendi DE'nizi yazmak zorunda kalmamanız gerekmez. Ancak, programlama diliniz bağlamında ifadeleri değerlendirebilen bir ifade değerlendiricisi (EE) yazmanız gerekir.

## <a name="discussion"></a>Tartışma
 Bilgisayar dili ifadeleri genellikle bir veri nesnesi kümesi ve bunları işlemek için kullanılan işleçler kümesi oluşturmak için ayrıştı. Örneğin, "A+B" ifadesi, ek işleç (+) veri nesnelerine "A" ve "B" uygulamak için ayrıştırılabilir ve bu da büyük olasılıkla başka bir veri nesnesi ile sonuçlanabilir. Toplam veri nesneleri kümesi, işleçler ve bunların ilişkilendirmeleri, ağacın düğümlerindeki işleçler ve dallardaki veri nesneleriyle birlikte, genellikle bir programda ağaç olarak temsil edilir. Ağaç biçimine ayrılmış bir ifadeye genellikle ayrıştırılmış ağaç denir.

 Bir ifade ayrıştırıldıktan sonra, her veri nesnesini değerlendirmek için bir sembol sağlayıcısı (SP) çağrılır. Örneğin, "A" birden fazla yöntemde tanımlanırsa, "Hangi A?" sorusu A değeri tespit edilmeden önce cevaplanmalıdır. SP tarafından döndürülen yanıt, "Beşinci yığın çerçevesindeki üçüncü öğe" veya "Bu yönteme ayrılan statik belleğin başlangıcının ötesinde 50 bayt olan A" gibi bir şeydir.

 ClR derleyicileri, programın kendisi için MSIL üretmenin yanı sıra, program database (*.pdb*) dosyasına yazılan çok açıklayıcı hata ayıklama bilgilerini de üretebilir. Özel bir dil derleyicisi CLR derleyicileri ile aynı biçimde hata ayıklama bilgileri ürettiği sürece, CLR'nin SP'si o dilin adlandırılmış veri nesnelerini belirleyebilir. Adlandırılmış bir veri nesnesi tanımlandıktan sonra, EE veri nesnesini söz konusu nesnenin değerini tutan bellek alanına ilişkilendirmek (veya bağlamak) için bir bağlayıcı nesnesi kullanır. DE daha sonra veri nesnesi için yeni bir değer alabilir veya ayarlayabilir.

 Özel bir `ISymbolWriter` derleyici, arabirimi arayarak CLR hata ayıklama bilgilerini sağlayabilir (ad alanında `System.Diagnostics.SymbolStore`.NET Framework'de tanımlanır). MSIL'e derleyerek ve bu arabirimler aracılığıyla hata ayıklama bilgilerini yazarak, özel bir derleyici CLR DE ve SP'yi kullanabilir. Bu, özel bir dili Visual Studio IDE'ye entegre etmeyi büyük ölçüde kolaylaştırır.

 CLR DE bir ifadeyi değerlendirmek için özel EE'yi aradığında, DE EE'yi bir SP ve bağlayıcı nesneye arabirimler sağlar. Bu nedenle, CLR tabanlı hata ayıklama altyapısı yazmak, yalnızca uygun ifade değerlendirici arabirimlerini uygulamak için gerekli olduğu anlamına gelir; CLR sizin için bağlama ve sembol işleme ilgilenir.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
