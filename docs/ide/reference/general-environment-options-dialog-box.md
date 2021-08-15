---
title: Genel, Ortam, Seçenekler İletişim Kutusu
description: IDE için renk temalarını, durum çubuğu ayarlarını, dosya uzantısı ilişkilendirmelerini ve daha fazlasını değiştirmek üzere ortam bölümündeki Genel sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6bc28e51942e8a1f52dbf573bdc477d081c74efb6aa714c07fc8eff351824fc1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121304235"
---
# <a name="options-dialog-box-environment--general"></a>Seçenekler iletişim kutusu: ortam \> genel

Bu sayfayı, tümleşik geliştirme ortamı (IDE) için diğer seçenekler arasında renk temalarını, durum çubuğu ayarlarını ve dosya uzantısı ilişkilendirmelerini değiştirmek için kullanın. **Seçenekler** Iletişim kutusuna **Araçlar** menüsünü açıp **Seçenekler**' i seçip, **ortam** klasörünü açıp **genel** sayfasını seçerek erişebilirsiniz.

## <a name="visual-experience"></a>Görsel deneyim

**Renk Teması**

IDE için **mavi**, **hafif**, **koyu** veya **mavi (ekstra kontrast)** renk temasını seçin.

[Visual Studio market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)'ten **Visual Studio Color Theme düzenleyicisini** indirip yükleyerek, önceden tanımlanmış ek temalar yükleyebilir ve özel temalar oluşturabilirsiniz. Bu aracı yükledikten sonra, **renk teması** liste kutusunda ek renk temaları görüntülenir.

**Menü çubuğuna başlık durumu Stili Uygula**

Menüler, varsayılan olarak başlık durumu stili kullanır. Bunun yerine tüm büyük harf stillerini kullanmak için bu seçeneğin işaretini kaldırın.

::: moniker range=">=vs-2019"

**Farklı pikseller içeren ekranlar için işlemeyi iyileştirin (yeniden başlatma gerektirir)**

Bu seçenek, inç başına nokta (DPI) tanıma (veya *PMA*) için bir veya devre dışı bırakır. pma etkinleştirildiğinde, Visual Studio kullanıcı arabirimi, birden çok monitörde de olmak üzere herhangi bir izleyici görüntü ölçek faktörü ve dpı yapılandırmasında net görünür. pma 'yı etkinleştirmek için, Windows 10 nisan 2018 güncelleştirmesi veya üzeri ve .NET Framework 4,8 ya da sonraki bir sürümü gerekir. (Bu iki önkoşul karşılanmazsa Bu seçenek gri renkte görünür.)

> [!TIP]
> - Windows 10, **uygulamaların bulanık olmaması için Windows uygulamayı düzeltmesine izin** veren bir ayara sahiptir. bu Windows ayarının **açık** olması, **farklı piksel denikler seçeneği işaretli ekranlarda en iyileştirme için işlemeyi en uygun hale getirir** .
> - Windows 10 ayrıca bir **Program uyumluluğu sorun gidericisini** içerir. bu sorun gidericiyi kullanarak Visual Studio görünümünü gidermeye çalışmamız önerilmez.

::: moniker-end

**İstemci performansına göre görsel deneyimi otomatik olarak ayarla**

Visual Studio ayarlamayı otomatik olarak ayarlayıp ayarlamadığını belirtir veya ayarlamayı açıkça ayarlayın. Bu ayarlama, renklerin degradeden düz renklere görüntüsünü değiştirebilir veya menülerde veya açılan pencerelerin animasyonların kullanımını kısıtlayabilir.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10, **uygulamaların bulanık olmaması için Windows uygulamayı düzeltmesine izin** veren bir ayara sahiptir. Visual Studio monitörünüzde bulanık **görünürse, bu ayarı açmak** önerilir. büyük ölçüde geliştirilmiş görüntüleme netliği olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)' a yükselterek, her bir for-of-of-aware uygulaması

::: moniker-end

**Zengin istemci deneyimini etkinleştir**

degradeler ve animasyonlar dahil olmak üzere Visual Studio tam görsel deneyimini mümkün bir şekilde sunar. Uzak Masaüstü bağlantıları veya daha eski grafik bağdaştırıcılar kullanılırken bu seçeneği temizleyin çünkü bu özellikler bu durumlarda düşük performansa sahip olabilir. Bu seçenek yalnızca, **istemci seçeneğine göre görsel deneyimi otomatik olarak ayarla** seçeneğini belirlediğinizde kullanılabilir.

**Kullanılabiliyorsa, donanım grafik hızlandırmasını kullanın**

Yazılım hızlandırma yerine, varsa, donanım grafik hızlandırmasını kullanır.

## <a name="other"></a>Diğer

**Pencere menüsünde gösterilecek Öğeler**

**pencere** menüsünün Windows listesinde görünen pencere sayısını özelleştirir. 1 ile 24 arasında bir sayı girin. Varsayılan değer 10'dur.

**Son kullanılan listelerde gösterilen öğeler**

**Dosya** menüsünde görünen en son kullanılan proje ve dosya sayısını özelleştirir. 1 ile 24 arasında bir sayı girin. Varsayılan değer 10'dur. Bu, son kullanılan projeleri ve dosyaları almanın kolay bir yoludur.

**Durum çubuğunu göster**

Durum çubuğunu görüntüler. Durum çubuğu IDE penceresinin alt kısmında bulunur ve devam eden işlemlerin ilerleme durumuyla ilgili bilgileri görüntüler.

**Kapat düğmesi yalnızca etkin araç penceresini etkiler**

**Kapat** düğmesine tıklandığında, yalnızca odağı olan araç penceresinin kapalı olduğunu ve yerleşik küme içindeki araç pencerelerinin tümünü değil ' i belirtir. Varsayılan olarak, bu seçenek seçilidir.

**Otomatik Gizle düğmesi yalnızca etkin araç penceresini etkiler**

**Otomatik Gizle** düğmesine tıklandığında, yalnızca odağı olan araç penceresinin, yerleşik küme içindeki araç pencerelerinin hepsi değil otomatik olarak gizlendiğini belirtir. Varsayılan olarak, bu seçenek seçili değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
