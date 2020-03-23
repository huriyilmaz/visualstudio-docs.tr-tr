---
title: Genel, Ortam, Seçenekler İletişim Kutusu
ms.date: 07/26/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 973e08ca6555f7da7873d3068e2794b8d34e3640
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569445"
---
# <a name="options-dialog-box-environment--general"></a>Seçenekler iletişim kutusu: \> Çevre Genel

Tümleşik geliştirme ortamı (IDE) için diğer seçeneklerin yanı sıra renk temalarını, durum çubuğu ayarlarını ve dosya uzantısı ilişkilendirmelerini değiştirmek için bu sayfayı kullanın. **Araçlar** menüsünü açarak, **Seçenekler'i**seçerek, **Çevre** klasörünü açarak ve ardından **Genel** sayfayı seçerek **Seçenekler** iletişim kutusuna erişebilirsiniz. Bu sayfa listede görünmüyorsa, **Seçenekler** iletişim kutusundaki **tüm ayarları göster** onay kutusunu seçin.

## <a name="visual-experience"></a>Görsel Deneyim

**Renk Teması**

IDE için **Mavi,** **Açık,** **Koyu**veya **Mavi (Ekstra Kontrast)** renk temayı seçin.

[Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)Marketplace'ten **Visual Studio Color Tema Düzenleyicisini** indirip kurarak özel temalar oluşturabilir ve özel temalar oluşturabilirsiniz. Bu aracı yükledikten sonra Renk **Teması** listesi kutusunda ek renk temaları görünür.

**Başlık büyük/küçük harf stilini menü çubuğuna uygulama**

Menülerde varsayılan olarak başlık örneği stili kullanılır. Bunun yerine tüm büyük harf stilini kullanmak için bu seçeneğin işaretlerini kaldırın.

::: moniker range=">=vs-2019"

**Farklı piksel yoğunluklarına sahip ekranlar için oluşturmayı optimize edin (yeniden başlatmayı gerektirir)**

Bu seçenek, inç başına monitör başına noktalar (DPI) farkındalığı (veya *PMA)* sağlar veya devre dışı eder. PMA etkinleştirildiğinde, Visual Studio kullanıcı arabirimi, birden çok monitör de dahil olmak üzere tüm monitör ekran ölçeği faktöründe ve DPI yapılandırmasında net görünür. PMA'yı etkinleştirmek için Windows 10 Nisan 2018 Güncelleştirmesi veya sonrası ve .NET Framework 4.8 veya daha sonra olmanız gerekir. (Bu iki ön koşul karşılanmazsa bu seçenek soluk olarak görünür.)

> [!TIP]
> - Windows 10'da, **Windows'un uygulamaları bulanık olmaması için düzeltmeye çalışalım**diyor. **Farklı piksel yoğunlukları** seçeneği işaretlenmiş ekranlar için Optimize render varsa, Windows ayarını **açmanın** ihmal edilebilir bir etkisi vardır.
> - Windows 10 da bir **Program Uyumluluk Sorun Giderici**içerir. Bu sorun gidericiyi kullanarak Visual Studio'nun görünümünü düzeltmeye çalışmanızı önermiyoruz.

::: moniker-end

**İstemci performansına göre görsel deneyimi otomatik olarak ayarlama**

Visual Studio'nun görsel deneyime ayarlamayı otomatik olarak ayarlayıp ayarlamadığını veya ayarlamayı açıkça ayarlayıp ayarlamadığınızı belirtir. Bu ayarlama renk ekranını degradelerden düz renklere değiştirebilir veya menülerde veya açılır pencerelerde animasyon kullanımını kısıtlayabilir.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10'da, **Windows'un uygulamaları bulanık olmaması için düzeltmeye çalışalım**diyor. Visual Studio monitörünüzde bulanık görünüyorsa bu ayarı **açmanız** önerilir. Inç başına bir monitör başına nokta farkında uygulama olduğu için önemli ölçüde geliştirilmiş olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)yükseltme düşünün.

::: moniker-end

**Zengin istemci deneyimini etkinleştirin**

Degradeler ve animasyonlar da dahil olmak üzere Visual Studio'nun tam görsel deneyimini sağlar. Uzak Masaüstü bağlantılarını veya eski grafik bağdaştırıcılarını kullanırken bu seçeneği temizleyin, çünkü bu özellikler bu gibi durumlarda düşük performansa sahip olabilir. Bu seçenek, yalnızca istemci seçeneğine **göre görsel deneyimi otomatik olarak ayarla'yı** temizlediğinizde kullanılabilir.

**Varsa donanım grafik hızlandırma kullanma**

Yazılım hızlandırma yerine varsa donanım grafik ivmesi kullanır.

## <a name="other"></a>Diğer

**Pencere menüsünde gösterilen öğeler**

**Pencere** menüsünün Windows listesinde görünen pencere sayısını özelleştirir. 1 ile 24 arasında bir sayı girin. Varsayılan değer 10'dur.

**Son kullanılan listelerde gösterilen öğeler**

**Dosya** menüsünde görünen en son kullanılan proje ve dosyaların sayısını özelleştirir. 1 ile 24 arasında bir sayı girin. Varsayılan değer 10'dur. Bu, son kullanılan projeleri ve dosyaları almak için kolay bir yoldur.

**Durum çubuğugöster**

Durum çubuğunu görüntüler. Durum çubuğu IDE penceresinin alt kısmında yer alır ve devam eden işlemlerin ilerlemesi hakkında bilgi görüntüler.

**Kapat düğmesi yalnızca etkin araç pencerelerini etkiler**

**Kapat** düğmesi tıklatıldığında, yalnızca odak noktası olan araç penceresinin kapatılmış olduğunu ve docked kümesindeki tüm araç pencerelerinin olmadığını belirtir. Varsayılan olarak, bu seçenek seçilidir.

**Otomatik Gizle düğmesi yalnızca etkin araç pencerelerini etkiler**

**Otomatik Gizle** düğmesi tıklatıldığında, yalnızca odak noktası olan araç penceresinin otomatik olarak gizlendiğini ve kenetlenmiş kümedeki tüm araç pencerelerinin gizlenmediğini belirtir. Varsayılan olarak, bu seçenek seçilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
