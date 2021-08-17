---
title: LINQ hata ayıklama | Microsoft Docs
description: Visual Studio 'da dil ile tümleşik sorgu (LINQ) hata ayıklayın. LINQ sonuçlarını görüntüleyin. LINQ koduna adımla davranış farklarını anlayın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 68b1929bf2849c0f3ba9d80191322c6733aa12c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097533"
---
# <a name="debugging-linq"></a>LINQ'de Hata Ayıklama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , dil ile tümleşik sorgu (LINQ) kodunda hata ayıklamayı destekler, bazı sınırlamalar vardır. Çoğu hata ayıklama özelliğinin adım adım, kesme noktaları ayarlama ve sonuçları hata ayıklayıcı penceresinde görüntüleme dahil olmak üzere LINQ deyimleriyle birlikte çalışır. Bu konu, LINQ hata ayıklamanın başlıca sınırlamalarını açıklamaktadır.

## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> LINQ sonuçlarını görüntüleme
 DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak bir LINQ deyimin sonucunu görüntüleyebilirsiniz. Kaynak penceresi kullandığınızda, kaynak penceredeki bir sorgu üzerindeki işaretçiyi duraklatabilir ve bir DataTip belirir. Bir LINQ değişkenini kopyalayabilir ve izleme penceresi veya QuickWatch iletişim kutusuna yapıştırabilirsiniz.

 LINQ içinde, bir sorgu oluşturulduğunda veya bildirildiğinde, ancak yalnızca sorgu kullanıldığında değerlendirilmez. Bu nedenle, sorgu değerlendirilene kadar bir değere sahip değildir. Sorgu oluşturma ve değerlendirme hakkında tam bir açıklama için bkz. [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) veya [Ilk LINQ sorgunuzu yazma](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).

 Bir sorgunun sonucunu göstermek için, hata ayıklayıcı tarafından değerlendirilmelidir. Hata ayıklayıcıda bir LINQ sorgu sonucu görüntülediğinizde oluşan bu örtük değerlendirme, dikkate almanız gereken bazı etkilere sahiptir:

- Sorgunun her değerlendirmesi zaman alır. Sonuçlar düğümünü genişletme zaman alır. Bazı sorgular için yinelenen değerlendirme, fark edilebilir bir performans cezasına neden olur.

- Bir sorguyu değerlendirmek, verilerin değerinde veya programınızın durumunda yapılan değişiklikler olan yan etkilere neden olabilir. Tüm sorguların yan etkileri yoktur. Bir sorgunun yan etkileri olmadan güvenle değerlendirilemeyeceğini anlamak için sorguyu uygulayan kodu anlamanız gerekir.

## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> Adımlama ve LINQ
 LINQ Code hata ayıklarken, adımlamayı bilmeniz gereken bazı davranış farklılıkları vardır.

### <a name="linq-to-sql"></a>LINQ to SQL
 LINQ to SQL sorgularda, koşul kodu hata ayıklayıcı denetiminin ötesinde olur. Bu nedenle, koşul koduna ilerlenemez. Bir ifade ağacına derlenen herhangi bir sorgu, hata ayıklayıcının denetiminin ötesinde bir kod üretir.

### <a name="stepping-in-visual-basic"></a>Visual Basic adımla
 bir Visual Basic programı aracılığıyla adımlarken ve hata ayıklayıcı bir sorgu bildirimiyle karşılaştığında, bildirime adımla, ancak tüm bildirimi tek bir ifade olarak vurgular. Bu davranış, sorgu çağrılana kadar değerlendirilmediği için oluşur. Daha fazla bilgi için bkz. [VISUAL BASIC LINQ 'e giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

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

 Bir kez daha adım hata ayıklayıcı vurgulanmıştır `For Each cur In x` . Sonraki adımda, işlevine adımları uygulayın `MyFunction` . Üzerinden adımladıktan sonra `MyFunction` , öğesine atlar `Console.WriteLine(cur.ToSting())` . Herhangi bir noktada, hata ayıklayıcı kodu değerlendirse de sorgu bildirimindeki koşul kodunda adım adım ilerlemez.

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

 Koşul kodunu, adlı yeni bir işleve taşıyabilirsiniz `IsEven` :

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

 Düzeltilen sorgu `IsEven` , her geçişte işlevini aracılığıyla çağırır `items` . Hata ayıklayıcı pencerelerini her bir öğenin belirtilen koşulu karşılayıp karşılamadığını görmek için kullanabilir ve içindeki kodda ilerlemeyeceğinizi görebilirsiniz `IsEven` . Bu örnekteki koşul oldukça basittir. Ancak, hata ayıklaması yapmanız için daha zor bir koşul varsa, bu teknik çok faydalı olabilir.

## <a name="edit-and-continue-not-supported-for-linq"></a><a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Düzenle ve devam et LINQ için desteklenmiyor
 Düzenle ve devam et, LINQ sorgularında yapılan değişiklikleri sınırlamalara göre destekler. Ayrıntılar için bkz. [ENC tarafından desteklenen değişiklikler](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)
- [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Visual Basic'de LINQ'e Giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
