---
title: Office çalışma zamanı için Visual Studio Araçları derlemeler
description: Visual Studio 'Nun Office çalışma zamanı derlemeleri için Visual Studio Araçları otomatik olarak başvurular eklemesine ilişkin bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86c3c2b77b6bbea1e609bbea092b44bd1dee1dd4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848306"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio Araçları derlemeler
  Bir Office projesi oluşturduğunuzda, Visual Studio, proje [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] türü ve projenin hedef .NET Framework için kullanılan derlemelere otomatik olarak başvurular ekler. .NET Framework 3,5, ve için Office uzantılarında farklı derlemeler vardır [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](includes/net-v45-md.md)] . Office uzantıları hakkında daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>.NET Framework 4 için Office uzantılarında derlemeler ve [!INCLUDE[net_v45](includes/net-v45-md.md)]
 Aşağıdaki tabloda, ve için Office uzantılarında dahil olan derlemeler listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](includes/net-v45-md.md)] . Bu derlemelerdeki ad alanları ve türler hakkındaki belgeler için bkz. [Visual Studio 'Da Office geliştirme &#40;yönetilen başvuru&#41;](managed-reference-office-development-in-visual-studio.md).

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Aşağıdaki türleri sağlar:<br /><br /> -Şerit özelleştirmeleri ve akıllı etiketler oluşturmak için türler. **Note:**      Akıllı Etiketler ve ' de kullanım dışıdır [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-VSTO Eklentilerindeki belge düzeyi özelleştirmelerde ve özel görev bölmelerinde eylemler bölmesi oluşturmaya yönelik türler.|
|Microsoft.Office.Tools.Excel.dll|Excel projeleri ve destekleyici türler için konak öğelerini ve konak denetimlerini temsil eden arabirimler sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Excel 'ı otomatikleştirme](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO eklentilerinde özel form bölgeleri oluşturmak için kullanabileceğiniz türler sağlar.|
|Microsoft.Office.Tools.Word.dll|, Word projeleri ve destekleyici türler için konak öğelerini ve konak denetimlerini temsil eden arabirimler sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Aşağıdaki türleri sağlar:<br /><br /> -Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulabilecek özel durumlar.<br />-Outlook form bölgeleri oluştururken kullanabileceğiniz öznitelikler.|
|Microsoft.Office.Tools.dll|Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan ve doğrudan kodunuzdan kullanılmaya yönelik olmayan türler sağlar.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Aşağıdaki türleri sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Belge düzeyi özelleştirmesindeki veri nesnelerini önbelleğe almak için kullanabileceğiniz öznitelik ve arabirim. Daha fazla bilgi için bkz. [önbelleği verileri](caching-data.md).<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Bir Office çözümü Için ClickOnce yükleyicisinin son adımı olarak ek yükleme adımları çalıştırmak için uygulayabileceğiniz arabirim. Daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](deploying-an-office-solution-by-using-clickonce.md).<br />-Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulabilecek özel durumlar.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Aşağıdaki türleri sağlar:<br /><br /> -Belgelere <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> özelleştirme derlemeleri iliştirmek ve belgelerdeki önbelleğe alınmış verilere erişmek için kullanabileceğiniz sınıfı. Daha fazla bilgi için, bkz. [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde önbelleğe alınmış verilerin hiyerarşisini temsil eden birkaç sınıf. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](accessing-data-in-documents-on-the-server.md).|

 Veya öğesini hedefleyen projeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](includes/net-v45-md.md)] Aşağıdaki derlemelere de başvurur. Bu derlemeler yeniden dağıtılabilir bir parçası değildir [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] . Bunun yerine, çözümünüz ile dağıtılması gereken bağımlı derlemelerdir. Varsayılan olarak, projeniz için derleme çıkış klasörüne kopyalanır (Bu derlemelerin **Copy Local** özelliği **true** olarak ayarlanır). Projenizi ClickOnce kullanarak dağıtırsanız, bu derlemeler oluşturulan pakete dahil edilir.

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|`ThisAddIn`VSTO Add-In projelerinde oluşturulan sınıf için temel sınıfları ve tüm projelerde oluşturulan Şerit sınıfını sağlar.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Aşağıdaki türleri sağlar:<br /><br /> - `ThisWorkbook` `Sheet` Excel için belge düzeyi projelerde oluşturulan ve sınıfların temel sınıfları.<br />-Excel projelerinde çalışma sayfalarında kullanabileceğiniz denetimleri Windows Forms.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|`ThisAddIn`Outlook projelerinde oluşturulan ve form bölgesi sınıfları için temel sınıflar sağlar.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Aşağıdaki türleri sağlar:<br /><br /> - `ThisDocument` Word için belge düzeyi projelerinde oluşturulan sınıfın temel sınıfları.<br />-Word projelerindeki belgelerde kullanabileceğiniz denetimleri Windows Forms.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3,5 için Office uzantılarında derlemeler
 Aşağıdaki tabloda .NET Framework 3,5 için Office uzantılarında eklenen derlemeler listelenmektedir. Bu derlemelerdeki ad alanları ve sınıflar hakkındaki belgeler için, Visual Studio 2008 belgelerindeki şu başvuru bölümüne bakın: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Aşağıdaki türleri sağlar:<br /><br /> -VSTO eklentileri için Microsoft. Office. Tools. AddIn temel sınıfı.<br />-Şerit özelleştirmeleri ve akıllı etiketler oluşturmak için sınıflar. **Note:**      Akıllı Etiketler ve ' de kullanım dışıdır [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-VSTO Eklentilerindeki belge düzeyi özelleştirmelerde ve özel görev bölmelerinde eylemler bölmesi oluşturmaya yönelik sınıflar.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Excel çözümleri için konak öğeleri ve konak denetimleri sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Excel 'ı otomatikleştirme](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Outlook VSTO eklentilerinde özel form bölgeleri oluşturmak için kullanabileceğiniz sınıflar sağlar.|
|Microsoft.Office.Tools.Word.v9.0.dll|Word çözümleri için konak öğeleri ve konak denetimleri sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Aşağıdaki türleri sağlar:<br /><br /> -Belge düzeyi özelleştirmelerde konak denetimleri için veri bağlama özellikleri sağlayan [Remotebindadblecomponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) sınıfı.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Aşağıdaki türleri sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Belge düzeyi özelleştirmesindeki veri nesnelerini önbelleğe almak için kullanabileceğiniz öznitelik ve arabirim. Daha fazla bilgi için bkz. [önbelleği verileri](caching-data.md).<br />-Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulabilecek özel durumlar.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|, <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Bir Office çözümünün ClickOnce yükleyicisinin son adımı olarak ek yükleme adımları çalıştırmak için uygulayabileceğiniz arabirimi sağlar. Daha fazla bilgi için bkz. [Gelişmiş Office çözüm dağıtımı](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Aşağıdaki türleri sağlar:<br /><br /> -Belgeler <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> için programlı olarak özelleştirme derlemeleri iliştirmek ve belgelerdeki önbelleğe alınmış verilere erişmek için kullanabileceğiniz sınıfı. Daha fazla bilgi için, bkz. [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde önbelleğe alınmış verilerin hiyerarşisini temsil eden birkaç sınıf. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Aşağıdaki türleri sağlar:<br /><br /> -.NET Framework 3,5 ' i hedefleyen Office çözümlerine güven sağlamak üzere Kullanıcı ekleme listesi girdileri oluşturmak için kullanabileceğiniz Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry ve Microsoft. VisualStudio. Tools. Office. Runtime. Security. Userlarıonlist sınıfları.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](visual-studio-tools-for-office-runtime-overview.md)
- [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](visual-studio-tools-for-office-runtime-installation-scenarios.md)
