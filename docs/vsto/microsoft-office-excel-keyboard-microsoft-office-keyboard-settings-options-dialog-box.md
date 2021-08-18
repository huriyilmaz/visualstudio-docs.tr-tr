---
title: Office Excel klavye, Ayarlar, seçenekler iletişim kutusu
description: belge odak edildiğinde dinamik klavye düzeni seçerek kısayol tuşu komutlarının nasıl Microsoft Excel alabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d33811c8b5fc38359e59a1ff2708ba05d2f2f1d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115089"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel klavye, Ayarlar, seçenekler iletişim kutusu
  Microsoft Office Excel ve Visual Studio her ikisi de kısayol tuşlarını işler. aynı kısayol tuşu birleşimi Excel ve Visual Studio farklı komutlar için de kullanılabilir. Excel belge düzeyindeki bir projede Visual Studio açıldığında, kısayol tuşu komutlarını yalnızca tek seferde bir uygulama alır. varsayılan olarak, Visual Studio tüm kısayol tuşu komutlarını alır, ancak belge odağa sahip olduğunda **dinamik klavye düzeni** seçerek Excel alabilir.

 Şu anda kısayol tuşlarını işleyen uygulamada bir komuta atanmamış bir kısayol tuşu kullanırsanız, kısayol tuşu diğer uygulamaya geçirilir.

 seçtiğiniz seçenek, siz değiştirene kadar Excel projeler için geçerli olmaya devam edecektir. seçim Word projelerini Microsoft Office etkilemez; word için Microsoft Office sözcük klavye seçeneklerini kullanarak herhangi bir değişiklik yapmanız gerekir.

## <a name="uielement-list"></a>UIElement listesi
 **Visual Studio klavye düzeni** Visual Studio, Excel odağa sahip olsa bile tüm kısayol tuşu komutlarını alır. örneğin, Excel odaklandığında **F5** işlev tuşuna basarsanız Visual Studio çözümünüzde hata ayıklamaya başlar.

 **dinamik klavye düzeni** Visual Studio, yalnızca odak olduğunda kısayol tuşu komutlarını alır. Excel odağa sahip olduğunda, Excel tüm kısayol tuşu komutlarını alır. örneğin, Excel odak olduğunda **F5** işlev tuşuna basarsanız, Excel **git** iletişim kutusunu açar. Visual Studio odaklandığında **F5** tuşuna basarsanız Visual Studio çözümünüzde hata ayıklamaya başlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Microsoft Office Word klavye, Microsoft Office klavye Ayarlar, seçenekler iletişim kutusu](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
