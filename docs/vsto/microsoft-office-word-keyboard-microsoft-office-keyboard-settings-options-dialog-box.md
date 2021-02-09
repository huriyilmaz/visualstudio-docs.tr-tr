---
title: Office Word Klavyesi, ayarlar, Seçenekler iletişim kutusu
description: Belge odaklanıldığında, dinamik klavye düzeni seçerek Microsoft Word 'Ün kısayol tuşu komutlarını nasıl alacağını öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0138fcd73ddf07202a9111ec2b3d17dcc0fb7a0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879429"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Microsoft Office sözcük klavyesi, ayarlar, Seçenekler iletişim kutusu
  Microsoft Office Word ve Visual Studio kısayol tuşlarını her ikisi de işler. Aynı kısayol tuşu birleşimi Word ve Visual Studio 'daki farklı komutlar için de kullanılabilir. Word, Visual Studio 'da belge düzeyindeki bir projede açıldığında, kısayol tuşu komutlarını yalnızca bir seferde tek bir uygulama alır. Varsayılan olarak, Visual Studio tüm kısayol tuşu komutlarını alır, ancak belge odaklanıldığında, **dinamik klavye düzeni** seçerek Word 'ün bunları almasını sağlayabilirsiniz.

 Şu anda kısayol tuşlarını işleyen uygulamada bir komuta atanmamış bir kısayol tuşu kullanırsanız, kısayol tuşu diğer uygulamaya geçirilir.

 Seçtiğiniz seçenek, siz değiştirene kadar Word projeleri için geçerli olmaya devam edecektir. Seçim Excel projelerini Microsoft Office etkilemez; Excel 'de Microsoft Office Excel klavye seçeneklerini kullanarak herhangi bir değişiklik yapmanız gerekir.

## <a name="uielement-list"></a>UIElement listesi
 **Visual Studio klavye düzeni** Word belgesi odağa sahip olsa bile, Visual Studio tüm kısayol tuşu komutlarını alır. Örneğin, belge odaklanmışken **F5** işlev tuşuna basarsanız, Visual Studio çözümünüzün hata ayıklamasını başlatır.

 **Dinamik klavye düzeni** Visual Studio yalnızca odağa sahip olduğunda kısayol tuşu komutlarını alır. Word belgesi odağa sahip olduğunda, Word tüm kısayol tuşu komutlarını alır. Örneğin, Word belgesi odağa sahip iken **F5** işlev tuşuna basarsanız, sözcük **Bul ve Değiştir** iletişim kutusunu seçili **Git** sekmesi ile açar. Visual Studio odaklandığında **F5** tuşuna basarsanız, Visual Studio çözümünüzün hata ayıklamasını başlatır.

## <a name="see-also"></a>Ayrıca bkz.
- [Microsoft Office Excel klavye, Microsoft Office Klavye ayarları, Seçenekler iletişim kutusu](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
