---
title: Seçenekler, Metin Düzenleyici, C#, IntelliSense
description: C# için IntelliSense 'in davranışını etkileyen ayarları değiştirmek için C# bölümünde IntelliSense sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 33dc002147ab07994dd3d64d64a595b896e9bcf41c594891ca4cf60e4bcb9061
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372159"
---
# <a name="options-text-editor-c-intellisense"></a>Seçenekler, Metin Düzenleyici, C#, IntelliSense

C# için IntelliSense davranışını etkileyen ayarları değiştirmek için **IntelliSense** seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için **Araçlar**  >  **Seçenekler**' i ve ardından **metin düzenleyici**  >  **C#**  >  **IntelliSense**' i seçin.

**IntelliSense** seçenekleri sayfası aşağıdaki seçenekleri içerir:

## <a name="completion-lists"></a>Tamamlanma listeleri

- Bir karakter yazıldıktan sonra tamamlanma listesini göster *

   Bu seçenek belirlendiğinde, yazmaya başladığınızda IntelliSense, tamamlanma listesini otomatik olarak görüntüler. Bu seçenek seçili olmadığında, IntelliSense tamamlanmaya hala **IntelliSense** menüsünde veya **CTRL** + **Space**'e basılarak ulaşılabilir.

- Bir karakter silindikten sonra tamamlanma listesini göster

- Tamamlanma listesi öğelerinin eşleşen bölümlerini Vurgula

- Tamamlama öğesi filtrelerini göster

## <a name="snippets-behavior"></a>Kod parçacıkları davranışı

- Kod parçacıklarını hiçbir şekilde eklemeyin

   Bu seçenek belirlendiğinde, IntelliSense hiçbir zaman tamamlama listesine C# kod parçacıkları için diğer adlar eklemektedir.

- Her zaman parçacıkları dahil et

   Bu seçenek belirlendiğinde, IntelliSense, tamamlama listesine C# kod parçacıkları için diğer adlar ekler. Kod parçacığı diğer adının bir anahtar sözcükle aynı olduğu durumda (örneğin, [sınıfı](/dotnet/csharp/language-reference/keywords/class)), anahtar sözcüğü kısayol ile değiştirilmiştir. Daha fazla bilgi için bkz. [C# kod parçacıkları](../../ide/visual-csharp-code-snippets.md).

- Bir tanımlayıcıdan sonra?-Tab yazıldığında kod parçacıklarını dahil et

   Bu **seçenek belirlendiğinde, IntelliSense ne zaman** + tamamlandığında, C# kod parçacıkları için diğer adları tamamlama listesine ekler. Bir tanımlayıcı sonrasında **sekmeye** basıldığında

## <a name="enter-key-behavior"></a>Anahtar davranışı girin

- ENTER 'a hiçbir şekilde yeni satır eklemeyin

   Tamamlanma listesindeki bir öğeyi seçip **ENTER** tuşuna basarak yeni bir satırın hiçbir şekilde otomatik olarak eklendiğine belirtir.

- Yalnızca tam yazılan kelimeden sonra ENTER 'a yeni satır ekle

   Tamamlanma listesindeki bir girdinin tüm karakterlerini yazıp **ENTER**' a basarsanız, otomatik olarak yeni bir satır eklenir ve imleç yeni satıra gider.

   Örneğin, yazıp ENTER `else` tuşuna basarsanız, düzenleyicide aşağıdakiler görüntülenir:

   `else`

   `|` (imleç konumu)

   Ancak, yalnızca yazıp `el` **ENTER** tuşuna basarsanız, düzenleyicide aşağıdakiler görüntülenir:

   `else|` (imleç konumu)

- ENTER 'a her zaman yeni satır ekle

   Tamamlanma listesindeki bir girdinin karakterlerinden *birini yazıp* **ENTER**' a basarsanız, otomatik olarak yeni bir satır eklenir ve imleç yeni satıra gider.

## <a name="show-name-suggestions"></a>Ad önerilerini göster

Son zamanlarda seçtiğiniz üyeler için otomatik nesne adı tamamlamayı gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense kullanma](../../ide/using-intellisense.md)
