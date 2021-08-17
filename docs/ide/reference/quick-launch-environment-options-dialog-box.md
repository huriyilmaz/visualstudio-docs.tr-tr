---
title: Hızlı Başlatma, Ortam, Seçenekler İletişim Kutusu
description: Seçenekler, şablonlar ve Hızlı Başlat IDE varlıkları için hızlı bir şekilde arama ve yürütme eylemleri yürütmek için Ortam bölümündeki Hızlı Başlat sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 79b5dc9863be3e9f0bdc0fadbd292948d8ad352f0ff6b5435d28fc07b7ad1fb9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400172"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Hızlı Başlatma, Ortam, Seçenekler İletişim Kutusu

Seçenekler, **şablonlar Hızlı Başlat** menüler gibi IDE varlıkları için hızlı bir şekilde arama ve yürütme eylemlerini yürütmek üzere Hızlı Başlat'i kullanabilirsiniz. Kod ve sembolleri **Hızlı Başlat** için bu özelliği kullanaabilirsiniz. Hızlı Başlat  arama kutusu menü çubuğunun sağ üst köşesinde bulunur ve **Ctrl** Q tuşlarına basarak + **erişilebilir.** Kutuya arama dizenizi yazın. @ içeren dizeleri aramak için '@@' kullanın.

**Hızlı Başlat** yüklemesi varsayılan olarak etkin Visual Studio. Menü çubuğunda Araçlar Seçenekler'i seçerek **Hızlı Başlat** veya   >  **gizleyebilirsiniz.** Ortamlar **düğümünü** genişletin ve **Hızlı Başlat.** Etkinleştir onay kutusunu **seçin Hızlı Başlat** temizleyin. Ayrıca bu sayfada arama kategorilerini etkinleştirebilirsiniz veya devre dışı abilirsiniz.

## <a name="category-list"></a>Kategori Listesi

Hızlı Başlat sonuçları dört kategoride görünür: En Son **Kullanılan** **,** **Menüler,** Seçenekler ve Belgeleri Aç **ile** kategorideki öğe sayısı. Arama sonuçlarında kategoriye göre çapraz geçiş yapmak için **Ctrl** + **Q** tuşlarını seçerek sonraki kategoriye ait tüm sonuçları görüntüleyin. Son kategori **görüntülendiğinde, Ctrl** + **Q** ile her kategoriye ait birkaç sonuç görüntülenir. Kategoriler arasında ters sırada gezinmek için **Ctrl** + **Shift** + **Q** tuşlarına basın. Bir kategori altındaki tüm arama sonuçlarını görüntülemek için kategori adını seçin.

Aramanızı belirli kategorilerle sınırlamak için aşağıdaki kısayolları kullanabilirsiniz.

|Kategori|Kısayol|Kısayol Açıklaması|
|--------------|--------------| - |
|En son kullanılan|@mru<br /><br /> Örneğin, `@mru font`|En Son Kullanılan öğelerden en fazla **beşi görüntüler.**|
|Menüler|@menu<br /><br /> Örneğin, `@menu project`|Arama ile menü öğelerini sınırlar.|
|Seçenekler|@opt<br /><br /> Örneğin, `@opt font`|Arama, Seçenekler iletişim kutusundaki **ayarlarla** sınırlar.|
|Belgeler|@doc<br /><br /> Örneğin, `@doc program.cs`|Arama ölçütlerini açık belgelerin dosya adları ve yolları ile sınırlar, ancak dosyaların içindeki metni aramaz.|

> [!NOTE]
> Kısayol tuşlarını Seçenekler iletişim kutusundaki **Genel**  >  **Klavye** sayfasında **değiştirebilirsiniz.**

## <a name="show-previous-results"></a>Önceki Sonuçları Göster

Varsayılan olarak, girersiniz arama terimi arama oturumları arasında kalıcı değildir. Bir terim için arama yaptıysanız arama dizesi temizlir, imleci Hızlı Başlat **dışına** gider ve sonra geri dönersiniz. Arama sonuçlarını korumak için Seçenekler  iletişim kutusuna gidin, Hızlı Başlat'ı seçin ve sonra etkin olduğunda önceki **aramadan arama sonuçlarını Hızlı Başlat seçin.** onay kutusunu işaretleyin. Bir sonraki aramada Hızlı Başlat bırakın ve geri Hızlı Başlat arama terimini korur ve arama sonuçlarını gösterir.
