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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660447"
---
# <a name="sample-excel-extension-element-classes"></a>Örnek Excel Eklentisi: Öğe Sınıfları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantı, ' den türetilmiş sınıfları kullanır <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> ve Içindeki çalışma sayfası denetimi ve hücre denetimini temsil eder [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .

 Bu uzantının temel öğesi `ExcelElement` . `ExcelWorksheetElement`Sınıfı ve `ExcelCellElement` sınıfı bu öğeden devralınır

## <a name="element-and-elementinformation-classes"></a>Element ve ElementInformation sınıfları
 , `Element` Excel uzantısı için tüm Kullanıcı arabirimi öğeleri için temel sınıftır ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> sınıfından devralır. `ElementInformation` , örnekteki öğe bilgisi sınıfları için temel sınıftır ve üyesi yoktur.

#### <a name="simple-properties-and-methods"></a>Basit özellikler ve Yöntemler
 Bu Üyeler özelliğin değeri veya özelliğin değeri gibi basit değerler döndürür `Name` `ClassName` ve kod net ve kolay okunabilir. Bazı değerler `Utility` , daha sonra ele alınan sınıfı kullanılarak döndürülür. Diğerleri `null` Bu örnek uzantıyla ilgili olmadıkları için döndürülür. İki üye diğerlerinden daha ilginç: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> özellik ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> yöntemi.

#### <a name="queryid-property"></a>QueryId özelliği
 Bu özellik, kayıttan yürütme sırasında denetimi benzersiz bir şekilde tanımlayan özellik adı-değer çiftleri tarafından oluşturulan bir koşul döndürür. Her türetilmiş denetim sınıfı için, geliştiricinin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> Kullanıcı arabiriminde denetimi bulmak için kullanabileceği bir nesne döndürmek için bu özelliği geçersiz kılması gerekir.

#### <a name="cacheproperties-method"></a>CacheProperties Yöntemi
 Bu yöntem, öğesine, önemli özelliklerin bir anlık görüntüsünü kaydetmesini bildirmek için kayıt işlemi sırasında test çerçevesi tarafından çağırılır. Bu, gerçek UI denetimi artık ekranda olmadığında bile özellikleri kullanılabilir halde tutar.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement ve WorksheetInformation sınıfları
 `WorksheetElement`Sınıfı, test çerçevesindeki bir Excel çalışma sayfasını temsil eder ve `Element` temel sınıftan devralır. Excel çalışma sayfası nesnesiyle ilgili belirli bilgileri sağlamak için üç özellik geçersiz kılınır: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A> , <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> , ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A> .

 <xref:System.Runtime.InteropServices.ComVisibleAttribute>Ayrıca, bu SıNıFA com tarafından görünür hale getirmek için de uygulanır.

 `WorksheetInformation`Sınıfı, bir Excel çalışma sayfası hakkındaki bilgileri temsil eder. Bu örnek için yeterli olan yalnızca bir üyeye sahiptir, `SheetName` özelliği.

## <a name="cellelement-and-cellinformation-classes"></a>CellElement ve CellInformation Sınıfları
 `CellElement`Sınıfı bir Excel hücresini temsil eder ve `Element` temel sınıftan devralır. Geçersiz kılınan üye, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> `RowIndex` hücreyi tanımlamak için ve özelliklerini kullanan bir öğesi döndüren özelliğidir `ColumnIndex` .

## <a name="utilities-and-excelutilities-classes"></a>Yardımcı programlar ve ExcelUtilities sınıfları
 İç `ExcelUtilities` sınıf, teknoloji adı gibi bazı sabit değerler ve sağlanan pencere tanıtıcısının bir Excel çalışma sayfasını temsil edip etmediğini belirleyen bir yöntemi sağlar.

 `Utilities`Sınıfında, Kullanıcı arabirimi hakkında çeşitli bilgiler döndüren yardımcı yöntemler vardır. Bazı yöntemler, kullanıcı arabiriminden pencere tutamaçları almak için **USER32.DLL** ve **OLEACC.DLL**gibi dış sistem dll 'lerine doğrudan çağrılar kullanır<strong>.</strong>

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
