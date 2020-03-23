---
title: Windows kullanıcıları için Mac için Visual Studio
description: Mac için Visual Studio'da erişilebilirlik özelliklerinin tanıtımı ve bunların nasıl etkinleştirilebileceği.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984264"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Windows kullanıcıları için Mac için Visual Studio

Bir işletim sisteminden diğerine geçiş yapmak zor olabilir. Kullanıcı arabiriminden menü öğelerinin kategorize inden platform ötesi uygulamalarda genellikle ince farklar vardır. Kullanıcılar ayrıca yeni işletim sisteminin kullanıcı arabirimine alışma öğrenme eğrisine sahip olacaktır. Burada Mac için Visual Studio ile Windows için Visual Studio arasındaki en yaygın farkları öğreneceksiniz. Ayrıca macOS ve Windows arasında birkaç farklı kural öğreneceksiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Geliştiriciler olarak, birçoğunuz görevleriniz ve gezinme için klavyeyi kullanmaya alışkın sınızdır. Klavyedeki bazı tuşlar Mac'ler ve Windows bilgisayarları arasında yaygındır. Kopyalama ve yapıştır gibi klavye eylemlerinin aynı tuş birleşimini kullandığını düşündüğünüz için affedilebilirsiniz. Bu her zaman böyle değildir. Neyse ki, Mac için Visual Studio'daki anahtar bağlamalarınızı Windows'daki Visual Studio ile yakından eşleştirmek için değiştirebilirsiniz.

Mac için Visual Studio'yu ilk çalıştırdığınızda klavye kısayolları ![seçim penceresini görürsünüz: Tuş bağlamapenceresi](media/ide-tour-2019-keyboard-shortcut.png)

Anahtar bağlamaları daha sonra değiştirmek isterseniz, ayarları tercihlerde bulabilirsiniz: ![Anahtar bağlama tercihleri](media/customizing-the-ide-image10a.png)

macOS'un Windows için sistem genelinde farklı kısayollar kullandığını unutmayın. Temel bağlama tercihlerini değiştirmek, Mac için Visual Studio'da tanıdık Windows kısayollarını kullanmanıza olanak tanır. Ancak, macOS'un diğer alanlarında macOS kısayollarına aşina olmanız gerekir.

macOS Komutu (3) değiştirici anahtarı, Windows'daki Denetim anahtarının yerini alabilir. Aşağıda bazı örnekler ve sık kullanılan diğer kısayollar verilmiştir:

|Görev                   |Windows Kısayolu         |macOS Kısayolu      |
|-----------------------|-------------------------|--------------------|
|Kopyala                   |`Ctrl + C`               |`⌘ + C`             |
|Yapıştır                  |`Ctrl + V`               |`⌘ + V`             |
|Kes                    |`Ctrl + X`               |`⌘ + X`             |
|Geri al                   |`Ctrl + Z`               |`⌘ + Z`             |
|Yinele                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|İmlecin sağını silme |`Delete`                 |`fn + Backspace`    |
|Sözcüğü silme            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> MacOS kısayollarının kapsamlı bir listesini [Apple Destek web sitesinde](https://support.apple.com/en-us/HT201236)bulabilirsiniz.

## <a name="menus"></a>Menüler

macOS'taki menüler Windows'daki menülerden farklı olarak düzenlenir. Mac için Visual Studio bir istisna değildir. En yaygın menü seçeneklerinden bazılarını burada bulabilirsiniz:

|Görev                   |Görsel Stüdyo (Windows)                                              |Mac için Visual Studio                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Tercihler (Seçenekler)  |Araçlar > Seçenekleri...                                                   |Görsel Stüdyo > Tercihleri...       |
|Uzantılar             |Uzantıları Yönetme > Uzantıları                                       |Visual Studio > Uzantıları...        |
|Düzenler                |Pencere > Uygula Pencere Düzeni > [Düzeni Seç]                       |> görüntüle [Düzeni seç]               |
|Güncelleştirmeler                |Güncellemeleri Denetleme> Yardım                                             |Visual Studio > Güncellemeler için kontrol edin ... |
|NuGet Paket Yöneticisi  |NuGet Paketlerini veya Çözümlerini Yönetmek > NuGet Paket Yöneticisi > Araçlar... |Proje > NuGet Paketlerini Yönetin...   |
|Pedler / Windows         |> [Pad Seç / pencere seç]                                         |> Pads > [Pad / pencere seç] görüntüle  |
|Araçları bulma             |> > Bul ve Değiştir [Aracı seç]                              |arama > [Aracı seç]               |
|Visual Studio Hakkında    |Microsoft Visual Studio Hakkında Yardım >                                 |Visual Studio > Visual Studio Hakkında  

> [!NOTE]
> [IDE Tour'da](ide-tour.md) Mac için Visual Studio'da en yaygın özelliklere genel bir bakış bulabilirsiniz