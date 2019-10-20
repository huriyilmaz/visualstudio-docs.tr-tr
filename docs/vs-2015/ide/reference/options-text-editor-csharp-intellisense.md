---
title: Seçenekler, metin düzenleyici, C#, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662292"
---
# <a name="options-text-editor-c-intellisense"></a>Seçenekler, Metin Düzenleyici, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IntelliSense 'in görsel C#için davranışını etkileyen ayarları değiştirmek için IntelliSense özellik sayfasını kullanın. **IntelliSense** Özellik sayfasına, **Araçlar** menüsünde **C#** **Seçenekler** ' i ve ardından **metin düzenleyici** klasörü ' ne tıklayıp IntelliSense ' e tıklayarak erişebilirsiniz **.**

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **IntelliSense** Özellik sayfası aşağıdaki özellikleri içerir:

## <a name="completion-lists"></a>Tamamlanma listeleri
 **Bir karakter yazıldıktan sonra tamamlanma listesini göster** Bu seçenek belirlendiğinde, yazmaya başladığınızda IntelliSense, tamamlanma listesini otomatik olarak görüntüler. Bu seçenek seçili olmadığında, IntelliSense tamamlanmasında **IntelliSense** menüsünde veya Ctrl + Space tuşlarına basarak yine de kullanılabilir.

 **Anahtar sözcükleri tamamlanma listelerine yerleştir** Bu seçenek belirlendiğinde, IntelliSense, örneğin, C# bir [sınıf](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690)gibi anahtar sözcükleri tamamlama listesine ekler.

 **Kod parçacıklarını tamamlama listelerine yerleştir** Bu seçenek belirlendiğinde, IntelliSense, kod parçacıkları için C# tamamlama listesine diğer adlar ekler. Kod parçacığı diğer adının bir anahtar sözcükle aynı olduğu durumda (örneğin, [sınıfı](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690)), anahtar sözcüğü kısayol ile değiştirilmiştir. Daha fazla bilgi için bkz [. C# görsel kod parçacıkları](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Tamamlanma listelerinde seçim
 **Aşağıdaki karakterler yazılarak işlendi:** Tüm seçili öğe için IntelliSense otomatik tamamlamayı, bu değerler yazıldıktan sonra çalıştıran tüm karakterleri belirtir.

 **Boşluk çubuğuna basılarak kararlıdır** Tamamlanma listesindeki seçili öğe için IntelliSense otomatik tamamlamayı yürütmek üzere boşluk çubuğuna basmak için eylemin ekleneceğini belirtir.

 **Tam yazılmış kelimenin sonunda ENTER 'a yeni satır ekle** Tamamlama listesindeki bir girdinin tüm karakterlerini yazıp ENTER tuşuna basarsanız, otomatik olarak yeni bir satır oluşturulur ve imleç yeni satıra gider.

 Örneğin, `else` yazıp ENTER tuşuna basarsanız, düzenleyicide aşağıdakiler görüntülenir:

 `else`

 `|` (imleç konumu)

 Ancak, yalnızca `el` yazıp ENTER tuşuna basarsanız, düzenleyicide aşağıdakiler görüntülenir:

 `else|` (imleç konumu)

## <a name="intellisense-member-selection"></a>IntelliSense üye seçimi
 **En son kullanılan üyeyi önceden seçer** Bu seçenek belirlendiğinde, IntelliSense, tümleşik geliştirme ortamında (IDE) geçerli oturumunuz sırasında otomatik nesne adı tamamlama için açılan liste üyeleri kutusunda son zamanlarda seçtiğiniz üyeleri önceden seçer. En son kullanılan üyelerin geçmişi, IDE içindeki her oturum arasında temizlenir. Daha fazla bilgi için bkz. [en son kullanılan Üyeler Için IntelliSense](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [IntelliSense kullanarak](../../ide/using-intellisense.md) [Genel, ortam, Seçenekler Iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md) [XML belgeleri açıklamaları](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)
