---
title: Oturum Hata Ayıklama Yöneticisi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712881"
---
# <a name="session-debug-manager"></a>Oturum hata ayıklama yöneticisi
Oturum hata ayıklama yöneticisi (SDM), birden çok işlemdeki herhangi bir sayıda programı herhangi bir sayıda makinede hata ayıklayan herhangi bir sayıda hata ayıklama altyapısını (DE) yönetir. Hata ayıklama motoru çoklayıcı olmasının yanı sıra, SDM Hata Ayıklama oturumunun IDE'ye birleşik bir görünümünü sağlar.

## <a name="session-debug-manager-operation"></a>Oturum hata ayıklama yöneticisi işlemi
 Oturum hata ayıklama yöneticisi (SDM) DE yönetir. Aynı anda bir makinede birden fazla hata ayıklama motoru çalıştırılabilir. DEs'i çok katlı hale getirmek için, SDM DEs'lerden bir dizi arabirimi sarar ve bunları tek bir arabirim olarak IDE'ye sunar.

 Performansı artırmak için bazı arabirimler çok katlı değildir. Bunun yerine, doğrudan DE'den kullanılırlar ve bu arabirimlere yapılan aramalar SDM'den geçmez. Örneğin, bellek, kod ve belge bağlamlarıyla kullanılan arabirimler, belirli bir DE tarafından debugged belirli bir programda belirli bir yönerge, bellek veya belgeye atıfta bulunduğundan çok katlı değildir. Başka hiçbir DE iletişim bu düzeyde yer almak gerekir.

 Bu tüm bağlamlar için geçerli değildir. İfade değerlendirme bağlamı arabirimine yapılan aramalar SDM'den geçer. İfade değerlendirmesi sırasında SDM, IDE'ye verdiği [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimini sarar, çünkü bu ifade değerlendirildiğinde, aynı iş parçacığı üzerinde çalışan aynı işlemde hata ayıklama programları olan birden çok DE içerebilir.

 SDM genellikle bir delegasyon mekanizması gibi davranır, ancak bir yayın mekanizması olarak hareket edebilir. Örneğin, ifade değerlendirmesi sırasında SDM, tüm DEs'leri belirli bir iş parçacığı üzerinde kod çalıştırabileceklerini bildirmek için bir yayın mekanizması görevi görür. Benzer şekilde, SDM bir durdurma olayı aldığında, yürütmeyi durdurmaları gereken programlara yayın yapar. Bir adım çağrıldığında, SDM çalışmaya devam edebilecekleri programlara yayın yapar. Kesme noktaları da her DE'ye yayınlanır.

 SDM geçerli programı, iş parçacığı veya yığın çerçevesini izlemez. İşlem, program ve iş parçacığı bilgileri, belirli hata ayıklama olayları ile birlikte SDM'ye gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md)
- [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md)
