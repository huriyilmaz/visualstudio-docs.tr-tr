---
title: 'Nasıl yapılır: null yapılabilir bir tür oluşturma (Sınıf Tasarımcısı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 438f84a172c7e0a2d0dc957c578adc568a46495f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668152"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Nasıl Yapılır: Boş Değer Atanabilir Tür Oluşturma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli değer türlerinde her zaman tanımlı bir değer yoktur (veya gerekli değildir). Bu, veritabanlarında yaygın bir uygulamadır ve bazı alanlara hiçbir değer atanmayabilir. Örneğin, henüz bir değer atanmadığını belirtmek için bir veritabanı alanına null değer atayabilirsiniz.

 Null *yapılabilir bir tür* , genişlettiğinizi, bu tür için tipik değer aralığını ve aynı zamanda null bir değer olacak şekilde genişlettiğinizi belirten bir değer türüdür. Örneğin, null yapılabilir \<Int32 > olarak da bilinen null olabilen `Int32`,-2147483648 ile 2147483647 arasında herhangi bir değer atanabilir veya null bir değer atanabilir. Null yapılabilir \<bool > `True`, `False` veya null değerler atanabilir (hiç bir değer yoktur).

 Null yapılabilir türler <xref:System.Nullable%601> yapısının örnekleridir. Null yapılabilir bir türdeki her bir örnek, `HasValue` ve `Value` iki ortak salt okunurdur.

- `HasValue` `bool` türündedir ve değişkenin tanımlanmış bir değer içerip içermediğini gösterir. `True`, değişkenin null olmayan bir değer içerdiği anlamına gelir. @No__t_0 veya `if (y != null)` gibi bir ifade kullanarak tanımlanmış bir değer için test edebilirsiniz.

- `Value`, temel alınan türle aynı türde. @No__t_0 `True`, `Value` anlamlı bir değer içerir. @No__t_0 `False`, `Value` erişimi geçersiz bir işlem özel durumu oluşturur.

  Varsayılan olarak, bir değişkeni null yapılabilir bir tür olarak bildirdiğinizde, temel alınan değer türünün varsayılan değeri dışında tanımlı bir değer (`HasValue` `False`) yoktur.

  Sınıf Tasarımcısı, temel alınan türünü gösterdiği gibi, null yapılabilir bir tür görüntüler.

  Görsel C#olarak null yapılabilir türler hakkında daha fazla bilgi için bkz. [Nullable türler](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Visual Basic null yapılabilir türler hakkında daha fazla bilgi için bkz. [Nullable değer türleri](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Sınıf Tasarımcısı kullanarak null yapılabilir bir tür eklemek için

1. Sınıf diyagramında, varolan bir sınıfı genişletin veya yeni bir sınıf oluşturun.

2. Projeye bir sınıf eklemek için, **sınıf diyagramı** menüsünde **Ekle**' ye ve ardından **Sınıf Ekle**' ye tıklayın.

3. Sınıf şeklini genişletmek için, **sınıf diyagramı** menüsünde **Genişlet**' e tıklayın.

4. Sınıf şeklini seçin. **Sınıf diyagramı** menüsünde, **Ekle**' ye ve ardından **alan**' a tıklayın. Varsayılan ad **alanı** olan yeni bir alan sınıf şeklinde ve ayrıca **Sınıf Ayrıntıları** penceresinde görünür.

5. **Sınıf Ayrıntıları** penceresinin (veya sınıf şeklinin kendisinde) **ad** sütununda, yeni alanın adını geçerli ve anlamlı bir adla değiştirin.

6. **Sınıf Ayrıntıları** penceresinin **tür** sütununda, aşağıdaki kodda gösterildiği gibi türü null yapılabilir bir tür olarak bildirin:

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

### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Kod düzenleyicisini kullanarak null yapılabilir bir tür eklemek için

1. Projeye bir sınıf ekleyin. **Çözüm Gezgini**' de proje düğümünü seçin ve **Proje** menüsünde **Sınıf Ekle**' ye tıklayın.

2. Yeni sınıfa ait. cs veya. vb dosyasında, sınıf bildirimine yeni sınıfta bir veya daha fazla null yapılabilir tür ekleyin.

3. Sınıf Görünümü yeni sınıf simgesini Sınıf Tasarımcısı tasarım yüzeyine sürükleyin. Sınıf şekli sınıf diyagramında görüntülenir.

4. Sınıf şeklinin ayrıntılarını genişletin ve fare işaretçisini sınıf üyelerinin üzerine taşıyın. Araç ipucu her üyenin bildirimini görüntüler.

5. Sınıf şekline sağ tıklayın ve **Sınıf Ayrıntıları**' na tıklayın. **Sınıf Ayrıntıları** penceresinde yeni türün özelliklerini görüntüleyebilir veya değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 Nullable [türler kullanarak](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28) [null yapılabilir türler](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6) <xref:System.Nullable%601> [nasıl yapılır: null yapılabilir tür](https://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387) [Nullable değer türlerini](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6) belirleme
