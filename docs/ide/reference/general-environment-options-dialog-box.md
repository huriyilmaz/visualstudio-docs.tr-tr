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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569445"
---
# <a name="options-dialog-box-environment--general"></a>Seçenekler iletişim kutusu: ortam \> genel

Bu sayfayı, tümleşik geliştirme ortamı (IDE) için diğer seçenekler arasında renk temalarını, durum çubuğu ayarlarını ve dosya uzantısı ilişkilendirmelerini değiştirmek için kullanın. **Seçenekler** Iletişim kutusuna **Araçlar** menüsünü açıp **Seçenekler**' i seçip, **ortam** klasörünü açıp **genel** sayfasını seçerek erişebilirsiniz. Bu sayfa listede görünmezse, **Seçenekler** iletişim kutusundaki **tüm ayarları göster** onay kutusunu seçin.

## <a name="visual-experience"></a>Görsel deneyim

**Renk teması**

IDE için **mavi**, **hafif**, **koyu**veya **mavi (ekstra kontrast)** renk temasını seçin.

[Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) **Visual Studio Color teması düzenleyicisini** indirip yükleyerek, önceden tanımlanmış ek temalar yükleyebilir ve özel temalar oluşturabilirsiniz. Bu aracı yükledikten sonra, **renk teması** liste kutusunda ek renk temaları görüntülenir.

**Menü çubuğuna başlık durumu Stili Uygula**

Menüler, varsayılan olarak başlık durumu stili kullanır. Bunun yerine tüm büyük harf stillerini kullanmak için bu seçeneğin işaretini kaldırın.

::: moniker range=">=vs-2019"

**Farklı pikseller içeren ekranlar için işlemeyi iyileştirin (yeniden başlatma gerektirir)**

Bu seçenek, inç başına nokta (DPI) tanıma (veya *PMA*) için bir veya devre dışı bırakır. PMA etkinleştirildiğinde, Visual Studio Kullanıcı arabirimi, birden çok monitöre dahil olmak üzere herhangi bir izleyici görüntü ölçek faktörü ve DPı yapılandırmasında net görünür. PMA 'yı etkinleştirmek için Windows 10 Nisan 2018 güncelleştirmesi veya üzeri ve .NET Framework 4,8 veya üzeri bir sürüme sahip olmanız gerekir. (Bu iki önkoşul karşılanmazsa Bu seçenek gri renkte görünür.)

> [!TIP]
> - Windows 10 ' **un, bulanık olmadıkları Için Windows 'un uygulamaları düzeltmesine Izin verdiğini**belirten bir ayarı vardır. **Farklı piksel denikler seçeneği işaretli ekranlarda en iyileştirme için Işlemeyi en uygun hale getirmeniz** durumunda, bu Windows ayarı **Açık** bir etkiye sahip olur.
> - Windows 10 ' da bir **Program uyumluluğu sorun giderici**de bulunur. Bu sorun gidericiyi kullanarak Visual Studio 'nun görünümünü gidermeye çalışmamız önerilmez.

::: moniker-end

**İstemci performansına göre görsel deneyimi otomatik olarak ayarla**

Visual Studio 'Nun ayarlamayı otomatik olarak ayarlama veya ayarlamayı açık olarak ayarlama gibi belirtir. Bu ayarlama, renklerin degradeden düz renklere görüntüsünü değiştirebilir veya menülerde veya açılan pencerelerin animasyonların kullanımını kısıtlayabilir.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 ' **un, bulanık olmadıkları Için Windows 'un uygulamaları düzeltmesine Izin verdiğini**belirten bir ayarı vardır. Visual Studio, monitörünüzde bulanık **görünürse, bu ayarın etkinleştirilmesi** önerilir. [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)' a yükseltmeyi göz önünde bulundurun. Bu, büyük ölçüde geliştirilmiş görüntüleme netliği olan, her/inç bir uygulama için ekran başına nokta olarak geliştirilmiştir.

::: moniker-end

**Zengin istemci deneyimini etkinleştir**

Degradeler ve animasyonlar dahil olmak üzere Visual Studio 'nun tam görsel deneyimini sunar. Uzak Masaüstü bağlantıları veya daha eski grafik bağdaştırıcılar kullanılırken bu seçeneği temizleyin çünkü bu özellikler bu durumlarda düşük performansa sahip olabilir. Bu seçenek yalnızca, **istemci seçeneğine göre görsel deneyimi otomatik olarak ayarla** seçeneğini belirlediğinizde kullanılabilir.

**Kullanılabiliyorsa, donanım grafik hızlandırmasını kullanın**

Yazılım hızlandırma yerine, varsa, donanım grafik hızlandırmasını kullanır.

## <a name="other"></a>Diğer

**Pencere menüsünde gösterilecek Öğeler**

**Pencere** menüsünün Windows listesinde görüntülenen pencerelerin sayısını özelleştirir. 1 ile 24 arasında bir sayı girin. Varsayılan değer 10 ' dur.

**Son kullanılan listelerde gösterilen öğeler**

**Dosya** menüsünde görünen en son kullanılan proje ve dosya sayısını özelleştirir. 1 ile 24 arasında bir sayı girin. Varsayılan değer 10 ' dur. Bu, son kullanılan projeleri ve dosyaları almanın kolay bir yoludur.

**Durum çubuğunu göster**

Durum çubuğunu görüntüler. Durum çubuğu IDE penceresinin alt kısmında bulunur ve devam eden işlemlerin ilerleme durumuyla ilgili bilgileri görüntüler.

**Kapat düğmesi yalnızca etkin araç penceresini etkiler**

**Kapat** düğmesine tıklandığında, yalnızca odağı olan araç penceresinin kapalı olduğunu ve yerleşik küme içindeki araç pencerelerinin tümünü değil ' i belirtir. Varsayılan olarak, bu seçenek seçilidir.

**Otomatik Gizle düğmesi yalnızca etkin araç penceresini etkiler**

**Otomatik Gizle** düğmesine tıklandığında, yalnızca odağı olan araç penceresinin, yerleşik küme içindeki araç pencerelerinin hepsi değil otomatik olarak gizlendiğini belirtir. Varsayılan olarak, bu seçenek seçili değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
