---
title: Kod bölgelerini daraltma ve genişletme
description: Genişletme ve daraltma komutlarını kullanarak Visual Studio ana hat modunda nasıl çalışkullanabileceğinizi öğrenin
ms.custom: SEO-VS-2020
ms.date: 10/15/2020
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8fdd0a67bb561f3b339ad7d8f6743c51182fa74ab9fd33dbd6cb39a6bafcc4a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412835"
---
# <a name="outlining"></a>Anahat Oluşturma

Bir kod bölgesini daraltarak bir ek işareti () altında görünmesi için bazı kodu görünümden gizlemeyi seçebilirsiniz **+** . Daraltılmış bir bölgeyi, artı işaretine tıklayarak genişletebilirsiniz. Klavye kullanıcısı kullanıyorsanız,  +  + daraltmak ve genişletmek için CTRL m **m** 'yi seçebilirsiniz. Ayrıca, yalnızca kodun solunda görüntülenen ana hat kenar boşluğunda yer alan bölgedeki herhangi bir satırı çift tıklayarak bir anahat bölgesini daraltabilirsiniz. Daraltılan bölgenin üzerine geldiğinizde, Daraltılan bir bölgenin içeriğini araç ipucu olarak görebilirsiniz.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Ana hat kenar boşluğundaki bölgeler, fare ile kenar boşluğunun üzerine geldiğinizde de vurgulanır. Varsayılan vurgulama rengi bazı renk yapılandırmalarında soluk görünebilir. Bunu, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **yazı tiplerinde ve renkler**  >  **Daraltılabilir bölgesinde** değiştirebilirsiniz.

Anahatları belirlenmiş kodda çalışırken, üzerinde çalışmak istediğiniz bölümleri genişletebilir, işiniz bittiğinde bunları daraltabilir ve sonra diğer bölümlere geçebilirsiniz. Ana hattını görüntülenmesini istemediğiniz zaman, temel kodunuzla ilgili kodu etkilemeden anahat bilgilerini kaldırmak için Seviyelendirmeyi **Durdur** komutunu kullanabilirsiniz.

**Düzenle** menüsündeki **geri al** ve **Yinele** komutları bu eylemleri etkiler. **Kopyala**, **Kes**, **Yapıştır** ve sürükle bırak işlemleri, ana hat bilgilerini tutar, ancak daraltılabilir bölgenin durumunu içermez. Örneğin, Daraltılan bir bölgeyi kopyaladığınızda, **Yapıştır** işlemi kopyalanmış metni genişletilmiş bölge olarak yapıştırır.

> [!CAUTION]
> Anahatları belirlenmiş bir bölgeyi değiştirdiğinizde, ana hat kaybolmuş olabilir. Örneğin, silme veya **bulma ve değiştirme** işlemleri bölgenin sonunu silebilir.

Aşağıdaki komutlar, ana   >  **hat** Düzenle alt menüsünde bulunabilir.

|Ad|Açıklama|
|-|-|
|Seçimi Gizle|(**CTRL** + **M**, **CTRL** + **H**)-bir blok gibi, normalde ana hat için kullanılamayacak seçili kod bloğunu daraltır `if` . Özel bölgeyi kaldırmak için, **geçerli gizlemeyi durdur** (veya **CTRL** + **M**, **CTRL** + **U**) seçeneğini kullanın. Visual Basic ' de kullanılamaz.|
|Anahat genişletmeyi değiştirme| (**CTRL** + **A**, **CTRL** + **ı**)-imleç, iç içe daraltılmış bir bölümde yer aldığı zaman, en içteki ana hat bölümünün geçerli gizli veya genişletilmiş durumunu tersine çevirir.|
|Tüm Anahatlamayı aç|(**CTRL** + **M**, **CTRL** + **L**)-tüm bölgeleri aynı daraltılmış veya genişletilmiş duruma ayarlar. Bazı bölgeler genişletilir ve bazıları daraltıldı, daraltılan bölgeler genişletilir.|
|Anahat oluşturmayı durdur|(**CTRL** + **M**, **CTRL** + **P**)-tüm belgenin tüm anahat bilgilerini kaldırır.|
|Geçerli gizlemeyi durdur|(**CTRL** + **M**, **CTRL** + **U**)-Şu anda seçili olan Kullanıcı tanımlı bölgenin ana hat bilgilerini kaldırır. Visual Basic ' de kullanılamaz.|
|Tanımlara Daralt|(**CTRL** + **M**, **CTRL** + **O**)-tüm türlerin üyelerini daraltır.|
|Engellemeyi daralt:\<logical boundary>|C++ İşlevde ekleme noktasını içeren bir bölgeyi daraltır. Örneğin, ekleme noktası bir döngü içinde yer alıyorsa, döngü gizlenir.|
|İçindeki hepsini daralt: \<logical structures>|C++ İşlev içindeki tüm yapıları daraltır.|

genişletmek veya daraltmak istediğiniz metin bölgelerini tanımlamak için Visual Studio SDK 'sını de kullanabilirsiniz. Bkz. [Izlenecek yol: Ana hat](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)
