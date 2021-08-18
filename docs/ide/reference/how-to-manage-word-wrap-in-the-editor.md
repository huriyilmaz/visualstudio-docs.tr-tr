---
title: Sözcük kaydırma
description: Kod düzenleyicisinde sözcük kaydırma seçeneğini açma ve kapatmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 626ecc63152ca2ee46b2d2a132975c0039a02daf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132112"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Nasıl: Düzenleyicide sözcük kaydırmayı yönetme

Sözcük kaydırma seçeneğini ayarp **temizebilirsiniz.** Bu seçenek ayarlendiğinde, Kod Düzenleyicisi penceresinin geçerli genişliğinin ötesine genişleten uzun bir satırın bölümü sonraki satırda görüntülenir. Bu seçenek temizlendiğinde, örneğin, satır numarası kullanımını kolaylaştırmak için sağa kaydırarak uzun satırların sonlarını görüntüebilirsiniz.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Kaynak düzenleyicisi: Sözcük kaydırma.](/visualstudio/mac/source-editor#word-wrap)

## <a name="to-set-word-wrap-preferences"></a>Sözcük kaydırma tercihlerini ayarlamak için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. Bu **seçeneği genel olarak** ayarlamak **için** Metin Düzenleyici klasöründe **Tüm** Diller alt klasöründeki Genel seçenekleri seçin.

     — veya —

     Programlamak  istediğiniz dil için alt klasörde Genel seçeneklerini belirleyin.

3. Bu **Ayarlar** Sözcük kaydırma seçeneğini belirleyin **veya silin.**

     Sözcük **kaydırma seçeneği** seçildiğinde, Sözcük **kaydırma için görselleri göster seçeneği** etkinleştirilir.

4. Uzun **bir çizginin ikinci bir** satıra kaydırılan bir dönüş oku göstergesi görüntülemeyi tercih ediyorsanız Sözcük Kaydırma için görselleri göster seçeneğini belirleyin. Gösterge oklarını görüntülememeyi tercih ediyorsanız bu seçeneğin içini boşaltın.

    > [!NOTE]
    > Bu anımsatıcı okları kodunuza eklenmez; Bunlar yalnızca görüntüleme amaçlıdır.

## <a name="known-issues"></a>Bilinen sorunlar

Not Defteri++, Sublime Text veya Visual Studio Code sözcük kaydırmayı biliyorsanız, Visual Studio'nin diğer düzenleyicilere göre farklı davranarak Visual Studio dikkat edin:

* [Üçlü tıklama tam satırı seçmez](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Bitiş tuşuna iki kez basılarak imleci satırın sonuna taşınmaz](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../../ide/writing-code-in-the-code-and-text-editor.md)
