---
title: 'Nasıl Yapılır: O-R tasarımcısını kullanarak devralmayı yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654700"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Nasıl Yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), genellikle ilişkisel sistemlerde uygulanan tek tablo devralma kavramını destekler. Tek tablo Devralmada, hem üst bilgiler hem de alt bilgi için alanlar içeren tek bir veritabanı tablosu vardır. İlişkisel veriler ile, bir Ayrıştırıcı sütunu herhangi bir kaydın hangi sınıfa ait olduğunu belirleyen değeri içerir.

 Örneğin, bir şirket tarafından görevli herkesi içeren bir kişiler tablosu düşünün. Bazı kişiler çalışanlar ve bazı kişiler yöneticilerdir. Kişiler tablosu, Yöneticiler için 1 değeri ve çalışanlar için 2 değeri olan `EmployeeType` adlı bir sütun içerir; Bu, ayrıştırıcı sütunudur. Bu senaryoda, çalışanların bir alt sınıfını oluşturabilir ve sınıfı yalnızca 2 `EmployeeType` değerine sahip kayıtlarla doldurabilirsiniz. Ayrıca sınıfların her birinden uygulanmayan sütunları da kaldırabilirsiniz.

 Devralmayı kullanan (ve ilişkisel verilere karşılık gelen) bir nesne modeli oluşturmak biraz kafa karıştırıcı olabilir. Aşağıdaki yordamda, O/R Tasarımcısı ile devralmayı yapılandırmak için gereken adımlar özetlenmektedir. Mevcut bir tabloya ve sütunlara başvurulmadan aşağıdaki genel adımlar zor olabilir, bu nedenle verileri kullanan bir anlatım sunulmaktadır. @No__t_0 kullanarak devralmayı yapılandırmaya yönelik ayrıntılı adım adım yönergeler için bkz. [Walkthrough: Tek tablo devralma (O/R Tasarımcısı) ](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) kullanarak LINQ to SQL sınıfları oluşturma.

### <a name="to-create-inherited-data-classes"></a>Devralınan veri sınıfları oluşturmak için

1. Mevcut bir Visual Basic veya C# projeye bir **LINQ to SQL sınıfları** öğesi ekleyerek [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] açın.

2. Temel sınıf olarak kullanmak istediğiniz tabloyu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sürükleyin.

3. Tablonun ikinci bir kopyasını [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] üzerine sürükleyin ve yeniden adlandırın. Bu, türetilmiş sınıf veya alt sınıfıdır.

4. **Araç kutusunun** **nesne ilişkisel Tasarımcısı** sekmesinde **Devralma** ' a tıklayın ve ardından alt sınıfa (yeniden adlandırdığınız tablo) tıklayın ve temel sınıfa bağlayın.

    > [!NOTE]
    > **Araç kutusu** ' nda **Devralma** öğesine tıklayın ve fare düğmesini bırakın, adım 3 ' te oluşturduğunuz sınıfın ikinci kopyasına tıklayın ve ardından 2. adımda oluşturduğunuz ilk sınıfa tıklayın. Devralma satırındaki ok ilk sınıfa işaret eder.

5. Her sınıfta, görünmesini istemediğiniz ve ilişkilendirmeler için kullanılmayan herhangi bir nesne özelliğini silin. İlişkilendirmeler için kullanılan nesne özelliklerini silmeye çalıştığınızda bir hata alırsınız: [@No__t_1property name > özelliği, association \<association ad > katıldığı için silinemiyor](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Türetilmiş bir sınıf kendi temel sınıfında tanımlanan özellikleri devraldığından, her sınıfta aynı sütunlar tanımlanamaz. (Sütunlar özellikler olarak uygulanır.) Temel sınıftaki özellikte devralma değiştiricisini ayarlayarak türetilmiş sınıfta sütun oluşturmayı etkinleştirebilirsiniz. Daha fazla bilgi için bkz. DERLEMEDE [NOT: Özellikleri ve yöntemleri geçersiz kılma ](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. @No__t_0 devralma satırını seçin.

7. **Özellikler** penceresinde, **ayrıştırıcı özelliğini** sınıflarınızda kayıtları ayırt etmek için kullanılan sütun adı olarak ayarlayın.

8. **Türetilmiş sınıf ayrıştırıcı değeri** özelliğini, veritabanındaki değeri devralınan tür olarak atayan değere ayarlayın. (Bu, ayrıştırıcı sütununda depolanan ve devralınmış sınıfı belirlemek için kullanılan değerdir.)

9. **Temel sınıf ayrıştırıcı değeri** özelliğini, kaydı temel tür olarak atayan değere ayarlayın. (Bu, ayrıştırıcı sütununda depolanan ve temel sınıfı belirlemek için kullanılan değerdir.)

10. İsteğe bağlı olarak, devralma **varsayılan** özelliğini, tanımlı devralma kodu ile eşleşmeyen satırlar yüklenirken kullanılan bir devralma hiyerarşisinde bir tür belirlemek için de ayarlayabilirsiniz. Diğer bir deyişle, bir kayıt, ayrıştırıcı sütununda, **türetilmiş sınıf ayrıştırıcı değeri** veya **temel sınıf ayrıştırıcı değeri** özelliklerindeki değerle eşleşmeyen bir değere sahipse, kayıt  **Devralma varsayılanı**.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio [Walkthrough LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) : LINQ to SQL sınıfları oluşturma (O-R Designer) [, Visual studio 2012 'de veri uygulama geliştirmeye yönelik yenilikler ](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) Pave](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [Visual Studio 'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Walkthrough: DERLEMEDE [NOT ](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) tek tablo devralma (O/R Tasarımcısı) kullanarak LINQ to SQL sınıfları oluşturma: Devralma Visual Basic ](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [Devralma](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
