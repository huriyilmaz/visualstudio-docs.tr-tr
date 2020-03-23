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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591040"
---
# <a name="how-to-manage-editor-modes"></a>Nasıl yapılsın: Editör modlarını yönetme

Visual Studio kod düzenleyicisini çeşitli ekran modlarında görüntüleyebilirsiniz.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürüme bağlı olarak bu makalede açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için, örneğin **Genel** veya **Görsel C++** ayarlarını değiştirmek **için, Araçlar** > **İçe Ve Dışa Aktar Ayarlarını**seçin ve ardından **tüm ayarları sıfırla'yı**seçin.

## <a name="enable-full-screen-mode"></a>Tam ekran modunu etkinleştirme

Tüm araç pencerelerini gizlemeyi ve **tam ekran** modunu etkinleştirerek yalnızca belge pencerelerini görüntülemeyi seçebilirsiniz.

- **Tam Ekran** moduna girmek veya çıkmak için **Alt**+**Shift**+**Enter** tuşuna basın.

     -- veya --

- **Komut** penceresinde `View.Fullscreen` komutu sorun.

## <a name="enable-virtual-space-mode"></a>Sanal alan modunu etkinleştirme

**Sanal Alan** modunda, boşluklar her kod satırının sonuna eklenir. Yorumları kodunuzun yanında tutarlı bir noktada konumlandırmak için bu seçeneği belirleyin.

1. **Araçlar** menüsünden **Seçenekler'i** seçin.

2. Metin **Düzenleyicisi** klasörünü genişletin ve bu seçeneği genel olarak ayarlamak için **Tüm Diller'i** seçin veya belirli bir dil klasörünü seçin. Örneğin, yalnızca Visual Basic'te satır numaralarını açmak için **Temel** > **Metin Düzenleyicisi** düğümini seçin.

3. **Genel** seçenekleri seçin ve **Ayarlar'ın**altında Sanal **Alanı Etkinleştir'i**seçin.

    > [!NOTE]
    > **Sanal Alan** **Sütun Seçimi** modunda etkinleştirilir. **Sanal Alan** modu etkinleştirilemediğinde, ekleme noktası doğrudan bir satırın sonundan sonrakinin ilk karakterine taşınır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Yazı Tipleri ve Renkler, Çevre, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
