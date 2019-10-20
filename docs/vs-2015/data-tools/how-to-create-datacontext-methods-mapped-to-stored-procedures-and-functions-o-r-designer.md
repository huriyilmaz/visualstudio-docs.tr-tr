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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665974"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Saklı yordamlar ve işlevler, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> yöntemlerine eklenebilir. Yöntemi çağırmak ve gerekli parametreleri geçirmek, veritabanında saklı yordamı veya işlevi çalıştırır ve <xref:System.Data.Linq.DataContext> yönteminin dönüş türündeki verileri döndürür. @No__t_0 yöntemleriyle ilgili ayrıntılı bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Saklı yordamlar Ayrıca, değişiklikler varlık sınıflarından veritabanına kaydedildiğinde ekleme, güncelleştirme ve silme işlemleri gerçekleştiren varsayılan [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] çalışma zamanı davranışını geçersiz kılmak için de kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>DataContext yöntemleri oluşturma
 Saklı yordamları veya işlevleri [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] üzerinde **Sunucu Gezgini/veritabanı Gezgini** sürükleyerek <xref:System.Data.Linq.DataContext> Yöntemler oluşturabilirsiniz.

> [!NOTE]
> Oluşturulan <xref:System.Data.Linq.DataContext> yönteminin dönüş türü, saklı yordamı veya işlevi [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bırakma yönteminize göre farklılık gösterir. Öğeleri doğrudan mevcut bir varlık sınıfına bırakmak, varlık sınıfının dönüş türüyle <xref:System.Data.Linq.DataContext> bir yöntem oluşturur. @No__t_0 boş bir alana öğe bırakma, otomatik olarak oluşturulan bir tür döndüren bir <xref:System.Data.Linq.DataContext> yöntemi oluşturur. Yöntem bölmesine eklendikten sonra bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü değiştirebilirsiniz. Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü incelemek veya değiştirmek için, bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Otomatik olarak oluşturulan türleri döndüren DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** /**veritabanı Gezgini**, üzerinde çalıştığınız veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] boş bir alanına sürükleyin.

     @No__t_0 yöntemi otomatik olarak oluşturulan bir dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Bir varlık sınıfının dönüş türüne sahip DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** /**veritabanı Gezgini**, üzerinde çalıştığınız veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] mevcut bir varlık sınıfının üzerine sürükleyin.

     @No__t_0 yöntemi, seçilen varlık sınıfının dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

> [!NOTE]
> Mevcut <xref:System.Data.Linq.DataContext> yöntemlerinin dönüş türünü değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [DataContext yöntemlerinde LINQ to SQL araçları (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Izlenecek yol: LINQ to SQL sınıfları oluşturma (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [nasıl yapılır: LINQ sorguları C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
