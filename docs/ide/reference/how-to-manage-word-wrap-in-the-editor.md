---
title: Sözcük kaydırma
ms.date: 11/07/2018
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f456a35f4a65438df5229492beb1f3e142e38f05
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508946"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Nasıl yapılsın: Editörde sözcük kaydırmayı yönetme

**Word kaydırma** seçeneğini ayarlayabilir ve temizleyebilirsiniz. Bu seçenek ayarlandığında, kod düzenleyicipenceresinin geçerli genişliğinin ötesine uzanan uzun bir satırın bölümü bir sonraki satırda görüntülenir. Bu seçenek, örneğin, satır numaralandırma kullanımını kolaylaştırmak için temizlendiğinde, uzun çizgilerin uçlarını görmek için sağa kaydırabilirsiniz.

> [!NOTE]
> Bu konu yalnızca Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio şu anda sözcük kaydırmayı desteklemiyor.

## <a name="to-set-word-wrap-preferences"></a>Sözcük kaydırma tercihlerini ayarlamak için

1. **Araçlar** menüsünde **Seçenekler**’i belirleyin.

2. Metin **Düzenleyicisi** klasöründe, bu seçeneği genel olarak ayarlamak için **Tüm Diller** alt klasöründeki **Genel** seçenekleri seçin.

     — veya —

     Programlama yaptığınız dil için alt klasördeki **Genel** seçenekleri seçin.

3. **Ayarlar**altında **Word kaydırma** seçeneğini seçin veya temizleyin.

     Word **kaydırma** seçeneği seçildiğinde, sözcük kaydırma seçeneği **için görsel glifleri göster** etkinleştirilir.

4. Uzun bir çizginin ikinci bir satıra kaydırıldığı bir dönüş ok göstergesi görüntülemeyi tercih **ederseniz, Word Wrap için görsel glifleri göster** seçeneğini belirleyin. Gösterge oklarını görüntülememek istiyorsanız bu seçeneği temizleyin.

    > [!NOTE]
    > Bu hatırlatma okları kodunuza eklenmez; bunlar yalnızca görüntü amaçlıdır.

## <a name="known-issues"></a>Bilinen sorunlar

Not Defteri++, Yüce Metin veya Visual Studio Kodu'nda sözcük kaydırma'ya aşinaysanız, Visual Studio'nun diğer editörlerden farklı davrandığını n ardından aşağıdaki sorunlardan haberdar olun:

* [Üçlü tıklama tüm satırı seçmez](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [End tuşuna iki kez basıldığında imleci satır sonuna taşımaz](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../../ide/writing-code-in-the-code-and-text-editor.md)
