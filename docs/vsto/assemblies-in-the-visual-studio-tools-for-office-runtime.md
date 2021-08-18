---
title: Office için Visual Studio Araçları çalışma zamanında derlemeler
description: Visual Studio otomatik olarak Office için Visual Studio Araçları çalışma zamanı derlemelerine başvuruları eklediği hakkında bilgi edinin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a811040f9106666a86778db4a8278d0f5f450855
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083784"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları çalışma zamanında derlemeler
  bir Office projesi oluşturduğunuzda, Visual Studio proje [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] türü ve projenin hedef .NET Framework için kullanılan derlemelere otomatik olarak başvurular ekler. .NET Framework 3,5, ve Office uzantılarında farklı derlemeler vardır [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](includes/net-v45-md.md)] . Office uzantıları hakkında daha fazla bilgi için bkz. [Office için Visual Studio Araçları çalışma zamanına genel bakış](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>.NET Framework 4 ve için Office uzantılarında derlemeler[!INCLUDE[net_v45](includes/net-v45-md.md)]
 aşağıdaki tabloda, ve için Office uzantılarına dahil olan derlemeler listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](includes/net-v45-md.md)] . bu derlemelerdeki ad alanları ve türler hakkındaki belgeler için bkz. [Visual Studio&#41;&#40;yönetilen başvuru Office geliştirme ](managed-reference-office-development-in-visual-studio.md).

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Aşağıdaki türleri sağlar:<br /><br /> -Şerit özelleştirmeleri ve akıllı etiketler oluşturmak için türler. **Note:**      Akıllı Etiketler ve ' de kullanım dışıdır [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-VSTO eklentilerdeki belge düzeyi özelleştirmelerde ve özel görev bölmelerinde eylemler bölmesi oluşturmaya yönelik türler.|
|Microsoft.Office.Tools.Excel.dll|Excel projeleri ve destekleyici türler için konak öğelerini ve konak denetimlerini temsil eden arabirimler sağlar. daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Excel otomatikleştirme](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|, Outlook VSTO eklentilerinde özel form bölgeleri oluşturmak için kullanabileceğiniz türler sağlar.|
|Microsoft.Office.Tools.Word.dll|, Word projeleri ve destekleyici türler için konak öğelerini ve konak denetimlerini temsil eden arabirimler sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Aşağıdaki türleri sağlar:<br /><br /> -Office için Visual Studio Araçları çalışma zamanı tarafından oluşturulabilecek özel durumlar.<br />-Outlook form bölgeleri oluştururken kullanabileceğiniz öznitelikler.|
|Microsoft.Office.Tools.dll|Office için Visual Studio Araçları çalışma zamanı altyapısının parçası olan ve doğrudan kodunuzdan kullanılmaya yönelik olmayan türler sağlar.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Aşağıdaki türleri sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Belge düzeyi özelleştirmesindeki veri nesnelerini önbelleğe almak için kullanabileceğiniz öznitelik ve arabirim. Daha fazla bilgi için bkz. [önbelleği verileri](caching-data.md).<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> bir Office çözümü için ClickOnce yükleyicisinin son adımı olarak ek yükleme adımları çalıştırmak için uygulayabileceğiniz arabirim. daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](deploying-an-office-solution-by-using-clickonce.md).<br />-Office için Visual Studio Araçları çalışma zamanı tarafından oluşturulabilecek özel durumlar.<br />-Office için Visual Studio Araçları çalışma zamanı altyapısının parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Aşağıdaki türleri sağlar:<br /><br /> -Belgelere <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> özelleştirme derlemeleri iliştirmek ve belgelerdeki önbelleğe alınmış verilere erişmek için kullanabileceğiniz sınıfı. Daha fazla bilgi için, bkz. [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde önbelleğe alınmış verilerin hiyerarşisini temsil eden birkaç sınıf. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](accessing-data-in-documents-on-the-server.md).|

 Veya öğesini hedefleyen projeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](includes/net-v45-md.md)] Aşağıdaki derlemelere de başvurur. Bu derlemeler yeniden dağıtılabilir bir parçası değildir [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] . Bunun yerine, çözümünüz ile dağıtılması gereken bağımlı derlemelerdir. Varsayılan olarak, projeniz için derleme çıkış klasörüne kopyalanır (Bu derlemelerin **Copy Local** özelliği **true** olarak ayarlanır). projenizi ClickOnce kullanarak dağıtırsanız, bu derlemeler oluşturulan pakete dahil edilir.

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|`ThisAddIn`VSTO Add-In projelerinde oluşturulan sınıf için temel sınıfları ve tüm projelerde oluşturulan şerit sınıfını sağlar.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Aşağıdaki türleri sağlar:<br /><br /> - `ThisWorkbook` `Sheet` Excel için belge düzeyi projelerdeki oluşturulan ve sınıfların temel sınıfları.<br />-Excel projelerindeki çalışma sayfalarında kullanabileceğiniz denetimleri Windows Forms.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|`ThisAddIn`Outlook projelerindeki oluşturulan ve form bölgesi sınıfları için temel sınıflar sağlar.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Aşağıdaki türleri sağlar:<br /><br /> - `ThisDocument` Word için belge düzeyi projelerinde oluşturulan sınıfın temel sınıfları.<br />-Word projelerindeki belgelerde kullanabileceğiniz denetimleri Windows Forms.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3,5 Office uzantılarında derlemeler
 aşağıdaki tabloda, .NET Framework 3,5 Office uzantılarında dahil olan derlemeler listelenmektedir. bu derlemelerdeki ad alanları ve sınıflar hakkındaki belgeler için Visual Studio 2008 belgelerinde aşağıdaki başvuru bölümüne bakın: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Aşağıdaki türleri sağlar:<br /><br /> -Microsoft. Office. VSTO eklentileri için Tools. addın temel sınıfı.<br />-Şerit özelleştirmeleri ve akıllı etiketler oluşturmak için sınıflar. **Note:**      Akıllı Etiketler ve ' de kullanım dışıdır [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-VSTO eklentilerdeki belge düzeyi özelleştirmelerde ve özel görev bölmelerinde eylemler bölmesi oluşturmaya yönelik sınıflar.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Excel çözümleri için konak öğeleri ve konak denetimleri sağlar. daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Excel otomatikleştirme](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|, Outlook VSTO eklentilerinde özel form bölgeleri oluşturmak için kullanabileceğiniz sınıflar sağlar.|
