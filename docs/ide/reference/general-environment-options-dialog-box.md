---
title: Genel, Ortam, Seçenekler İletişim Kutusu
description: IDE için renk temalarını, durum çubuğu ayarlarını, dosya uzantısı ilişkilendirmelerini ve daha fazlasını değiştirmek için Ortam bölümündeki Genel sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/29/2021
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 19c96e580a55c6b6a5deaf307fbe9e0653c7b0da
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133256977"
---
# <a name="options-dialog-box-environment--general"></a>Seçenekler iletişim kutusu: Ortam \> Genel

Renk temalarını, durum çubuğu ayarlarını ve dosya uzantısı ilişkilendirmelerini, tümleşik geliştirme ortamı (IDE) için diğer seçenekleri değiştirmek için bu sayfayı kullanın. Seçenekler iletişim kutusuna **Araçlar menüsünü,** Seçenekler'i ve Ortam  klasörünü ve ardından Genel sayfasını seçerek  **erişebilirsiniz.**

## <a name="visual-experience"></a>Görsel Deneyim

**Renk Teması**

IDE **için** **Mavi, Açık,** **Koyu** veya Mavi (Ek Karşıtlık) renk temasını seçin. 

::: moniker range="vs-2022"

Ayrıca Sistem ayarını kullan'ı seçerek Windows **temayı da kullanabilirsiniz.**

::: moniker-end

Önceden tanımlanmış ek temaları yükleyebilir ve şu anda kullanmakta olduğunuz sürüm için **Visual Studio Tema** Tasarımcısı'Visual Studio indirip yükleyerek özel temalar oluşturabilirsiniz:

- [Visual Studio 2022 için Renk Teması Tasarımcısı](https://marketplace.visualstudio.com/items?itemName=idex.colorthemedesigner2022)
- [Visual Studio 2019 için Renk Teması Tasarımcısı.](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)
- [Visual Studio 2017 için Renk Teması Düzenleyicisi](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)

Bu aracı yükledikten sonra, Renk Teması liste kutusunda **ek renk temaları** görünür.

::: moniker range="vs-2022"

> [!NOTE]
> Daha fazla tema seçmek ister misiniz? Visual Studio Market'te çok çeşitli [**özel temalara göz atabilirsiniz.**](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Themes&sortBy=Installs) VS Code tabanlı yeni Visual Studio 2022 özel temalarının örneklerini görmek için Yeni Visual Studio temaları koleksiyonuna tanıtma blog [**gönderisi'ne**](https://devblogs.microsoft.com/visualstudio/custom-themes/) göz atabilirsiniz.

::: moniker-end

**Menü çubuğuna başlık durumu stili uygulama**

Menüler varsayılan olarak başlık büyük/harf stili kullanır. Bunun yerine tüm büyük harf stillerini kullanmak için bu seçeneğin işaretini kaldırın.

::: moniker range=">=vs-2019"

**Farklı piksel yoğunluğuna sahip ekranlar için işlemeyi iyileştirme (yeniden başlatma gerektirir)**

Bu seçenek, monitör başına nokta/inç (DPI) farkındalığını (veya PMA) etkinleştirir veya *devre dışı bıraktır.* PMA etkinleştirildiğinde, Visual Studio monitörler arasında da dahil olmak üzere tüm izleyicilerde görünen ölçek faktörü ve DPI yapılandırmasında PMA kullanıcı arabirimi görünür. PMA'yı etkinleştirmek için Nisan 2018 Güncelleştirmesi Windows 10 veya sonraki bir .NET Framework 4.8 veya sonraki bir güncelleştirmeye ihtiyacınız var. (Bu iki önkoşul karşılanmazsa bu seçenek gri görünür.)

> [!TIP]
> - Windows 10 bulanık olmayan uygulamaları **düzeltmeye Windows Let Windows (İzin ver)** ayarı vardır. Farklı piksel Windows **ekranlar** için işlemeyi en iyi duruma getirme seçeneğini işaretli hale getirme seçeneğiniz varsa, bu Windows ayarının açması önemsiz **bir etkiye** neden olur.
> - Windows 10 Program Uyumluluğu Sorun **Gidericisi de içerir.** Sorun gidericiyi kullanarak uygulamanın görünümünü Visual Studio önerilmez.

::: moniker-end

**Görsel deneyimi istemci performansına göre otomatik olarak ayarlama**

Ayarları görsel Visual Studio otomatik olarak ayar mı yoksa ayarlamayı açıkça ayar mı ayarlaycazı belirtir. Bu ayarlama, renklerin gradyanlardan düz renklere görüntülenmesini değiştirebilir veya menülerde veya açılır pencerelerde animasyon kullanımını kısıtlar.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 bulanık olmayan uygulamaları **düzeltmeye Windows Let Windows (İzin ver)** ayarı vardır. Bu **ayarın,** izleyiciniz üzerinde Visual Studio görünürse bu ayarın kullanılması önerilir. Ekran netliğini önemli [ölçüde artıran Visual Studio 2019](https://visualstudio.microsoft.com/downloads)sürümüne yükseltmeyi göz önünde bulundurabilirsiniz. Bu, monitör başına nokta/inç farkında olan bir uygulamadır.

::: moniker-end

**Zengin istemci deneyimini etkinleştirme**

Gradyanlar ve animasyonlar dahil olmak Visual Studio tam görsel deneyimi sağlar. Uzak Masaüstü bağlantıları veya eski grafik bağdaştırıcıları kullanılırken bu seçeneğin temizlenebilirsiniz çünkü bu özellikler bu durumlarda düşük performansa sahip olabilir. Bu seçenek yalnızca Görsel deneyimi istemciye göre **otomatik olarak ayarla seçeneğini temizleyseniz** kullanılabilir.

**Varsa donanım grafik hızlandırmasını kullanma**

Varsa yazılım hızlandırma yerine donanım grafik hızlandırmasını kullanır.

## <a name="other"></a>Diğer

**Pencere menüsünde gösterilen öğeler**

Pencere menüsünün Windows pencere sayısını **özeller.** 1 ile 24 arasında bir sayı girin. Varsayılan değer 10'dur.

**Son kullanılan listelerde gösterilen öğeler**

Dosya menüsünde en son kullanılan projelerin ve dosyaların **sayısını** özeller. 1 ile 24 arasında bir sayı girin. Varsayılan değer 10'dur. Bu, son kullanılan projeleri ve dosyaları almak için kolay bir yol sağlar.

**Durum çubuğunu göster**

Durum çubuğunu görüntüler. Durum çubuğu IDE penceresinin en altında bulunur ve devam eden işlemlerin ilerleme durumuyla ilgili bilgileri görüntüler.

**Kapat düğmesi yalnızca etkin araç penceresini etkiler**

Kapat düğmesine **tıkıldığında,** yerleştirme kümesinde tüm araç pencerelerinin değil, yalnızca odağı olan araç penceresinin kapatılacak olduğunu belirtir. Varsayılan olarak, bu seçenek seçilidir.

**Otomatik Gizle düğmesi yalnızca etkin araç penceresini etkiler**

Otomatik Gizle düğmesine **tıkıldığında,** yerleştirme kümesinde tüm araç pencerelerinin değil, yalnızca odağı olan araç penceresinin otomatik olarak gizlenir. Varsayılan olarak, bu seçenek seçili değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
