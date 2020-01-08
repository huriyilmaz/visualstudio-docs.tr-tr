---
title: Tam ekran ve sanal alan modu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f224a6e3a1b12ed17799ddf6a2fc5c23f5d4cc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591040"
---
# <a name="how-to-manage-editor-modes"></a>Nasıl yapılır: Düzenleyici modlarını yönetme

Visual Studio Kod Düzenleyicisi'ni çeşitli görüntüleme modlarında görüntüleyebilirsiniz.

> [!NOTE]
> İletişim kutuları ve menü komutları gördüğünüz, etkin ayarlarınıza ve sürüm bağlı olarak bu makalede açıklanan olanlardan farklı olabilir. Ayarlarınızı, örneğin değiştirileceğini **genel** veya **Visual C++** ayarları seçebilirsiniz **Araçları** > **içeri ve dışarı aktarma ayarları**ve ardından **tüm ayarları Sıfırla**.

## <a name="enable-full-screen-mode"></a>Tam ekran modunu etkinleştirme

Tüm araç pencerelerini Gizle ve belge pencereleri etkinleştirerek görüntülemek seçebileceğiniz **tam ekran** modu.

- Tuşuna **Alt**+**Shift**+**Enter** girin ya da çıkmak için **tam ekran** modu.

     --veya--

- Komutu Yürüt `View.Fullscreen` içinde **komut** penceresi.

## <a name="enable-virtual-space-mode"></a>Sanal alan modu etkinleştir

İçinde **sanal adres alanı** modu, her kod satırının sonunda boşluklar eklenir. Kodunuzu yanındaki tutarlı bir noktada açıklamaları yerleştirmek için bu seçeneği belirleyin.

1. Seçin **seçenekleri** gelen **Araçları** menüsü.

2. Genişletin **metin düzenleyici** klasöründe ve **tüm diller** bu seçeneği genel olarak ayarlayın ya da belirli bir dil klasörü seçin. Örneğin, yalnızca Visual Basic'te satır numaralarını etkinleştirmek için tercih **temel** > **metin düzenleyici** düğümü.

3. Seçin **genel** seçenekleri altında **ayarları**seçin **sanal boşluğu etkinleştir**.

    > [!NOTE]
    > **Sanal adres alanı** etkin **sütun seçimi** modu. Zaman **sanal adres alanı** modu etkin değil, ekleme noktasını bir satır sonundan sonraki ilk karakteri için doğrudan taşır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
