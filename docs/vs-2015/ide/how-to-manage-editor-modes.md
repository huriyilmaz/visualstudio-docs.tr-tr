---
title: 'Nasıl yapılır: düzenleyici modlarını yönetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a188e90d3feeb903eb8b4efceb91eb53cac3bdce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651845"
---
# <a name="how-to-manage-editor-modes"></a>Nasıl Yapılır: Düzenleyici Modlarını Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Code düzenleyicisini çeşitli görüntü modlarında gösterebilirsiniz.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="enabling-full-screen-mode"></a>Tam ekran modunu etkinleştirme
 Tüm araç pencerelerini gizlemeyi ve yalnızca **tam ekran** modunu etkinleştirerek yalnızca belge pencerelerini görüntülemeyi seçebilirsiniz.

#### <a name="to-enable-full-screen-mode"></a>Tam ekran modunu etkinleştirmek için

- **Tam ekran** moduna girmek veya ÇıKMAK için alt + SHIFT + enter tuşlarına basın.

     -- veya --

- Komut penceresinde komutunu verin `View.Fullscreen` . **Command**

## <a name="enabling-virtual-space-mode"></a>Sanal alan modunu etkinleştirme
 **Sanal alan** modunda, her kod satırının sonuna boşluklar eklenir. Açıklamaları kodunuzun yanındaki tutarlı bir noktada konumlandırmak için bu seçeneği belirleyin.

#### <a name="to-enable-virtual-space-mode"></a>Sanal boşluk modunu etkinleştirmek için

1. **Araçlar** menüsünde **Seçenekler** ' i seçin.

2. **Metin düzenleyici** klasörünü genişletin ve bu seçeneği Global olarak ayarlamak Için **tüm diller** ' i seçin veya belirli bir dil klasörü seçin. (Örneğin, satır numaralarını yalnızca Visual Basic açmak için temel, metin düzenleyici seçeneklerini belirleyin.)

3. **Genel** Seçenekler ' i seçin ve **Ayarlar**altında **sanal alanı etkinleştir**' i seçin.

    > [!NOTE]
    > **Sütun seçim** modunda **sanal alan** etkindir. **Sanal boşluk** modu etkin olmadığında, ekleme noktası bir satırın sonundan doğrudan bir sonraki ilk karaktere gider.

## <a name="see-also"></a>Ayrıca Bkz.
 [Düzenleyiciyi özelleştirme](../ide/customizing-the-editor.md) [nasıl yapılır: Windows](../misc/how-to-arrange-and-dock-windows.md) [yazı tipi ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) yerleştirme ve yerleştirme
