---
title: 'Nasıl Yapılır: Sınıfı Kısmi Sınıflara Bölme (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 48672e2d316828019ede7097306517b270062327
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588687"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Nasıl yapilir: Sınıf Tasarımcısı'nda bir sınıfı kısmi sınıflara bölme

Bir sınıfın `partial` veya yapının bildirimini birkaç bildirim arasında bölmek için (Visual`Partial` Basic'te) anahtar sözcüğünün kullanılması gerekir. İstediğiniz kadar kısmi bildirim kullanabilirsiniz.

Bildirimler bir veya birden çok kaynak dosyada olabilir. Tüm bildirimler aynı derleme ve aynı ad alanında olmalıdır.

Kısmi sınıflar çeşitli durumlarda yararlıdır. Örneğin, büyük bir projede, bir sınıfı birden çok dosyaya ayırmak, birden fazla programcının proje üzerinde aynı anda çalışmasını sağlar. Visual Studio'nun oluşturduğu kodla çalışırken, kaynak dosyayı yeniden oluşturmak zorunda kalmadan sınıfı değiştirebilirsiniz. (Visual Studio'nun oluşturduğu kod örnekleri arasında Windows Formları ve web hizmeti paketleyici kodu verilebilir.) Böylece Visual Studio'nun oluşturduğu dosyayı değiştirmek zorunda kalmadan otomatik olarak oluşturulan sınıfları kullanan kod oluşturabilirsiniz.

İki tür kısmi yöntem vardır. C#'da beyan ve uygulama olarak adlandırılırlar; Visual Basic'te bildirim ve uygulama olarak adlandırılır.

**Sınıf Tasarımcısı** kısmi sınıfları ve yöntemleri destekler. Sınıf diyagramındaki tür şekli, kısmi sınıf için tek bir bildirim konumu anlamına gelir. Kısmi sınıf birden çok dosyada tanımlanmışsa, **Özellikler** penceresinde **Yeni Üye Konumu** özelliğini ayarlayarak Sınıf **Tasarımcısı'nın** hangi bildirim konumunu kullanacağını belirtebilirsiniz. Diğer bir de, bir sınıf şeklini çift tıklattığınızda, **Sınıf Tasarımcısı** Yeni **Üye Konumu** özelliği tarafından tanımlanan sınıf bildirimini içeren kaynak dosyaya gider. Bir sınıf şeklinde kısmi bir yöntemi çift tıklattığınızda, **Sınıf Tasarımcısı** kısmi yöntem bildirimine gider. Ayrıca, **Özellikler** penceresinde, **Dosya Adı** özelliği bildirim konumuna başvurur. Kısmi sınıflar için **Dosya Adı,** o sınıfın bildirim ve uygulama kodu içeren tüm dosyaları listeler. Ancak, kısmi yöntemler için **Dosya Adı** yalnızca kısmi yöntem bildirimini içeren dosyayı listeler.

Aşağıdaki örnekler, sınıf `Employee` tanımını her biri farklı bir yordam tanımlayan iki bildirime böler. Örneklerdeki iki kısmi tanım bir kaynak dosyada veya iki farklı kaynak dosyasında olabilir.

> [!NOTE]
> Visual Basic, Visual Studio tarafından oluşturulan kodu kullanıcı tarafından yazılmış koddan ayırmak için kısmi sınıf tanımları kullanır. Kod ayrı kaynak dosyalarına ayrılır. Örneğin, **Windows Form Tasarımcısı** gibi `Form`denetimler için kısmi sınıflar tanımlar. Bu denetimlerde oluşturulan kodu değiştirmemelisiniz.

Visual Basic'teki kısmi türler hakkında daha fazla bilgi için Bkz. [Kısmi.](/dotnet/visual-basic/language-reference/modifiers/partial)

## <a name="example"></a>Örnek

Bir sınıf tanımını `partial` bölmek için,`Partial` aşağıdaki örnekte gösterildiği gibi anahtar sözcüğü (Visual Basic'te) kullanın:

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
- [kısmi (Tür) (C# Referans)](/dotnet/csharp/language-reference/keywords/partial-type)
- [kısmi (Yöntem) (C# Referans)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Kısmi (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
