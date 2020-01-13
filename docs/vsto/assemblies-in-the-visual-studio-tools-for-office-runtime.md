---
title: Office çalışma zamanı için Visual Studio Araçları derlemeler
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
ms.openlocfilehash: b2fc47aa917fa9c9d5351fd313ec46ae4aaa0664
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918791"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio Araçları derlemeler
  Bir Office projesi oluşturduğunuzda, Visual Studio, proje türü ve projenin hedef .NET Framework için kullanılan [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] derlemelerine otomatik olarak başvurular ekler. .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ve [!INCLUDE[net_v45](includes/net-v45-md.md)]için Office uzantılarında farklı derlemeler vardır. Office uzantıları hakkında daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenet_v45includesnet-v45-mdmd"></a>.NET Framework 4 ve [!INCLUDE[net_v45](includes/net-v45-md.md)] için Office uzantılarında derlemeler
 Aşağıdaki tabloda [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve [!INCLUDE[net_v45](includes/net-v45-md.md)]için Office uzantılarında dahil olan derlemeler listelenmektedir. Bu derlemelerdeki ad alanları ve türler hakkındaki belgeler için bkz. [Visual Studio &#40;&#41;'da yönetilen başvuru Office geliştirme](managed-reference-office-development-in-visual-studio.md).

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Aşağıdaki türleri sağlar:<br /><br /> -Şerit özelleştirmeleri ve akıllı etiketler oluşturmak için türler. **Note:**      Akıllı Etiketler [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](includes/word-14-short-md.md)]kullanım dışıdır.<br />-VSTO Eklentilerindeki belge düzeyi özelleştirmelerde ve özel görev bölmelerinde eylemler bölmesi oluşturmaya yönelik türler.|
|Microsoft.Office.Tools.Excel.dll|Excel projeleri ve destekleyici türler için konak öğelerini ve konak denetimlerini temsil eden arabirimler sağlar. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO eklentilerinde özel form bölgeleri oluşturmak için kullanabileceğiniz türler sağlar.|
|Microsoft.Office.Tools.Word.dll|, Word projeleri ve destekleyici türler için konak öğelerini ve konak denetimlerini temsil eden arabirimler sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](automating-word-by-using-extended-objects.md).|
|Microsoft. Office. Tools. v 4.0. Framework. dll|Aşağıdaki türleri sağlar:<br /><br /> -Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulabilecek özel durumlar.<br />-Outlook form bölgeleri oluştururken kullanabileceğiniz öznitelikler.|
|Microsoft.Office.Tools.dll|Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan ve doğrudan kodunuzdan kullanılmaya yönelik olmayan türler sağlar.|
|Microsoft. VisualStudio. Tools. Applications. Runtime. dll|Aşağıdaki türleri sağlar:<br /><br /> -Bir belge düzeyi özelleştirmesinde veri nesnelerini önbelleğe almak için kullanabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği ve <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> arabirimi. Daha fazla bilgi için bkz. [önbelleği verileri](caching-data.md).<br />-Bir Office çözümü için ClickOnce yükleyicisinin son adımı olarak ek yükleme adımları çalıştırmak için uygulayabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> arabirimi. Daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](deploying-an-office-solution-by-using-clickonce.md).<br />-Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulabilecek özel durumlar.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll|Aşağıdaki türleri sağlar:<br /><br /> -Belgelere özelleştirme derlemeleri iliştirmek ve belgelerdeki önbelleğe alınmış verilere erişmek için kullanabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı. Daha fazla bilgi için, bkz. [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde önbelleğe alınmış verilerin hiyerarşisini temsil eden birkaç sınıf. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](accessing-data-in-documents-on-the-server.md).|

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](includes/net-v45-md.md)] hedefleyen projeler aşağıdaki derlemelere de başvurur. Bu derlemeler [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] yeniden dağıtılabilir bir parçası değildir. Bunun yerine, çözümünüz ile dağıtılması gereken bağımlı derlemelerdir. Varsayılan olarak, projeniz için derleme çıkış klasörüne kopyalanır (Bu derlemelerin **Copy Local** özelliği **true**olarak ayarlanır). Projenizi ClickOnce kullanarak dağıtırsanız, bu derlemeler oluşturulan pakete dahil edilir.

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|VSTO eklenti projelerinde oluşturulan `ThisAddIn` sınıfı için temel sınıfları ve tüm projelerde oluşturulan Şerit sınıfını sağlar.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Aşağıdaki türleri sağlar:<br /><br /> -Excel için belge düzeyi projelerinde oluşturulan `ThisWorkbook` ve `Sheet` sınıfları için temel sınıflar.<br />-Excel projelerinde çalışma sayfalarında kullanabileceğiniz denetimleri Windows Forms.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Outlook projelerinde oluşturulan `ThisAddIn` ve form bölgesi sınıfları için temel sınıflar sağlar.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Aşağıdaki türleri sağlar:<br /><br /> -Word için belge düzeyi projelerinde oluşturulan `ThisDocument` sınıfı için temel sınıflar.<br />-Word projelerindeki belgelerde kullanabileceğiniz denetimleri Windows Forms.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3,5 için Office uzantılarında derlemeler
 Aşağıdaki tabloda .NET Framework 3,5 için Office uzantılarında eklenen derlemeler listelenmektedir. Bu derlemelerdeki ad alanları ve sınıflar hakkındaki belgeler için, Visual Studio 2008 belgelerindeki şu başvuru bölümüne bakın: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md).

