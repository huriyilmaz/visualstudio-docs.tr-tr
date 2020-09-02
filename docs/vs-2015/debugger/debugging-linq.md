---
title: LINQ hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0292bf5b62bf150a598b4c750929ba6928216a50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691265"
---
# <a name="debugging-linq"></a>LINQ'de Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , dil ile tümleşik sorgu (LINQ) kodunda hata ayıklamayı destekler, bazı sınırlamalar vardır. Çoğu hata ayıklama özelliğinin adım adım, kesme noktaları ayarlama ve sonuçları hata ayıklayıcı penceresinde görüntüleme dahil olmak üzere LINQ deyimleriyle birlikte çalışır. Bu konu, LINQ hata ayıklamanın başlıca sınırlamalarını açıklamaktadır.  
  
## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> LINQ sonuçlarını görüntüleme  
 DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak bir LINQ deyimin sonucunu görüntüleyebilirsiniz. Kaynak penceresi kullandığınızda, kaynak penceredeki bir sorgu üzerindeki işaretçiyi duraklatabilir ve bir DataTip belirir. Bir LINQ değişkenini kopyalayabilir ve izleme penceresi veya QuickWatch iletişim kutusuna yapıştırabilirsiniz.  
  
 LINQ içinde, bir sorgu oluşturulduğunda veya bildirildiğinde, ancak yalnızca sorgu kullanıldığında değerlendirilmez. Bu nedenle, sorgu değerlendirilene kadar bir değere sahip değildir. Sorgu oluşturma ve değerlendirme hakkında tam bir açıklama için bkz. [LINQ Sorgularına Giriş (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8) veya [Ilk LINQ sorgunuzu yazma](https://msdn.microsoft.com/library/4affb732-3e9b-4479-aa31-1f9bd8183cbe).  
  
 Bir sorgunun sonucunu göstermek için, hata ayıklayıcı tarafından değerlendirilmelidir. Hata ayıklayıcıda bir LINQ sorgu sonucu görüntülediğinizde oluşan bu örtük değerlendirme, dikkate almanız gereken bazı etkilere sahiptir:  
  
- Sorgunun her değerlendirmesi zaman alır. Sonuçlar düğümünü genişletme zaman alır. Bazı sorgular için yinelenen değerlendirme, fark edilebilir bir performans cezasına neden olur.  
  
- Bir sorguyu değerlendirmek, verilerin değerinde veya programınızın durumunda yapılan değişiklikler olan yan etkilere neden olabilir. Tüm sorguların yan etkileri yoktur. Bir sorgunun yan etkileri olmadan güvenle değerlendirilemeyeceğini anlamak için sorguyu uygulayan kodu anlamanız gerekir.  
  
## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> Adımlama ve LINQ  
 LINQ Code hata ayıklarken, adımlamayı bilmeniz gereken bazı davranış farklılıkları vardır.  
  
### <a name="linq-to-sql"></a>LINQ to SQL  
 LINQ to SQL sorgularda, koşul kodu hata ayıklayıcı denetiminin ötesinde olur. Bu nedenle, koşul koduna ilerlenemez. Bir ifade ağacına derlenen herhangi bir sorgu, hata ayıklayıcının denetiminin ötesinde bir kod üretir.  
  
### <a name="stepping-in-visual-basic"></a>Visual Basic adımla  
 Bir Visual Basic programı aracılığıyla adımlarken ve hata ayıklayıcı bir sorgu bildirimiyle karşılaştığında, bildirime adımla, ancak tüm bildirimi tek bir ifade olarak vurgular. Bu davranış, sorgu çağrılana kadar değerlendirilmediği için oluşur. Daha fazla bilgi için bkz. [VISUAL BASIC LINQ 'e giriş](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984).  
  
 Aşağıdaki örnek kodda ilerederseniz, hata ayıklayıcı sorgu bildirimini veya sorgu oluşturmayı tek bir ifade olarak vurgular.  
  
```  
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
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Koşul kodunu, adlı yeni bir işleve taşıyabilirsiniz `IsEven` :  
  
```  
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
 Düzenle ve devam et, LINQ sorgularında yapılan değişiklikleri desteklemez. Hata ayıklama oturumu sırasında bir LINQ ifadesi ekler, kaldırırsanız veya değiştirirseniz, değişikliğin Düzenle ve devam et tarafından desteklenmediğini belirten bir iletişim kutusu görüntülenir. Bu noktada, değişiklikleri geri alabilir ya da hata ayıklama oturumunu durdurabilir ve düzenlenmiş kodla yeni bir oturumu yeniden başlatabilirsiniz.  
  
 Ayrıca, Düzenle ve devam et, LINQ ifadesinde kullanılan bir değişkenin türünün veya değerinin değiştirilmesini desteklemez. Yine, değişiklikleri geri alabilir veya hata ayıklama oturumunu durdurup yeniden başlatabilirsiniz.  
  
 C# ' de, LINQ sorgusu içeren bir yöntemde Düzenle ve devam et kullanamazsınız.  
  
 Visual Basic, LINQ sorgusu içeren bir yöntemde bile, LINQ olmayan kodda Düzenle ve devam et ' i kullanabilirsiniz. Değişiklikler LINQ sorgusunun satır numarasını etkilese bile, LINQ ifadesinden önce kod ekleyebilir veya kaldırabilirsiniz. LINQ dışı koda yönelik Visual Basic hata ayıklama deneyimi, LINQ 'ın tanıtılmasından önceki gibi kalır. Değişiklikleri uygulamak için hata ayıklamayı durdurmak istemediğiniz müddetçe, LINQ sorgusunu değiştiremez, ekleyemez veya kaldıramazsınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL hatalarını ayıklama](https://msdn.microsoft.com/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Yan etkiler ve Ifadeler](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)   
 [Hata ayıklayıcı ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md)   
 [LINQ Sorgularına Giriş (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)   
 [Visual Basic'de LINQ'e Giriş](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)
