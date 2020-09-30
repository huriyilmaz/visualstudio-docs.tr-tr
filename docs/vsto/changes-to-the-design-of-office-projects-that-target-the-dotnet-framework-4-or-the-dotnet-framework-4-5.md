---
title: Office projelerinde .NET Framework hedefleme için değişiklikler tasarlama
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be681bb930e22b3e4cdd4597eb4d265c27b08139
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583833"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 ' ü veya .NET Framework 4,5 ' i hedefleyen Office projelerinin tasarımında yapılan değişiklikler
  ' Den itibaren [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , Visual Studio, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki sürümlerini hedefleyen Office projelerinin tasarımında bazı değişiklikler getirmiştir. Visual Studio 'nun önceki sürümlerindeki Office projelerine alışkın değilseniz, .NET Framework 4,0 veya üzeri sürümlerini hedefleyen Office projeleri geliştirebilmeniz için bu değişikliklerden haberdar olmanız gerekir. Varsayılan olarak, Visual Studio 2013 veya üzeri kullanarak oluşturduğunuz tüm projeler .NET Framework 4,0 veya üstünü hedefleyin.

 Aşağıdaki bölümlerde bu Office proje tasarım değişiklikleri açıklanır.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio 2010 araçları 'nın arabirim tabanlı tasarımını anlama
 Veya sonraki bir sürümü hedefleyen bir Office projesi geliştirirken [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , Office çalışma zamanı Için Visual Studio 2010 araçlarında kullandığınız türlerin çoğu arayüzlerdir. Bu, ' nin, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Bu türlerin sınıflar olduğu önceki sürümlerinden büyük bir değişimdir. Örneğin, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümünü hedeflediğinizde, <xref:Microsoft.Office.Tools.Excel.Worksheet> ve <xref:Microsoft.Office.Tools.Word.Document> türleri sınıflar yerine arayüzlerdir. Daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Daha önceki sürümlerinde doğrudan örneklenebilen herhangi bir tür için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] artık `Globals.Factory` Bu türlerin örneklerini almak üzere nesne yöntemlerini kullanacaksınız. Örneğin, arabirimini uygulayan bir nesne almak için <xref:Microsoft.Office.Tools.Excel.SmartTag> `Globals.Factory.CreateSmartTag` yöntemini kullanın. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office Projelerindeki Şerit özelleştirmelerini güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Outlook Projelerindeki Form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Office projelerinde yeni temel sınıflar
 Office çalışma zamanı için Visual Studio 2010 araçları 'nın yeni arabirim tabanlı tasarımı,, ve gibi Office projelerinde oluşturulan sınıfları etkiler `ThisDocument` `ThisWorkbook` `ThisAddIn` . .NET Framework 3,5 ' i ve Framework 'ün önceki sürümlerini hedefleyen Office projelerinde, oluşturulan bu sınıflar, ve gibi sınıflarından türetilir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] `Microsoft.Office.Tools.Word.Document` `Microsoft.Office.Tools.Excel.Worksheet` `Microsoft.Office.Tools.AddIn` . [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sınıflar artık arayüzlerdir. Bu nedenle, Office projelerindeki oluşturulan sınıflar bundan böyle kendi uygulamasını bundan türemez. Bunun yerine, oluşturulan sınıflar, ve gibi yeni temel sınıflardan türetilir <xref:Microsoft.Office.Tools.Word.DocumentBase> <xref:Microsoft.Office.Tools.Excel.WorksheetBase> <xref:Microsoft.Office.Tools.AddInBase> . Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md) ve [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

 Temel sınıflar yeniden dağıtılabilir bir parçası değildir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Bunun yerine, Visual Studio 'da bulunan yardımcı programlar Derlemeleriyle tanımlanmıştır. Bu derlemeler Office projeleri oluşturduğunuzda çıkış klasörüne kopyalanır ve çözümünüz ile birlikte dağıtılması gerekir. Yardımcı programlar derlemeleri hakkında daha fazla bilgi için, bkz. [Office çalışma zamanı için Visual Studio Araçları derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>.NET Framework 4 ' e yeniden hedeflenmiş Office projelerindeki son değişiklikler
 Aşağıdaki tabloda, veya daha sonra yeniden hedeflenen Office projelerinde karşılaşabileceğiniz ana son değişiklikler listelenmiştir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Daha fazla ayrıntı için bkz. [Office çözümlerini .NET Framework 4 veya sonraki bir sürüme geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Son değişiklik|Sonucudur|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute>Office projelerinde artık kullanılmıyor veya desteklenmiyordur.|Bu özniteliği, Visual Studio 2008 ' den yükselttiğiniz Office projelerindeki AssemblyInfo kod dosyasından kaldırmanız gerekir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçirebileceğiniz Office projelerini çalıştırmak Için gereken değişiklikler](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)konusuna bakın.|
|**ExcelLocale1033Attribute** artık Excel projelerinde kullanılmamaktadır veya desteklenmez.|Bu özniteliği Excel projelerindeki *AssemblyInfo* kod dosyasından kaldırmanız gerekir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|**Şerit (görsel Tasarımcı)** proje öğelerinin programlama modeli değişti.|Projenizdeki herhangi bir şerit öğesi için arka plan kod dosyasını değiştirmeniz gerekir. Ayrıca, çalışma zamanında Şerit denetimlerini örnekleyen, Şerit olaylarını işleyen veya Şerit bileşeninin konumunu programlı bir şekilde ayarlayan herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için bkz. [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office Projelerindeki Şerit özelleştirmelerini güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md).|
|Outlook form bölgelerinin programlama modeli değişti.|Projenizdeki herhangi bir form bölgesi için arka plan kod dosyasını ve belirli form bölgesi sınıflarını çalışma zamanında örnekleyen tüm kodları değiştirmeniz gerekir. Daha fazla bilgi için, bkz. [.NET Framework 4 ' e veya .NET Framework 4,5 'e geçirdiğinizde Outlook Projelerindeki güncelleştirme form bölgeleri](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Excel ve Word projelerindeki akıllı etiketler için programlama modeli değişmiştir. Akıllı Etiketler ve ' de kullanım dışıdır [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] .|Çözümünüz Akıllı Etiketler kullanıyorsa, projeyi oluşturduğunuzda hatalar oluşur. Ve içinde Akıllı Etiketler kullanım dışı [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] olduğundan [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] , veya sonraki kısımlarında çözümü test etmeden ve hata ayıklamadan önce etiketleri kaldırmanız gerekir [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .|
|`GetVstoObject`Ve `HasVstoObject` yöntemlerinin sözdizimi değiştirildi|`Globals.Factory`Bu yöntemlere, birincil birlikte çalışma derlemelerinden (PIA 'lar) yerel nesneler üzerinde eriştiğinizde veya projenizdeki özelliği tarafından döndürülen nesnede bu yöntemlere erişmeniz gerekir `Globals.Factory` . Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|Word içerik denetimlerinin olayları yeni temsilcilerle ilişkilendirilir.|Yeni temsilcileri belirtmek için Word içerik denetimlerinin olaylarını işleyen herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|`OLEObject`Ve `OLEControl` sınıfları yeniden adlandırıldı.|<xref:Microsoft.Office.Tools.Excel.ControlSite>Bunun yerine veya nesnelerini kullanmak için bu sınıfların örneklerini kullanan herhangi bir kodu değiştirmeniz gerekir <xref:Microsoft.Office.Tools.Word.ControlSite> . Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|`ThisWorkbook`, `Sheet` *N*,, ve gibi konak öğesi sınıfları `ThisDocument` `ThisAddIn` artık `Dispose` geçersiz kılabileceğiniz bir yöntem sağlamaz.|`Dispose`Yöntemi geçersiz kılmada bulunan herhangi bir kodu `Shutdown` konak öğesi sınıfındaki olay işleyicisine taşımanız gerekir, örneğin,, ve sonra da `ThisAddIn_Shutdown` `Dispose` konak öğesi sınıfınızdan yöntem geçersiz kılmayı kaldırın.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Office geliştirme yenilikleri](/previous-versions/86bkz018(v=vs.110))
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)