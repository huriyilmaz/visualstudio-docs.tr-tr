---
title: Bul-komut kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b7c5f9c19573a04b1d9a8d7b8c6e9450aef9bc44
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645726"
---
# <a name="findcommand-box"></a>Bul/Komut Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Bul/komut** kutusundan metin araması yapabilir ve Visual Studio komutlarını çalıştırabilirsiniz. **Bul/komut** kutusu hala bir araç çubuğu denetimi olarak kullanılabilir, ancak artık varsayılan olarak görünmez. **Standart** araç çubuğunda **Düğme Ekle veya Kaldır** ' ı ve ardından **bul**' u seçerek **Bul/komut** kutusunu görüntüleyebilirsiniz.

 Bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komutu çalıştırmak için, (>) işaretiyle daha büyük bir işareti ile ön yüzü.

 **Bul/komut** kutusu, girilen son 20 öğeyi korur ve bir açılan listede görüntüler. Ok tuşlarını seçerek listede gezinebilirsiniz.

 ![Bul&#47;komut kutusu](../ide/media/findcommandbox.png "FindCommandBox") Bul/komut kutusu

## <a name="searching-for-text"></a>Metin arama
 Varsayılan olarak, **Bul/komut** kutusunda metin belirttiğinizde ve ardından Enter tuşunu seçtiğinizde, Visual Studio geçerli belgeyi veya araç penceresini **dosyalarda bul** iletişim kutusunda belirtilen seçenekleri kullanarak arar. Daha fazla bilgi için bkz. [metni bulma ve değiştirme](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Komutları girme
 Metin aramak yerine tek bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komutu veya diğer ad vermek üzere **Bul/komut** kutusunu kullanmak için, daha büyük (>) sembolüyle önceden ortaya çıkacak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komutunu girin. Örneğin:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

 Alternatif olarak, tek veya birden çok komut girmek ve yürütmek için Komut penceresi de kullanabilirsiniz. Bazı komutlar veya diğer adlar kendileri tarafından girilebilir ve çalıştırılabilir; Diğerlerinin sözdiziminde bağımsız değişkenler olması gerekir. Bağımsız değişkenlere sahip komutların listesi için bkz. [Visual Studio komutları](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Kaçış karakterleri
 Komut satırında bir şapka işareti (^) karakteri, bir denetim karakteri olarak değil, bundan hemen sonra gelen karakterin bir şekilde yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerindeki düz tırnak işaretlerini ("), boşlukları, baştaki eğik çizgileri, yüzleri veya diğer sabit karakterleri eklemek için kullanılabilir. Örneğin,

```
>Edit.Find ^^t /regex
```

 Bir giriş işareti, tırnak işaretlerinin içinde mi yoksa dışında mı olduğunu görür. Şapka, satırdaki son karakter ise yok sayılır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Komut penceresi](../ide/reference/command-window.md) [metni bulma ve değiştirme](../ide/finding-and-replacing-text.md)
