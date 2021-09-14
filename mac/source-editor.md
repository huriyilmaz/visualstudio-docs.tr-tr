---
title: Kaynak Düzenleyicisi
description: Mac için Visual Studio 'de kaynak düzenleyiciyi kullanma
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: c4a22ec0765c39a8bec83f9e2acff7b22b706890
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725977"
---
# <a name="source-editor"></a>Kaynak Düzenleyicisi

Güvenilir bir kaynak Düzenleyicisi, kod succinctly ve verimli bir şekilde yazmak için gereklidir. Mac için Visual Studio ıde ile etkileşimlerinizin merkezinde olan gelişmiş bir kaynak düzenleyicisi sağlar. Kaynak Düzenleyicisi, bekleyebileceğiniz ve işinizi kolayca yapmanız gerekebilecek özellikler sağlar: Bu tür bir sözdizimi vurgulaması, kod parçacıkları ve kod katlama sayesinde, tam işlevli IntelliSense kod tamamlama gibi Roslyn derleyici tümleştirmesinin avantajları.

Mac için Visual Studio kaynak düzenleyicisi, ıde 'deki hata ayıklama, yeniden düzenleme ve sürüm denetimi tümleştirmesi gibi tüm diğer işlevlerle sorunsuz bir deneyim sağlar.

bu makalede, kaynak düzenleyicisi 'nin bazı önemli özellikleri tanıtılmakta ve Mac için Visual Studio olabildiğince üretken olmak için nasıl kullanabileceğiniz açıklanır.

## <a name="the-source-editor-experience"></a>Kaynak Düzenleyicisi deneyimi

Kod genelinde etkili bir şekilde görüntüleme ve taşıma, geliştirme iş akışının ayrılmaz bir parçasıdır. Kodu görüntüleme ve sürdürme konusunda tam olarak nasıl karar vereceğiniz, geliştiriciler arasında ve genellikle projeler arasında farklılık gösteren bir kişisel karardır.

Mac için Visual Studio platformlar arası geliştirmeyi erişilebilir ve mümkün olduğunca kullanışlı hale getirmek için birçok güçlü özellik sunar. Aşağıdaki bölümlerde bazı vurguların bazıları açıklanır.

## <a name="code-folding"></a>Kod katlama

Kod katlama, geliştiricilerin yönergeler, demirbaş kodu ve açıklamaları ve #region deyimlerini kullanma gibi tüm kod bölümlerini göstermesini veya gizlemesini sağlayarak büyük kaynak kodu dosyalarını yönetmeyi kolaylaştırır. kod katlama Mac için Visual Studio varsayılan olarak kapalıdır

kod katlamayı açmak için **Visual Studio > tercihleri > metin düzenleyicisine gidin > genel > kod katlaması**:

![Kod katlama seçenekleri](media/source-neweditor-image1.png)

Bu menü Ayrıca, kod yerine adlandırılmış bir ipucu görüntüleyerek #regions ve açıklamaları varsayılan olarak katlama seçeneğini de içerir.

Bölümleri göstermek veya gizlemek için, satır numarasının yanındaki açıklama pencere öğesini kullanın:

![Koddaki bölümleri gösterme veya gizleme](media/source-neweditor-image2.png)

Ayrıca, **görünüm > katlamayı kullanarak katların** gösterilmesi ve gizlenmesi arasında geçiş yapabilirsiniz > katlama ve menüyü değiştir menü öğesi:

![Katlama menüsü öğesi](media/source-editor-image19.png)

Bu menü öğesi, kod katlamayı etkinleştirmek veya devre dışı bırakmak için de kullanılabilir.

## <a name="word-wrap"></a>Sözcük kaydırma

Sözcük kaydırması, uzun kod satırları veya sınırlı görünüm alanı ile çalışırken alanı yönetmenize yardımcı olabilir. Word sarması Ayrıca, görünümü gizlememiş veya kaynak görünümlerinizin genişliğini azaltan bölmeleri açarken bile kod görünümlerinizin kaynak dosyanızın tüm içeriğini içerdiğinden emin olabilir. 

sözcük kaydırması varsayılan olarak devre dışıdır, ancak Mac için Visual Studio içindeki **tercihler** aracılığıyla etkinleştirilebilir. 

sözcük kaydırmayı etkinleştirmek için **Visual Studio > tercihleri > metin düzenleyicisi > kelime kaydırması**' e gidin:

![Sözcük kaydır seçenekleri](media/source-neweditor-wordwrap1.png)

Sözcük kaydırması etkinken, kaynak Düzenleyicisi görünümlerinizin genişliğini aşan satırlar otomatik olarak kaynak dosyanızda bir sonraki satıra kaydırılır. Kaydırılmış çizgiler ' in yanında görünür bir karakter görüntülenecek bir seçeneği de etkinleştirebilirsiniz. Bu, otomatik olarak sarmalanmış satırlar ve el ile sarmalanmış satırlar arasında ayrım yapmanıza olanak tanır.

![Sözcük sarmalama etkinken sarmalanmış metin](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Cetvel

Sütun cetveli, özellikle satır uzunluğu yönergelerine sahip bir ekip üzerinde çalışırken, satır uzunluklarını belirlemek için faydalıdır. sütun cetvelini **Visual Studio > tercihleri > metin düzenleyicisi > işaretleyiciler ve cetveller** ' e giderek, aşağıdaki görüntüde gösterildiği gibi **sütun cetvelini** seçerek (veya seçimini kaldırarak) açılır:

!["Sütun cetvelini göster" vurgulanmış Tercihler iletişim kutusu](media/source-editor-image5.png)

 Bu, kaynak düzenleyicide dikey açık gri çizgi olarak görüntülenir.

## <a name="highlight-identifier-references"></a>Tanımlayıcı başvurularını Vurgula

"Tanımlayıcı başvurularını Vurgula" seçeneği etkin olduğunda, kaynak kodda herhangi bir sembol seçebilirsiniz ve kaynak Düzenleyici bu dosyadaki diğer tüm başvurulara görsel kılavuz sağlar. bu seçeneği etkinleştirmek için **Visual Studio > tercihleri > metin düzenleyici > işaretleyiciler ve cetveller** ' e gidin ve aşağıdaki görüntüde gösterildiği gibi _tanımlayıcı başvurularını vurgula_' yı seçin:

!["Tanımlayıcı başvurularını Vurgula" vurgulanmış Tercihler iletişim kutusu](media/source-editor-image6.png)

Vurgulamanın rengi, bir şeyin atandığını veya başvurulduğunu belirten da yararlıdır. Bir şey atanmışsa, kırmızı renkle vurgulanır; başvuruluyorsa mavi renkle vurgulanır:

![Vurgulamanın rengini gösteren örnek](media/source-editor-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

- [kod düzenleyicisinin özellikleri (Windows Visual Studio)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [anahat oluşturma (Windows Visual Studio)](/visualstudio/ide/outlining)
