---
title: Visio nesne modeline genel bakış
description: Microsoft Visio için Office çözümleri geliştirmek üzere Visio nesne modeliyle nasıl etkileşim kurabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d7a83b5a900defb63ceffe4f63d57e2b200c47b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921773"
---
# <a name="visio-object-model-overview"></a>Visio nesne modeline genel bakış
  Microsoft Office Visio için Office çözümleri geliştirmek üzere Visio nesne modeliyle etkileşim kurabilirsiniz. Bu nesne modeli, Visio için birincil birlikte çalışma derlemesinde sunulan sınıflardan ve arabirimlerden oluşur ve `Microsoft.Office.Interop.Visio` ad alanında tanımlanır.

 Bu konuda Visio nesne modeline kısa bir genel bakış sunulmaktadır. Office projelerinde görevleri gerçekleştirmek için Visio nesne modelini kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Visio belgeleriyle çalışma](../vsto/working-with-visio-documents.md)

- [Visio şekilleri ile çalışma](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Visio nesne modelini anlama
 Visio, etkileşime girebilmeniz için birçok nesne sağlar. Bu nesneler, Kullanıcı arabirimini yakından takip eden bir hiyerarşide düzenlenir. Hiyerarşinin en üstünde [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application) nesnesi bulunur. Bu nesne, geçerli Visio örneğini temsil eder. `Microsoft.Office.Interop.Visio.Application`Nesnesi `Microsoft.Office.Interop.Visio.Document` ve koleksiyonlarını ve koleksiyonlarını içerir `Microsoft.Office.Interop.Visio.Page` `Microsoft.Office.Interop.Visio.Documents` `Microsoft.Office.Interop.Visio.Pages` . Bu nesnelerin ve koleksiyonların her birinde, işleme ve bunlarla etkileşime geçmek için erişebileceğiniz birçok yöntem ve özellik vardır.

 Daha fazla bilgi için bkz. [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.DocUment](/office/vba/api/Visio.Document)ve [Microsoft. Office. Interop. Visio. Page](/office/vba/api/Visio.Page) nesneleri ve ayrıca [Microsoft.Office.Interop.Visio.Documlar](/office/vba/api/Visio.Documents) ve [Microsoft. OFFICE. Interop. Visio. Pages](/office/vba/api/Visio.Pages) koleksiyonları için VBA başvuru belgeleri.

 Aşağıdaki bölümler en üst düzey nesneleri ve birbirleriyle nasıl etkileşime gireceğini kısaca açıklamaktadır. Bu nesneler aşağıdaki nesneleri içerir:

- Uygulama nesnesi

- Belge nesnesi

- Sayfa nesnesi

### <a name="application-object"></a>Uygulama nesnesi
 Microsoft. Office. Interop. Visio. Application nesnesi, Visio uygulamasını temsil eder ve diğer tüm nesnelerin üst öğesidir. Üyeleri genellikle Visio için bir bütün olarak uygulanır. Visio ortamını denetlemek için Microsoft. Office. Interop. Visio. Application ve nesnelerinin özelliklerini ve yöntemlerini kullanabilirsiniz `Microsoft.Office.Interop.Visio.ApplicationSettings` .

 VSTO eklenti projelerinde, sınıfının alanını kullanarak Microsoft. Office. Interop. Visio. Application nesnesine erişebilirsiniz `Application` `ThisAddIn` . Daha fazla bilgi için bkz. [VSTO Eklentilerini Programlama](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Belge nesnesi
 Microsoft.Office.Interop.Visio.Document nesnesi, Visio programlamasında merkezi bir belgedir. Bir çizim, kalıp veya şablon dosyasını temsil eder. Bir Visio belgesi açtığınızda veya yeni bir belge oluşturduğunuzda, Microsoft. Office. Interop. Visio. Application nesnesinin Microsoft.Office.Interop.Visio.Doctastaları koleksiyonuna eklenen yeni bir Microsoft.Office.Interop.Visio.Document nesnesi oluşturursunuz.

 Odağa sahip belgeye etkin belge denir. `Microsoft.Office.Interop.Visio.Application.ActiveDocument`Microsoft. Office. Interop. Visio. Application nesnesinin özelliği tarafından temsil edilir.

### <a name="page-object"></a>Sayfa nesnesi
 Microsoft. Office. Interop. Visio. Page nesnesi bir ön plan sayfasının veya bir arka plan sayfasının çizim alanını temsil eder. `Microsoft.Office.Interop.Visio.Page.Background`Bir sayfanın ön plan veya arka plan sayfası olduğunu anlamak için özelliğini kullanabilirsiniz.

 Şekil oluşturmak için ve yöntemlerini içeren yöntemleri kullanabilirsiniz `Microsoft.Office.Interop.Visio.Page.DrawSpline` `Microsoft.Office.Interop.Visio.Page.DrawOval` . Ayrıca, kalıplardan ana bilgisayarlar alabilir ve veya yöntemlerini kullanarak şekilleri sayfaya yerleştirebilirsiniz `Microsoft.Office.Interop.Visio.Page.Drop` `Microsoft.Office.Interop.Visio.Page.DropMany` .

## <a name="use-the-visio-object-model-documentation"></a>Visio nesne modeli belgelerini kullanma
 Visio nesne modeli hakkında tüm bilgiler için Visio VBA nesne modeli başvurusuna başvurabilirsiniz. VBA nesne modeli başvurusu, Visio nesne modelini Visual Basic for Applications (VBA) koduna açık olarak belgeler. Daha fazla bilgi için bkz. [Visio nesne modeli başvurusu](/office/vba/api/overview/visio/object-model).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler, Visio birincil birlikte çalışma derlemesindeki (PIA) türlere ve üyelere karşılık gelir. Örneğin, `Document` VBA nesne modeli başvurusundaki nesne, VISIO PIA 'teki Microsoft.Office.Interop.Visio.Document türüne karşılık gelir. VBA nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, Visual Studio 'yu kullanarak oluşturduğunuz bir Visio VSTO eklentisi projesinde kullanmak istiyorsanız bu başvurudaki VBA kodunu Visual Basic veya Visual C# ' ye çevirmeniz gerekir.

> [!NOTE]
> Şu anda, Visio birincil birlikte çalışma derlemesi için başvuru belgesi yoktur.

 İlgili kod örnekleri ve Visio çözümleri oluşturmaya yönelik ek araçlar için bkz. [visio 2010 yazılım geliştirme seti](https://www.microsoft.com/download/details.aspx?id=12365).

### <a name="additional-types-in-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemelerindeki ek türler
 Uygulama farklılıkları nedeniyle, VBA 'da görünmeyen birincil birlikte çalışma derlemelerindeki türleri bulabilirsiniz. VBA, Visio nesne modelinin yalnızca doğrudan kullanabileceğiniz nesneleri ve üyeleri içeren bir görünümünü sağlar. Birincil birlikte çalışma derlemeleri aynı nesne modelini sunar, ancak aynı zamanda COM nesne modelindeki nesneleri yönetilen koda çeviren diğer arabirimleri, sınıfları ve üyeleri de kapsar. Bu ek öğelerin doğrudan kodunuzda kullanılması amaçlanmamaktadır.

 Daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)) ve [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio belgeleriyle çalışma](../vsto/working-with-visio-documents.md)
- [Visio şekilleri ile çalışma](../vsto/working-with-visio-shapes.md)
