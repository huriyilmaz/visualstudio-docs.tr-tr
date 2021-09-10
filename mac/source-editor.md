---
title: Kaynak Düzenleyicisi
description: Kaynak düzenleyicisini Mac için Visual Studio
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: c4a22ec0765c39a8bec83f9e2acff7b22b706890
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964786"
---
# <a name="source-editor"></a>Kaynak düzenleyicisi

Güvenilir bir kaynak düzenleyicisi, kısa ve verimli bir şekilde kod yazmak için gereklidir. Mac için Visual Studio, IDE ile etkileşimlerinin merkezinde yer alan gelişmiş bir kaynak düzenleyicisi sağlar. Kaynak düzenleyici, beklediğiniz ve çalışmanızı kolayca tamamlamanız gereken özellikler sağlar: Söz dizimi vurgulama, kod parçacıkları ve kod katlama gibi temel bilgilerden, Roslyn derleyici tümleştirmesi avantajlarına (tam işlevsel IntelliSense kodu tamamlama gibi) kadar çeşitli özellikler sunar.

Mac için Visual Studio düzenleyicisi, IDE'de hata ayıklama, yeniden düzenleme ve sürüm denetimi tümleştirmesi gibi diğer tüm işlevlerle sorunsuz bir deneyim sağlar.

Bu makalede, kaynak düzenleyicinin temel özelliklerinden bazıları tanıt ve mümkün olduğunca üretken olmak için Mac için Visual Studio nasıl kullanabileceğiniz keşfedildi.

## <a name="the-source-editor-experience"></a>Kaynak düzenleyici deneyimi

Kod genelinde verimli bir şekilde görüntüleme ve taşıma, geliştirme iş akışının ayrılmaz bir parçasıdır. Kodu görüntülemek ve korumak için tam olarak nasıl karar vermeniz, geliştiriciler arasında ve genellikle projeler arasında değişiklik olan kişisel bir karardır.

Mac için Visual Studio platformlar arası geliştirmeyi mümkün olduğunca erişilebilir ve kullanışlı hale getirin. Aşağıdaki bölümlerde bazı önemli özellikler açıklanmaktadır.

## <a name="code-folding"></a>Kod katlama

Kod katlama, geliştiricilerin yönergeleri, ortak kod ve açıklamaları kullanma ve deyimleri kullanma gibi kodun tüm bölümlerini göstermelerine veya gizlemelerine olanak sağlayarak büyük kaynak kod dosyalarını #region kolaylaştırır. Kod katlama, kodda varsayılan olarak Mac için Visual Studio

Kod katlamayı açmak için Visual Studio > **Tercihler > Metin Düzenleyici > Genel >'na gidin:**

![Kod Katlama Seçenekleri](media/source-neweditor-image1.png)

Bu menü ayrıca kod yerine adlandırılmış #regions ve açıklamalarını varsayılan olarak katlama seçeneğini de içerir.

Bölümleri göstermek veya gizlemek için satır numarasının yanındaki açıklama pencere öğesi kullanın:

![Kodda bölümleri gösterme veya gizleme](media/source-neweditor-image2.png)

Ayrıca, Görünüm ve Katlama > Katlama/ Tüm **Katları** Aç/Kapat menü öğesini > kullanarak katları gösterme ve gizleme arasında geçiş yapabilirsiniz:

![Katlama Menü öğesi](media/source-editor-image19.png)

Bu menü öğesi, kod katlama özelliğini etkinleştirmek veya devre dışı bırakmak için de kullanılabilir.

## <a name="word-wrap"></a>Sözcük kaydırma

Sözcük kaydırma, uzun kod satırlarında veya sınırlı görünüm alanıyla çalışırken alanı yönetme konusunda size yardımcı olabilir. Sözcük kaydırma, görünümlerinizi gizleyen veya kaynak görünüm genişliğini azaltan bölmeleri alarken bile kod görünümünüzde kaynak dosyanın tam içeriğinin olmasını da sağlar. 

Sözcük kaydırma varsayılan olarak devre dışıdır, ancak Mac için Visual Studio.  

Sözcük kaydırmayı etkinleştirmek için, Visual Studio > **Tercihler'e > Düzenleyici'ye gidin > Kaydırma:**

![Sözcük Kaydırma Seçenekleri](media/source-neweditor-wordwrap1.png)

Sözcük kaydırma etkinleştirildiğinde, kaynak düzenleyici görünümünüz genişliğini aşan satırlar otomatik olarak kaynak dosyanız içindeki sonraki satıra kaydırılır. Sarmalanmış satırların yanında görünür bir glyph görüntüecek bir seçeneği de etkinleştirebilirsiniz. Bu, otomatik olarak sarmalanmış olan satırlar ile el ile sarmalanmış olan satırları ayırt edebilirsiniz.

![Sözcük Kaydırma EtkinKen Sarmalanmış Metin](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Cetvel

Sütun cetveli, özellikle de satır uzunluğu yönergelerine sahip bir ekip üzerinde çalışırken çizgi uzunluklarını belirlemek için kullanışlıdır. Sütun cetveli, aşağıdaki görüntüde gösterildiği gibi **Visual Studio >** Tercihleri > Metin Düzenleyici > İşaretçileri ve Cetveller'i seçerek (veya seçimi kaldırarak) Sütun cetvelini göster seçeneğine giderek açık veya kapalı olabilir: 

!["Sütun cetvelini göster" vurgulanmış Tercihler iletişim kutusu](media/source-editor-image5.png)

 Bu, kaynak düzenleyicide dikey açık gri çizgi olarak görüntülenir.

## <a name="highlight-identifier-references"></a>Tanımlayıcı başvurularını vurgulama

"Tanımlayıcı başvurularını vurgula" seçeneği etkinleştirildiğinde, kaynak kodda herhangi bir simgeyi seçebilirsiniz ve kaynak düzenleyici bu dosyada yer alan diğer tüm başvurulara görsel bir kılavuz sağlar. Bu seçeneği açmak için, Visual Studio > görüntüde **gösterildiği gibi > Düzenleyicisi'nde >** İşaretçiler ve Cetveller'i seçin ve Tanımlayıcı başvurularını vurgula'yı seçin:

!["Tanımlayıcı başvurularını vurgula" seçeneğinin vurgulanmış olduğu Tercihler iletişim kutusu](media/source-editor-image6.png)

Vurgulanan rengi, bir şeyin atandığı veya başvuruldığı vurgusu için de yararlıdır. Bir şey atanmışsa kırmızı renkle vurgulanır; Başvurulsa mavi renkle vurgulanır:

![vurgu rengini gösteren örnek](media/source-editor-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri (Visual Studio Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Outlining (Visual Studio Windows)](/visualstudio/ide/outlining)