|Microsoft.Office.Tools.Word.v9.0.dll|Word çözümleri için konak öğeleri ve konak denetimleri sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Aşağıdaki türleri sağlar:<br /><br /> -Belge düzeyi özelleştirmelerde konak denetimleri için veri bağlama özellikleri sağlayan [Remotebindadblecomponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) sınıfı.<br />-Office için Visual Studio Araçları çalışma zamanı altyapısının parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Aşağıdaki türleri sağlar:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Belge düzeyi özelleştirmesindeki veri nesnelerini önbelleğe almak için kullanabileceğiniz öznitelik ve arabirim. Daha fazla bilgi için bkz. [önbelleği verileri](caching-data.md).<br />-Office için Visual Studio Araçları çalışma zamanı tarafından oluşturulabilecek özel durumlar.<br />-Office için Visual Studio Araçları çalışma zamanı altyapısının parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|, <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> bir Office çözümü için ClickOnce yükleyicisinin son adımı olarak ek yükleme adımları çalıştırmak için uygulayabileceğiniz arabirimi sağlar. daha fazla bilgi için bkz. [gelişmiş Office çözüm dağıtımı](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Aşağıdaki türleri sağlar:<br /><br /> -Belgeler <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> için programlı olarak özelleştirme derlemeleri iliştirmek ve belgelerdeki önbelleğe alınmış verilere erişmek için kullanabileceğiniz sınıfı. Daha fazla bilgi için, bkz. [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde önbelleğe alınmış verilerin hiyerarşisini temsil eden birkaç sınıf. Daha fazla bilgi için [bkz. sunucusundaki belgelerde verilere erişme.](accessing-data-in-documents-on-the-server.md)|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Aşağıdaki türleri sağlar:<br /><br /> - Microsoft.VisualStudio.Tools. Office. Runtime.Security.AddInSecurityEntry ve Microsoft.VisualStudio.Tools. Office. Runtime.Security.UserInclusionList sınıfları, 3.5'i hedef alan Office çözümlerine güven vermek üzere kullanıcı ekleme listesi .NET Framework oluşturabilirsiniz.<br />- Çalışma zamanı altyapısının Office için Visual Studio Araçları olan ve doğrudan kodunuzdan kullanılmaya yönelik olmayan diğer türler.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office için Visual Studio Araçları çalışma zamanının genel bakışı](visual-studio-tools-for-office-runtime-overview.md)
- [Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları](visual-studio-tools-for-office-runtime-installation-scenarios.md)
