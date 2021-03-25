---
title: Ortak dil çalışma zamanı ve Ifade değerlendirmesi | Microsoft Docs
description: Ortak dil çalışma zamanının hata ayıklama altyapısıyla nasıl etkileşime gireceğini ve özel bir programlama dilinin Visual Studio IDE ile nasıl tümleştirileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ddc218d0e9499253269a12687fa89122cfe007
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055017"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Ortak dil çalışma zamanı ve ifade değerlendirmesi
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ortak dil çalışma zamanını (CLR) hedefleyen Visual Basic ve C# (C-Sharp) gibi derleyiciler, daha sonra yerel koda derlenen Microsoft ara dili (MSIL) oluşturur. CLR, ortaya çıkan kodun hatalarını ayıklamak için bir hata ayıklama altyapısı (DE) sağlar. Özel programlama dilinizi Visual Studio IDE ile tümleştirmeyi planlıyorsanız MSIL 'e derlemeyi seçebilir ve bu nedenle kendi DE yazmak zorunda olmayacaktır. Ancak, programlama diliniz bağlamı dahilinde ifadeleri değerlendirebilen bir ifade değerlendirici (EE) yazmanız gerekir.

## <a name="discussion"></a>Tartışma
 Bilgisayar dili ifadeleri genellikle bir veri nesneleri kümesi ve bunları işlemek için kullanılan bir dizi işleç oluşturmak için ayrıştırılır. Örneğin, "a + B" ifadesi "A" ve "B" veri nesnelerine ek işleci (+) uygulamak için ayrıştırılabilir ve muhtemelen başka bir veri nesnesine neden olabilir. Toplam veri nesnesi kümesi, işleç ve ilişkilendirmeleri, ağaç düğümleri ve dallardaki veri nesneleri ile birlikte genellikle bir programda ağaç olarak temsil edilir. Ağaç formuna bölündüğü bir ifade genellikle ayrıştırılmış ağaç olarak adlandırılır.

 Bir ifade ayrıştırıldıktan sonra, her veri nesnesini değerlendirmek için bir sembol sağlayıcısı (SP) çağırılır. Örneğin, "A" her ikisi de birden fazla yöntemde tanımlıysa, "A?" sorusu öğesinin değeri bunun olabilecek şekilde yanıtlanmalıdır. SP tarafından döndürülen yanıt, "Beşinci yığın çerçevesindeki üçüncü öğe" veya "Bu yönteme ayrılan statik belleğin başlangıcından daha fazla 50 bayt olan A" gibi bir şeydir.

 Programın kendisi için MSIL üretmenin yanı sıra, CLR derleyicileri, bir program veritabanı (*. pdb*) dosyasına yazılan çok açıklayıcı hata ayıklama bilgileri de oluşturabilir. Özel dil derleyicisi, hata ayıklama bilgilerini CLR derleyicileri ile aynı biçimde oluşturduğu sürece, CLR 'nin SP adı bu dilin adlandırılmış veri nesnelerini tanımlayabilir. Adlandırılmış bir veri nesnesi tanımlandıktan sonra, EE veri nesnesini ilgili nesnenin değerini tutan bellek alanına ilişkilendirmek (veya bağlamak) için bir Ciltçi nesnesi kullanır. Aynı daha sonra veri nesnesi için yeni bir değer alabilir veya ayarlayabilir.

 Özel bir derleyici, arayüzü çağırarak CLR hata ayıklama bilgilerini sağlayabilir `ISymbolWriter` (ad alanındaki .NET Framework tanımlanır `System.Diagnostics.SymbolStore` ). MSIL 'e derlerken ve hata ayıklama bilgilerini bu arabirimler aracılığıyla yazarak, özel bir derleyici CLR DE ve SP 'yi kullanabilir. Bu, özel bir dilin Visual Studio IDE ile tümleştirilmesine büyük ölçüde basitleştirir.

 CLR, bir ifadeyi değerlendirmek için özel EE 'ı çağırdığında, bir SP ve bir Ciltçi nesnesine arabirimler içeren EE sağlar. Bu nedenle, CLR tabanlı hata ayıklama altyapısını yazmak yalnızca uygun ifade değerlendirici arabirimlerini uygulamak için gereklidir; CLR, bağlama ve sembol işlemeyi sizin yerinize gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
