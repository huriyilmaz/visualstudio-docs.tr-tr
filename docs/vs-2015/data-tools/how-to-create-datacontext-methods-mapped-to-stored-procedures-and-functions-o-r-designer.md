---
title: 'Nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665974"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Saklı yordamlar ve işlevler [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] as <xref:System.Data.Linq.DataContext> yöntemlerine eklenebilir. Yöntemi çağırmak ve gerekli parametreleri geçirmek, veritabanında saklı yordamı veya işlevi çalıştırır ve yöntemin dönüş türündeki verileri döndürür <xref:System.Data.Linq.DataContext> . Yöntemler hakkında ayrıntılı bilgi için <xref:System.Data.Linq.DataContext> bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Saklı yordamlar Ayrıca [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] , değişiklikler varlık sınıflarından veritabanına kaydedildiğinde ekleme, güncelleştirme ve silme işlemleri gerçekleştiren varsayılan çalışma zamanı davranışını geçersiz kılmak için de kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>DataContext yöntemleri oluşturma
 <xref:System.Data.Linq.DataContext>Saklı yordamları veya işlevleri **Sunucu Gezgini/veritabanı Gezgini** ' den üzerine sürükleyerek Yöntemler oluşturabilirsiniz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

> [!NOTE]
> Oluşturulan metodun dönüş türü <xref:System.Data.Linq.DataContext> , saklı yordamı veya işlevi üzerinde nerede bıraktığınızda olduğuna bağlı olarak farklılık gösterir [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Öğelerin doğrudan mevcut bir varlık sınıfına düşürülme, <xref:System.Data.Linq.DataContext> varlık sınıfının dönüş türüyle bir yöntem oluşturur. Öğesinin boş bir alanına öğe bırakma, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren bir yöntem oluşturur. Bir yöntemin dönüş türünü, <xref:System.Data.Linq.DataContext> Yöntemler bölmesine eklendikten sonra değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için <xref:System.Data.Linq.DataContext> , bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Otomatik olarak oluşturulan türleri döndüren DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** / **veritabanı Gezgini**, üzerinde çalıştığınız veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve boş bir alanı üzerine sürükleyin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     <xref:System.Data.Linq.DataContext>Yöntemi otomatik olarak oluşturulan bir dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Bir varlık sınıfının dönüş türüne sahip DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** / **veritabanı Gezgini**, üzerinde çalıştığınız veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve içindeki mevcut bir varlık sınıfına sürükleyin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     <xref:System.Data.Linq.DataContext>Yöntemi, seçilen varlık sınıfının dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

> [!NOTE]
> Mevcut yöntemlerin dönüş türünü değiştirme hakkında daha fazla bilgi için <xref:System.Data.Linq.DataContext> bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio DataContext yöntemlerinde LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [(o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Izlenecek yol: LINQ to SQL sınıfları oluşturma (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [nasıl yapılır: C# dilinde LINQ sorguları yazma](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
