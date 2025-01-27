---
title: .NET Framework Office projelerinde tasarım değişiklikleri .NET Framework
description: 4 veya daha sonraki bir Visual Studio hedef Office projelerinin tasarımına yönelik .NET Framework öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b86909364d214ebb28a77a90716773c236a3c68c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635430"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 veya Office 4.5'i hedef alan .NET Framework değişiklikleri
  'den [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] başlayarak Visual Studio veya sonrakini hedef alan Office projelerinin tasarımında bazı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] değişiklikler yaptı. Visual Studio'ın önceki sürümlerindeki Office projelerini biliyorsanız, Office 4.0 veya sonraki sürümlerini hedef alan .NET Framework projeleri geliştirmeden önce bu değişiklikleri biliyorsanız. Varsayılan olarak, Visual Studio 2013 veya sonraki bir .NET Framework 4.0 veya sonraki bir sonraki bir 4.0 veya sonraki bir sonraki bir 4.0'ı kullanarak oluşturabilirsiniz.

 Aşağıdaki bölümlerde, proje tasarımı Office aşağıdaki bölümlerde açıklanmaktadır.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio 2010 Araçları'nın arabirim Office anlama
 veya sonraki bir Office hedef alan bir Office projesi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] geliştirirken, Visual Studio 2010 Tools for Office arabirimidir. Bu, bu türlerin sınıf olduğu önceki [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sürümlerinden önemli bir değişikliktir. Örneğin, veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] hedefle, <xref:Microsoft.Office.Tools.Excel.Worksheet> ve türleri sınıflar yerine <xref:Microsoft.Office.Tools.Word.Document> arabirimler olur. Daha fazla bilgi için bkz. [Office için Visual Studio Araçları genel bakış.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

 Doğrudan önceki sürümlerinde örneği oluşturmanın herhangi bir türü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] için, artık bu türlerin örneklerini `Globals.Factory` almak için nesnesinin yöntemlerini kullanır. Örneğin, arabirimini uygulayan bir nesnesi <xref:Microsoft.Office.Tools.Excel.SmartTag> almak için yöntemini `Globals.Factory.CreateSmartTag` kullanın. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Excel 4 veya .NET Framework 4.5'e .NET Framework Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4.5'e veya Office projelerinde Şerit özelleştirmelerini .NET Framework güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 veya Outlook 4.5'e .NET Framework projelerinde form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Office projelerinde yeni temel sınıflar
 Office çalışma zamanı için Visual Studio 2010 Araçları'nın yeni arabirim tabanlı tasarımı, , ve gibi Office projelerinde oluşturulan `ThisDocument` `ThisWorkbook` sınıfları `ThisAddIn` etkiler. Çerçevenin Office 3.5 ve önceki sürümlerini .NET Framework projelerinde oluşturulan bu sınıflar , ve gibi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] `Microsoft.Office.Tools.Word.Document` `Microsoft.Office.Tools.Excel.Worksheet` sınıflarından türetmektedir. `Microsoft.Office.Tools.AddIn` veya sonrakini hedef [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] alan projelerde bu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sınıflar artık arabirimlerdir. Bu nedenle, Office projelerde oluşturulan sınıflar artık uygulamalarını onlardan türeyamaz. Bunun yerine, oluşturulan sınıflar , ve gibi yeni temel <xref:Microsoft.Office.Tools.Word.DocumentBase> <xref:Microsoft.Office.Tools.Excel.WorksheetBase> sınıflardan türetir. <xref:Microsoft.Office.Tools.AddInBase> Daha fazla bilgi için [bkz. Program VSTO Ve](../vsto/programming-vsto-add-ins.md) [Program belge düzeyi özelleştirmeleri.](../vsto/programming-document-level-customizations.md)

 Temel sınıflar yeniden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dağıtılabilir'in parçası değildir. Bunun yerine, bu derlemelere dahil edilen yardımcı program derlemelerinde Visual Studio. Bu derlemeler, projelerinizi derlemek için Office klasörüne kopyalanır ve çözümünüzle birlikte dağıtılması gerekir. Yardımcı programlar derlemeleri hakkında daha fazla bilgi için bkz. Office için Visual Studio Araçları [çalışma zamanı.](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>.NET Framework 4'e yeniden hedeflene Office projelerinde yeni değişiklikler
 Aşağıdaki tabloda, veya sonraki bir ya da sonraki bir Office projelerinde karşılaşabilirsiniz ana hataya neden olan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] değişiklikler listele. Diğer ayrıntılar için [bkz. Office 4 veya sonraki bir .NET Framework geçiş.](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)

