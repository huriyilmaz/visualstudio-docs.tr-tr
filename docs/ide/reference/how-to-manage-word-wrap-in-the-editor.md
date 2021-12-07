---
title: Sözcük kaydırma
description: Kod düzenleyicisinde sözcük kaydır seçeneğini açma ve kapatma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 12/06/2021
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
ms.openlocfilehash: d704f105b878aefcfc8233029ac421326167b11a
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133978165"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Nasıl yapılır: düzenleyicide sözcük kaydırmayı yönetme

**Sözcük kaydır** seçeneğini ayarlayabilir ve temizleyebilirsiniz. Bu seçenek ayarlandığında, uzun bir çizginin, kod düzenleyici penceresinin geçerli genişliğini aşan kısmı sonraki satırda görüntülenir. Örneğin, satır numaralandırma kullanımını kolaylaştırmak için bu seçenek temizlendiğinde, uzun çizgilerin uçlarını görmek için sağa kaydırma yapabilirsiniz.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kaynak düzenleyicisi: sözcük kaydır](/visualstudio/mac/source-editor#word-wrap).

## <a name="to-set-word-wrap-preferences"></a>Sözcük kaydırmayı tercihleri ayarlamak için

1. Visual Studio menü çubuğunda **araçlar**' ı seçin ve ardından **seçenekler**' i seçin.

    :::image type="content" source="media/vs-2022/tools-options-menu-bar.png" alt-text="araçlar ve seçenekler seçiliyken Visual Studio menü çubuğunun ekran görüntüsü.":::

2. **Metin düzenleyici** klasöründe, bu seçeneği küresel olarak ayarlamak Için **tüm diller** alt klasöründeki **genel** seçenekleri seçin.

     veya

     Programlamadaki dilin alt klasöründeki **genel** seçenekleri seçin.

3. **Ayarlar** altında **sözcük kaydır** seçeneğini belirleyin veya temizleyin.

     **Sözcük kaydır** seçeneği belirlendiğinde **sözcük kaydırması Için görsel glifleri göster** seçeneği etkinleştirilmiştir.

    > [!NOTE]
    > **Sözcük kaydırma için görsel glifleri göster** seçeneği, uzun bir çizginin ikinci bir satıra kaydırılacağını gösteren bir dönüş oku göstergesi görüntüler. Bu anımsatıcı okları kodunuza eklenmez; Bunlar yalnızca görüntüleme amaçlıdır.

## <a name="known-issues"></a>Bilinen sorunlar

Not Defteri + +, alt açık metin veya Visual Studio Code sözcük kaydırmayı biliyorsanız, Visual Studio diğer düzenleyicilerle farklı davrandığı sorunları göz önünde bulundurun:

* [Üçlü tıklama tüm satırı seçmeyin](https://developercommunity.visualstudio.com/t/fix-known-issues-in-word-wrap/351760)
* [Bitiş tuşuna iki kez basıldığında imleç satır sonuna taşınamaz](https://developercommunity.visualstudio.com/t/fix-known-issues-in-word-wrap/351760)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../../ide/writing-code-in-the-code-and-text-editor.md)