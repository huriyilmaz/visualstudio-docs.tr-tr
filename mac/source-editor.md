---
title: Kaynak Düzenleyicisi
description: Mac için Visual Studio'daki kaynak düzenleyiciyi kullanma
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: d1ea74b4893032252d04ebe5fe5e65ca1eedaeeb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68493279"
---
# <a name="source-editor"></a>Kaynak editör

Güvenilir bir kaynak düzenleyici, kodları kısa ve verimli bir şekilde yazmak için gereklidir. Mac için Visual Studio, IDE ile etkileşimlerinizin merkezinde yer alan gelişmiş bir kaynak editör sağlar. Kaynak düzenleyici, işinizi kolaylıkla yapacağınız ve yapmanız gereken özellikler sağlar: Temellerden, sözdizimi vurgulama, kod parçacıkları ve kod katlama gibi temel özelliklerden, roslyn derleyicisi tümleştirmesinin yararlarına, örneğin tamamen işlevsel IntelliSense kodu Tamamlama.

Visual Studio for Mac'teki kaynak editör, hata ayıklama, yeniden düzenleme ve sürüm kontrol tümleştirmesi gibi IDE'deki diğer tüm işlevlerle sorunsuz bir deneyim sağlar.

Bu makalede, kaynak düzenleyicinin bazı temel özellikleri tanıtılır ve Mac için Visual Studio'yu mümkün olduğunca üretken olması için nasıl kullanabileceğinizi araştırır.

## <a name="the-source-editor-experience"></a>Kaynak editör deneyimi

Kod boyunca verimli bir şekilde görüntülemek ve hareket etmek geliştirme iş akışının ayrılmaz bir parçasıdır. Kodu görüntülemeye ve korumaya tam olarak nasıl karar verebilirsiniz, geliştiriciler ve genellikle projeler arasında değişen kişisel bir karardır.

Mac için Visual Studio, platformlar arası geliştirmeyi olabildiğince erişilebilir ve olabildiğince kullanışlı hale getirmek için birçok güçlü özellik sunar. Aşağıdaki bölümlerde bazı önemli noktalar açıklanır.

## <a name="code-folding"></a>Kod katlama

Kod katlama, geliştiricilerin yönergeleri, ortak kod kodu ve açıklamaları ve #region ifadeleri kullanma gibi kodun tüm bölümlerini göstermesine veya gizlemesine izin vererek büyük kaynak kod dosyalarını yönetmeyi kolaylaştırır. Kod katlama Mac için Visual Studio varsayılan olarak kapatılır

Kod katlama açmak için Visual **Studio > Tercihleri > Metin Editörü > Genel > Kod Katlama**gidin:

![Kod Katlama Seçenekleri](media/source-neweditor-image1.png)

Bu menü, kod yerine adlandırılmış bir ipucu nu görüntüleyerek varsayılan olarak #regions ve yorumları katlamak seçeneğini de içerir.

Bölümleri göstermek veya gizlemek için satır numarasının yanındaki açıklama widgetını kullanın:

![Bölümleri kodda gösterme veya gizleme](media/source-neweditor-image2.png)

Ayrıca **Görünüm > Katlama > Toggle Fold / Tüm Kıvrımlar** menü öğesini değiştirerek kıvrımları gösterme ve gizleme arasında geçiş yapabilirsiniz:

![Katlanır Menü öğesi](media/source-editor-image19.png)

Bu menü öğesi, kod katlamayı etkinleştirmek veya devre dışı kakmak için de kullanılabilir.

## <a name="word-wrap"></a>Sözcük kaydırma

Sözcük kaydırma, uzun kod satırları üzerinde çalışırken veya sınırlı görüş alanıyla alanı yönetmeniz de size yardımcı olabilir. Word kaydırma, görünümünüzü gizleyebilen veya kaynak görünümünüzün genişliğini azaltabilecek bölmeleri açarken bile kod görünümünüzde kaynak dosyanızın tam içeriğini içerdiğinden de emin olabilir. 

Word kaydırma varsayılan olarak devre dışı bırakılır, ancak Mac için Visual Studio'daki **Tercihler** aracılığıyla etkinleştirilebilir. 

Word wrap etkinleştirmek için, **Visual Studio > Tercihleri > Metin Editörü > Yeni Editör > Word Wrap**gidin:

![Sözcük Kaydırma Seçenekleri](media/source-neweditor-wordwrap1.png)

Sözcük kaydırma etkinleştirildiğinde, kaynak düzenleyici görünümünüzgenişliğini aşan satırlar, kaynak dosyanızdaki bir sonraki satıra otomatik olarak kaydırılacaktır. Ayrıca, sarılmış çizgilerin yanında görünür bir glifleri görüntüleyecek bir seçeneği de etkinleştirebilirsiniz. Bu, otomatik olarak sarılmış çizgilerle el ile sardığınız satırlar arasında ayrım yapmak için izin verir.

![Sözcük Kaydırma Etkinleştirilmiş Sarılmış Metin](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Cetvel

Sütun cetveli, özellikle satır uzunluğu yönergeleri olan bir takım üzerinde çalışırken satır uzunluklarını belirlemek için yararlıdır. Sütun cetveli Visual **Studio > Tercihleri > Metin Düzenleyicisi > İşaretçileri ve Cetvelleri'ne** yönlendirilerek ve aşağıdaki resimde gösterildiği gibi **Sütun cetvelini göster'i**seçerek (veya seçerek) seçilerek açılabilir veya kapatılabilir:

!["Sütun cetvelini göster" vurgulu tercihler iletişim kutusu](media/source-editor-image5.png)

 Bu, kaynak düzenleyicide dikey açık gri bir çizgi olarak görüntülenir.

## <a name="highlight-identifier-references"></a>Tanımlayıcı başvurularını vurgulama

"Vurgu tanımlayıcı başvuruları" seçeneği etkinleştirildiğinde, kaynak koddaki herhangi bir simgeyi seçebilirsiniz ve kaynak düzenleyici bu dosyadaki diğer tüm başvurular için görsel bir kılavuz sağlar. Bu seçeneği açmak için **Visual Studio > Tercihleri > Metin Düzenleyicisi > İşaretçileri ve Cetvelleri'ne** gidin ve aşağıdaki resimde gösterildiği gibi _Vurgu tanımlayıcı referanslarını_seçin:

!["Vurgutanımlayıcı referansları" vurgulanan tercihler iletişim kutusu](media/source-editor-image6.png)

Vurgunun rengi, bir şeyin atandığını veya başvurulmakta olduğunu belirtmek için de yararlıdır. Bir şey atanmışsa, kırmızı ile vurgulanır; başvurulmuşsa, mavi ile vurgulanır:

![vurgunun rengini gösteren örnek](media/source-editor-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri (Windows'da Visual Studio)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Anahat Oluşturma (Windows'da Visual Studio)](/visualstudio/ide/outlining)
