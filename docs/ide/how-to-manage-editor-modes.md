---
title: Tam ekran ve sanal boşluk modu
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd3e238813c6cfd8674e5392d9ad20889e79c900
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645848"
---
# <a name="how-to-manage-editor-modes"></a>Nasıl yapılır: düzenleyici modlarını yönetme

Visual Studio kod düzenleyicisini çeşitli görüntü modlarında görüntüleyebilirsiniz.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak bu makalede açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için (örneğin, **genel** veya  **C++ görsel** ayarları), **Araçlar** > **içeri ve dışarı aktarma ayarları**' nı seçin ve ardından **tüm ayarları Sıfırla**' yı seçin.

## <a name="enable-full-screen-mode"></a>Tam ekran modunu etkinleştir

Tüm araç pencerelerini gizlemeyi ve yalnızca **tam ekran** modunu etkinleştirerek yalnızca belge pencerelerini görüntülemeyi seçebilirsiniz.

- **Tam ekran** moduna girmek veya çıkmak için **Alt** +**SHIFT** +**ENTER** tuşuna basın.

     --veya--

- **Komut penceresinde komut** `View.Fullscreen` verin.

## <a name="enable-virtual-space-mode"></a>Sanal boşluk modunu etkinleştir

**Sanal alan** modunda, her kod satırının sonuna boşluklar eklenir. Açıklamaları kodunuzun yanındaki tutarlı bir noktada konumlandırmak için bu seçeneği belirleyin.

1. **Araçlar** menüsünde **Seçenekler** ' i seçin.

2. **Metin düzenleyici** klasörünü genişletin ve bu seçeneği Global olarak ayarlamak Için **tüm diller** ' i seçin veya belirli bir dil klasörü seçin. Örneğin, satır numaralarını yalnızca Visual Basic açmak için **temel**  > **metin düzenleyici** düğümünü seçin.

3. **Genel** Seçenekler ' i seçin ve **Ayarlar**altında **sanal alanı etkinleştir**' i seçin.

    > [!NOTE]
    > **Sütun seçim** modunda **sanal alan** etkindir. **Sanal boşluk** modu etkin olmadığında, ekleme noktası bir satırın sonundan doğrudan bir sonraki ilk karaktere gider.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)