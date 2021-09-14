---
title: Kod Analiz İlkesi Hataları
ms.date: 11/04/2016
description: Kod analizi ilkesi hataları hakkında bilgi Visual Studio. Kod iade edilirken ilke karşılanmazsa oluşan hataların açıklamalarını görüntüleme.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632079"
---
# <a name="code-analysis-policy-errors"></a>Kod Analiz İlkesi Hataları

Kod analizi ilkesi iade sırasında karşılanmazsa aşağıdaki hatalar oluşur:

**Bir Code Analysis proje için ilke ayarları, bir veya daha fazla proje için Code Analysis uyumlu değildir.**

Proje kaynak denetimine giriş yapılan kod analizi gereksinimleri bir veya daha fazla kod projesi için karşılanmaz. Bu hata aşağıdaki koşullardan biri veya daha fazlası nedeniyle olabilir:

- Code Analysis çözümde tüm projeler için derlemede etkinleştirilmemiş.

- Visual Studio'daki proje için yerel kural kümesi, proje  kuralı kümesinden daha az kısıtlayıcı bir Eylem ayarına sahip olabilir. Örneğin, sunucuda Eylem Hatası olarak ayarlanmış bir kural, kural kümesinde Uyarı veya Yok olarak =  ayarlanmış Visual Studio).   

- içinde belirtilen kural Visual Studio, projenin iade ilkesinde belirtilen kural kümesinde belirtilen Code Analysis kuralların hepsini içermez.

**İlke Code Analysis başarısız oldu. Projede hatalar var {0} veya derleme güncel değil.**

Derleme hatalar içeriyor veya hatalar düzeltildi, ancak düzeltmeden sonra kod analizi gerçekleştirilmiyor.

**Giriş başarısız oldu. Code Analysis İlkesi, açık bir çözümle Visual Studio aracılığıyla iade gerektirir.**

Kod analizi ilkesi, iade olan tüm dosyaların o anda açık olan çözümde olması gerekir. Bu hatayı düzeltmek için iade etmek istediğiniz dosyayı içeren çözümü açın.

**Bekleyen iadedeki tüm dosyalar o anda açık olan çözüm içinde yer alan dosyalar değildir.**

Kod analizi ilkesi, iade olan tüm dosyaların o anda açık olan çözümde olması gerekir. Bu hata açık bir çözüm olduğunda ortaya çıkar, ancak "bekleyen iade" görünümündeki bazı dosyalar o anda açık olan çözümün parçası değildir. Bu hatayı düzeltmek için iade etmek istediğiniz dosyayı içeren çözümü açın.

**'' {0} sürümü doğru değil. İlkede belirtilen strong-name şu {1} şekildedir: ' '.**

Bu hata .NET projeleri için geçerlidir. Kod .dll ilkesi için gerekli olan bir kural yerel bilgisayarda mevcuttur, ancak sürüm/ortak anahtar eşleşmez. Bu hatayı düzeltmek için, ilke oluşturucusu bilgisayarlarında *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules \\* dizininde .dll'leri güncelleştirmesi gerekir.

**İlkede belirtilen ' {0} ' derlemesi yok.**

Bu hata .NET projeleri için geçerlidir. Kod analizi ilkesi için gerekli olan bir kural, istemci bilgisayarda karşılık gelen dll'ye sahip değildir. Bu hatayı düzeltmek için, ilke oluşturucusu bilgisayarlarında *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules \\* dizininde dll'yi güncelleştirmesi gerekir.

**{0}Project kural ayarları, ilkeyle uyumlu Code Analysis değildir.**

Bu hata .NET projeleri için geçerlidir. Yönetilen kod kuralları ayarları ilkenin gerektirdiği kadar katı değildir. Bu hatayı düzeltmek için istemci ayarının sunucuda ilke gereksinimiyle aynı veya daha katı olması gerekir.

**Code Analysis yapılandırmada etkin değil. Denetlemeden önce {0} yapılandırmaya ve {1} derleme projesine geçiş yap.**

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'de, etkin yapılandırmada kod analizi etkin değildir, ancak en az bir kod analizi etkindir.

**Giriş öncesinde proje Code Analysis ve derlemede yönetilen ikili dosyalar için yönetilen {0} ikili dosyalar için ilkeyi etkinleştirmeniz gerekir.**

Bu hata [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .NET uygulamaları için geçerlidir. İlkenin gerçekleştirilecek yönetilen kod analizi gerekir, ancak istemcide geçerli projede etkinleştirilmez.

**Giriş Code Analysis proje özelliklerinde {0} ve derlemesinde bu özelliği etkinleştirmeniz gerekir.**

Bu hata projelere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve web projelerine uygulanır. İlkenin gerçekleştirilecek yönetilen kod analizi gerekir, ancak istemcide geçerli projede etkinleştirilmez.

**Giriş öncesinde proje özelliklerinde ve derlemede C/C++ Code Analysis {0} etkinleştirmeniz gerekir.**

Bu hata, unmanaged projeleri için geçerlidir. Kod analizi ilkesi C/C++ için Code Analysis gerektirir, ancak istemcide geçerli projede etkinleştirilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Code Analysis Uygulama Hataları](../code-quality/code-analysis-application-errors.md)
