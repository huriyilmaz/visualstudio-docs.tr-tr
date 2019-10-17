---
title: Kod Analiz İlkesi Hataları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 661f029b617c430f7205552080a94affc5bd543b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445883"
---
# <a name="code-analysis-policy-errors"></a>Kod Analiz İlkesi Hataları

Kod Analizi ilkesi iadede karşılanmıyorsa aşağıdaki hatalar oluşur:

**Bir veya daha fazla projenin kod analizi ayarları, kod analizi ilkesiyle uyumlu değil.**

Bir veya daha fazla kod projesi için proje kaynak denetimine iade etme kod analizi gereksinimleri karşılanmadı. Bu hata, aşağıdaki koşullardan biri veya birkaçı nedeniyle oluşabilir:

- Kod Analizi, Çözümdeki tüm projelere yönelik derlemede etkin değildir.

- Visual Studio 'da projeye yönelik yerel kural kümesi, proje kuralı kümesinden daha az kısıtlayıcı bir **eylem** ayarına sahiptir. sunucu üzerinde **eylem**=**hatası** olarak ayarlanan bir kural, **eylemi** **Uyarı** olarak ayarlanmış veya Visual Studio 'da çalıştırılmakta olan kural kümesinde **yok** ).

- Visual Studio 'da belirtilen kural kümesi, proje için kod analizi iade ilkesinde belirtilen kural kümesinde belirtilen kuralların tümünü içermiyor.

**Kod Analizi ilkesi başarısız oldu. @No__t-1 projesinde hatalar var veya derleme güncel değil.**

Derleme hatalar içeriyor ya da hatalar düzeltildi, ancak düzeltme sonrasında kod analizi gerçekleştirilmedi.

**İade etme başarısız oldu. Kod Analizi Ilkesi, Visual Studio 'Yu açık bir çözümle iade etmeniz gerekir.**

Kod Analizi ilkesi, iade edilen tüm dosyaların Şu anda açık olan çözümde olması gerekir. Bu hatayı düzeltmek için, iade edilecek dosyayı içeren çözümü açın.

**Bekleyen iadedeki tüm dosyalar şu anda açık olan çözüm içinde değil.**

Kod Analizi ilkesi, iade edilen tüm dosyaların Şu anda açık olan çözümde olması gerekir. Bu hata, açık bir çözüm olduğunda tetiklenir, ancak "bekleyen iade etme" görünümündeki bazı dosyalar şu anda açılan çözümün parçası değildir. Bu hatayı düzeltmek için, iade edilecek dosyayı içeren çözümü açın.

**' @No__t-1 ' sürümü doğru değil. İlkede belirtilen tanımlayıcı adı ' {1} '.**

Bu hata .NET projeleri için geçerlidir. Yerel bilgisayarda kod analizi ilkesi için gereken bir kural. dll var, ancak sürüm/ortak anahtar eşleşmiyor. Bu hatayı düzeltmek için, ilke oluşturucunun, bilgisayarında *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules @ no__t-1* dizinindeki. dll 'leri güncelleştirmesi gerekir.

**ilkede belirtilen ' {0} ' bütünleştirilmiş kodu yok.**

Bu hata .NET projeleri için geçerlidir. Kod Analizi ilkesinin gerektirdiği bir kuralda, istemci bilgisayarda karşılık gelen dll yüklü değil. Bu hatayı düzeltmek için, ilke Oluşturucu bilgisayarında *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules @ no__t-1* dizinindeki dll 'nin güncelleştirilmesi gerekir.

**Proje {0} Kural ayarları, kod analizi ilkesiyle uyumlu değil.**

Bu hata .NET projeleri için geçerlidir. Yönetilen kod kuralları ayarları, ilke gerektirdiğinden katı değildir. Bu hatayı düzeltmek için, istemci ayarı sunucusundaki ilke gereksiniminden daha katı olmalıdır.

**Kod Analizi etkin yapılandırmada etkin değil. İade etmeden önce, yapılandırma {0} ' e geçin ve proje @no__t oluşturun.**

@No__t-0 ' da, etkin yapılandırmada kod analizi etkin değil, ancak en az bir kod analizi etkin.

**' İ iade etmeden önce Project {0} özellikleri ve derleme içindeki yönetilen ikililer için kod analizini etkinleştirmeniz gerekir.**

Bu hata, [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .NET uygulamaları için geçerlidir. İlke, yönetilen kod analizinin gerçekleştirilmesini gerektiriyor, ancak istemcideki geçerli projede etkin değil.

**İade etmeden önce Project {0} özellikleri ve derleme 'da Kod analizini etkinleştirmeniz gerekir.**

Bu hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projelerine ve Web projelerine uygulandı. İlke, yönetilen kod analizinin gerçekleştirilmesini gerektiriyor, ancak istemcideki geçerli projede etkin değil.

**' In iade etmeden önceC++ Project {0} özellikleri ve derlemesi ' nde C/Code analizini etkinleştirmeniz gerekir.**

Bu hata, yönetilmeyen projeler için geçerlidir. Kod Analizi ilkesi, C/C++Için kod analizi gerektiriyor, ancak istemcideki geçerli projede etkin değil.

## <a name="see-also"></a>Ayrıca Bkz.

- [Kod Çözümleme Uygulama Hataları](../code-quality/code-analysis-application-errors.md)
