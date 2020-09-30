---
title: Office Excel Klavyesi, ayarlar, Seçenekler iletişim kutusu
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b590f82d5f28c3a71e86e18dfe16b1c3e6c4c5a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584522"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel Klavyesi, ayarlar, Seçenekler iletişim kutusu
  Excel ve Visual Studio 'Nun her ikisi de kısayol tuşlarını işler. Microsoft Office Aynı kısayol tuşu birleşimi Excel ve Visual Studio 'daki farklı komutlar için de kullanılabilir. Excel, Visual Studio 'daki belge düzeyi bir projede açıldığında, kısayol tuşu komutlarını yalnızca bir seferde tek bir uygulama alır. Varsayılan olarak, Visual Studio tüm kısayol tuşu komutlarını alır, ancak belge odağa sahip olduğunda, **dinamik klavye düzeni**seçerek Excel 'in bunları almasını sağlayabilirsiniz.

 Şu anda kısayol tuşlarını işleyen uygulamada bir komuta atanmamış bir kısayol tuşu kullanırsanız, kısayol tuşu diğer uygulamaya geçirilir.

 Seçtiğiniz seçenek, siz değiştirene kadar Excel projeleri için geçerli olmaya devam edecektir. Seçim Word projelerini Microsoft Office etkilemez; Word için Microsoft Office sözcük klavye seçeneklerini kullanarak herhangi bir değişiklik yapmanız gerekir.

## <a name="uielement-list"></a>UIElement listesi
 **Visual Studio klavye düzeni** Excel odağa sahip olsa bile, Visual Studio tüm kısayol tuşu komutlarını alır. Örneğin, Excel odağa sahip olduğunda **F5** işlev tuşuna basarsanız, Visual Studio çözümünüzün hata ayıklamasını başlatır.

 **Dinamik klavye düzeni** Visual Studio yalnızca odağa sahip olduğunda kısayol tuşu komutlarını alır. Excel odağa sahip olduğunda, Excel tüm kısayol tuşu komutlarını alır. Örneğin, Excel odağa sahip olduğunda **F5** işlev tuşuna basarsanız, Excel **şuraya git** iletişim kutusunu açar. Visual Studio odaklandığında **F5** tuşuna basarsanız, Visual Studio çözümünüzün hata ayıklamasını başlatır.

## <a name="see-also"></a>Ayrıca bkz.
- [Microsoft Office Word klavye, Microsoft Office Klavye ayarları, Seçenekler iletişim kutusu](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
