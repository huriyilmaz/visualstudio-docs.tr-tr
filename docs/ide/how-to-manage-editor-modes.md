---
title: Tam ekran ve sanal boşluk modu
description: tüm araçların ve pencerelerin sizin için en uygun şekilde görüntülenmesi için Visual Studio düzenleyicisi modlarını nasıl yöneteceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 88d615cc82de737fda485a5a179ac14e0a92f607
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086085"
---
# <a name="how-to-manage-editor-modes"></a>Nasıl yapılır: düzenleyici modlarını yönetme

Visual Studio kod düzenleyicisini çeşitli görüntü modlarında görüntüleyebilirsiniz.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak bu makalede açıklananlardan farklı bir durum içerebilir. ayarlarınızı değiştirmek (örneğin, **genel** veya **Visual C++** ayarları) için **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**' ı seçin ve ardından **tüm ayarları sıfırla**' yı seçin.

## <a name="enable-full-screen-mode"></a>Tam ekran modunu etkinleştir

Tüm araç pencerelerini gizlemeyi ve yalnızca **tam ekran** modunu etkinleştirerek yalnızca belge pencerelerini görüntülemeyi seçebilirsiniz.

-  +  + **Tam ekran** moduna girmek veya çıkmak için alt SHIFT **ENTER** tuşuna basın.

     -- veya --

- Komut penceresinde komutunu verin `View.Fullscreen` . 

## <a name="enable-virtual-space-mode"></a>Sanal boşluk modunu etkinleştir

**Sanal alan** modunda, her kod satırının sonuna boşluklar eklenir. Açıklamaları kodunuzun yanındaki tutarlı bir noktada konumlandırmak için bu seçeneği belirleyin.

1. **Araçlar** menüsünde **Seçenekler** ' i seçin.

2. **Metin düzenleyici** klasörünü genişletin ve bu seçeneği Global olarak ayarlamak Için **tüm diller** ' i seçin veya belirli bir dil klasörü seçin. örneğin, satır numaralarını yalnızca Visual Basic açmak için **temel**  >  **metin düzenleyici** düğümünü seçin.

3. **genel** seçenekler ' i seçin ve **Ayarlar** altında **sanal alanı etkinleştir**' i seçin.

    > [!NOTE]
    > **Sütun seçim** modunda **sanal alan** etkindir. **Sanal boşluk** modu etkin olmadığında, ekleme noktası bir satırın sonundan doğrudan bir sonraki ilk karaktere gider.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'de pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
