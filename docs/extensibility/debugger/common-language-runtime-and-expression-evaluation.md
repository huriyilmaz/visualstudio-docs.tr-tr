---
title: Ortak Dil Çalışma Zamanı ve İfade Değerlendirme | Microsoft Docs
description: Common Language Runtime'ın hata ayıklama altyapısıyla nasıl etkileşim kurarak özel bir programlama dilini Visual Studio öğrenin.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2c3c0566acf6a0216e5301cefceca061aae9d974
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043628"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Ortak dil çalışma zamanı ve ifade değerlendirmesi
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Ortak Dil Çalışma Zamanı'Visual Basic (CLR) hedef alan Visual Basic ve C# (C-sharp olarak okunur) gibi derleyiciler, daha sonra yerel koda derlenmiş Microsoft Ara Dili (MSIL) üretir. CLR, sonuçta elde edilen kodun hata ayıklaması için bir hata ayıklama altyapısı (DE) sağlar. Özel programlama dilinizi IDE'ye Visual Studio planlıyorsanız, MSIL'ye derlemeyi seçebilirsiniz ve bu nedenle kendi DE'nizi yazmak zorunda olmaz. Ancak, programlama diliniz bağlamında ifadeleri değerlendirebilecek bir ifade değerlendiricisi (EE) yazmanız gerekir.

## <a name="discussion"></a>Tartışma
 Bilgisayar dili ifadeleri genellikle bir veri nesnesi kümesi ve bunları işlemek için kullanılan bir dizi işleç üretmek için ayrıştırıldı. Örneğin, "A+B" ifadesi , "A" ve "B" veri nesnelerine ekleme işleci (+) uygulamak için ayrıştırarak başka bir veri nesnesine neden olabilir. Toplam veri nesnesi, işleç kümesi ve bunların ilişkilendirmeleri genellikle bir programda ağaç olarak, işleçler ağacın düğümlerinde, veri nesneleri ise dallarda temsil eder. Ağaç biçimine ayrıştırılan bir ifade genellikle ayrıştırılan ağaç olarak anılır.

 Bir ifade ayrıştırıldıktan sonra, her veri nesnesini değerlendirmek için bir sembol sağlayıcısı (SP) çağrılır. Örneğin, "A" birden fazla yöntemde tanımlanmışsa "Hangi A?" sorusu değerinin tespiti için önce yanıt ver gerekir. SP tarafından döndürülen yanıt "Beşinci yığın çerçevesindeki üçüncü öğe" veya "Bu yönteme ayrılan statik belleğin başlangıcının 50 bayt ötesindeki A".

 CLR derleyicileri, programın kendisi için MSIL oluşturmanın yanı sıra, Program DataBase (*.pdb*) dosyasına yazılan çok açıklayıcı hata ayıklama bilgileri de üretebilir. Özel bir dil derleyicisi, CLR derleyicileri ile aynı biçimde hata ayıklama bilgileri ürettiği sürece, CLR'nin SP'si bu dilin adlandırılmış veri nesnelerini tanımlayabilir. Adlandırılmış veri nesnesi tanımlandıktan sonra, EE nesnesini bu nesnenin değerini tutan bellek alanına ilişkilendirmek (veya bağlamak) için bir bağlayıcı nesnesi kullanır. Daha sonra DE veri nesnesi için yeni bir değer elde eder veya yeni bir değer ayarlar.

 Özel bir derleyici, arabirimini çağırarak CLR hata ayıklama bilgilerini (ad alanı içinde .NET Framework `ISymbolWriter` `System.Diagnostics.SymbolStore` sağlar). MSIL'ye derlenmiş ve bu arabirimler aracılığıyla hata ayıklama bilgileri yazarak, özel bir derleyici CLR DE ve SP kullanabilir. Bu, özel bir dili IDE ile tümleştirmeyi büyük ölçüde Visual Studio kolaylaştırır.

 CLR DE, bir ifadeyi değerlendirmek için EE özel mülkiyeti çağıran DE, EE sp ve bağlayıcı nesnesine arabirimler sağlar. Bu nedenle, CLR tabanlı hata ayıklama altyapısı yazmak yalnızca uygun ifade değerlendirici arabirimlerini uygulamanın gerekli olduğu anlamına gelir; CLR bağlamayı ve sembol işlemeyi sizin için ele alır.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
