---
title: 'Nasıl Yapılır: Boş Değer Atanabilir Tür Oluşturma (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 671b2230daafbbdf92edda2ba1a671b688723796
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647852"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı null yapılabilir bir tür oluşturma

Belirli değer türlerinde her zaman tanımlı bir değer yoktur (veya gerekli değildir). Bu, veritabanlarında yaygın bir uygulamadır ve bazı alanlara hiçbir değer atanmayabilir. Örneğin, henüz bir değer atanmadığını belirtmek için bir veritabanı alanına null değer atayabilirsiniz.

Null *yapılabilir bir tür* , genişlettiğinizi, bu tür için tipik değer aralığını ve aynı zamanda null bir değer olacak şekilde genişlettiğinizi belirten bir değer türüdür. Örneğin, null yapılabilir \<Int32 > olarak da bilinen null olabilen `Int32`,-2147483648 ile 2147483647 arasında herhangi bir değer atanabilir veya null bir değer atanabilir. Null yapılabilir \<bool > `True`, `False` veya null değerler atanabilir (hiç bir değer yoktur).

Null yapılabilir türler <xref:System.Nullable%601> yapısının örnekleridir. Null yapılabilir bir türdeki her bir örnek, `HasValue` ve `Value` iki ortak salt okunurdur.

- `HasValue` `bool` türündedir ve değişkenin tanımlanmış bir değer içerip içermediğini gösterir. `True`, değişkenin null olmayan bir değer içerdiği anlamına gelir. @No__t_0 veya `if (y != null)` gibi bir ifade kullanarak tanımlanmış bir değer için test edebilirsiniz.

- `Value`, temel alınan türle aynı türde. @No__t_0 `True`, `Value` anlamlı bir değer içerir. @No__t_0 `False`, `Value` erişimi geçersiz bir işlem özel durumu oluşturur.

Varsayılan olarak, bir değişkeni null yapılabilir bir tür olarak bildirdiğinizde, temel alınan değer türünün varsayılan değeri dışında tanımlı bir değer (`HasValue` `False`) yoktur.

Sınıf Tasarımcısı, temel alınan türünü gösterdiği gibi, null yapılabilir bir tür görüntüler.

İçindeki C#null yapılabilir türler hakkında daha fazla bilgi için bkz. [Nullable türler](/dotnet/csharp/programming-guide/nullable-types/index). Visual Basic null yapılabilir türler hakkında daha fazla bilgi için bkz. [Nullable değer türleri](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Sınıf Tasarımcısı kullanarak null yapılabilir bir tür eklemek için

1. Sınıf diyagramında, varolan bir sınıfı genişletin veya yeni bir sınıf oluşturun.

2. Projeye bir sınıf eklemek için **sınıf diyagramı** menüsünde **Ekle**  > **sınıf**Ekle ' ye tıklayın.

3. Sınıf şeklini genişletmek için, **sınıf diyagramı** menüsünde **Genişlet**' e tıklayın.

4. Sınıf şeklini seçin. **Sınıf diyagramı** menüsünde  > **alanı** **Ekle** ' ye tıklayın. Varsayılan ad **alanı** olan yeni bir alan sınıf şeklinde ve ayrıca **Sınıf Ayrıntıları** penceresinde görünür.

5. **Sınıf Ayrıntıları** penceresinin (veya sınıf şeklinin kendisinde) **ad** sütununda, yeni alanın adını geçerli ve anlamlı bir adla değiştirin.

6. **Sınıf Ayrıntıları** penceresinin **tür** sütununda, aşağıdakini belirterek türü null yapılabilir bir tür olarak bildirin:

    - `int?` (görsel C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Kod düzenleyicisini kullanarak null yapılabilir bir tür eklemek için

1. Projeye bir sınıf ekleyin. **Çözüm Gezgini**' de proje düğümünü seçin ve **Proje** menüsünde **Sınıf Ekle**' ye tıklayın.

2. Yeni sınıfa ait. cs veya. vb dosyasında, sınıf bildirimine yeni sınıfta bir veya daha fazla null yapılabilir tür ekleyin.

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

3. Sınıf Görünümü yeni sınıf simgesini Sınıf Tasarımcısı tasarım yüzeyine sürükleyin. Sınıf şekli sınıf diyagramında görüntülenir.

4. Sınıf şeklinin ayrıntılarını genişletin ve fare işaretçisini sınıf üyelerinin üzerine taşıyın. Araç ipucu her üyenin bildirimini görüntüler.

5. Sınıf şekline sağ tıklayın ve **Sınıf Ayrıntıları**' na tıklayın. **Sınıf Ayrıntıları** penceresinde yeni türün özelliklerini görüntüleyebilir veya değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [Boş Değer Atanabilir Tipler](/dotnet/csharp/programming-guide/nullable-types/index)
- [Boş Değer Atanabilir Tipleri Kullanma](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Nasıl yapılır: Boş Değer Atanabilir Tipi Tanımlama](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Boş Değer Atanabilen Değer Türleri](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
