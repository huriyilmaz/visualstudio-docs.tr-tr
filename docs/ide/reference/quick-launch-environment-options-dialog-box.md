---
title: Hızlı Başlatma, Ortam, Seçenekler İletişim Kutusu
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
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 706b54e3ee925b1833f860da2f84c8d28af9617e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565675"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Hızlı Başlatma, Ortam, Seçenekler İletişim Kutusu

Seçenekler, şablonlar, menüler gibi IDE varlıkları için eylemleri hızlı bir şekilde aramak ve yürütmek için **Hızlı Başlatma'yı** kullanabilirsiniz. Kod ve sembolleri aramak için **Hızlı Başlatma'yı** kullanamazsınız. **Hızlı Başlat** arama kutusu menü çubuğunun sağ üst köşesinde yer alır ve **Ctrl**+**Q**tuşuna basarak erişilebilir. Arama dizenizi kutuya yazın. @içeren dizeleri aramak için '@@' kullanın.

**Visual Studio'yı** yüklediğinizde hızlı başlatma varsayılan olarak etkinleştirilir. Menü **çubuğunda, Araç** > **Seçenekleri'ni**seçerek **Hızlı Başlatma'yı** gösterebilir veya gizleyebilirsiniz. **Ortam** düğümlerini genişletin ve ardından **Hızlı Başlat'ı**seçin. **Hızlı Başlat'ı Etkinleştir** onay kutusunu seçin veya temizleyin. Ayrıca bu sayfada arama kategorilerini etkinleştirebilir veya devre dışı kullanabilirsiniz.

## <a name="category-list"></a>Kategori Listesi

Hızlı Başlatma arama sonuçları dört kategoride görünür: **Options**En Son **Kullanılanlar, Menüler,** Seçenekler ve **Belgeleri Aç**, kategorideki öğe sayısıyla birlikte. **Most Recently Used** Arama sonuçlarında kategoriye göre geçiş yapmak için, bir sonraki kategorideki tüm sonuçları göstermek için **Ctrl**+**Q** tuşlarını seçin. Son kategori görüntüledikten sonra **Ctrl**+**Q** size her kategoriden birkaç sonuç gösterir. Kategorilerde ters sırada gezinmek için **Ctrl**+**Shift**+**Q** tuşuna basın. Bir kategori altındaki tüm arama sonuçlarını görüntülemek için kategori adını seçin.

Aramanızı belirli kategorilerle sınırlamak için aşağıdaki kısayolları kullanabilirsiniz.

|Kategori|Kısayol|Kısayol Açıklaması|
|--------------|--------------| - |
|En son kullanılan|@mru<br /><br /> Örneğin, `@mru font`|**En Son Kullandığınız**öğelerden en fazla beşini görüntüler.|
|Menüler|@menu<br /><br /> Örneğin, `@menu project`|Aramayı menü öğeleriyle sınırlar.|
|Seçenekler|@opt<br /><br /> Örneğin, `@opt font`|Aramayı **Seçenekler** iletişim kutusundaki ayarlarla sınırlar.|
|Belgeler|@doc<br /><br /> Örneğin, `@doc program.cs`|Aramayı, arama ölçütleri için açık belgelerin adlarını ve yollarını dosyalamak üzere sınırlar, ancak dosyaların içindeki metni kendileri aramaz.|

> [!NOTE]
> **Seçenekler** iletişim kutusundaki **Genel** > **Klavye** sayfasındaki kısayol tuşlarını değiştirebilirsiniz.

## <a name="show-previous-results"></a>Önceki Sonuçları Göster

Varsayılan olarak, girdiğiniz arama terimi arama oturumları arasında kalıcı değildir. Bir terim ararsanız, imleci **Hızlı Başlatma** alanının dışına taşırsanız ve sonra geri dönerseniz arama dizesi temizlenir. Arama sonuçlarını korumak için **Seçenekler** iletişim kutusuna gidin, **Hızlı Başlat'ı**seçin ve Hızlı **Başlatma etkinleştirildiğinde önceki aramadan arama sonuçlarını göster'i seçin.** onay kutusunu işaretleyin. Bir sonraki arama yaptığınızda, Hızlı Başlatma alanından çıktığınızda ve geri döndüğünüzde, Hızlı Başlatma en son kullanılan arama terimini korur ve ayrıca arama sonuçlarını gösterir.
