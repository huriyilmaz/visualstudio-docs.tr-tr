---
title: Genel Windows Forms ve Web Forms için kültüre özgü sınıflar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c2d048387e4e81763a63b5bf010c36c87beeacf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665915"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Genel Windows Formları ve Web Formları İçin Kültüre Özgü Sınıflar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Her kültürün Tarih, saat, sayı, para birimi ve diğer bilgileri görüntülemek için farklı kuralları vardır. @No__t_0 ad alanı, <xref:System.Globalization.DateTimeFormatInfo>, **Takvim**ve <xref:System.Globalization.NumberFormatInfo> gibi kültüre özgü değerlerin nasıl görüntülendiğini değiştirmek için kullanılabilecek sınıfları içerir.

## <a name="using-the-culture-setting"></a>Kültür ayarını kullanma
 Ancak çoğu zaman, çalışma zamanında kuralları otomatik olarak belirleyebilmek ve bilgileri uygun şekilde biçimlendirmek için uygulamada veya **Bölgesel Seçenekler** denetim masasında depolanan kültür ayarını kullanırsınız. Kültürü ayarlama hakkında daha fazla bilgi için bkz. [How: Windows Forms Genelleştirme ](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) veya [How için kültür ve Kullanıcı Arabirimi kültürünü ayarlayın: ASP.NET Web sayfası Genelleştirme ](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0) için kültür ve UI kültürü ayarlayın. Kültür ayarına göre bilgileri otomatik olarak biçimlendiruygulayan sınıflar kültüre özgü olarak adlandırılır. Kültüre özgü bazı yöntemler <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName> ve <xref:System.String.Format%2A?displayProperty=fullName>. Kültüre özgü bazı işlevler (Visual Basic dilde) `MonthName` ve `WeekDayName`.

 Örneğin, aşağıdaki kod, geçerli kültürün para birimini biçimlendirmek için <xref:System.IFormattable.ToString%2A> yöntemini nasıl kullanabileceğinizi gösterir:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))

```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

 Kültür "fr-FR" olarak ayarlandıysa, çıkış penceresinde bunu görürsünüz:

 `100,00`

 Kültür "en-US" olarak ayarlanırsa, çıkış penceresinde bunu görürsünüz:

 `$100.00`

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName><xref:System.Globalization.DateTimeFormatInfo>
 <xref:System.Globalization.NumberFormatInfo>
 <xref:System.Globalization.Calendar>
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>
 <xref:System.String.Format%2A?displayProperty=fullName>
 [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)
