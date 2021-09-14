---
title: Find-Command Box
description: Bul/Komut kutusunu ve bu kutuyu metin aramak ve komut satırı çalıştırmak için nasıl kullanabileceğiniz hakkında Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4492836ed06ea65a829d659ba81f261f0f99fe69
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625917"
---
# <a name="findcommand-box"></a>Bul/Komut kutusu

Bul/Komut kutusundan metin Visual Studio komutlarını **çalıştırabilirsiniz.** **Bul/Komut** kutusu hala bir araç çubuğu denetimi olarak kullanılabilir, ancak artık varsayılan olarak görünür değildir. Standart araç çubuğunda Düğme Ekle veya Kaldır'ı  ve **ardından** Bul'ı seçerek **Bul/Komut** kutusunu **görüntüleyebilirsiniz.**

Bir komutu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştırmak için büyük ( ) işaretiyle **>** önsöze yazın.

**Bul/Komut** kutusu girilen son 20 öğeyi korur ve bunları açılan listede görüntüler. Ok tuşlarını seçerek listede **gezinebilirsiniz.**

![Komut&#47;Kutusunu Bulma](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Metin arama

Varsayılan olarak, **Bul/Komut** kutusunda metin belirttiğinizde ve **ardından Enter** tuşuna basın; Visual Studio Dosyalarda Bul iletişim kutusunda belirtilen seçenekleri kullanarak geçerli belgeyi veya araç penceresini arar.  Daha fazla bilgi için [bkz. Metin bulma ve değiştirme.](../ide/finding-and-replacing-text.md)

## <a name="entering-commands"></a>Komutları girme

**Bul/Komut kutusunu kullanarak** metin aramak yerine tek bir komut veya diğer ad kullanmak için komutun öncesini büyüktür ( ) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **>** simgesiyle yazın. Örnek:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatif olarak, tek veya birden çok **komut girmek** ve yürütmek için Komut penceresini de kullanabilirsiniz. Bazı komutlar veya diğer adlar kendi kendilerine girilebilir ve yürütülebilirsiniz; diğerlerinde ise söz dizimlerinde gerekli bağımsız değişkenler vardır. Bağımsız değişkenleri olan komutların listesi için bkz. [Visual Studio.](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Kaçış karakterleri

Komutta caret ( ) karakteri, onu takip eden karakterin denetim karakteri yerine tam anlamıyla **^** yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerine düz tırnak işaretleri (**"**), boşluklar, baştaki eğik çizgi, işaret işareti veya diğer değişmez karakterleri eklemek için kullanılabilir. Örnek:

```
>Edit.Find ^^t /regex
```

İster tırnak içinde ister dışında olsun, bir işaret aynı şekilde işlev gösterir. Çizgideki son karakter bir karakterse yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../ide/reference/command-window.md)
- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
