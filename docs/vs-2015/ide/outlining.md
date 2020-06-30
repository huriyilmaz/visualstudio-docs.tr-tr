---
title: Ana hat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 907d075f597799edd582c9f2bae693eac92c0b2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544969"
---
# <a name="outlining"></a>Anahat Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kod bölgesini daraltarak bir, bir artı işareti (+) altında görünmesi için, bazı kodları görünümden gizlemeyi seçebilirsiniz. Daraltılmış bir bölgeyi, artı işaretine tıklayarak genişletebilirsiniz. (Ya da bir bölgeyi daraltmak için CTRL + e + e tuşlarına basabilir, sonra da bunu yeniden genişletmek için CTRL + e + e tuşlarına basabilirsiniz.) Ayrıca, yalnızca kodun solunda görüntülenen ana hat kenar boşluğunda yer alan bölgedeki herhangi bir satırı çift tıklayarak bir anahat bölgesini daraltabilirsiniz. Daraltılan bölgenin üzerine geldiğinizde, Daraltılan bir bölgenin içeriğini araç ipucu olarak görebilirsiniz.

 Ana hat kenar boşluğundaki bölgeler, fare ile kenar boşluğunun üzerine geldiğinizde de vurgulanır. Varsayılan vurgulama rengi bazı renk yapılandırmalarında soluk görünebilir. Bunu, **Araçlar/Seçenekler/ortam/yazı tipleri ve renkler/daraltılabilir bölgede**değiştirebilirsiniz.

 Anahatları belirlenmiş kodda çalışırken, üzerinde çalışmak istediğiniz bölümleri genişletebilir, işiniz bittiğinde bunları daraltabilir ve sonra diğer bölümlere geçebilirsiniz. Ana hattını görüntülenmesini istemediğiniz zaman, temel kodunuzla ilgili kodu etkilemeden anahat bilgilerini kaldırmak için Seviyelendirmeyi **Durdur** komutunu kullanabilirsiniz.

 **Düzenle** menüsündeki **geri al** ve **Yinele** komutları bu eylemleri etkiler. **Kopyala**, **Kes**, **Yapıştır**ve sürükle bırak işlemleri, ana hat bilgilerini tutar, ancak daraltılabilir bölgenin durumunu içermez. Örneğin, Daraltılan bir bölgeyi kopyaladığınızda, **Yapıştır** işlemi kopyalanmış metni genişletilmiş bölge olarak yapıştırır.

> [!CAUTION]
> Anahatları belirlenmiş bir bölgeyi değiştirdiğinizde, ana hat kaybolmuş olabilir. Örneğin, silme veya bulma ve değiştirme işlemleri bölgenin sonunu silebilir.

 Aşağıdaki komutlar **düzenleme/anahat** alt menüsünde bulunabilir.

|Komut|Description|
|-|-|
|Seçimi Gizle|(CTRL + M, CTRL + H)-ana hat için, örneğin bir blok için kullanılamayacak seçili bir kod bloğunu daraltır `if` . Özel bölgeyi kaldırmak için, **geçerli gizlemeyi durdur** (veya CTRL + M, CTRL + U) kullanın. Visual Basic ' de kullanılamaz.|
|Anahat genişletmeyi değiştirme|-İmleç, iç içe daraltılmış bir bölümde yer aldığı zaman, en içteki ana hat bölümünün geçerli gizli veya genişletilmiş durumunu tersine çevirir.|
|Tüm Anahatlamayı aç|(CTRL + M, CTRL + L)-tüm bölgeleri aynı daraltılmış veya genişletilmiş duruma ayarlar. Bazı bölgeler genişletilir ve bazıları daraltıldı, daraltılan bölgeler genişletilir.|
|Anahat oluşturmayı durdur|(CTRL + M, CTRL + P)-tüm belgeye ilişkin tüm ana hat bilgilerini kaldırır.|
|Geçerli gizlemeyi durdur|(CTRL + M, CTRL + U)-Şu anda seçili olan Kullanıcı tanımlı bölgenin ana hat bilgilerini kaldırır. Visual Basic ' de kullanılamaz.|
|Tanımlara Daralt|(CTRL + M, CTRL + O)-tüm türlerin üyelerini daraltır.|
|Engellemeyi daralt:\<logical boundary>|(Visual C++) İşlevde ekleme noktasını içeren bir bölgeyi daraltır. Örneğin, ekleme noktası bir döngü içinde yer alıyorsa, döngü gizlenir.|
|İçindeki hepsini daralt:\<logical structures>|(Visual C++) İşlev içindeki tüm yapıları daraltır.|

 Genişletmek veya daraltmak istediğiniz metin bölgelerini tanımlamak için Visual Studio SDK 'sını de kullanabilirsiniz. Bkz. [Izlenecek yol: Ana hat](../extensibility/walkthrough-outlining.md).
