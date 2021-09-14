---
title: Visio modeline genel bakış
description: Microsoft Office çözümlerini geliştirmek için Visio nesne modeliyle nasıl etkileşim kurabilirsiniz Visio.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e2c82deca11d11d96afce5365b04b68247807789
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726103"
---
# <a name="visio-object-model-overview"></a>Visio modeline genel bakış
  Bu Office çözümlerini geliştirmek Microsoft Office Visio nesne modeliyle Visio etkileşim kurabilirsiniz. Bu nesne modeli, Visio için birincil birlikte çalışma derlemesinde sağlanan ve ad alanında tanımlanan sınıflardan ve arabirimlerden `Microsoft.Office.Interop.Visio` oluşur.

 Bu konu, nesne modeline kısa bir Visio genel bakış sağlar. Visio projelerinde görevleri Office nesne modelini kullanma hakkında bilgi için aşağıdaki konulara bakın:

- [Belgelerle Visio çalışma](../vsto/working-with-visio-documents.md)

- [Farklı şekillerde Visio çalışma](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Nesne Visio anlama
 Visio etkileşim kurabilirsiniz birçok nesne sağlar. Bu nesneler, kullanıcı arabirimini yakından izleyen bir hiyerarşide düzenlenir. Hiyerarşinin en üstünde [Microsoft.Office. Birlikte çalış -abilir -lik. Visio. Uygulama](/office/vba/api/Visio.Application) nesnesi. Bu nesne, geçerli Visio. nesnesi, `Microsoft.Office.Interop.Visio.Application` ve `Microsoft.Office.Interop.Visio.Document` `Microsoft.Office.Interop.Visio.Page` nesnelerinin yanı sıra `Microsoft.Office.Interop.Visio.Documents` ve `Microsoft.Office.Interop.Visio.Pages` koleksiyonlarını içerir. Bu nesnelerin ve koleksiyonların her biri, onu işlemek ve etkileşim kurmak için erişebilirsiniz birçok yöntem ve özele sahiptir.

 Daha fazla bilgi için [Bkz. Microsoft.Office. Birlikte çalış -abilir -lik. Visio. Uygulama](/office/vba/api/Visio.Application), [Microsoft.Office. Birlikte çalış -abilir -lik. Visio. ,](/office/vba/api/Visio.Document)ve [Microsoft.Office. Birlikte çalış -abilir -lik. Visio. Sayfa](/office/vba/api/Visio.Page) nesneleri ve [microsoft.Office. Birlikte çalış -abilir -lik. Visio. Belgeler](/office/vba/api/Visio.Documents) ve [Microsoft.Office. Birlikte çalış -abilir -lik. Visio. Sayfa](/office/vba/api/Visio.Pages) koleksiyonları.

 Aşağıdaki bölümlerde, üst düzey nesneler ve birbirleriyle nasıl etkileşime geçmeleri kısaca açıklanmaktadır. Bu nesneler aşağıdaki nesneleri içerir:

- Uygulama nesnesi

- Belge nesnesi

- Sayfa nesnesi

### <a name="application-object"></a>Uygulama nesnesi
 The Microsoft. Office. Birlikte çalış -abilir -lik. Visio. Uygulama nesnesi Visio temsil eder ve diğer tüm nesnelerin üst öğesidir. Üyeleri genellikle Visio için geçerlidir. Microsoft'un özelliklerini ve yöntemlerini kullanabilirsiniz. Office. Birlikte çalış -abilir -lik. Visio. Uygulama ve `Microsoft.Office.Interop.Visio.ApplicationSettings` ortamı denetlemeye Visio.

 Eklenti VSTO microsoft'a erişin. Office. Birlikte çalış -abilir -lik. Visio. Sınıfının alanını kullanarak `Application` uygulama `ThisAddIn` nesnesi. Daha fazla bilgi için [bkz. VSTO Programlama.](../vsto/programming-vsto-add-ins.md)

### <a name="document-object"></a>Belge nesnesi
 The Microsoft. Office. Birlikte çalış -abilir -lik. Visio. Belge nesnesi, programlama ve programlama Visio. Çizim, kalıp veya şablon dosyasını temsil eder. Yeni bir Visio veya yeni bir belge ekleyebilirsiniz, yeni bir Microsoft oluşturabilirsiniz. Office. Birlikte çalış -abilir -lik. Visio. Microsoft'a eklenen belge nesnesi. Office. Birlikte çalış -abilir -lik. Visio. Microsoft'un belge koleksiyonu. Office. Birlikte çalış -abilir -lik. Visio. Uygulama nesnesi.

 Odak noktası olan belgeye etkin belge denir. `Microsoft.Office.Interop.Visio.Application.ActiveDocument`Microsoft.Office. Birlikte çalış -abilir -lik. Visio. Uygulama nesnesi.

### <a name="page-object"></a>Sayfa nesnesi
 The Microsoft. Office. Birlikte çalış -abilir -lik. Visio. Sayfa nesnesi, ön plan sayfasının veya arka plan sayfasının çizim alanıdır. Bir sayfanın ön `Microsoft.Office.Interop.Visio.Page.Background` plan mı yoksa arka plan sayfası mı olduğunu belirlemek için özelliğini kullanabilirsiniz.

 Şekiller oluşturmak için ve yöntemlerini içeren yöntemleri `Microsoft.Office.Interop.Visio.Page.DrawSpline` `Microsoft.Office.Interop.Visio.Page.DrawOval` kullanabilirsiniz. Ayrıca, kalıplardan ana verileri alabilir ve veya yöntemlerini kullanarak şekilleri bir sayfaya `Microsoft.Office.Interop.Visio.Page.Drop` `Microsoft.Office.Interop.Visio.Page.DropMany` yerleyebilirsiniz.

## <a name="use-the-visio-object-model-documentation"></a>Visio nesne modeli belgelerini kullanma
 Nesne modeliyle ilgili Visio bilgi için, Visio VBA nesne modeli başvurusuna başvurabilirsiniz. VBA nesne modeli başvurusu, Visio (VBA) koduna açık olduğu Visual Basic for Applications nesne modelini belgeler. Daha fazla bilgi için [bkz. Visio modeli başvurusu.](/office/vba/api/overview/visio/object-model)

 VBA nesne modeli başvurusunda yer alan tüm nesneler ve üyeler, birincil birlikte çalışma derlemesi (PIA) içindeki Visio ve üyelere karşılık geldi. Örneğin, `Document` VBA nesne modeli başvurusunda yer alan nesne Microsoft.Office. Birlikte çalış -abilir -lik. Visio. PiA'da belge Visio yazın. VBA nesne modeli başvurusu çoğu özellik, yöntem ve olay için kod örnekleri sağlar, ancak bu başvuruda VBA kodunu Visual Basic veya Visual C# diliyle oluşturmak istediğiniz bir Visio VSTO Eklenti projesinde kullanmak istediğiniz VBA kodunu Visual Studio.

> [!NOTE]
> Şu anda, birincil birlikte çalışma derlemesi için Visio belgeleri yoktur.

 İlgili kod örnekleri ve yazılım çözümleri oluşturmaya Visio araçlar için bkz. [Visio 2010 yazılım geliştirme seti.](https://www.microsoft.com/download/details.aspx?id=12365)

### <a name="additional-types-in-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemelerinde ek türler
 Uygulama farklılıkları nedeniyle VBA tarafından görülebilen birincil birlikte çalışma derlemelerinde türleri bulabilirsiniz. VBA, yalnızca doğrudan Visio ve üyeleri içeren bir nesne modeli görünümü sağlar. Birincil birlikte çalışma derlemeleri aynı nesne modelini ortaya çıkarır, ancak com nesne modelinde nesneleri yönetilen koda çeviren diğer arabirimleri, sınıfları ve üyeleri de içerir. Bu ek öğelerin doğrudan kodunda kullanılmaya yönelik değildir.

 Daha fazla bilgi için [bkz.](/previous-versions/office/office-12/ms247299(v=office.12)) Birincil birlikte çalışma derlemeleri ve Office derlemelerinde [sınıflara ve arabirimlere Office genel bakış.](../vsto/office-primary-interop-assemblies.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Belgelerle Visio çalışma](../vsto/working-with-visio-documents.md)
- [Farklı şekillerde Visio çalışma](../vsto/working-with-visio-shapes.md)
