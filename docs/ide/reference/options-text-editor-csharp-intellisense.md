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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2d1e330788b72ff0b4395d1e5d531d1d233f59e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666235"
---
# <a name="options-text-editor-c-intellisense"></a>Seçenekler, Metin Düzenleyici, C#, IntelliSense

İçin C#IntelliSense 'in davranışını etkileyen ayarları değiştirmek için **IntelliSense** seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için **araçlar**  > **Seçenekler**' i seçin ve ardından**IntelliSense** >   > **C#** **metin düzenleyici** ' yi seçin.

**IntelliSense** seçenekleri sayfası aşağıdaki seçenekleri içerir:

## <a name="completion-lists"></a>Tamamlanma listeleri

- Bir karakter yazıldıktan sonra tamamlanma listesini göster *

   Bu seçenek belirlendiğinde, yazmaya başladığınızda IntelliSense, tamamlanma listesini otomatik olarak görüntüler. Bu seçenek seçili olmadığında, IntelliSense tamamlanmaya hala **IntelliSense** menüsünde veya **CTRL** +**Space**' i basılarak erişilebilir.

- Bir karakter silindikten sonra tamamlanma listesini göster

- Tamamlanma listesi öğelerinin eşleşen bölümlerini Vurgula

- Tamamlama öğesi filtrelerini göster

## <a name="snippets-behavior"></a>Kod parçacıkları davranışı

- Kod parçacıklarını hiçbir şekilde eklemeyin

   Bu seçenek belirlendiğinde, IntelliSense hiçbir zaman kod parçacıkları için C# tamamlama listesine diğer adlar eklemektedir.

- Her zaman parçacıkları dahil et

   Bu seçenek belirlendiğinde, IntelliSense, kod parçacıkları için C# tamamlama listesine diğer adlar ekler. Kod parçacığı diğer adının bir anahtar sözcükle aynı olduğu durumda (örneğin, [sınıfı](/dotnet/csharp/language-reference/keywords/class)), anahtar sözcüğü kısayol ile değiştirilmiştir. Daha fazla bilgi için bkz [ C# . kod parçacıkları](../../ide/visual-csharp-code-snippets.md).

- Bir tanımlayıcıdan sonra?-Tab yazıldığında kod parçacıklarını dahil et

   Bu **seçenek belirlendiğinde,** IntelliSense ne zaman bir tanımlayıcıdan C# sonra +**sekmesine** basıldığında, IntelliSense, kod parçacıkları için diğer adlar ekler.

## <a name="enter-key-behavior"></a>Anahtar davranışı girin

- ENTER 'a hiçbir şekilde yeni satır eklemeyin

   Tamamlanma listesindeki bir öğeyi seçip **ENTER**tuşuna basarak yeni bir satırın hiçbir şekilde otomatik olarak eklendiğine belirtir.

- Yalnızca tam yazılan kelimeden sonra ENTER 'a yeni satır ekle

   Tamamlanma listesindeki bir girdinin tüm karakterlerini yazıp **ENTER**' a basarsanız, otomatik olarak yeni bir satır eklenir ve imleç yeni satıra gider.

   Örneğin, `else` yazıp **ENTER**tuşuna basarsanız, düzenleyicide aşağıdakiler görüntülenir:

   `else`

   `|` (imleç konumu)

   Ancak, yalnızca `el` yazıp **ENTER**tuşuna basarsanız, düzenleyicide aşağıdakiler görüntülenir:

   `else|` (imleç konumu)

- ENTER 'a her zaman yeni satır ekle

   Tamamlanma listesindeki bir girdinin karakterlerinden *birini yazıp* **ENTER**' a basarsanız, otomatik olarak yeni bir satır eklenir ve imleç yeni satıra gider.

## <a name="show-name-suggestions"></a>Ad önerilerini göster

Son zamanlarda seçtiğiniz üyeler için otomatik nesne adı tamamlamayı gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)