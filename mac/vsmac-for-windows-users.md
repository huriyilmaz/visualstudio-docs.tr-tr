---
title: Windows kullanıcılar için Mac için Visual Studio
description: Windows işletim sisteminde Visual Studio kullanmayla ilgili tanıdık geliştiriciler için Mac için Visual Studio tanıtım.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2021
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: c6a98e8314bfdb9c838db3dc36afbec004755d2b
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350995"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Windows kullanıcılar için Mac için Visual Studio

Bir işletim sisteminden diğerine geçiş yapmak çok fazla olabilir. Platformlar arası uygulamalarda, kullanıcı arabiriminden menü öğelerinin kategorilere ayrılması arasında genellikle daha hafif farklılıklar vardır. burada Windows için Mac için Visual Studio ve Visual Studio arasındaki en yaygın farklılıkları öğreneceksiniz. Ayrıca macOS ve Windows arasında birkaç farklı kural öğreneceksiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Geliştirici olarak, sizin görevleriniz ve gezinileriniz için klavyeyi kullanmaya alışkın olursunuz. klavyedeki bazı anahtarlar, mac ve Windows bilgisayarlar arasında ortaktır. Kopyalama ve yapıştırma gibi klavye eylemlerinin aynı anahtar birleşimlerini kullanmasını düşünmeye yönelik bir anlayışın. Bu her zaman durum değildir. neyse ki, Windows Visual Studio Mac için Visual Studio içindeki anahtar bağlamalarınızı değiştirebilirsiniz.

Mac için Visual Studio ilk kez çalıştırdığınızda klavye kısayolları seçim penceresini görürsünüz: ![ tuş bağlamaları penceresi](media/ide-tour-2019-keyboard-shortcut.png)

Anahtar bağlamalarını daha sonra değiştirmek istiyorsanız, bu ayarı Tercihler: ![ anahtar bağlamaları tercihlerinde bulabilirsiniz](media/customizing-the-ide-image10a.png)

MacOS 'un Windows için farklı sistem genelinde kısayollar kullandığını unutmamak önemlidir. anahtar bağlama tercihlerini değiştirmek, Mac için Visual Studio tanıdık Windows kısayollarını kullanmanıza olanak tanır. Ancak, macOS 'un diğer alanlarında macOS kısayollarıyla ilgili bilgi sahibi olmanız gerekir.

MacOS komutu (⌘) değiştirici tuşu genellikle Windows içindeki denetim anahtarının yerini alabilir. Aşağıda bazı örnekler ve diğer yaygın olarak kullanılan kısayollar verilmiştir:

|Görev                   |Windows Kısayol         |macOS kısayolu      |
|-----------------------|-------------------------|--------------------|
|Kopyala                   |`Ctrl + C`               |`⌘ + C`             |
|Yapıştır                  |`Ctrl + V`               |`⌘ + V`             |
|Kes                    |`Ctrl + X`               |`⌘ + X`             |
|Geri Al                   |`Ctrl + Z`               |`⌘ + Z`             |
|Yinele                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|İmleci sağ Sil |`Delete`                 |`fn + Backspace`    |
|Kelimeyi Sil            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> [Apple Support Web sitesinde](https://support.apple.com/en-us/HT201236)MacOS kısayollarının kapsamlı bir listesini bulabilirsiniz.

## <a name="menus"></a>Menüler

MacOS menüleri Windows menülerinden farklı şekilde düzenlenmiştir. Mac için Visual Studio özel durum değildir. En yaygın menü seçeneklerinden bazılarını buradan bulabilirsiniz:

|Görev                   |Visual Studio (Windows)                                              |Mac için Visual Studio                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Tercihler (Seçenekler)  |Araçlar > seçenekleri...                                                   |Visual Studio > tercihleri...       |
|Uzantıları             |Uzantılar > uzantıları yönetme                                       |> uzantıları Visual Studio...        |
|Düzenler                |Pencere > pencere düzeni uygula > [Düzen Seç]                       |> düzeni görüntüleme > [Düzen Seç]               |
|Güncelleştirmeler                |Güncelleştirme > için yardım denetimi                                             |güncelleştirmeleri denetlemek > Visual Studio... |
|NuGet Paket Yöneticisi  |araçlar > NuGet Paket Yöneticisi > NuGet paketleri veya çözümü yönet... |NuGet paketlerini yönetmek > Project...   |
|Araç bul             |Düzenle > bul ve Değiştir > [araç seçin]                              |Arama > [Araç seçme]               |
|Visual Studio Hakkında    |Microsoft Visual Studio hakkında yardım >                                 |Visual Studio hakkında > Visual Studio  

> [!NOTE]
> [ıde turundan](ide-tour.md) Mac için Visual Studio en yaygın özelliklere genel bakış bulabilirsiniz
