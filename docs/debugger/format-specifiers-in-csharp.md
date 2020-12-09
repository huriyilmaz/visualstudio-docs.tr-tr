---
title: Hata ayıklayıcıda biçim belirticileri (C#) | Microsoft Docs
description: Bir değerin izleme penceresi görüntülendiği biçimi değiştirmek için Biçim belirleyicisi kullanın. Bu makalede kullanım ayrıntıları sağlanmaktadır.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31739b9c8fecc862c891173a792986b467730400
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862795"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında C# içindeki biçim belirticileri
Biçim belirticilerini kullanarak, **izleme** penceresinde bir değerin görüntülendiği biçimi değiştirebilirsiniz. Biçim belirticilerini **hemen** penceresinde, **komut** penceresinde, [izlenenoktalarda](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)ve kaynak penceresinde de kullanabilirsiniz. Bu pencerelerin bir ifadesinde durakladıysanız, sonuç belirtilen biçim görüntüsüne göre bir  [veri ipucunda](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) görüntülenir.

Biçim belirleyicisi kullanmak için, değişken ifadesini ve ardından virgül ve uygun belirticisi girin.

## <a name="set-format-specifiers"></a>Biçim belirticilerini ayarla
Aşağıdaki örnek kodu kullanacağız:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

`my_var1`Hata ayıklama sırasında değişkeni **izleme** penceresine ekleyin, Windows Watch 'da **hata ayıklama**  >  **Windows**  >  **Watch**  >  **1**' i izleyin. Sonra, değişkene sağ tıklayıp **onaltılık görüntü**' i seçin. Şimdi **İzle** penceresinde 0x0065 değeri gösterilir. Bu değeri bir onaltılık tamsayı yerine ondalık tamsayı olarak görmek için, değişken adından sonra **ad** sütununa **d** ondalık biçim belirleyicisi ekleyin. **Değer** sütununda artık **101** gösterilmektedir.

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

::: moniker range=">= vs-2019" 

**İzleme** penceresindeki değere bir virgül (,) ekleyerek kullanılabilir biçim belirticileri listesinden görüntüleyebilir ve seçim yapabilirsiniz. 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Biçim belirticileri
Aşağıdaki tabloda, Visual Studio hata ayıklayıcısı için C# biçim belirticileri açıklanmaktadır.

|Belirleyici|Biçimlendir|Özgün Izleme değeri|Görüntülenmektedir|
|---------------|------------|--------------------------|--------------|
|m|Özellik ve örtük işlev çağrılarının örtük değerlendirmesi kapalıyken yararlı olabilecek bir ifadenin değerlendirmesini zorla.|İleti "örtük işlev değerlendirmesi Kullanıcı tarafından kapatılmış"|\<value>|
|d|ondalık tamsayı|0x0065|101|
|dynamic|Belirtilen nesneyi dinamik görünüm kullanarak görüntüler|Dinamik görünüm dahil olmak üzere nesnenin tüm üyelerini görüntüler|Yalnızca dinamik görünümü görüntüler|
|h|onaltılı tamsayı|61541|0x0000F065|
|nq|tırnak işareti olmayan dize|"Dizim"|Dizim|
|No dili|Biçimi değil, davranışı belirtir. İfadeyi "yan etkisi yok" ile değerlendirir. İfade yorumlanamaz ve yalnızca bir değerlendirme tarafından çözümlenebiliyorsa (örneğin, işlev çağrısı), bunun yerine bir hata görürsünüz.|Yok|Yok|
|gizli|Tüm genel ve genel olmayan üyeleri görüntüler|Ortak üyeleri görüntüler|Tüm üyeleri görüntüler|
|Madde|Öğeyi ham öğe düğümünde göründüğü gibi görüntüler. Yalnızca Proxy nesnelerinde geçerlidir.|Sözlük\<T>|Sözlüğün ham görünümü\<T>|
|sonuçlar|Genellikle bir sorgu ifadesinin sonucu olan IEnumerable veya IEnumerable uygulayan bir tür değişkeniyle kullanılır \<T> . Yalnızca sorgu sonucunu içeren üyeleri görüntüler.|Tüm üyeleri görüntüler|Sorgunun koşullarını karşılayan üyeleri görüntüler|

## <a name="see-also"></a>Ayrıca bkz.
- [İzleme ve hızlı gözcü pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Oto ve Yereller pencereleri](../debugger/autos-and-locals-windows.md)