|Bütünleştirilmiş kod adı|Açıklama|
|-------------------|-----------------|
|Microsoft. Office. Tools. Common. v 9.0. dll|Aşağıdaki türleri sağlar:<br /><br /> -VSTO eklentileri için Microsoft. Office. Tools. AddIn temel sınıfı.<br />-Şerit özelleştirmeleri ve akıllı etiketler oluşturmak için sınıflar. **Note:**      Akıllı Etiketler [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](includes/word-14-short-md.md)]kullanım dışıdır.<br />-VSTO Eklentilerindeki belge düzeyi özelleştirmelerde ve özel görev bölmelerinde eylemler bölmesi oluşturmaya yönelik sınıflar.|
|Microsoft. Office. Tools. Excel. v 9.0. dll|Excel çözümleri için konak öğeleri ve konak denetimleri sağlar. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](automating-excel-by-using-extended-objects.md).|
|Microsoft. Office. Tools. Outlook. v 9.0. dll|Outlook VSTO eklentilerinde özel form bölgeleri oluşturmak için kullanabileceğiniz sınıflar sağlar.|
|Microsoft. Office. Tools. Word. v 9.0. dll|Word çözümleri için konak öğeleri ve konak denetimleri sağlar. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](automating-word-by-using-extended-objects.md).|
|Microsoft. Office. Tools. v 9.0. dll|Aşağıdaki türleri sağlar:<br /><br /> -Belge düzeyi özelleştirmelerde konak denetimleri için veri bağlama özellikleri sağlayan [Remotebindadblecomponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) sınıfı.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft. VisualStudio. Tools. Applications. Runtime. v 9.0. dll|Aşağıdaki türleri sağlar:<br /><br /> -Bir belge düzeyi özelleştirmesinde veri nesnelerini önbelleğe almak için kullanabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği ve <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> arabirimi. Daha fazla bilgi için bkz. [önbelleği verileri](caching-data.md).<br />-Office çalışma zamanı için Visual Studio Araçları tarafından oluşturulabilecek özel durumlar.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|Microsoft. VisualStudio. Tools. Applications. Runtime. v 10.0. dll|, Bir Office çözümünün ClickOnce yükleyicisinin son adımı olarak ek yükleme adımları çalıştırmak için uygulayabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> arabirimini sağlar. Daha fazla bilgi için bkz. [Gelişmiş Office çözüm dağıtımı](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft. VisualStudio. Tools. Applications. ServerDocument. v 10.0. dll|Aşağıdaki türleri sağlar:<br /><br /> -Program aracılığıyla özelleştirme derlemelerini belgelere eklemek ve belgelerde önbelleğe alınmış verilere erişmek için kullanabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı. Daha fazla bilgi için, bkz. [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Belge düzeyi özelleştirmesinde önbelleğe alınmış verilerin hiyerarşisini temsil eden birkaç sınıf. Daha fazla bilgi için bkz. [sunucudaki belgelerdeki verilere erişme](accessing-data-in-documents-on-the-server.md).|
|Microsoft. VisualStudio. Tools. Office. Runtime. v 10.0. dll|Aşağıdaki türleri sağlar:<br /><br /> -Office için güven sağlamak üzere Kullanıcı ekleme listesi girdileri oluşturmak için kullanabileceğiniz Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry ve Microsoft. VisualStudio. Tools. Office. Runtime. Security. Userlarıonlist sınıfları .NET Framework 3,5 ' i hedefleyen çözümler.<br />-Office çalışma zamanı altyapısının Visual Studio Araçları parçası olan diğer türler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](visual-studio-tools-for-office-runtime-overview.md)
- [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](visual-studio-tools-for-office-runtime-installation-scenarios.md)
