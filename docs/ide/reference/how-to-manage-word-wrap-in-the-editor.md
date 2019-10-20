---
title: Sözcük kaydırma
ms.date: 11/07/2018
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30bfe549100a06df6b9a8163cad1e3d519c3a91b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663116"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Nasıl yapılır: düzenleyicide sözcük kaydırmayı yönetme

**Sözcük kaydır** seçeneğini ayarlayabilir ve temizleyebilirsiniz. Bu seçenek ayarlandığında, uzun bir çizginin, kod düzenleyici penceresinin geçerli genişliğini aşan kısmı sonraki satırda görüntülenir. Örneğin, satır numaralandırma kullanımını kolaylaştırmak için bu seçenek temizlendiğinde, uzun çizgilerin uçlarını görmek için sağa kaydırma yapabilirsiniz.

> [!NOTE]
> Bu konu yalnızca Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio, sözcük kaydırmayı Şu anda desteklemiyor.

## <a name="to-set-word-wrap-preferences"></a>Sözcük kaydırmayı tercihleri ayarlamak için

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

2. **Metin düzenleyici** klasöründe, bu seçeneği küresel olarak ayarlamak Için **tüm diller** alt klasöründeki **genel** seçenekleri seçin.

     veya

     Programlamadaki dilin alt klasöründeki **genel** seçenekleri seçin.

3. **Ayarlar**altında **sözcük kaydır** seçeneğini belirleyin veya temizleyin.

     **Sözcük kaydır** seçeneği belirlendiğinde **sözcük kaydırması Için görsel glifleri göster** seçeneği etkinleştirilmiştir.

4. Uzun bir çizginin ikinci bir satıra kaydırılacağını gösteren bir dönüş oku göstergesini görüntülemeyi tercih ediyorsanız, **sözcük kaydırma için görsel glifleri göster** seçeneğini belirleyin. Gösterge oklarını görüntülememayı tercih ediyorsanız bu seçeneği temizleyin.

    > [!NOTE]
    > Bu anımsatıcı okları kodunuza eklenmez; Bunlar yalnızca görüntüleme amaçlıdır.

## <a name="known-issues"></a>Bilinen sorunlar

Not defteri + +, alt açık metin veya Visual Studio Code Word sarması hakkında bilgi sahibiyseniz, Visual Studio 'Nun diğer düzenleyicilerle farklı davrandığı aşağıdaki sorunlardan haberdar olun:

* [Üçlü tıklama tüm satırı seçmeyin](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Kes komutu tüm satırı silmez](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [Bitiş tuşuna iki kez basıldığında imleç satır sonuna taşınamaz](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../../ide/writing-code-in-the-code-and-text-editor.md)