|Yeni değişiklik|Sonucu|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute>artık bu projelerde kullanılamaz veya Office desteklenmiyor.|Bu özniteliği, 2008'den yükseltilen Office projelerinde AssemblyInfo kod dosyasından Visual Studio gerekir. Daha fazla bilgi için [bkz. Office 4 veya .NET Framework 4.5'e](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).NET Framework projeleri çalıştırmak için gerekli değişiklikler.|
|**ExcelLocale1033Attribute** artık bu projelerde kullanılamaz veya Excel desteklenmiyor.|Bu özniteliği projelerinde *AssemblyInfo* kod dosyasından Excel gerekir. Daha fazla bilgi için [bkz. Excel 4'e veya .NET Framework 4.5'e .NET Framework Word projelerini güncelleştirme.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|Şerit **(Görsel Tasarımcı) proje öğelerinin** programlama modeli değişti.|Projenizin tüm şerit öğeleri için arkadaki kod dosyasını değiştirmeniz gerekir. Ayrıca çalışma zamanında şerit denetimlerinin örneğini bulan, şerit olaylarını işen veya şerit bileşeninin konumunu program aracılığıyla ayaran herhangi bir kodu da değiştirmeniz gerekir. Daha fazla bilgi için bkz. [.NET Framework 4'e veya Office 4.5'e](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)geçirerek .NET Framework özelleştirmeleri.|
|Form bölgelerinin Outlook modeli değişti.|Projenizin tüm form bölgeleri ve çalışma zamanında belirli form bölgesi sınıflarını örnek alan tüm kodlar için arka arkasındaki kod dosyasını değiştirmeniz gerekir. Daha fazla bilgi için [bkz. Outlook 4'e veya .NET Framework 4.5'e .NET Framework bölgelerini güncelleştirme.](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|Excel ve Word projelerinde akıllı etiketler için programlama modeli değişti. akıllı etiketleri ve içinde kullanım [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] dışıdır.|Çözümünüz akıllı etiketler kullanıyorsa, projeyi derleme sırasında hatalar oluşur. akıllı etiketleri ve içinde kullanım dışı olduğundan, veya daha sonra çözümü test etmek ve hata ayıklamak için önce [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] etiketleri [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] kaldırmanız gerekir.|
|ve yöntemlerinin `GetVstoObject` `HasVstoObject` söz dizimi değişti|Birincil birlikte çalışma derlemelerinden (PIA) yerel nesnelere erişerek bu yöntemlere erişerek nesnesini bu yöntemlere geçmeniz gerekir veya projenizin özelliği tarafından döndürülen nesnesinde bu yöntemlere `Globals.Factory` `Globals.Factory` erişebilirsiniz. Daha fazla bilgi için [bkz. Excel 4'e veya .NET Framework 4.5'e .NET Framework Word projelerini güncelleştirme.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|Word içerik denetimlerinin olayları yeni temsilcilerle ilişkilendirildi.|Yeni temsilcileri belirtmek için Word içerik denetimlerinin olaylarını ele alan herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için [bkz. Excel 4'e veya .NET Framework 4.5'e .NET Framework Word projelerini güncelleştirme.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|`OLEObject`ve `OLEControl` sınıfları yeniden adlandırıldı.|Veya nesneleri kullanmak için bu sınıfların örneklerini kullanan herhangi bir <xref:Microsoft.Office.Tools.Excel.ControlSite> kodu değiştirmeniz <xref:Microsoft.Office.Tools.Word.ControlSite> gerekir. Daha fazla bilgi için [bkz. Excel 4'e veya .NET Framework 4.5'e .NET Framework Word projelerini güncelleştirme.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|, n , ve `ThisWorkbook` gibi konak öğesi sınıfları artık geçersiz `Sheet`  `ThisDocument` `ThisAddIn` `Dispose` kılabilirsiniz bir yöntem sağlamaz.|Yöntem geçersiz kılmada yer alan herhangi bir kodu, örneğin, konak öğesi sınıfındaki olay işleyicisine taşımanız ve yöntem geçersiz kılmayı konak öğe `Dispose` `Shutdown` `ThisAddIn_Shutdown` `Dispose` sınıfınıza kaldırmanız gerekir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office 4 veya sonraki .NET Framework geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Geliştirme aşamasındaki Office](/previous-versions/86bkz018(v=vs.110))
- [Office için Visual Studio Araçları çalışma zamanının genel bakışı](../vsto/visual-studio-tools-for-office-runtime-overview.md)