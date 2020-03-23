---
title: Subversion ile çalışma
description: Mac için Visual Studio'da Subversion'ı kullanma.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: d687215bc91dc01a284c49c141a6e52a16ce9e7a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692133"
---
# <a name="working-with-subversion"></a>Subversion ile çalışma

Subversion, merkezi leştirilmiş verilerin tek bir ana kopyasını kontrol etmenizi sağlayan merkezi sürüm denetim sistemidir. Git'in aksine, bir Subversion deposunu kontrol etmek tüm depoyu klonlamaz, yalnızca o noktada anlık görüntü alır.

Subversion, kullanıcıların aynı depo üzerinde aynı anda çalışmasına izin vermek için bir kopyalama-değiştirme-birleştirme modeli kullanır. Bu, her kullanıcının bağımsız olarak üzerinde çalıştıkları merkezi leştirilmiş verilerin yerel veya çalışan bir kopyasını oluşturduğu anlamına gelir. Kopyaları çalıştıran kullanıcılarda yapılan değişiklikler kronolojik bir şekilde birleştirilir.

Örneğin, Kullanıcı A ve Kullanıcı B'nin hem uzak depodan bir kopyayı kullanıma aldıklarını ve her birinin dosyaları değiştirdiğini düşünün. Kullanıcı A değişiklikleri bitirir ve uzaktan işler. Kullanıcı B çalışmalarını gerçekleştirmeden önce, çalışma kopyalarını uzaktan kumandadaki değişikliklerle güncelleştirmeleri ve Kullanıcı A'nın değişikliklerinde birleştirilmesi gerekir.

Aşağıdaki bölümlerde, Subversion'un Mac için Visual Studio'da sürüm kontrolü için nasıl kullanılabileceğini araştırın.

Aşağıdaki resim, Visual Studio tarafından Mac için Sürüm Denetimi menü öğesi tarafından sağlanan seçenekleri göstermektedir:

![Sürüm Denetimi menü öğeleri](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Ödeme...

Uzaktan Sürüm deposunu kullanmaya başlamadan önce, yerel makinenizde bu dizinin çalışan bir kopyasını oluşturmak için repo'ya göz atın.

Mac için Visual Studio'da **Ödeme** özelliğini kullanma hakkında bilgi edinmek için, [Alt Sürüm deposu oluşturma](set-up-subversion-repository.md) bölümündeki adımları izleyin.

## <a name="update-solution"></a>Çözümü güncelleştir

Uzaktan depo kullanırken, diğer kullanıcıların dosyaları değiştirerek çalışma kopyanızı eski haline getirebileceğini unutmamak gerekir. Çakışma beklentisiyle, işe başlamadan önce ve taahhüt etmeden önce depodaki değişiklikleri çözümünüze çekmeniz her zaman önerilir. Çekme değişiklikleri yapmak için **Sürüm Denetimi > Update Solution** menü öğesini seçin.

## <a name="review-solution-and-commit"></a>Çözümü gözden geçirin ve işleme

Dosyalardaki değişiklikleri gözden geçirmek için, aşağıdaki resimde gösterildiği gibi her belgede Değişiklikler, Suçlama, Günlük ve Birleştirme sekmelerini kullanın:

![Sürüm Denetim Sekmeleri](media/version-control-vcTabs.png)

Sürüm Denetimi > Gözden Geçir **çözümünün ve Ekle** menü öğesine göz atarak projedeki tüm değişiklikleri gözden geçirin:

![Çözümü İncele](media/version-control-vcStatus.png)

Bu, bir projenin her dosyasındaki tüm değişiklikleri Revert, Create Patch veya Commit seçeneğiyle görüntülemeye olanak tanır.

Dosyayı uzak depoya işlemek için Commit...', commit iletisi girin ve Commit Düğmesi ile onaylayın:

![Dosya işleme](media/version-control-svnCommit.png)

Bu, değişiklikleri depoya gönderve tüm değişikliklerinizin yeni revizyonunu oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir Subversion deposu ayarlama](set-up-subversion-repository.md)
