---
title: 'Örnek Excel uzantısı: öğe sınıfları | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21c7777be710f0175708629eb9507b34f0d70be2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660447"
---
# <a name="sample-excel-extension-element-classes"></a>Örnek Excel Eklentisi: Öğe Sınıfları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantı, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> türetilen sınıfları kullanır ve [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] çalışma sayfası denetimini ve hücre denetimini temsil eder.

 Bu uzantının temel öğesi `ExcelElement`. @No__t_0 sınıfı ve `ExcelCellElement` sınıfı bu öğeden devralınır

## <a name="element-and-elementinformation-classes"></a>Element ve ElementInformation sınıfları
 @No__t_0, Excel uzantısı için tüm Kullanıcı arabirimi öğeleri için temel sınıftır ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> sınıfından devralır. `ElementInformation`, örnekteki öğe bilgisi sınıfları için temel sınıftır ve üyesi yoktur.

#### <a name="simple-properties-and-methods"></a>Basit özellikler ve Yöntemler
 Bu Üyeler `Name` özelliğinin değeri veya `ClassName` özelliğinin değeri gibi basit değerler döndürür ve kod net ve kolay okunabilir. Bazı değerler, daha sonra ele alınan `Utility` sınıfı kullanılarak döndürülür. Diğerleri Bu örnek uzantıyla ilgili olmadığından `null` döndürür. İki üye diğerlerinden daha ilginç: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> özelliği ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> yöntemi.

#### <a name="queryid-property"></a>QueryId özelliği
 Bu özellik, kayıttan yürütme sırasında denetimi benzersiz bir şekilde tanımlayan özellik adı-değer çiftleri tarafından oluşturulan bir koşul döndürür. Her türetilmiş denetim sınıfı için, geliştiricinin Kullanıcı arabiriminde denetimi bulmak için kullanabileceği bir <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> nesnesi döndürecek şekilde bu özelliği geçersiz kılması gerekir.

#### <a name="cacheproperties-method"></a>CacheProperties Yöntemi
 Bu yöntem, öğesine, önemli özelliklerin bir anlık görüntüsünü kaydetmesini bildirmek için kayıt işlemi sırasında test çerçevesi tarafından çağırılır. Bu, gerçek UI denetimi artık ekranda olmadığında bile özellikleri kullanılabilir halde tutar.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement ve WorksheetInformation sınıfları
 @No__t_0 sınıfı, test çerçevesindeki bir Excel çalışma sayfasını temsil eder ve `Element` temel sınıftan devralır. Excel çalışma sayfası nesnesiyle ilgili belirli bilgileri sağlamak için üç özellik geçersiz kılınır: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.

 @No__t_0, bu sınıfa COM 'un görünmesini sağlamak için de uygulanır.

 @No__t_0 sınıfı bir Excel çalışma sayfası hakkındaki bilgileri temsil eder. Bu örnek için yeterli olan yalnızca bir üyeye (`SheetName` özelliği) sahiptir.

## <a name="cellelement-and-cellinformation-classes"></a>CellElement ve CellInformation Sınıfları
 @No__t_0 sınıfı bir Excel hücresini temsil eder ve `Element` temel sınıftan devralır. Geçersiz kılınan üye, hücreyi tanımlamak için `RowIndex` ve `ColumnIndex` özelliklerini kullanan bir <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> döndüren <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> özelliğidir.

## <a name="utilities-and-excelutilities-classes"></a>Yardımcı programlar ve ExcelUtilities sınıfları
 İç `ExcelUtilities` sınıfı, teknoloji adı gibi bazı sabit değerler ve sağlanan pencere tanıtıcısının bir Excel çalışma sayfasını temsil edip etmediğini belirleyen bir yöntemi sağlar.

 @No__t_0 sınıfı, Kullanıcı arabirimi hakkında çeşitli bilgiler döndüren yardımcı yöntemlere sahiptir. Bazı yöntemler User32 gibi dış sistem dll 'Lerine doğrudan çağrılar kullanır **. DLL** ve **oleacc. DLL**, kullanıcı arabiriminden pencere tutamaçları almak için<strong>.</strong>

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.ComVisibleAttribute><xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
