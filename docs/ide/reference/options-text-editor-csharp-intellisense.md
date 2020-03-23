---
title: Seçenekler, Metin Düzenleyici, C#, IntelliSense
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 87a167a75f3b06522da77d562b0137df89757975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596222"
---
# <a name="options-text-editor-c-intellisense"></a>Seçenekler, Metin Düzenleyici, C#, IntelliSense

C# için **IntelliSense'in** davranışını etkileyen ayarları değiştirmek için IntelliSense seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Metin Düzenleyicisi** > **C#** > **IntelliSense'i**seçin.

**IntelliSense** seçenekleri sayfası aşağıdaki seçenekleri içerir:

## <a name="completion-lists"></a>Tamamlama Listeleri

- Bir karakter yazdıktan sonra tamamlanma listesini göster*

   Bu seçenek seçildiğinde, Yazmaya başladığınızda IntelliSense tamamlanma listesini otomatik olarak görüntüler. Bu seçenek seçilmediğinde, IntelliSense tamamlama hala **IntelliSense** menüsünden veya **Ctrl**+**Space**tuşuna basarak kullanılabilir.

- Karakter silindikten sonra tamamlanma listesini göster

- Tamamlama listesi öğelerinin eşleşen bölümlerini vurgulama

- Tamamlama öğesi filtrelerini göster

## <a name="snippets-behavior"></a>Parçacıklar davranışı

- Asla parçacıklar içermez

   Bu seçenek seçildiğinde, IntelliSense hiçbir zaman c# kodu parçacıkları için diğer adları tamamlama listesine eklenmez.

- Her zaman parçacıklar içerir

   Bu seçenek seçildiğinde, IntelliSense tamamlama listesine C# kodu parçacıkları için takma adlar ekler. Kod snippet diğer adı bir anahtar kelime ile aynı olduğu durumlarda, örneğin, [sınıf,](/dotnet/csharp/language-reference/keywords/class)anahtar kelime kısayol ile değiştirilir. Daha fazla bilgi için [C# Kodu Parçacıkları'na](../../ide/visual-csharp-code-snippets.md)bakın.

- ?-Sekme tanımlayıcıdan sonra yazıldığında parçacıkları ekleme

   Bu seçenek seçildiğinde, IntelliSense tamamlanma listesine C# kodu parçacıkları için takma adlar **ekler?** + **Sekme** tanımlayıcıdan sonra basılır

## <a name="enter-key-behavior"></a>Anahtar davranışı girin

- Enter'a asla yeni satır ekleme

   Tamamlanma listesinde bir öğe seçilip **Enter**tuşuna bastıktan sonra yeni bir satırın otomatik olarak eklenmediğini belirtir.

- Yalnızca tam olarak yazılan sözcüğün sonundan sonra enter'a yeni satır ekleyin

   Tamamlanma listesindeki bir giriş için tüm karakterleri yazıp Enter **tuşuna**basarsan, yeni bir satır otomatik olarak eklenir ve imleç yeni satıra taşınır.

   Örneğin, yazıp `else` **Enter**tuşuna basarsan, editörde aşağıdakiler görünür:

   `else`

   `|`(imleç konumu)

   Ancak, yalnızca `el` yazarsanız ve sonra **Enter**tuşuna baslarsanız, editörde aşağıdakiler görüntülenir:

   `else|`(imleç konumu)

- Enter'a her zaman yeni satır ekleyin

   Tamamlanma listesindeki bir giriş için karakterlerden *herhangi* birini yazıp Enter **tuşuna**basarsan, yeni bir satır otomatik olarak eklenir ve imleç yeni satıra taşınır.

## <a name="show-name-suggestions"></a>Ad önerilerini göster

Yakın zamanda seçtiğiniz üyeler için otomatik nesne adı tamamlama gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)
