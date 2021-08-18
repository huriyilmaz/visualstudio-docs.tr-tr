---
title: Sınıfı kısmi sınıflara bölme
description: Bir sınıfın veya yapının bildirimini bir sınıf içinde çeşitli bildirimlere bölmek için Partial anahtar sözcüğünün nasıl Sınıf Tasarımcısı.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4dd3fa82e4309ed5a6aacd1f8218737f9db2db9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034532"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Nasıl Sınıf Tasarımcısı

Bir sınıfın veya yapının bildirimini birkaç bildirim arasında bölmek için anahtar sözcüğünü `partial` (Visual Basic `Partial` içinde) kullanabilirsiniz. Istediğiniz kadar çok kısmi bildirim kullanabilirsiniz.

Bildirim bir veya birden çok kaynak dosyada olabilir. Tüm bildirimlerin aynı derlemede ve aynı ad alanı içinde olması gerekir.

Kısmi sınıflar çeşitli durumlarda yararlıdır. Örneğin büyük bir projede bir sınıfı birden çok dosyaya ayırmak, birden fazla programcının aynı anda proje üzerinde çalışmasına olanak sağlar. Oluşturulan kodla çalışırken Visual Studio yeniden oluşturmak zorunda kalmadan sınıfı değiştirebilirsiniz. (Formlar ve web Visual Studio sarmalayıcı kodu Windows kod örnekleridir.) Bu nedenle, otomatik olarak oluşturulan sınıfları kullanan bir kod oluşturabilirsiniz ve bu sınıfların oluşturduğu dosyayı değiştirmek Visual Studio oluşturabilirsiniz.

İki tür kısmi yöntem vardır. C# ile bildirim ve uygulama olarak adlandırılan bu çağrılar; bu Visual Basic bildirim ve uygulama olarak adlandırılan bir uygulamadır.

**Sınıf Tasarımcısı** kısmi sınıfları ve yöntemleri destekler. Sınıf diyagramında tür şekli, kısmi sınıf için tek bir bildirim konumunu ifade eder. Kısmi sınıf birden çok dosyada tanımlanmışsa, Özellikler penceresinde **Yeni Üye Sınıf Tasarımcısı**  özelliğini ayarerek hangi bildirim konumunun **kullanmayacaklarını belirtebilirsiniz.** Başka bir ifadeyle, bir sınıf  şekline çift Sınıf Tasarımcısı, Yeni Üye Konumu özelliği tarafından tanımlanan sınıf bildirimini içeren kaynak **dosyaya** gider. Sınıf şeklinde kısmi bir yönteme çift tıklarken, **Sınıf Tasarımcısı** yöntem bildirimine gider. Ayrıca, **Özellikler penceresinde** Dosya **Adı özelliği** bildirim konumunu ifade eder. Kısmi sınıflar için Dosya **Adı,** o sınıfın bildirim ve uygulama kodunu içeren tüm dosyaları listeler. Ancak, kısmi yöntemler için Dosya **Adı** yalnızca kısmi yöntem bildirimini içeren dosyayı listeler.

Aşağıdaki örnekler, sınıfının tanımını her `Employee` biri farklı bir yordam tanımlayan iki bildirime böler. Örneklerde yer alan iki kısmi tanım, bir kaynak dosyada veya iki farklı kaynak dosyada olabilir.

> [!NOTE]
> Visual Basic tarafından oluşturulan kodu kullanıcı tarafından Visual Studio ayırmak için kısmi sınıf tanımları kullanır. Kod, ayrık kaynak dosyalarına ayrılır. Örneğin, **form Windows gibi denetimler** için kısmi sınıflar `Form` tanımlar. Bu denetimlerde oluşturulan kodu değiştirmeyebilirsiniz.

Veri verilerinde kısmi türler hakkında daha fazla Visual Basic bkz. [Kısmi](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Örnek

Bir sınıf tanımını bölmek için, aşağıdaki `partial` örnekte gösterildiği Visual Basic () anahtar `Partial` sözcüğünü kullanın:

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

## <a name="see-also"></a>Ayrıca bkz.

- [Kısmi sınıflar ve yöntemler](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (Tür) (C# Başvurusu)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial (Yöntem) (C# Başvurusu)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Kısmi (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
