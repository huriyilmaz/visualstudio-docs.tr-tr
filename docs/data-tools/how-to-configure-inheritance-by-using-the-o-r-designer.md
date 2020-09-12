---
title: O-R tasarımcısını kullanarak devralmayı yapılandırma
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a0f56d7b123571e9a65d5bb2baa99a8d7dac2461
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037061"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma
**Nesne ilişkisel Tasarımcısı** (**O/R Designer**), genellikle ilişkisel sistemlerde uygulanan tek tablo devralma kavramını destekler. Tek tablo Devralmada, hem üst bilgiler hem de alt bilgi için alanlar içeren tek bir veritabanı tablosu vardır. İlişkisel veriler ile, bir Ayrıştırıcı sütunu herhangi bir kaydın hangi sınıfa ait olduğunu belirleyen değeri içerir.

Örneğin, `Persons` bir şirket tarafından görevli herkesi içeren bir tablo düşünün. Bazı kişiler çalışanlar ve bazı kişiler yöneticilerdir. `Persons`Tablo, `EmployeeType` Yöneticiler için 1 değeri ve çalışanlar için 2 değeri olan adlı bir sütun içerir; bu, ayrıştırıcı sütunudur. Bu senaryoda, çalışanların bir alt sınıfını oluşturabilir ve sınıfı yalnızca 2 değeri olan kayıtlarla doldurabilirsiniz `EmployeeType` . Ayrıca sınıfların her birinden uygulanmayan sütunları da kaldırabilirsiniz.

Devralmayı kullanan (ve ilişkisel verilere karşılık gelen) bir nesne modeli oluşturmak biraz kafa karıştırıcı olabilir. Aşağıdaki yordamda, **O/R Tasarımcısı**ile devralmayı yapılandırmak için gereken adımlar özetlenmektedir. Mevcut bir tabloya ve sütunlara başvurulmadan aşağıdaki genel adımlar zor olabilir, bu nedenle veri kullanan bir anlatım sağlanır. **O/r tasarımcısını**kullanarak devralmayı yapılandırmaya yönelik ayrıntılı adım adım yönergeler için bkz. [Walkthrough: tek tablo devralma (O/r designer) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Devralınan veri sınıfları oluşturmak için

1. Mevcut bir Visual Basic veya C# projesine **LINQ to SQL sınıfları** öğesi ekleyerek **O/R tasarımcısını** açın.

2. Temel sınıf olarak kullanmak istediğiniz tabloyu **O/R tasarımcısına**sürükleyin.

3. Tablonun ikinci bir kopyasını **O/R tasarımcısına** sürükleyin ve yeniden adlandırın. Bu, türetilmiş sınıf veya alt sınıfıdır.

4. **Araç kutusunun** **nesne ilişkisel Tasarımcısı** sekmesinde **Devralma** ' a tıklayın ve ardından alt sınıfa (yeniden adlandırdığınız tablo) tıklayın ve temel sınıfa bağlayın.

    > [!NOTE]
    > **Araç kutusu** ' nda **Devralma** öğesine tıklayın ve fare düğmesini bırakın, adım 3 ' te oluşturduğunuz sınıfın ikinci kopyasına tıklayın ve ardından 2. adımda oluşturduğunuz ilk sınıfa tıklayın. Devralma satırındaki ok ilk sınıfa işaret eder.

5. Her sınıfta, görünmesini istemediğiniz ve ilişkilendirmeler için kullanılmayan herhangi bir nesne özelliğini silin. İlişkilendirmeler için kullanılan nesne özelliklerini silmeye çalıştığınızda bir hata alıyorsunuz: [ \<property name> \<association name> ilişkiye katıldığı için özellik silinemiyor ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Türetilmiş bir sınıf kendi temel sınıfında tanımlanan özellikleri devraldığından, her sınıfta aynı sütunlar tanımlanamaz. (Sütunlar özellikler olarak uygulanır.) Temel sınıftaki özellikte devralma değiştiricisini ayarlayarak türetilmiş sınıfta sütun oluşturmayı etkinleştirebilirsiniz. Daha fazla bilgi için bkz. [Devralma Temelleri (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. **O/R tasarımcısında**devralma satırını seçin.

7. **Özellikler** penceresinde, **ayrıştırıcı özelliğini** sınıflarınızda kayıtları ayıran sütun adı olarak ayarlayın.

8. **Türetilmiş sınıf ayrıştırıcı değeri** özelliğini, veritabanındaki değeri devralınan tür olarak atayan değere ayarlayın. (Bu, ayrıştırıcı sütununda saklanan ve devralınmış sınıfı belirlemek için kullanılan değerdir.)

9. **Temel sınıf ayrıştırıcı değeri** özelliğini, kaydı temel tür olarak atayan değere ayarlayın. (Bu, ayrıştırıcı sütununda depolanan ve temel sınıfı belirlemek için kullanılan değerdir.)

10. İsteğe bağlı olarak, devralma **varsayılan** özelliğini, tanımlı devralma kodu ile eşleşmeyen satırlar yüklenirken kullanılan bir devralma hiyerarşisinde bir tür belirlemek için de ayarlayabilirsiniz. Diğer bir deyişle, bir kayıt, ayrıştırıcı sütununda, **türetilmiş sınıf ayrıştırıcı değeri** veya **temel sınıf ayrıştırıcı değeri** özelliklerindeki değerle eşleşmeyen bir değere sahipse, kayıt **Devralma varsayılanı**olarak belirlenmiş türe yüklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ - SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [İzlenecek yol: tek tablo devralma (O/R Designer) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Devralma Temelleri (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Devralma](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
