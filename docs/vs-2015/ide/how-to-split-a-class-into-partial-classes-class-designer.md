---
title: 'Nasıl yapılır: sınıfı kısmi sınıflara bölme (Sınıf Tasarımcısı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e93ebc58e4e9b6092921e4155fe3d821bb552c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670711"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Nasıl Yapılır: Sınıfı Kısmi Sınıflara Bölme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Basic `Partial` anahtar sözcüğünü veya Visual C#'teki `partial` anahtar sözcüğünü kullanarak bir sınıfın veya yapının bildirimini birkaç bildirim arasında ayırabilirsiniz. İstediğiniz kadar çok sayıda kısmi bildirim, istediğiniz sayıda farklı kaynak dosyada veya bir kaynak dosyasında kullanabilirsiniz. Ancak, tüm bildirimlerin aynı derlemede ve aynı ad alanında olması gerekir.

 Kısmi sınıflar çeşitli durumlarda faydalıdır. Örneğin, büyük projeler üzerinde çalışırken, bir sınıfı birden fazla dosyaya ayırmak, birden fazla programcının aynı anda üzerinde çalışmasını sağlar. Visual Studio 'Nun oluşturduğu kodla çalışırken, kaynak dosyayı yeniden oluşturmaya gerek kalmadan sınıfı değiştirebilirsiniz. (Visual Studio 'Nun oluşturduğu kod örnekleri Windows Forms ve Web hizmeti sarmalayıcı kodu içerir.) Bu nedenle, Visual Studio 'Nun oluşturduğu dosyayı değiştirmek zorunda kalmadan otomatik olarak oluşturulan sınıflar kullanan kod oluşturabilirsiniz.

 İki tür kısmi yöntem vardır. Görsel C#olarak, bunlar bildirme ve uygulama olarak adlandırılır; Visual Basic, bildirim ve uygulama olarak adlandırılırlar.

 Sınıf Tasarımcısı kısmi sınıfları ve yöntemleri destekler. Sınıf diyagramındaki tür şekli, kısmi sınıf için tek bir bildirim konumuna başvurur. Kısmi sınıf birden çok dosyada tanımlanmışsa, **Özellikler** penceresinde **yeni üye konumu** özelliğini ayarlayarak hangi bildirim konumunun Sınıf Tasarımcısı kullanacağınızı belirtebilirsiniz. Diğer bir deyişle, bir sınıf şekline çift tıkladığınızda Sınıf Tasarımcısı **yeni üye konumu** özelliği tarafından tanımlanan sınıf bildirimini içeren kaynak dosyaya gider. Bir sınıf şeklinin içindeki kısmi bir yönteme çift tıkladığınızda Sınıf Tasarımcısı kısmi Yöntem bildirimine gider. Ayrıca, **Özellikler** penceresinde, **dosya adı** özelliği bildirim konumunu ifade eder. Kısmi sınıflar için **dosya adı** , bu sınıf için bildirim ve uygulama kodu içeren tüm dosyaları listeler. Ancak, kısmi yöntemler için **dosya adı** yalnızca kısmi Yöntem bildirimini içeren dosyayı listeler.

 Aşağıdaki örnekler, her biri farklı bir yordam tanımlayan `Employee` sınıfının tanımını iki bildirime ayırır. Örneklerdeki iki kısmi Tanım, bir kaynak dosyasında veya iki farklı kaynak dosyada olabilir.

> [!NOTE]
> Visual Basic, Kullanıcı tarafından yazılan koddan oluşturulan kodu Visual Studio 'Yu ayırmak için kısmi sınıf tanımları kullanır. Kod ayrı kaynak dosyalarına ayrılmıştır. Örneğin, **Windows form tasarımcısı** `Form` gibi denetimler için kısmi sınıfları tanımlar. Bu denetimlerde oluşturulan kodu değiştirmemelisiniz.

 Visual Basic kısmi türleri hakkında daha fazla bilgi için bkz. [kısmi](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).

## <a name="example"></a>Örnek
 Visual Basic bir sınıf tanımını ayırmak için, aşağıdaki örnekte gösterildiği gibi `Partial` anahtar sözcüğünü kullanın.

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="example"></a>Örnek
 Bir sınıf tanımını görselde C#ayırmak için, aşağıdaki örnekte gösterildiği gibi `partial` anahtar sözcüğünü kullanın.

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Kısmi sınıflar ve Yöntemler](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [kısmi (tür)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334) kısmi ( [Yöntem) (C# başvuru)](https://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137) [kısmi](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
