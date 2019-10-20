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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657402"
---
# <a name="datacontext-methods-or-designer"></a>DataContext Metotları (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId: dan/T: System. Data. Linq. DataContext? qualifyHint = false & oto Upgrade = true) yöntemleri ( [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)bağlamında) <xref:System.Data.Linq.DataContext>, bir veritabanınızı.

 @No__t_0 sınıfı, bir SQL Server veritabanı ile bu veritabanıyla eşlenen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] varlık sınıfları arasında bir iletken görevi gören bir [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sınıfıdır. @No__t_0 sınıfı, bağlantı dizesi bilgilerini ve veritabanına bağlanma ve veritabanındaki verileri düzenleme yöntemlerini içerir. Varsayılan olarak <xref:System.Data.Linq.DataContext> sınıfı, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sınıflardan veritabanına güncelleştirilmiş verileri gönderen <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi gibi çağırabilmeniz için çeşitli yöntemler içerir. Ayrıca, saklı yordamlar ve işlevlerle eşlenen ek <xref:System.Data.Linq.DataContext> yöntemler de oluşturabilirsiniz. Diğer bir deyişle, bu özel yöntemleri çağırmak, <xref:System.Data.Linq.DataContext> yönteminin eşlendiği veritabanında saklı yordamı veya işlevi çalıştırır. Herhangi bir sınıfı genişletmek için yöntemler ekleyeceğiniz gibi <xref:System.Data.Linq.DataContext> sınıfına yeni yöntemler ekleyebilirsiniz. Ancak, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bağlamındaki <xref:System.Data.Linq.DataContext> yöntemler hakkında tartışmalarda, ele alınan saklı yordamlar ve işlevlerle eşlenen <xref:System.Data.Linq.DataContext> yöntemleri vardır.

## <a name="methods-pane"></a>Yöntemler bölmesi
 saklı yordamlar ve işlevlerle eşlenen <xref:System.Data.Linq.DataContext> Yöntemler, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Yöntemler bölmesinde görüntülenir. Yöntemler bölmesi, **varlıklar** bölmesinin (ana tasarım yüzeyi) yanındaki bölmesidir. Yöntemler bölmesi, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] kullanarak oluşturduğunuz tüm <xref:System.Data.Linq.DataContext> yöntemlerini listeler. Varsayılan olarak, Yöntemler bölmesi boştur; saklı yordamları veya işlevleri **Sunucu Gezgini** /**veritabanı Gezgini** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] üzerine sürükleyerek <xref:System.Data.Linq.DataContext> Yöntemler oluşturun ve Yöntemler bölmesini doldurun. Daha fazla bilgi için bkz. [nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> @No__t_0 sağ tıklayıp Yöntemler bölmesini **Gizle** veya **Yöntemler bölmesini göster**' e tıklayarak veya CTRL + 1 klavye kısayolunu kullanarak Yöntemler bölmesini açın ve kapatın.

## <a name="two-types-of-datacontext-methods"></a>İki tür DataContext yöntemi
 DataContext yöntemleri, veritabanındaki saklı yordamlar ve işlevlerle eşlenen yöntemlerdir. @No__t_0 Yöntemler bölmesinde DataContext yöntemleri oluşturabilir ve ekleyebilirsiniz. @No__t_0 yöntemlerinin iki farklı türü vardır; bir veya daha fazla sonuç kümesi döndürenler ve olmayanlar:

- bir veya daha fazla sonuç kümesi döndüren <xref:System.Data.Linq.DataContext> Yöntemler:

     Uygulamanız yalnızca veritabanında saklı yordamları ve işlevleri çalıştırmak ve sonuçları döndürmek için ihtiyaç duyduğunda, bu tür bir <xref:System.Data.Linq.DataContext> yöntemi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: saklı yordamlar ve işlevler (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. LINQ. ISingleResult \<T > ve <xref:System.Data.Linq.IMultipleResults> Ile eşlenmiş DataContext yöntemleri oluşturma.

- Sonuç kümesi döndürmeyen <xref:System.Data.Linq.DataContext> Yöntemler: belirli bir varlık sınıfı için ekleme, güncelleştirme ve silme gibi.

     Uygulamanız, değiştirilen verileri bir varlık sınıfı ve veritabanı arasında kaydetmek için varsayılan [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] davranışını kullanmak yerine, saklı yordamları çalıştırmak zorunda olduğunda bu tür bir <xref:System.Data.Linq.DataContext> yöntemi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>DataContext yöntemlerinin dönüş türleri
 Saklı yordamları ve işlevleri **Sunucu Gezgini** /**veritabanı Gezgini** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] üzerine sürüklediğinizde, oluşturulan <xref:System.Data.Linq.DataContext> yönteminin dönüş türü, öğeyi nerede bıraktığınızda olduğuna göre farklılık gösterir. Öğeleri doğrudan mevcut bir varlık sınıfına bırakmak, varlık sınıfının dönüş türüyle <xref:System.Data.Linq.DataContext> yöntemi oluşturur; öğelerin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] boş bir alanına (her iki bölmede) bırakma, otomatik olarak oluşturulan bir tür döndüren bir <xref:System.Data.Linq.DataContext> yöntemi oluşturur. Oluşturulan otomatik olarak oluşturulan türün, saklı yordam veya işlev adı ve saklı yordam veya işlev tarafından döndürülen alanlarla eşlenen özelliklerle eşleşen bir adı vardır.

> [!NOTE]
> @No__t_0 yönteminin dönüş türünü Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü incelemek veya değiştirmek için, bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Veritabanından O/R Designer yüzeyine sürüklediğiniz nesneler, veritabanındaki nesnelerin adına göre otomatik olarak adlandırılır. Aynı nesneyi birden çok kez sürüklerseniz, adları farklılaştırır yeni adın sonuna bir sayı eklenir. Veritabanı nesne adları boşluk veya Visual Basic veya C#içinde desteklenmeyen karakterler içerdiğinde, boşluk veya geçersiz karakter alt çizgiyle değiştirilmiştir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [saklı](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) yordamlar [: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [nasıl yapılır: güncelleştirme gerçekleştirmek için saklı yordamlar atama, ekleme, ve siler (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [izlenecek yol: varlık sınıflarının INSERT, Update ve DELETE davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [Izlenecek yol: LINQ to SQL sınıfları oluşturma (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
