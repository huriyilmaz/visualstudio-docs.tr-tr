---
title: Subversion ile çalışma
description: Mac için Visual Studio ' de merkezi sürüm denetim sistemi olarak alt sürümle nasıl çalışacağınızı öğrenin.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 512432a7210999e1d432494ec67bb2bf7a0e6a11
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846849"
---
# <a name="working-with-subversion"></a>Subversion ile çalışma

Alt sürüm, merkezi verilerin tek bir ana kopyasını denetlemenizi sağlayan merkezi sürüm denetim sistemidir. Git 'in aksine bir alt sürüm deposu, deponun tamamını kopyalamaz ve bu noktada yalnızca bir anlık görüntü alır.

Alt sürüm, kullanıcıların aynı depoda aynı anda çalışmasına izin vermek için bir kopyalama-değiştirme-birleştirme modeli kullanır. Bu, her kullanıcının bağımsız olarak çalıştıkları merkezi verilerin yerel veya çalışan bir kopyasını oluşturduğu anlamına gelir. Kullanıcı çalışma kopyalarında yapılan değişiklikler kronolojik biçimde birleştirilir.

Örneğin, A kullanıcısının A ve B kullanıcısının uzak depodan bir kopyayı kontrol etmekte olduğunu ve bunların her birinin dosyayı değiştirmekte olduğunu düşünün. Kullanıcı A değişiklikleri tamamlar ve uzaktan kaydeder. Kullanıcı B işlerini işlemeden önce, çalışma kopyalarını, Kullanıcı A 'nın değişikliklerinde bulunan değişikliklerle güncelleştirmeleri gerekir.

Aşağıdaki bölümlerde, Mac için Visual Studio ' de sürüm denetimi için alt sürümün nasıl kullanılabileceği araştırılamaz.

Aşağıdaki görüntüde, sürüm denetim menüsü öğesi tarafından Mac için Visual Studio tarafından belirtilen seçenekler gösterilmektedir:

![Sürüm denetimi menü öğeleri](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Kullanıma al...

Uzak bir alt sürüm deposunu kullanmaya başlamadan önce, yerel makinenizde bu dizinin çalışma kopyasını oluşturmak için depoyu inceleyin.

Mac için Visual Studio ' de **kullanıma alma** özelliğini kullanma hakkında bilgi edinmek için, [bir alt sürüm deposu ayarlama](set-up-subversion-repository.md) bölümündeki adımları izleyin.

## <a name="update-solution"></a>Çözümü Güncelleştir

Uzak bir depo kullanırken, diğer kullanıcıların dosyaları değiştiriyor olabileceğini unutmamak önemlidir. Bu, çalışma kopyanızın güncelliğini yitirmiş hale getirir. Olasılığına ' de, her zaman, iş başlamadan önce ve işlemeden önce, depodaki tüm değişiklikleri çözümünüze çekmeye önerilir. Çekme değişiklikleri yapmak için **sürüm denetimi > çözüm** menü öğesini seçin.

## <a name="review-solution-and-commit"></a>Çözümü gözden geçir ve Yürüt

Dosyalardaki değişiklikleri gözden geçirmek için, aşağıdaki görüntüde gösterildiği gibi her bir belgedeki değişiklikleri, güçlendirme, günlük ve birleştirme sekmelerini kullanın:

![Sürüm denetimi sekmeleri](media/version-control-vcTabs.png)

Sürüm denetimine göz atarak bir projedeki tüm değişiklikleri gözden geçirin **> çözüm ve COMMIT** menü öğesi:

![Çözümü gözden geçir](media/version-control-vcStatus.png)

Bu, bir proje dosyasındaki tüm değişiklikleri alma, düzeltme eki oluşturma veya tamamlama seçeneğiyle görüntülemeyi sağlar.

Uzak depoya bir dosyayı yürütmek için, Yürüt... düğmesine basın, bir teslim iletisi girin ve Kaydet düğmesini kullanarak onaylayın:

![Dosya yürütülüyor](media/version-control-svnCommit.png)

Bu işlem, değişiklikleri depoya tüm değişikliklerinizin yeni düzeltmesini oluşturduklarında gönderir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir alt sürüm deposu ayarlama](set-up-subversion-repository.md)
