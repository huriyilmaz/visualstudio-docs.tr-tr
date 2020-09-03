---
title: Kod çözümleme Ilkesi hataları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8cb50fffc1411e77f771b0f74fbb947144eb6017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672916"
---
# <a name="code-analysis-policy-errors"></a>Kod Analiz İlkesi Hataları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi ilkesi iadede karşılanmıyorsa aşağıdaki hatalar oluşur:

 **Bir veya daha fazla projenin kod analizi ayarları, kod analizi ilkesiyle uyumlu değil.**

 Takım projesi kaynak denetimine iade etme, bir veya daha fazla kod projesi için karşılanmadı. Bu hata, aşağıdaki koşullardan biri veya birkaçı nedeniyle oluşabilir:

1. Kod Analizi, Çözümdeki tüm projelere yönelik derlemede etkin değildir.

2. Visual Studio 'da projenin yerel kural kümesi, takım projesi kural kümesinden daha az kısıtlayıcı bir **eylem** ayarına sahiptir. sunucu üzerinde **eylem**hatası olarak ayarlanan bir kural, = **Error** **eylemi** **Uyarı** olarak ayarlanmış veya kural kümesinde Visual Studio 'da çalıştırmakta olan bir kural **yok** .

3. Visual Studio 'da belirtilen kural kümesi, takım projesi için kod analizi iade ilkesinde belirtilen kural kümesinde belirtilen kuralların tümünü içermez.

   **Kod Analizi ilkesi başarısız oldu. Projede hatalar var {0} veya derleme güncel değil.**

   Derleme hatalar içeriyor ya da hatalar düzeltildi, ancak düzeltme sonrasında kod analizi gerçekleştirilmedi.

   **İade etme başarısız oldu. Kod Analizi Ilkesi, Visual Studio 'Yu açık bir çözümle iade etmeniz gerekir.**

   Kod Analizi ilkesi, iade edilen tüm dosyaların Şu anda açık olan çözümde olması gerekir. Bu hatayı düzeltmek için, iade edilecek dosyayı içeren çözümü açın.

   **Bekleyen iadedeki tüm dosyalar şu anda açık olan çözüm içinde değil.**

   Kod Analizi ilkesi, iade edilen tüm dosyaların Şu anda açık olan çözümde olması gerekir. Bu hata, açık bir çözüm olduğunda tetiklenir, ancak "bekleyen iade etme" görünümündeki bazı dosyalar şu anda açılan çözümün parçası değildir. Bu hatayı düzeltmek için, iade edilecek dosyayı içeren çözümü açın.

   **' ' Öğesinin sürümü {0} doğru değil. İlkede belirtilen tanımlayıcı adı ' {1} '.**

   Bu hata .NET projeleri için geçerlidir. Yerel bilgisayarda kod analizi ilkesi için gereken bir kural. dll var, ancak sürüm/ortak anahtar eşleşmiyor. Bu hatayı düzeltmek için, ilke oluşturucunun, bilgisayarındaki *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\ * dizinindeki. dll 'leri güncelleştirmesi gerekir.

   **{0}ilkede belirtilen ' ' derlemesi yok.**

   Bu hata .NET projeleri için geçerlidir. Kod Analizi ilkesinin gerektirdiği bir kuralda, istemci bilgisayarda karşılık gelen dll yüklü değil. Bu hatayı düzeltmek için, ilke Oluşturucu bilgisayarında *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\ * dizininde bulunan dll 'yi güncelleştirmeniz gerekir.

   **Proje {0} kuralı ayarları, kod analizi ilkesiyle uyumlu değil.**

   Bu hata .NET projeleri için geçerlidir. Yönetilen kod kuralları ayarları, ilke gerektirdiğinden katı değildir. Bu hatayı düzeltmek için, istemci ayarı sunucusundaki ilke gereksiniminden daha katı olmalıdır.

   **Kod Analizi etkin yapılandırmada etkin değil. {0} İade etmeden önce yapılandırma ve derleme projesi ' ne geçin {1} .**

   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' De, etkin yapılandırmada kod analizi etkin değil, ancak en az bir kod analizi etkin.

   **Proje özelliklerinde yönetilen ikililer için kod analizini etkinleştirmeniz {0} ve iade etmeden önce derleme yapmanız gerekir.**

   Bu hata [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] .NET uygulamaları için geçerlidir. İlke, yönetilen kod analizinin gerçekleştirilmesini gerektiriyor, ancak istemcideki geçerli projede etkin değil.

   **{0}İade etmeden önce proje özellikleri ve derleme ' de Kod analizini etkinleştirmeniz gerekir.**

   Bu hata [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , projelere ve Web projelerine uygulanır. İlke, yönetilen kod analizinin gerçekleştirilmesini gerektiriyor, ancak istemcideki geçerli projede etkin değil.

   **Proje özelliklerinde C/C++ Kod analizini etkinleştirmeniz {0} ve iade etmeden önce derleme yapmanız gerekir.**

   Bu hata, yönetilmeyen projeler için geçerlidir. Kod Analizi ilkesi C/C++ için kod analizi gerektiriyor, ancak istemcideki geçerli projede etkin değil.

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod Analizi uygulama hataları](../code-quality/code-analysis-application-errors.md)
