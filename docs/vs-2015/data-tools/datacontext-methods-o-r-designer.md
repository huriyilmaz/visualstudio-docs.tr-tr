---
title: DataContext yöntemleri (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657402"
---
# <a name="datacontext-methods-or-designer"></a>DataContext Metotları (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId: gt/T: System. Data. LINQ. DataContext? qualifyHint = false&oto Upgrade = true) yöntemleri ( [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)bağlamında), <xref:System.Data.Linq.DataContext> bir veritabanındaki saklı yordamları ve işlevleri çalıştıran sınıfın yöntemleridir.

 Sınıfı, bir <xref:System.Data.Linq.DataContext> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] SQL Server veritabanı ile [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Bu veritabanıyla eşlenen varlık sınıfları arasında bir iletken görevi gören bir sınıftır. <xref:System.Data.Linq.DataContext>Sınıfı, bağlantı dizesi bilgilerini ve veritabanına bağlanma ve veritabanındaki verileri düzenleme yöntemlerini içerir. Varsayılan olarak, <xref:System.Data.Linq.DataContext> sınıfı, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veri sınıflarından güncelleştirilmiş verileri gönderen Yöntem gibi çağırabilmeniz gereken birkaç yöntem içerir [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] . Ayrıca, <xref:System.Data.Linq.DataContext> saklı yordamlar ve işlevlerle eşlenen ek yöntemler de oluşturabilirsiniz. Diğer bir deyişle, bu özel yöntemleri çağırmak, yöntemin eşlendiği veritabanında saklı yordamı veya işlevi çalıştırır <xref:System.Data.Linq.DataContext> . <xref:System.Data.Linq.DataContext>Herhangi bir sınıfı genişletmek için yöntemler ekleyeceğiniz gibi sınıfa yeni yöntemler ekleyebilirsiniz. Ancak, yöntemleri hakkında tartışmalarda, <xref:System.Data.Linq.DataContext> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> açıklanan saklı yordamlar ve işlevlerle eşlenen yöntemlerdir.

## <a name="methods-pane"></a>Yöntemler bölmesi
 <xref:System.Data.Linq.DataContext> saklı yordamlar ve işlevlerle eşlenen Yöntemler, öğesinin Yöntemler bölmesinde görüntülenir [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Yöntemler bölmesi, **varlıklar** bölmesinin (ana tasarım yüzeyi) yanındaki bölmesidir. Yöntemler bölmesinde <xref:System.Data.Linq.DataContext> , kullanarak oluşturduğunuz tüm yöntemler listelenir [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Varsayılan olarak, Yöntemler bölmesi boştur; **Server Explorer** / **Database Explorer** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> Yöntem oluşturmak ve Yöntemler bölmesini doldurmak için Sunucu Gezgini veritabanı Gezgini içindeki saklı yordamları veya işlevleri üzerine sürükleyin. Daha fazla bilgi için bkz. [nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Sağ tıklayıp Yöntemler bölmesini [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] **Gizle** veya **Yöntemler bölmesini göster**' e tıklayarak Yöntemler bölmesini açın ve kapatın ya da CTRL + 1 klavye kısayolunu kullanın.

## <a name="two-types-of-datacontext-methods"></a>İki tür DataContext yöntemi
 DataContext yöntemleri, veritabanındaki saklı yordamlar ve işlevlerle eşlenen yöntemlerdir. ' Nin Yöntemler bölmesinde DataContext yöntemleri oluşturabilir ve ekleyebilirsiniz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . İki farklı yöntem türü vardır <xref:System.Data.Linq.DataContext> ; bir veya daha fazla sonuç kümesi döndüren ve olmayanlar:

- <xref:System.Data.Linq.DataContext> bir veya daha fazla sonuç kümesi döndüren yöntemler:

     <xref:System.Data.Linq.DataContext>Uygulamanız yalnızca veritabanında saklı yordamları ve işlevleri çalıştırmak ve sonuçları döndürmek için ihtiyaç duyduğunda, bu tür bir yöntem oluşturun. Daha fazla bilgi için bkz [. nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. LINQ. ISingleResult \<T> , ve <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> Sonuç kümesi döndürmeyen Yöntemler: belirli bir varlık sınıfı için ekleme, güncelleştirme ve silme gibi.

     <xref:System.Data.Linq.DataContext>Uygulamanız, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] değiştirilen verileri bir varlık sınıfı ve veritabanı arasında kaydetmek için varsayılan davranışı kullanmak yerine saklı yordamları çalıştırmak gerektiğinde bu tür bir yöntem oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>DataContext yöntemlerinin dönüş türleri
 **Sunucu Gezgini**veritabanı Gezgini içindeki saklı yordamları ve işlevleri / **Database Explorer** üzerine sürüklediğinizde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , oluşturulan metodun dönüş türü, <xref:System.Data.Linq.DataContext> öğeyi nereye bıraktığınızda olduğuna göre farklılık gösterir. Öğeleri doğrudan mevcut bir varlık sınıfına bırakmak, <xref:System.Data.Linq.DataContext> varlık sınıfının dönüş türüyle bir yöntem oluşturur; öğelerin boş bir alanına [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (herhangi bir bölmede) bırakma, <xref:System.Data.Linq.DataContext> otomatik olarak üretilen bir tür döndüren bir yöntem oluşturur. Oluşturulan otomatik olarak oluşturulan türün, saklı yordam veya işlev adı ve saklı yordam veya işlev tarafından döndürülen alanlarla eşlenen özelliklerle eşleşen bir adı vardır.

> [!NOTE]
> Bir yöntemin dönüş türünü <xref:System.Data.Linq.DataContext> Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için <xref:System.Data.Linq.DataContext> , bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Veritabanından O/R Designer yüzeyine sürüklediğiniz nesneler, veritabanındaki nesnelerin adına göre otomatik olarak adlandırılır. Aynı nesneyi birden çok kez sürüklerseniz, adları farklılaştırır yeni adın sonuna bir sayı eklenir. Veritabanı nesne adları boşluk veya Visual Basic veya C# ' de desteklenmeyen karakterler içerdiğinde, boşluk veya geçersiz karakter alt çizgiyle değiştirilmiştir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçlar](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [saklı yordamlar](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) [: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (o/r Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [nasıl yapılır: güncelleştirme, ekleme ve silme Işlemleri için saklı yordamlar atama (o/r Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [Izlenecek yol: varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [izlenecek yol: LINQ to SQL sınıfları oluşturma (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
