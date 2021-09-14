---
title: Oturum Hata Ayıklama Yöneticisi | Microsoft Docs
description: Herhangi bir sayıda makinede birden çok işlemde birden çok hata ayıklama altyapısının hata ayıklama programlarını yöneten oturum hata ayıklama yöneticisi hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3ecfcf276339a54c4c77157101b03b9297d54512
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626438"
---
# <a name="session-debug-manager"></a>Oturum hata ayıklama yöneticisi
Oturum hata ayıklama yöneticisi (SDM), herhangi bir sayıda makinede birden çok işlemde herhangi bir sayıda programda hata ayıklarken herhangi bir sayıda hata ayıklama altyapısını (DE) yönetir. SDM, hata ayıklama altyapısı multiplexer'sı olmanın yanı sıra IDE'de hata ayıklama oturumunun birleşik bir görünümünü sağlar.

## <a name="session-debug-manager-operation"></a>Oturum hata ayıklama yöneticisi işlemi
 OTURUM hata ayıklama yöneticisi (SDM) DE'i yönetir. Bir makinede aynı anda birden fazla hata ayıklama altyapısı çalıştırabilirsiniz. SDM, DE'leri çok kat daha fazla yapmak için DE'lerden bir dizi arabirimi sarmalar ve bunları tek bir arabirim olarak IDE'de gösterir.

 Performansı artırmak için bazı arabirimler çok sayıda değil. Bunun yerine, bunlar doğrudan DE'den kullanılır ve bu arabirimlere yapılan çağrılar SDM'den geçmz. Örneğin, bellek, kod ve belge bağlamları ile kullanılan arabirimler, belirli bir DE tarafından hata ayıklaması yapılan belirli bir programda belirli bir yönergeye, belleğe veya belgeye başvurarak birden çok kez kullanılamaz. Bu iletişim düzeyine başka de dahil olmak zorunda değil.

 Bu durum tüm bağlamlar için doğru değildir. İfade değerlendirme bağlam arabirimine yapılan çağrılar SDM'den geçmektedir. İfade değerlendirmesi sırasında SDM, [IDE'ye verdiği IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimini sarmalar çünkü bu ifade değerlendir geldiğinde, aynı işlemde aynı iş parçacığı üzerinde çalışıyor olan aynı işlemde programlarda hata ayıklayıcı olan birden çok DE içeriyor olabilir.

 SDM genellikle bir temsilci mekanizması olarak hareket eder, ancak bir yayın mekanizması olarak hareket eder. Örneğin, ifade değerlendirmesi sırasında SDM, tüm DE'lere belirtilen iş parçacığında kod çalıştıracaklarını bildiren bir yayın mekanizması olarak davranır. Benzer şekilde, SDM bir durdurma olayı aldığında, çalıştırmayı durdurması gereken programlara yayınlar. Bir adım çağrıldında SDM, çalışmaya devam edecekleri programlara yayınlar. Kesme noktaları her DE'ye de yayındadır.

 SDM geçerli programı, iş parçacığını veya yığın çerçevesini izlemez. İşlem, program ve iş parçacığı bilgileri, belirli hata ayıklama olaylarıyla birlikte SDM'ye gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklayıcısı bileşenleri](../../extensibility/debugger/debugger-components.md)
- [Hata ayıklayıcısı bağlamları](../../extensibility/debugger/debugger-contexts.md)
