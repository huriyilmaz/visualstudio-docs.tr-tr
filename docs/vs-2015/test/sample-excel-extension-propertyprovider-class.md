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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660430"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Örnek Excel Uzantısı: PropertyProvider Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu iç sınıf <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> sınıfını genişletir ve Kullanıcı arabirimi (UI) testlerini kaydetmek ve oynatmak için [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] öğeleri için özellik hizmetleri sağlar.

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel yöntemi
 @No__t_0 yöntemi, özellik sağlayıcısının belirtilen denetim için sunabileceği desteğin düzeyini gösteren bir sayı döndürür. Döndürülen değer arttıkça, özellik sağlayıcısı denetimi de destekleyebilir. Bu durumda, yöntemi, belirtilen denetimin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> özelliğinin değerini denetler. Değer "Excel" ise ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> bir `CellElement` olduğunu gösteriyorsa, yöntem en yüksek değeri döndürür; Aksi halde, hiçbir desteğin sağlanmadığını belirten sıfır döndürür.

## <a name="getpropertynames-method"></a>GetPropertyNames yöntemi
 Excel hücre denetiminin desteklenen özellikleri için özellik adlarının ve özellik tanımlayıcılarının bir sözlüğünü döndürür.

## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor yöntemi
 Bu yöntem, belirtilen özellik adı için önceden tanımlanmış özellik tanımlayıcısını almak üzere test çerçevesi tarafından çağırılır.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue ve SetPropertyValue yöntemleri
 @No__t_0 yöntemi, Excel 'den özellik değerini döndürmek için bu uzantının `Communicator` sınıfını kullanır. @No__t_0 yöntemi, özellik değerini ayarlamak için <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> sınıfını ve `Communicator` bileşenini kullanır. Bu yöntemler test çerçevesi tarafından çağırılır.

## <a name="code-generation-customization-methods"></a>Kod üretimi özelleştirme yöntemleri
 Bu yöntemler bu uzantı için uygulanmıyor. Bu nedenle, `null` döndürür ya da <xref:System.NotImplementedException> oluşturur.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider><xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
