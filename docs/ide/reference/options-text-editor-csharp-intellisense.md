---
title: Seçenekler, Metin Düzenleyici, C#, IntelliSense
description: C# için IntelliSense'in davranışını etkileyen ayarları değiştirmek üzere C# bölümündeki IntelliSense sayfasını kullanmayı öğrenin.
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
ms.openlocfilehash: 9dbb48c2d629ec4afef7a56218bf6af785540d73
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100952"
---
# <a name="options-text-editor-c-intellisense"></a>Seçenekler, Metin Düzenleyici, C#, IntelliSense

C# **için IntelliSense'in** davranışını etkileyen ayarları değiştirmek için IntelliSense seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için Araçlar **Seçenekleri'ni**  >  **ve** ardından Metin Düzenleyici   >  **C#**  >  **IntelliSense'i seçin.**

**IntelliSense seçenekleri** sayfası aşağıdaki seçenekleri içerir:

## <a name="completion-lists"></a>Tamamlama Listeleri

- Karakter yazıldıktan sonra tamamlama listesini göster*

   Bu seçenek seçildiğinde, yazmaya başladığınızda IntelliSense tamamlama listesini otomatik olarak görüntüler. Bu seçenek seçilmezse IntelliSense tamamlaması **IntelliSense** menüsünden veya **Ctrl** Tuşu tuşlarına basarak + kullanılabilir.

- Bir karakter silindikten sonra tamamlanma listesini göster

- Tamamlama listesi öğelerinin eşleşen bölümlerini vurgulama

- Tamamlanma öğesi filtrelerini gösterme

## <a name="snippets-behavior"></a>Kod parçacıklarının davranışı

- Kod parçacıklarını hiçbir zaman dahil ekleyebilirsiniz

   Bu seçenek seçildiğinde, IntelliSense hiçbir zaman tamamlama listesine C# kod parçacıkları için diğer adlar eklemez.

- Kod parçacıklarını her zaman dahil etmek

   Bu seçenek seçildiğinde, IntelliSense tamamlama listesine C# kod parçacıkları için diğer adlar ekler. Kod parçacığı diğer adı bir anahtar sözcükle aynı ise (örneğin, [sınıfı)](/dotnet/csharp/language-reference/keywords/class)anahtar sözcüğü kısayolla değiştirilir. Daha fazla bilgi için [bkz. C# Kod Parçacıkları.](../../ide/visual-csharp-code-snippets.md)

- Bir tanımlayıcıdan sonra ?-Tab yazıldıktan sonra kod parçacıkları ekleme

   Bu seçenek seçildiğinde IntelliSense, ? olduğunda tamamlama listesine C# kod parçacıkları için diğer adlar **ekler** + **Tanımlayıcıdan** sonra sekmeye basıldığında

## <a name="enter-key-behavior"></a>Anahtar davranışını girin

- Enter'a hiçbir zaman yeni satır ekleme

   Tamamlama listesinde bir öğe seçdikten ve **Enter** tuşuna baslandıktan sonra hiçbir zaman otomatik olarak yeni bir satır eklenmez.

- Tam olarak yazıldı sözcüğün sonundan sonra enter taraklarına yalnızca yeni satır ekleyin

   Tamamlama listesine bir girişin tüm karakterlerini girer ve **Enter** tuşuna bassanız otomatik olarak yeni bir satır eklenir ve imleç yeni satıra taşınır.

   Örneğin, yazın ve `else` Enter tuşuna **basın,** düzenleyicide aşağıdakiler görünür:

   `else`

   `|` (imleç konumu)

   Ancak, yalnızca yazın ve `el` **Enter** tuşuna basın; düzenleyicide aşağıdakiler görünür:

   `else|` (imleç konumu)

- Enter'da her zaman yeni satır ekle

   Tamamlama listesinde bir  giriş için karakterlerden herhangi birini yazmanız ve **Enter** tuşuna basmanız, otomatik olarak yeni bir satır eklenmiştir ve imleç yeni satıra taşınır.

## <a name="show-name-suggestions"></a>Ad önerilerini göster

Kısa süre önce seçtiğiniz üyeler için otomatik nesne adı tamamlanmasını gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense'i kullanma](../../ide/using-intellisense.md)
