---
title: Bul-Komut Kutusu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591534"
---
# <a name="findcommand-box"></a>Bul/Komut kutusu

Metni arayabilir ve **Bul/Komut** kutusundan Visual Studio komutlarını çalıştırabilirsiniz. **Bul/Komut** kutusu hala araç çubuğu denetimi olarak kullanılabilir, ancak varsayılan olarak artık görünmez. **Standart** araç çubuğunda Ekle veya **Kaldır Düğmeleri'ni** seçerek ve ardından **Bul'u**seçerek **Bul/Komut** kutusunu görüntüleyebilirsiniz.

Bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komutu çalıştırmak için, komutu**>** daha büyük bir ( ) işaretiyle önsöze belirtin.

**Bul/Komut** kutusu girilen son 20 öğeyi korur ve bunları açılır listede görüntüler. **Ok tuşlarını**seçerek listede gezinebilirsiniz.

![Komut Kutusunu bul&#47;](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Metin arama

Varsayılan olarak, **Bul/Komut** kutusunda metin belirttiğiniz ve sonra **Enter** tuşunu seçtiğinizde, Visual Studio **Dosyalarda Bul** iletişim kutusunda belirtilen seçenekleri kullanarak geçerli belgeyi veya araç penceresini arar. Daha fazla bilgi için [bkz.](../ide/finding-and-replacing-text.md)

## <a name="entering-commands"></a>Komutları girme

Metin aramak yerine tek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir komut veya takma ad vermek için **Bul/Komut** kutusunu kullanmak**>** için komutu () 'den büyük bir simgeyle önsöze belirtin. Örnek:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatif olarak, tek veya birden çok komut girmek ve yürütmek için **Komut** penceresini de kullanabilirsiniz. Bazı komutlar veya takma adlar kendileri tarafından girilebilir ve yürütülebilir; diğerleri sözdiziminde bağımsız değişkenler gerekmemektedir. Bağımsız değişkenleri olan komutların listesi için [Visual Studio komutlarına](../ide/reference/visual-studio-commands.md)bakın.

## <a name="escape-characters"></a>Kaçış karakterleri

Komuttaki bir**^** caret ( ) karakteri, onu hemen izleyen karakterin bir kontrol karakteri olarak değil, kelimenin tam anlamıyla yorumlanması anlamına gelir. Bu, anahtar adları hariç, düz tırnak işaretleri **("**), boşluklar, satır başları, carets veya bir parametre veya anahtar değeri diğer tüm gerçek karakterleri gömmek için kullanılabilir. Örnek:

```
>Edit.Find ^^t /regex
```

Bir caret, tırnak işaretlerinin içinde veya dışında olsun aynı işlevi görür. Bir basamak satırdaki son karakterse, yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../ide/reference/command-window.md)
- [Metni bulma ve değiştirme](../ide/finding-and-replacing-text.md)
