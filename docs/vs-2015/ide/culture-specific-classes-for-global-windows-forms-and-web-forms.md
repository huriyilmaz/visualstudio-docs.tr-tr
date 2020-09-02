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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665915"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Genel Windows Formları ve Web Formları İçin Kültüre Özgü Sınıflar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Her kültürün Tarih, saat, sayı, para birimi ve diğer bilgileri görüntülemek için farklı kuralları vardır. <xref:System.Globalization>Ad alanı <xref:System.Globalization.DateTimeFormatInfo> ,,, ve **gibi**kültüre özgü değerlerin görüntülenme şeklini değiştirmek için kullanılabilecek sınıfları içerir <xref:System.Globalization.NumberFormatInfo> .

## <a name="using-the-culture-setting"></a>Kültür ayarını kullanma
 Ancak çoğu zaman, çalışma zamanında kuralları otomatik olarak belirleyebilmek ve bilgileri uygun şekilde biçimlendirmek için uygulamada veya **Bölgesel Seçenekler** denetim masasında depolanan kültür ayarını kullanırsınız. Kültürü ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Kültür ve Kullanıcı Arabirimi kültürünü Windows Forms Genelleştirme Için ayarlama](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) veya [nasıl yapılır: ASP.NET Web sayfası Genelleştirme için kültürü ve Kullanıcı Arabirimi kültürünü ayarlama](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). Kültür ayarına göre bilgileri otomatik olarak biçimlendiruygulayan sınıflar kültüre özgü olarak adlandırılır. Kültüre özgü bazı yöntemler <xref:System.IFormattable.ToString%2A?displayProperty=fullName> , ve ' dir <xref:System.Console.WriteLine%2A?displayProperty=fullName> <xref:System.String.Format%2A?displayProperty=fullName> . Kültüre özgü bazı işlevler (Visual Basic dilinde) `MonthName` ve ' dir `WeekDayName` .

 Örneğin, aşağıdaki kod, <xref:System.IFormattable.ToString%2A> geçerli kültürün para birimini biçimlendirmek için yöntemini nasıl kullanabileceğinizi gösterir:

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
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName> <xref:System.Globalization.DateTimeFormatInfo>
 <xref:System.Globalization.NumberFormatInfo>
 <xref:System.Globalization.Calendar>
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>
 <xref:System.String.Format%2A?displayProperty=fullName>
 [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)
