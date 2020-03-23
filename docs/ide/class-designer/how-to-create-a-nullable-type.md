---
title: 'Nasıl Yapılır: Boş Değer Atanabilir Tür Oluşturma (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5be8b553dfead4b8c05f29bbd18c16fcef847130
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592236"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Nasıl?

Belirli değer türlerinin her zaman tanımlanmış bir değeri yoktur (veya gereksinimi) vardır. Bu, bazı alanların herhangi bir değer atanmamış olabileceği veritabanlarında yaygın bir uygulamadır. Örneğin, henüz bir değer atanmadığını belirtmek için bir veritabanı alanına null bir değer atayabilirsiniz.

*Nullable türü,* bu tür için tipik değer aralığını ve aynı zamanda null değeri alması için uzattığınız bir değer türüdür. Örneğin, nullable `Int32`bir , ayrıca Nullable\<Int32> olarak gösterilir, -2147483648 2147483647 herhangi bir değer atanabilir, ya da bir null değer atanabilir. Nullable\<bool> değerleri `True`atanabilir `False`, veya null (hiç değer).

Nullable türleri <xref:System.Nullable%601> yapıörnekleridir. Nullable türün her örneği iki ortak salt `HasValue` `Value`okunur özelliği vardır ve:

- `HasValue`türündendir `bool` ve değişkenin tanımlı bir değer iyi pöncelip içermediğini gösterir. `True`değişkenin null olmayan bir değer içerdiği anlamına gelir. Tanımlı bir değer için örneğin `if (x.HasValue)` bir ifade `if (y != null)`kullanarak sınama yapabilirsiniz.

- `Value`altta yatan türle aynı türdendir. `HasValue` Ise, `True` `Value` anlamlı bir değer içerir. `HasValue` Ise, `False`erişim `Value` geçersiz bir işlem özel durum alacaktır.

Varsayılan olarak, bir değişkeni nullable türü olarak beyan ettiğinizde, `False`temel değer türünün varsayılan değeri dışında tanımlı bir değeri yoktur(`HasValue`

Sınıf Tasarımcısı, altta yatan türünü gösterdiği gibi boşta bir tür görüntüler.

C#'daki nullable türleri hakkında daha fazla bilgi için [Nullable Types'a](/dotnet/csharp/programming-guide/nullable-types/index)bakın. Visual Basic'teki nullable türleri hakkında daha fazla bilgi için, [Nullable Value Types'a](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)bakın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Sınıf Tasarımcısı'nı kullanarak nullable türü eklemek için

1. Sınıf diyagramında, varolan bir sınıfı genişletin veya yeni bir sınıf oluşturun.

2. Projeye sınıf eklemek için Sınıf **Diyagramı** menüsünde > **Sınıf** **Ekle'yi**tıklatın.

3. Sınıf şeklini genişletmek için **Sınıf Diyagramı** menüsünde **Genişlet'i**tıklatın.

4. Sınıf şeklini seçin. Sınıf **Diyagramı** menüsünde**Alan** **Ekle'yi** > tıklatın. Varsayılan ad **Alanı** olan yeni bir alan sınıf şeklinde ve ayrıca **Sınıf Ayrıntıları** penceresinde görünür.

5. **Sınıf Ayrıntıları** penceresinin **Ad** sütununda (veya sınıf şeklinin kendisinde), yeni alanın adını geçerli ve anlamlı bir ada değiştirin.

6. **Sınıf Ayrıntıları** penceresinin **Yazı** sütununda, aşağıdakileri belirterek türü nullable türü olarak bildirin:

    - `int?`(Görsel C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Kod Düzenleyicisi'ni kullanarak nullable türü eklemek için

1. Projeye bir sınıf ekleyin. **Çözüm Gezgini'nde**proje düğümünü seçin ve **Proje** menüsünde **Sınıf Ekle'yi**tıklatın.

2. Yeni sınıfın .cs veya .vb dosyasında, sınıf bildirimine yeni sınıfta bir veya daha fazla nullable türleri ekleyin.

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

3. Sınıf Görünümü'nden, yeni sınıf simgesini Sınıf Tasarımcısı tasarım yüzeyine sürükleyin. Sınıf diyagramında bir sınıf şekli görüntülenir.

4. Sınıf şeklinin ayrıntılarını genişletin ve fare işaretçisini sınıf üyelerinin üzerine taşıyın. Araç ipucu her üyenin bildirimini görüntüler.

5. Sınıf şekline sağ tıklayın ve **Sınıf Ayrıntıları'nı**tıklatın. **Sınıf Ayrıntıları** penceresinde yeni türün özelliklerini görüntüleyebilir veya değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [Boş Değer Atanabilir Tipler](/dotnet/csharp/programming-guide/nullable-types/index)
- [Nullable Türleri Kullanma](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Nasıl yapılır: Boş Değer Atanabilir Tipi Tanımlama](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Boş Değer Atanabilen Değer Türleri](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
