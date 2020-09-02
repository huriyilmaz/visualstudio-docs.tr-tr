---
title: C# içinde biçim belirticileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6085ba95d3880417e517530069734052741113e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682474"
---
# <a name="format-specifiers-in-c"></a>C 'de biçim belirticileri\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Biçim belirticilerini kullanarak **izleme** penceresinde bir değerin görüntülendiği biçimi değiştirebilirsiniz. Biçim belirticilerini **hemen** penceresinde, **komut** penceresinde ve hatta kaynak penceresinde de kullanabilirsiniz. Bu pencerelerin bir ifadesinde durakladıysanız, sonuç bir DataTip içinde görüntülenir. DataTips, Datatıp görüntüsüne biçim belirticisini yansıtır.

Biçim belirleyicisi kullanmak için, ifadeyi ve ardından virgül yazın. Virgülden sonra uygun belirticisi ekleyin.

## <a name="using-format-specifiers"></a>Biçim belirticilerini kullanma

Aşağıdaki koda sahipseniz:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

`my_var1`Değişkeni izleme penceresi ekleyin (hata ayıklama, **hata ayıklama/Windows/Izleme/izleme 1**) ve ekranı onaltılı olarak ayarlayın ( **Gözcü** penceresinde, değişkene sağ tıklayıp **onaltılık görüntü**' i seçin). Şimdi **İzle** penceresi, 0x0065 değerini içerdiğini gösterir. Bu değeri, onaltılık tamsayı yerine bir ondalık tamsayı olarak ifade etmek için, ad sütununda, değişken adından sonra, ondalık biçim belirleyicisi ekleyin: **, d**. Değer sütunu artık ondalık 101 değerini görüntülüyor

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

## <a name="format-specifiers"></a>Biçim belirticileri

Aşağıdaki tabloda hata ayıklayıcı tarafından tanınan C# biçim belirticileri gösterilmektedir.

|Belirleyici|Biçimlendir|Özgün Izleme değeri|Görüntülenmektedir|
|---------------|------------|--------------------------|--------------|
|m|Bir ifadenin değerlendirmesini zorla. Bu, özelliklerin örtük değerlendirmesi ve örtük işlev çağrıları kapalıyken yararlı olabilir. Bkz. [yan etkiler ve ifadeler](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|İleti "örtük işlev değerlendirmesi Kullanıcı tarafından kapatılmış"|\<value>|
|d|ondalık tamsayı|0x0065|101|
|dynamic|Belirtilen nesneyi dinamik görünüm kullanarak görüntüler|Dinamik görünüm dahil olmak üzere nesnenin tüm üyelerini görüntüler|Yalnızca dinamik görünümü görüntüler|
|h|onaltılı tamsayı|61541|0x0000F065|
|nq|tırnak işareti olmayan dize|"Dizim"|Dizim|
|gizli|Tüm genel ve genel olmayan üyeleri görüntüler|Ortak üyeleri görüntüler|Tüm üyeleri görüntüler|
|Madde|Öğeyi ham öğe düğümünde göründüğü gibi görüntüler. Yalnızca Proxy nesnelerinde geçerlidir.|Sözlük\<T>|Sözlüğün ham görünümü\<T>|
|sonuçlar|Genellikle bir sorgu ifadesinin sonucu olan IEnumerable veya IEnumerable uygulayan bir tür değişkeniyle kullanılır \<T> . Yalnızca sorgu sonucunu içeren üyeleri görüntüler.|Tüm üyeleri görüntüler.|Sorgunun koşullarını karşılayan üyeleri görüntüler.|

## <a name="see-also"></a>Ayrıca Bkz.

- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Değişken pencereleri](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
