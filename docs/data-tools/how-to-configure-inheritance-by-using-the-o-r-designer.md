---
title: O-R Tasarımcısını kullanarak devralmayı yapılandırma
description: Tek tablo devralmayı destekleyen Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) kullanarak devralmayı yapılandırmayı öğrenin. Devralınan veri sınıfları oluşturuldu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 669bcc567b06b4d0202ede2547f00c7c025de996f02233d5a4bd1603501d1f27
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347096"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma
Bu **Nesne İlişkisel Tasarımcısı** **(O/R Tasarımcısı)** genellikle ilişkisel sistemlerde uygulanan tek tablolu devralma kavramını destekler. Tek tablo devralmada, hem üst bilgiler hem de alt bilgiler için alanlar içeren tek bir veritabanı tablosu vardır. İlişkisel verilerde, bir ayrımcı sütun herhangi bir kaydın hangi sınıfa ait olduğunu belirleyen değeri içerir.

Örneğin, bir şirket `Persons` tarafından çalışan herkesi içeren bir tablo düşünün. Bazı kişiler çalışan, bazıları ise yöneticidir. Tablo, yöneticiler için 1, çalışanlar için 2 değerine sahip olan adlı bir sütun `Persons` `EmployeeType` içerir. Bu, ayrımcı sütundur. Bu senaryoda, çalışanların bir alt sınıfını oluşturabilir ve sınıfı yalnızca 2 değerine sahip `EmployeeType` kayıtlarla doldurmak için kullanabilirsiniz. Sınıfların her biri için geçerli olan sütunları da kaldırabilirsiniz.

Devralma kullanan (ve ilişkisel verilere karşılık gelen) bir nesne modeli oluşturmak biraz kafa karıştırıcı olabilir. Aşağıdaki yordam, O/R Tasarımcısı ile devralmayı yapılandırmak için **gereken adımları özetler.** Mevcut bir tabloya ve sütunlara başvurulmadan genel adımların takip etmek zor olabilir, bu nedenle verileri kullanan bir izlenecek yol sağlanır. **O/R** Tasarımcısını kullanarak devralmayı yapılandırmaya ilişkin ayrıntılı adım adım yönler için bkz. Adım adım kılavuz: Tek tablo devralma [(O/R Tasarımcısı)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)kullanarak LINQ to SQL sınıfları oluşturma.

## <a name="to-create-inherited-data-classes"></a>Devralınan veri sınıfları oluşturmak için

1. Mevcut bir Visual Basic veya C# **projesine LINQ to SQL** Sınıf öğesi ekleyerek **O/R** Tasarımcısı'Visual Basic açın.

2. Temel sınıf olarak kullanmak istediğiniz tabloyu **O/R Tasarımcısı'na sürükleyin.**

3. Tablonun ikinci bir kopyasını **O/R Tasarımcısı'na sürükleyip** yeniden adlandırabilirsiniz. Bu türetilen sınıf veya alt sınıftır.

4. Araç **Kutusunun** **Nesne İlişkisel Tasarımcısı** sekmesinde Devralma'ya tıklayın **ve** ardından alt sınıfa (yeniden adlandırdınız tablo) tıklayın ve bunu temel sınıfa bağlayın.

    > [!NOTE]
    > Araç **Kutusunda Devralma**  öğesi'ne tıklayın ve fare düğmesini bırakın, 3. adımda oluşturduğunuz sınıfın ikinci kopyasına tıklayın ve ardından 2. adımda oluşturduğunuz ilk sınıfa tıklayın. Devralma çizgisinin okunu ilk sınıfa gösterir.

5. Her sınıfta, görünmesini istemeyebilirsiniz ve ilişkilendirmeler için kullanılmaz nesne özelliklerini silin. İlişkiler için kullanılan nesne özelliklerini silebilirsanız bir hata alırsınız: özelliği ilişkilendirmeye katıldığı [ \<property name> için silinemiyor. \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md)

    > [!NOTE]
    > Türetilmiş bir sınıf kendi temel sınıfında tanımlanan özellikleri devralına olduğundan, her sınıfta aynı sütunlar tanımlanmalıdır. (Sütunlar özellik olarak uygulanır.) Temel sınıftaki özelliğinde devralma değiştiricisini ayarerek türetilmiş sınıfta sütunların oluşturulmasını etkinleştirebilirsiniz. Daha fazla bilgi için [bkz. Devralma temelleri (Visual Basic).](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)

6. O/R Tasarımcısı'nda **devralma çizgisini seçin.**

7. Özellikler **penceresinde,** **Discriminator Özelliğini** sınıflarınızdaki kayıtları ayıran sütun adına ayarlayın.

8. Derived **Class Discriminator Value özelliğini,** kaydı devralınmış tür olarak ataan veritabanındaki değere ayarlayın. (Bu, ayrımcı sütununda depolanan ve devralınan sınıfı ayırt etmek için kullanılan değerdir.)

9. Temel **Sınıf AyırıcıSı Değer özelliğini,** kaydı temel tür olarak ifade eden değere ayarlayın. (Bu, ayrımcı sütunda depolanan ve temel sınıfı ayırt etmek için kullanılan değerdir.)

10. İsteğe bağlı olarak,  Herhangi bir tanımlı devralma koduyla eşleşmez satırları yüklerken kullanılan bir devralma hiyerarşisinde bir tür ayarlamak için Devralma Varsayılan özelliğini de ayarlayın. Başka bir deyişle, bir kaydın ayrımcı sütununda Türetilmiş Sınıf Ayrımı Değeri  veya Temel Sınıf Ayrımı Değeri özelliklerinde bulunan değerle eşleşmez bir değeri varsa, kayıt Devralma Varsayılanı olarak belirlenen türe **yüklenir.** 

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [adım adım kılavuz: LINQ to SQL sınıfları oluşturma (O-R Tasarımcısı)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [adım adım kılavuz: LINQ to SQL devralma (O/R Tasarımcısı) kullanarak tek tablo sınıflarını oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Devralma temelleri (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Devralma](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
