---
title: Kaynak Düzenleyicisi
description: Mac için Visual Studio 'de kaynak düzenleyiciyi kullanma
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 187805767e9f67851975dccf8513c708c4233ccc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985208"
---
# <a name="source-editor"></a>Kaynak Düzenleyicisi

Güvenilir bir kaynak Düzenleyicisi, kod succinctly ve verimli bir şekilde yazmak için gereklidir. Mac için Visual Studio IDE ile etkileşimlerinizin merkezinde olan gelişmiş bir kaynak Düzenleyicisi sağlar. Kaynak Düzenleyicisi, bekleyebileceğiniz ve işinizi kolayca yapmanız gerekebilecek özellikler sağlar: Bu tür bir sözdizimi vurgulaması, kod parçacıkları ve kod katlama sayesinde, tam işlevli IntelliSense kod tamamlama gibi Roslyn derleyici tümleştirmesinin avantajları.

Mac için Visual Studio kaynak Düzenleyicisi, IDE 'deki hata ayıklama, yeniden düzenleme ve sürüm denetimi tümleştirmesi gibi tüm diğer işlevlerle sorunsuz bir deneyim sağlar.

Bu makalede, kaynak Düzenleyicisi 'nin bazı önemli özellikleri tanıtılmakta ve Mac için Visual Studio olabildiğince üretken olmak için nasıl kullanabileceğiniz açıklanır.

## <a name="the-source-editor-experience"></a>Kaynak Düzenleyicisi deneyimi

Kod genelinde etkili bir şekilde görüntüleme ve taşıma, geliştirme iş akışının ayrılmaz bir parçasıdır. Kodu görüntüleme ve sürdürme konusunda tam olarak nasıl karar vereceğiniz, geliştiriciler arasında ve genellikle projeler arasında farklılık gösteren bir kişisel karardır.

Mac için Visual Studio platformlar arası geliştirmeyi erişilebilir ve mümkün olduğunca kullanışlı hale getirmek için birçok güçlü özellik sunar. Aşağıdaki bölümlerde bazı vurguların bazıları açıklanır.

## <a name="code-folding"></a>Kod katlama

Kod katlama, geliştiricilerin yönergeler, demirbaş kodu ve açıklamaları ve #region deyimlerini kullanma gibi tüm kod bölümlerini göstermesini veya gizlemesini sağlayarak büyük kaynak kodu dosyalarını yönetmeyi kolaylaştırır. Kod katlama Mac için Visual Studio varsayılan olarak kapalıdır

Kod katlamayı açmak için **Visual Studio > tercihleri > metin Düzenleyicisi ' ne gidin > genel > kod katlaması**:

![Kod katlama seçenekleri](media/source-editor-image1.png)

Bu menü Ayrıca, kod yerine adlandırılmış bir ipucu görüntüleyerek #regions ve açıklamaları varsayılan olarak katlama seçeneğini de içerir.

Bölümleri göstermek veya gizlemek için, satır numarasının yanındaki açıklama pencere öğesini kullanın:

![Koddaki bölümleri gösterme veya gizleme](media/source-editor-image2.png)

Ayrıca, **görünüm > katlamayı kullanarak katların** gösterilmesi ve gizlenmesi arasında geçiş yapabilirsiniz > katlama ve menüyü değiştir menü öğesi:

![Katlama menüsü öğesi](media/source-editor-image19.png)

Bu menü öğesi, kod katlamayı etkinleştirmek veya devre dışı bırakmak için de kullanılabilir.

## <a name="white-space"></a>Boşluk

Kaynak kodda görünmeyen karakterleri görüntülemeniz gerekebilir. Bu, kodlama standartlarına bağlı olduğunuzdan ve gereksiz bir şekilde alan beklediğinizden emin olmak için görülebilir bir yoldur. Ayrıca, kodu değerlendirmek için tam olarak girintili satırlara bağlı olan F # yazma sırasında da yararlıdır.

**Visual Studio > tercihleri > metin düzenleyicisi > işaretçileri ve cetvellere**giderek boşluğu göstermek için seçenekleri ayarlayın. Bu seçeneğin belirlenmesi, görünmeyen karakterler gösterildiğinde _ayarlamaya izin_verir   : hiçbir zaman, seçimde veya her zaman:

![Görünmeyen karakter seçeneklerini göster](media/source-editor-image3.png)

Sekmeleri, boşlukları ve satır sonlarını gösterme seçeneği de kullanılabilir:

![Sekmeleri ve boşlukları göster](media/source-editor-image4.png)

Görünmez karakterler, aşağıdaki görüntüde gösterildiği gibi gri noktalar olarak görüntülenir:

![boşluk görüntülendi](media/source-editor-image22.png)

## <a name="ruler"></a>Cetvel

Sütun cetveli, özellikle satır uzunluğu yönergelerine sahip bir ekip üzerinde çalışırken, satır uzunluklarını belirlemek için faydalıdır. Aşağıdaki görüntüde gösterildiği gibi, **Visual Studio > tercihleri > metin düzenleyicisi > işaretçileri ve cetvellerinin** yanı sıra **sütun cetvelini**seçerek (veya seçimini kaldırarak), sütun cetveli açılabilir veya kapatılabilir:

!["Sütun cetvelini göster" vurgulanmış Tercihler iletişim kutusu](media/source-editor-image5.png)

 Bu, kaynak düzenleyicide dikey açık gri çizgi olarak görüntülenir.

## <a name="highlight-identifier-references"></a>Tanımlayıcı başvurularını Vurgula

"Tanımlayıcı başvurularını Vurgula" seçeneği etkin olduğunda, kaynak kodda herhangi bir sembol seçebilirsiniz ve kaynak Düzenleyici bu dosyadaki diğer tüm başvurulara görsel kılavuz sağlar. Bu seçeneği etkinleştirmek için **Visual Studio > tercihleri > metin düzenleyicisi > işaretleyiciler ve cetveller** ' e gidin ve aşağıdaki görüntüde gösterildiği gibi _tanımlayıcı başvurularını Vurgula_' yı seçin:

!["Tanımlayıcı başvurularını Vurgula" vurgulanmış Tercihler iletişim kutusu](media/source-editor-image6.png)

Vurgulamanın rengi, bir şeyin atandığını veya başvurulduğunu belirten da yararlıdır. Bir şey atanmışsa, kırmızı renkle vurgulanır; başvuruluyorsa mavi renkle vurgulanır:

![Vurgulamanın rengini gösteren örnek](media/source-editor-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri (Windows üzerinde Visual Studio)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Anahat oluşturma (Windows üzerinde Visual Studio)](/visualstudio/ide/outlining)