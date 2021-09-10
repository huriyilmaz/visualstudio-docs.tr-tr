---
title: Subversion ile çalışma
description: Subversion'ı Mac için Visual Studio.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: bd46a9eba7770b73425f1461fab6cb8443ace26c
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962222"
---
# <a name="working-with-subversion"></a>Subversion ile çalışma

Subversion, merkezi verilerin tek bir ana kopyasını denetlemeye olanak sağlayan merkezi sürüm denetim sistemidir. Git'in aksine, Subversion deposuna göz atarak deponun tamamını kopyalamaz, yalnızca o anda anlık görüntü alır.

Subversion, kullanıcıların aynı depoda aynı anda çalışmasına olanak sağlayan bir copy-modify-merge modeli kullanır. Bu, her kullanıcının bağımsız olarak üzerinde çalıştığı merkezi verilerin yerel veya çalışan bir kopyasını oluşturduğu anlamına gelir. Kopyaları çalışan kullanıcılara yapılan değişiklikler kronolojik olarak birleştirilir.

Örneğin, A Kullanıcısı ve B Kullanıcısı'nın uzak depodan bir kopyasını kontrol edin ve her biri dosyaları değiştirir. A kullanıcısı değişiklikleri tamamlar ve uzaktan işler. B Kullanıcısı kendi çalışmalarını işlemeden önce, çalışma kopyasını uzaktan yapılan değişikliklerle güncelleştirmeli ve A Kullanıcı değişiklikleriyle birleştirmektedir.

Aşağıdaki bölümlerde Subversion'un sürüm denetimi için nasıl kullanıla Mac için Visual Studio.

Aşağıdaki görüntüde, Sürüm Denetimi menü öğesi Mac için Visual Studio tarafından sağlanan seçenekler verilmektedir:

![Sürüm Denetimi menü öğeleri](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Ödeme...

Uzak bir Subversion deposu kullanmaya başlamadan önce, yerel makinede bu dizinin çalışan bir kopyasını oluşturmak için depoyu kontrol edin.

Mac için Visual Studio'de **Checkout** özelliğini kullanma hakkında bilgi için [Subversion deposu](set-up-subversion-repository.md) ayarlama bölümündeki adımları izleyin.

## <a name="update-solution"></a>Çözümü güncelleştirme

Uzak depo kullanırken, diğer kullanıcıların dosyaları değiştirerek çalışma kopyanızı yeni bir şekilde değiştirmiş olduğunu unutmanız önemlidir. Çakışmalar göz önünde bulundurarak, işe başlamadan önce ve işlemeden önce her zaman depodan çözümünüze değişiklikleri çekmeniz önerilir. Çekme değişiklikleri yapmak için Sürüm **Denetimi'> Güncelleştirme menü** öğesini seçin.

## <a name="review-solution-and-commit"></a>Çözümü ve işlemeyi gözden geçirme

Dosyalarda yapılan değişiklikleri gözden geçirmek için, aşağıdaki görüntüde gösterildiği gibi her belgeye yönelik Değişiklikler, Sorumlu, Günlük ve Birleştir sekmelerini kullanın:

![Sürüm Denetimi Sekmeleri](media/version-control-vcTabs.png)

Çözüm ve Yürütme menü öğesini gözden geçirerek Sürüm **Denetimi'ne göz > projesinde yapılan tüm değişiklikleri** gözden geçirme:

![Çözümü Gözden Geçirme](media/version-control-vcStatus.png)

Bu, projenin her dosyasındaki tüm değişiklikleri Geri Döndürme, Düzeltme Eki Oluşturma veya Yürütme seçeneğiyle görüntülemeye olanak sağlar.

Bir dosyayı uzak depoya işlemek için, Commit... tuşuna basın, bir işleme iletisi girin ve Commit Düğmesi ile onaylayın:

![Dosya işleme](media/version-control-svnCommit.png)

Bu, tüm değişikliklerinizin yeni düzeltmelerini oluşturdukları depoya gönderir.

## <a name="see-also"></a>Ayrıca bkz.

- [Subversion deposu ayarlama](set-up-subversion-repository.md)
