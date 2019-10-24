---
title: LINQ hata ayıklama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 256dadfeea4108f12e24864017b6e1752ece25a5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738199"
---
# <a name="debugging-linq"></a>LINQ'de Hata Ayıklama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dil ile tümleşik sorgu (LINQ) kodunda hata ayıklamayı destekler, bazı sınırlamalar vardır. Çoğu hata ayıklama özelliğinin adım adım, kesme noktaları ayarlama ve sonuçları hata ayıklayıcı penceresinde görüntüleme dahil olmak üzere LINQ deyimleriyle birlikte çalışır. Bu konu, LINQ hata ayıklamanın başlıca sınırlamalarını açıklamaktadır.

## <a name="BKMK_ViewingLINQResults"></a>LINQ sonuçlarını görüntüleme
 DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak bir LINQ deyimin sonucunu görüntüleyebilirsiniz. Kaynak penceresi kullandığınızda, kaynak penceredeki bir sorgu üzerindeki işaretçiyi duraklatabilir ve bir DataTip belirir. Bir LINQ değişkenini kopyalayabilir ve izleme penceresi veya QuickWatch iletişim kutusuna yapıştırabilirsiniz.

 LINQ içinde, bir sorgu oluşturulduğunda veya bildirildiğinde, ancak yalnızca sorgu kullanıldığında değerlendirilmez. Bu nedenle, sorgu değerlendirilene kadar bir değere sahip değildir. Sorgu oluşturma ve değerlendirme hakkında tam bir açıklama için bkz. [LINQ Sorgularına GirişC#()](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) veya [ilk LINQ sorgunuzu yazma](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).

 Bir sorgunun sonucunu göstermek için, hata ayıklayıcı tarafından değerlendirilmelidir. Hata ayıklayıcıda bir LINQ sorgu sonucu görüntülediğinizde oluşan bu örtük değerlendirme, dikkate almanız gereken bazı etkilere sahiptir:

- Sorgunun her değerlendirmesi zaman alır. Sonuçlar düğümünü genişletme zaman alır. Bazı sorgular için yinelenen değerlendirme, fark edilebilir bir performans cezasına neden olur.

- Bir sorguyu değerlendirmek, verilerin değerinde veya programınızın durumunda yapılan değişiklikler olan yan etkilere neden olabilir. Tüm sorguların yan etkileri yoktur. Bir sorgunun yan etkileri olmadan güvenle değerlendirilemeyeceğini anlamak için sorguyu uygulayan kodu anlamanız gerekir.

## <a name="BKMK_SteppingAndLinq"></a>Adımlama ve LINQ
 LINQ Code hata ayıklarken, adımlamayı bilmeniz gereken bazı davranış farklılıkları vardır.

### <a name="linq-to-sql"></a>LINQ - SQL
 LINQ to SQL sorgularda, koşul kodu hata ayıklayıcı denetiminin ötesinde olur. Bu nedenle, koşul koduna ilerlenemez. Bir ifade ağacına derlenen herhangi bir sorgu, hata ayıklayıcının denetiminin ötesinde bir kod üretir.

### <a name="stepping-in-visual-basic"></a>Visual Basic adımla
 Bir Visual Basic programı aracılığıyla adımlarken ve hata ayıklayıcı bir sorgu bildirimiyle karşılaştığında, bildirime adımla, ancak tüm bildirimi tek bir ifade olarak vurgular. Bu davranış, sorgu çağrılana kadar değerlendirilmediği için oluşur. Daha fazla bilgi için bkz. [VISUAL BASIC LINQ 'e giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

 Aşağıdaki örnek kodda ilerederseniz, hata ayıklayıcı sorgu bildirimini veya sorgu oluşturmayı tek bir ifade olarak vurgular.

```vb
Function MyFunction(ByVal x As Char)
    Return True
End Function

Sub Main()
    'Query creation
    Dim x = From it In "faoaoeua" _
            Where MyFunction(it) _
            Select New With {.a = it}

    ' Query execution
    For Each cur In x
        Console.WriteLine(cur.ToString())
    Next
End Sub
```

 Bir kez daha adım hata ayıklayıcı `For Each cur In x`vurgular. Sonraki adımda `MyFunction`işlev adımları. `MyFunction`adımladıktan sonra `Console.WriteLine(cur.ToSting())`geri atlar. Herhangi bir noktada, hata ayıklayıcı kodu değerlendirse de sorgu bildirimindeki koşul kodunda adım adım ilerlemez.

### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Bir koşulu adımlamayı etkinleştirmek için bir Işlevle değiştirme (Visual Basic)
 Hata ayıklama amacıyla koşul kodu ' nu adım adım yapmanız gerekirse, koşulu özgün koşul kodunu içeren bir işlev çağrısıyla değiştirebilirsiniz. Örneğin, bu koda sahip olduğunuzu varsayalım:

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 Koşul kodunu `IsEven`adlı yeni bir işleve taşıyabilirsiniz:

```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt

For each item in query
      Console.WriteLine(item)
Next
...
Function IsEven(item As =Integer) as Boolean
      Return item Mod 2 = 0
End Function
```

 Düzeltilen sorgu, `items`her geçişte işlev `IsEven` çağırır. Hata ayıklayıcı pencerelerini her bir öğenin belirtilen koşulu karşılayıp karşılamadığını görmek için kullanabilir ve `IsEven`kodda ilerlemeyeceğinizi görebilirsiniz. Bu örnekteki koşul oldukça basittir. Ancak, hata ayıklaması yapmanız için daha zor bir koşul varsa, bu teknik çok faydalı olabilir.

## <a name="BKMK_EditandContinueNotSupportedforLINQ"></a>Düzenle ve devam et LINQ için desteklenmiyor
 Düzenle ve devam et, LINQ sorgularında yapılan değişiklikleri sınırlamalara göre destekler. Ayrıntılar için bkz. [ENC tarafından desteklenen değişiklikler](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))

## <a name="see-also"></a>Ayrıca bkz.

- [SQL hatalarını ayıklama](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)
- [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Visual Basic LINQ 'e giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
