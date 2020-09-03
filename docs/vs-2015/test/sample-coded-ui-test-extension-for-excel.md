---
title: Excel için kodlanmış UI testi uzantısı örneği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672235"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Excel için Kodlanmış UI Testi Uzantısı Örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örneğin uzantı bileşeni, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] KODLANMıŞ UI test sürecinde çalışır ve temel aldığı sınıfla biraz hiyerarşik olarak yapılır `ExtensionPackage` . `TechnologyManager`, `ActionFilter` Ve sınıfları, `PropertyProvider` en üst düzeydeki denetim öğeleriyle birlikte bir sonraki düzeyindedir.

 ![Excel test uzantısı mimarisi](../test/media/excel-extarch.png "Excel_ExtArch") Excel genişletme mimarisi

## <a name="extension-points"></a>Uzantı noktaları
 Bu sınıflar, için kodlanmış UI testini etkinleştirmek üzere örneğe uygulanan uzantı noktalarını temsil eder [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .

### <a name="extensionpackage"></a>ExtensionPackage
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>Sınıfından devralınmış, bu, KODLANMıŞ UI testi uzantısının giriş noktasıdır. Bu soyut sınıfı uygulamak, kodlanmış UI test çerçevesini Özel UI test teknoloji yöneticinize, UI test özelliği sağlayıcısına ve yeni kullanıcı arabirimini test etmek için UI test eylem filtresine iç erişim sağlar. Daha fazla bilgi için bkz. [ExtensionPackage Sınıfı](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>Sınıfından devralınmış Bu sınıf, test kaydı ve kayıttan yürütme için bir teknoloji Yöneticisi sağlar. Daha fazla bilgi için bkz. [TechnologyManager sınıfı](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 [Uitestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) sınıfından devralınan bu sınıf, benzer test eylemi sonuçlarını tek bir test sonucuna toplamak için bir temel sınıf sağlar. Daha fazla bilgi için bkz. [ActionFilter sınıfı](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Teknoloji öğeleri
 Sınıfından devralınan bir temel sınıf, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> kaydedilip OYNATıLABILECEK UI testlerinizde bulunan teknoloji öğeleri için temel sağlar. Daha fazla bilgi için bkz. [öğe sınıfları](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>Sınıfından devralınmış Bu sınıf, test kaydı ve kayıttan yürütme için Kullanıcı arabirimi öğelerinin özelliklerini desteklemek için bir temel sınıf sağlar. Daha fazla bilgi için bkz. [PropertyProvider sınıfı](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage Sınıfı](../test/sample-excel-extension-extensionpackage-class.md)
- [TechnologyManager Sınıfı](../test/sample-excel-extension-technologymanager-class.md)
- [ActionFilter Sınıfı](../test/sample-excel-extension-actionfilter-class.md)
- [Element Sınıfları](../test/sample-excel-extension-element-classes.md)
- [PropertyProvider Sınıfı](../test/sample-excel-extension-propertyprovider-class.md)
