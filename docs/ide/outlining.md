---
title: Kod bölgelerini daraltma ve genişletme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 791663c04d1c1e79eebaed39d339d8d118ffeaae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748861"
---
# <a name="outlining"></a>Anahat Oluşturma

Bir kod bölgesini daraltarak bir kodu bir ve işareti ( **+** ) altında görünecek şekilde gizleyerek, bazı kodları görünümden gizlemeyi seçebilirsiniz. Daraltılmış bir bölgeyi, artı işaretine tıklayarak genişletebilirsiniz. Klavye kullanıcısı kullanıyorsanız, daraltmak ve genişletmek için **Ctrl** +**m** +**m** seçeneklerini belirleyebilirsiniz. Ayrıca, yalnızca kodun solunda görüntülenen ana hat kenar boşluğunda yer alan bölgedeki herhangi bir satırı çift tıklayarak bir anahat bölgesini daraltabilirsiniz. Daraltılan bölgenin üzerine geldiğinizde, Daraltılan bir bölgenin içeriğini araç ipucu olarak görebilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Ana hat kenar boşluğundaki bölgeler, fare ile kenar boşluğunun üzerine geldiğinizde de vurgulanır. Varsayılan vurgulama rengi bazı renk yapılandırmalarında soluk görünebilir. **Araç**  > **seçenekleri**  > **ortam**  > **yazı tipi ve renkler**  > **Daraltılabilir bölge**' de bunu değiştirebilirsiniz.

Anahatları belirlenmiş kodda çalışırken, üzerinde çalışmak istediğiniz bölümleri genişletebilir, işiniz bittiğinde bunları daraltabilir ve sonra diğer bölümlere geçebilirsiniz. Ana hattını görüntülenmesini istemediğiniz zaman, temel kodunuzla ilgili kodu etkilemeden anahat bilgilerini kaldırmak için Seviyelendirmeyi **Durdur** komutunu kullanabilirsiniz.

**Düzenle** menüsündeki **geri al** ve **Yinele** komutları bu eylemleri etkiler. **Kopyala**, **Kes**, **Yapıştır**ve sürükle bırak işlemleri, ana hat bilgilerini tutar, ancak daraltılabilir bölgenin durumunu içermez. Örneğin, Daraltılan bir bölgeyi kopyaladığınızda, **Yapıştır** işlemi kopyalanmış metni genişletilmiş bölge olarak yapıştırır.

> [!CAUTION]
> Anahatları belirlenmiş bir bölgeyi değiştirdiğinizde, ana hat kaybolmuş olabilir. Örneğin, silme veya bulma ve değiştirme işlemleri bölgenin sonunu silebilir.

Aşağıdaki**komutlar  >  ana** hattı **Düzenle** alt menüsünde bulunabilir.

|||
|-|-|
|Seçimi Gizle|(**Ctrl** +**M**, **CTRL** +**H**)-bir `if` bloğu gibi, normalde ana hat için kullanılamayacak seçili kod bloğunu daraltır. Özel bölgeyi kaldırmak için, **geçerli gizlemeyi durdur** (veya **CTRL** +**M**, **CTRL** +**U**) kullanın. Visual Basic ' de kullanılamaz.|
|Anahat genişletmeyi değiştirme|-İmleç, iç içe daraltılmış bir bölümde yer aldığı zaman, en içteki ana hat bölümünün geçerli gizli veya genişletilmiş durumunu tersine çevirir.|
|Tüm Anahatlamayı aç|(**Ctrl** +**m**, **CTRL** +**L**)-tüm bölgeleri aynı daraltılmış veya genişletilmiş duruma ayarlar. Bazı bölgeler genişletilir ve bazıları daraltıldı, daraltılan bölgeler genişletilir.|
|Anahat oluşturmayı durdur|(**Ctrl** +**M**, **CTRL** +**P**)-tüm belgeye ilişkin tüm ana hat bilgilerini kaldırır.|
|Geçerli gizlemeyi durdur|(**Ctrl** +**M**, **CTRL** +**U**)-Şu anda seçili olan Kullanıcı tanımlı bölgenin ana hat bilgilerini kaldırır. Visual Basic ' de kullanılamaz.|
|Tanımlara Daralt|(**Ctrl** +**M**, **CTRL** +**O**)-tüm türlerin üyelerini daraltır.|
|Engellemeyi daralt: \<logical sınır >|(C++) Ekleme noktasını içeren işlevdeki bir bölgeyi daraltır. Örneğin, ekleme noktası bir döngü içinde yer alıyorsa, döngü gizlenir.|
|Tüm içinde daralt: \<logical yapıları >|(C++), İşlev içindeki tüm yapıları daraltır.|

Genişletmek veya daraltmak istediğiniz metin bölgelerini tanımlamak için Visual Studio SDK 'sını de kullanabilirsiniz. Bkz. [Izlenecek yol: Ana hat](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)