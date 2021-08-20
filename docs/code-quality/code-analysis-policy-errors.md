---
title: Kod Analiz İlkesi Hataları
ms.date: 11/04/2016
description: Visual Studio kod analizi ilke hataları hakkında bilgi edinin. Kod iade edildiğinde ilke karşılanmıyorsa oluşan hataların açıklamalarını görüntüleyin.
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 9ca28097058c0f9c7722aacd806f00af3ef263a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105827"
---
# <a name="code-analysis-policy-errors"></a>Kod Analiz İlkesi Hataları

Kod Analizi ilkesi iadede karşılanmıyorsa aşağıdaki hatalar oluşur:

**bir veya daha fazla projenin Code Analysis ayarları Code Analysis ilkesiyle uyumlu değil.**

Bir veya daha fazla kod projesi için proje kaynak denetimine iade etme kod analizi gereksinimleri karşılanmadı. Bu hata, aşağıdaki koşullardan biri veya birkaçı nedeniyle oluşabilir:

- Code Analysis çözümdeki tüm projelere yönelik derlemede etkin değil.

- Visual Studio içindeki proje için yerel kural kümesi, proje kuralı kümesinden daha az kısıtlayıcı bir **eylem** ayarına sahip. örneğin, sunucuda **eylem** hatası olarak ayarlanan bir kuralın =  **eylemi** **uyarı** olarak ayarlanmış veya kural kümesinde Visual Studio olarak çalıştırılmakta olan bir kural **yok** .

- Visual Studio belirtilen kural kümesi, proje için Code Analysis iade ilkesinde belirtilen kural kümesinde belirtilen kuralların tümünü içermiyor.

**Code Analysis ilkesi başarısız oldu. Projede hatalar var {0} veya derleme güncel değil.**

Derleme hatalar içeriyor ya da hatalar düzeltildi, ancak düzeltme sonrasında kod analizi gerçekleştirilmedi.

**İade etme başarısız oldu. Code Analysis ilkesi, açık bir çözümle birlikte Visual Studio iade etmeniz gerekir.**

Kod Analizi ilkesi, iade edilen tüm dosyaların Şu anda açık olan çözümde olması gerekir. Bu hatayı düzeltmek için, iade edilecek dosyayı içeren çözümü açın.

**Bekleyen iadedeki tüm dosyalar şu anda açık olan çözüm içinde değil.**

Kod Analizi ilkesi, iade edilen tüm dosyaların Şu anda açık olan çözümde olması gerekir. Bu hata, açık bir çözüm olduğunda tetiklenir, ancak "bekleyen iade etme" görünümündeki bazı dosyalar şu anda açılan çözümün parçası değildir. Bu hatayı düzeltmek için, iade edilecek dosyayı içeren çözümü açın.

**' ' Öğesinin sürümü {0} doğru değil. İlkede belirtilen tanımlayıcı adı ' {1} '.**

Bu hata .NET projeleri için geçerlidir. Kod Analizi ilkesinin gerektirdiği bir kural .dll yerel bilgisayarda bulunuyor, ancak sürüm/ortak anahtar eşleşmiyor. bu hatayı düzeltmek için, ilke oluşturucunun, bilgisayarında *C:\Program Files \ Microsoft Visual Studio 8 \ Team tools\static Analysis tools\fxcop\rules \\* dizinindeki. dll 'leri güncelleştirmesi gerekir.

**{0}ilkede belirtilen ' ' derlemesi yok.**

Bu hata .NET projeleri için geçerlidir. Kod Analizi ilkesinin gerektirdiği bir kuralda, istemci bilgisayarda karşılık gelen dll yüklü değil. bu hatayı düzeltmek için, ilke oluşturucu bilgisayarında *C:\Program Files \ Microsoft Visual Studio 8 \ Team tools\static Analysis tools\fxcop\rules \\* dizininde bulunan dll 'yi güncelleştirmeniz gerekir.

**Project {0} kural ayarları Code Analysis ilkesiyle uyumlu değil.**

Bu hata .NET projeleri için geçerlidir. Yönetilen kod kuralları ayarları, ilke gerektirdiğinden katı değildir. Bu hatayı düzeltmek için, istemci ayarı sunucusundaki ilke gereksiniminden daha katı olmalıdır.

**Code Analysis etkin yapılandırmada etkin değil. {0}İade etmeden önce yapılandırma ve derleme projesi ' ne geçin {1} .**

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' De, etkin yapılandırmada kod analizi etkin değil, ancak en az bir kod analizi etkin.

**proje özelliklerinde yönetilen ikililer için Code Analysis etkinleştirmeniz {0} ve iade etmeden önce derleme yapmanız gerekir.**

Bu hata [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .NET uygulamaları için geçerlidir. İlke, yönetilen kod analizinin gerçekleştirilmesini gerektiriyor, ancak istemcideki geçerli projede etkin değil.

**{0}iade etmeden önce proje özellikleri ve derleme Code Analysis etkinleştirmeniz gerekir.**

Bu hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , projelere ve Web projelerine uygulanır. İlke, yönetilen kod analizinin gerçekleştirilmesini gerektiriyor, ancak istemcideki geçerli projede etkin değil.

**proje özelliklerinde C/C++ Code Analysis etkinleştirmeniz {0} ve iade etmeden önce derleme yapmanız gerekir.**

Bu hata, yönetilmeyen projeler için geçerlidir. kod analizi ilkesi C/C++ için Code Analysis gerektiriyor, ancak istemcideki geçerli projede etkin değil.

## <a name="see-also"></a>Ayrıca bkz.

- [Code Analysis Uygulama hataları](../code-quality/code-analysis-application-errors.md)
