---
title: 'Örnek Excel uzantısı: PropertyProvider sınıfı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ae254f85b00c47ba00250641f7afe0a638ceabc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660430"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Örnek Excel Uzantısı: PropertyProvider Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu iç sınıf, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> sınıfını genişletir ve [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] öğe ve kullanıcı ARABIRIMI (UI) testlerini kaydetmek ve oynatmak için özellik hizmetleri sağlar.

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel yöntemi
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A>Yöntemi, özellik sağlayıcısının belirtilen denetim için sunabileceği desteğin düzeyini gösteren bir sayı döndürür. Döndürülen değer arttıkça, özellik sağlayıcısı denetimi de destekleyebilir. Bu durumda, yöntemi, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> belirtilen denetimin özelliğinin değerini denetler. Değer "Excel" ise ve olduğunu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> gösteriyorsa `CellElement` , yöntem en yüksek değeri döndürür; Aksi takdirde, hiçbir desteğin sağlandığını belirten sıfır döndürür.

## <a name="getpropertynames-method"></a>GetPropertyNames yöntemi
 Excel hücre denetiminin desteklenen özellikleri için özellik adlarının ve özellik tanımlayıcılarının bir sözlüğünü döndürür.

## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor yöntemi
 Bu yöntem, belirtilen özellik adı için önceden tanımlanmış özellik tanımlayıcısını almak üzere test çerçevesi tarafından çağırılır.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue ve SetPropertyValue yöntemleri
 `GetPropertyValue`Yöntemi, `Communicator` Excel 'den özellik değerini döndürmek için bu uzantının sınıfını kullanır. `SetPropertyValue`Yöntemi, <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> `Communicator` özellik değerini ayarlamak için sınıfını ve bileşenini kullanır. Bu yöntemler test çerçevesi tarafından çağırılır.

## <a name="code-generation-customization-methods"></a>Kod üretimi özelleştirme yöntemleri
 Bu yöntemler bu uzantı için uygulanmıyor. Bu nedenle, döndürür `null` ya da atar <xref:System.NotImplementedException> .

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
