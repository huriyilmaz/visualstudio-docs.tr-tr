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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565675"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Hızlı Başlatma, Ortam, Seçenekler İletişim Kutusu

Seçenekler, şablonlar, menüler gibi IDE varlıkları için eylemleri hızlıca aramak ve yürütmek üzere **Hızlı Başlat** ' ı kullanabilirsiniz. Kodu ve sembolleri aramak için **Hızlı başlatma** kullanamazsınız. **Hızlı Başlat** arama kutusu, menü çubuğunun sağ üst köşesinde bulunur ve **CTRL** + **Q**tuşlarına basarak erişilebilir. Arama dizenizi kutuya yazın. @ İçeren dizeleri aramak için ' @ @ ' kullanın.

**Hızlı başlatma** , Visual Studio 'yu yüklediğinizde varsayılan olarak etkindir. Menü çubuğunda, **Araçlar**Seçenekler ' i seçerek **hızlı başlatmayı** gösterebilir veya gizleyebilirsiniz  >  **Options**. **Ortamlar** düğümünü genişletin ve **Hızlı Başlat**' ı seçin. **Hızlı başlatmayı etkinleştir** onay kutusunu seçin veya temizleyin. Ayrıca, bu sayfada arama kategorilerini etkinleştirebilir veya devre dışı bırakabilirsiniz.

## <a name="category-list"></a>Kategori listesi

Hızlı başlatma arama sonuçları dört kategoride görünür: **en son kullanılanlar**, **menüler**, **Seçenekler**ve **Açık belgeler**, kategori içindeki öğe sayısı ile birlikte. Arama sonuçlarıyla kategoriye göre geçiş yapmak için, **Ctrl** + sonraki kategorinin tüm sonuçlarını göstermek üzere CTRL**Q** tuşlarını seçin. Son kategori görüntülendikten sonra, **CTRL** + **Q** her kategoriden birkaç sonuç gösterir. **Ctrl** + **Shift** + Kategoriler arasında ters sırada gezinmek için CTRL SHIFT**Q** tuşuna basın. Bir kategori altındaki tüm arama sonuçlarını görüntülemek için kategori adını seçin.

Aramanızı belirli kategorilere sınırlamak için aşağıdaki kısayolları kullanabilirsiniz.

|Kategori|Kısayol|Kısayol açıklaması|
|--------------|--------------| - |
|En son kullanılan|@mru<br /><br /> Örneğin, `@mru font`|**En son kullandığınız**öğelerin en fazla beş sayısını görüntüler.|
|Menüler|@menu<br /><br /> Örneğin, `@menu project`|Aramayı menü öğeleriyle sınırlandırır.|
|Seçenekler|@opt<br /><br /> Örneğin, `@opt font`|**Seçenekler** iletişim kutusundaki arama ayarlarını sınırlandırır.|
|Belgeler|@doc<br /><br /> Örneğin, `@doc program.cs`|Arama kriterlerine yönelik açık belgelerin dosya adlarıyla ve yollarına yönelik aramayı kısıtlar, ancak dosyaların içinde metinde arama yapmaz.|

> [!NOTE]
> **General**  >  **Seçenekler** iletişim kutusundaki Genel**klavye** sayfasında kısayol tuşlarını değiştirebilirsiniz.

## <a name="show-previous-results"></a>Önceki sonuçları göster

Varsayılan olarak, girdiğiniz arama terimi arama oturumları arasında kalıcı olmaz. Arama dizesi bir terim arıyorsanız, imleci **Hızlı başlatma** alanının dışına taşıyın ve ardından geri dönün. Arama sonuçlarını sürdürmek için **Seçenekler** iletişim kutusuna gidin, **Hızlı Başlat**' ı seçin ve ardından **Hızlı başlatma etkinleştirildiğinde önceki aramadan arama sonuçlarını göster** ' i seçin. onay kutusunu işaretleyin. Bir sonraki sefer bir arama yaptığınızda hızlı başlatma alanını bırakın ve geri dönüp, hızlı başlatma en son kullanılan arama terimini korur ve ayrıca arama sonuçlarını gösterir.
