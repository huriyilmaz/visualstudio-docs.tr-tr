---
title: Office projelerinde .NET Framework hedefleme için değişiklikler tasarlama
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
ms.openlocfilehash: c46b0e7ea6cad5cb96117dedaa28ba6c4505a90b
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189652"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 ' ü veya .NET Framework 4,5 ' i hedefleyen Office projelerinin tasarımında yapılan değişiklikler
  [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]başlayarak, Visual Studio [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üstünü hedefleyen Office projelerinin tasarımında bazı değişiklikler getirmiştir. Visual Studio 'nun önceki sürümlerindeki Office projelerine alışkın değilseniz, .NET Framework 4,0 veya üzeri sürümlerini hedefleyen Office projeleri geliştirebilmeniz için bu değişikliklerden haberdar olmanız gerekir. Varsayılan olarak, Visual Studio 2013 veya üzeri kullanarak oluşturduğunuz tüm projeler .NET Framework 4,0 veya üstünü hedefleyin.

 Aşağıdaki bölümlerde bu Office proje tasarım değişiklikleri açıklanır.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio 2010 araçları 'nın arabirim tabanlı tasarımını anlama
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üstünü hedefleyen bir Office projesi geliştirirken, Office çalışma zamanı için Visual Studio 2010 araçlarında kullandığınız türlerin çoğu arayüzlerdir. Bu, bu türlerin sınıf olduğu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]önceki sürümlerinden büyük bir değişimdir. Örneğin, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üstünü hedeflediğinizde, <xref:Microsoft.Office.Tools.Excel.Worksheet> ve <xref:Microsoft.Office.Tools.Word.Document> türleri sınıflar yerine arayüzlerdir. Daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]önceki sürümlerinde doğrudan örneklenebilen herhangi bir tür için, artık bu türlerin örneklerini almak üzere `Globals.Factory` nesnesinin yöntemlerini kullanacaksınız. Örneğin, <xref:Microsoft.Office.Tools.Excel.SmartTag> arabirimini uygulayan bir nesne almak için `Globals.Factory.CreateSmartTag` yöntemini kullanın. Daha fazla bilgi için aşağıdaki konulara bakın:

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office Projelerindeki Şerit özelleştirmelerini güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Outlook Projelerindeki Form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Office projelerinde yeni temel sınıflar
 Office çalışma zamanı için Visual Studio 2010 araçları 'nın yeni arabirim tabanlı tasarımı, Office projelerinde `ThisDocument`, `ThisWorkbook`ve `ThisAddIn`gibi oluşturulan sınıfları etkiler. Framework 'ün .NET Framework 3,5 ve önceki sürümlerini hedefleyen Office projelerinde, oluşturulan bu sınıflar `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet`ve `Microsoft.Office.Tools.AddIn`gibi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sınıflarından türetilir. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üstünü hedefleyen projelerde, bu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sınıfları artık arayüzlerdir. Bu nedenle, Office projelerindeki oluşturulan sınıflar bundan böyle kendi uygulamasını bundan türemez. Bunun yerine, oluşturulan sınıflar <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>ve <xref:Microsoft.Office.Tools.AddInBase>gibi yeni temel sınıflardan türetilir. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md) ve [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

 Temel sınıflar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yeniden dağıtılabilir bir parçası değildir. Bunun yerine, Visual Studio 'da bulunan yardımcı programlar Derlemeleriyle tanımlanmıştır. Bu derlemeler Office projeleri oluşturduğunuzda çıkış klasörüne kopyalanır ve çözümünüz ile birlikte dağıtılması gerekir. Yardımcı programlar derlemeleri hakkında daha fazla bilgi için, bkz. [Office çalışma zamanı için Visual Studio Araçları derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>.NET Framework 4 ' e yeniden hedeflenmiş Office projelerindeki son değişiklikler
 Aşağıdaki tabloda, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürüme yeniden hedeflenmiş Office projelerinde karşılaşabileceğiniz ana son değişiklikler listelenmiştir. Daha fazla ayrıntı için bkz. [Office çözümlerini .NET Framework 4 veya sonraki bir sürüme geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Son değişiklik|Sonucudur|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute> artık Office projelerinde kullanılmıyor veya desteklenmiyor.|Bu özniteliği, Visual Studio 2008 ' den yükselttiğiniz Office projelerindeki AssemblyInfo kod dosyasından kaldırmanız gerekir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçirebileceğiniz Office projelerini çalıştırmak Için gereken değişiklikler](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)konusuna bakın.|
|**ExcelLocale1033Attribute** artık Excel projelerinde kullanılmamaktadır veya desteklenmez.|Bu özniteliği Excel projelerindeki *AssemblyInfo* kod dosyasından kaldırmanız gerekir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|**Şerit (görsel Tasarımcı)** proje öğelerinin programlama modeli değişti.|Projenizdeki herhangi bir şerit öğesi için arka plan kod dosyasını değiştirmeniz gerekir. Ayrıca, çalışma zamanında Şerit denetimlerini örnekleyen, Şerit olaylarını işleyen veya Şerit bileşeninin konumunu programlı bir şekilde ayarlayan herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için bkz. [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office Projelerindeki Şerit özelleştirmelerini güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md).|
|Outlook form bölgelerinin programlama modeli değişti.|Projenizdeki herhangi bir form bölgesi için arka plan kod dosyasını ve belirli form bölgesi sınıflarını çalışma zamanında örnekleyen tüm kodları değiştirmeniz gerekir. Daha fazla bilgi için, bkz. [.NET Framework 4 ' e veya .NET Framework 4,5 'e geçirdiğinizde Outlook Projelerindeki güncelleştirme form bölgeleri](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Excel ve Word projelerindeki akıllı etiketler için programlama modeli değişmiştir. Akıllı Etiketler [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]kullanım dışıdır.|Çözümünüz Akıllı Etiketler kullanıyorsa, projeyi oluşturduğunuzda hatalar oluşur. Akıllı Etiketler [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]kullanım dışı olduğundan, çözüm [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] veya sonraki bir sürümde test etmeden ve hata ayıklamadan önce etiketleri kaldırmanız gerekir.|
|`GetVstoObject` ve `HasVstoObject` yöntemlerinin sözdizimi değiştirildi|Bu yöntemlere birincil birlikte çalışma derlemelerinden (PIA 'lar) yerel nesneler üzerinde eriştiğinizde `Globals.Factory` nesnesini geçirmeniz gerekir ya da bu yöntemlere projenizdeki `Globals.Factory` özelliği tarafından döndürülen nesnede erişebilirsiniz. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|Word içerik denetimlerinin olayları yeni temsilcilerle ilişkilendirilir.|Yeni temsilcileri belirtmek için Word içerik denetimlerinin olaylarını işleyen herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|`OLEObject` ve `OLEControl` sınıfları yeniden adlandırıldı.|Bunun yerine <xref:Microsoft.Office.Tools.Excel.ControlSite> veya <xref:Microsoft.Office.Tools.Word.ControlSite> nesneleri kullanmak için bu sınıfların örneklerini kullanan herhangi bir kodu değiştirmeniz gerekir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçiş yaptığınız Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)bölümüne bakın.|
|`ThisWorkbook`, `Sheet`*n*, `ThisDocument`ve `ThisAddIn`gibi konak öğesi sınıfları artık geçersiz kılabileceğiniz bir `Dispose` yöntemi sağlamaz.|`Dispose` yöntemi geçersiz kılmada herhangi bir kodu konak öğesi sınıfındaki `Shutdown` olay işleyicisine taşımanız gerekir, örneğin, `ThisAddIn_Shutdown`ve `Dispose` yöntemi geçersiz kılmayı konak öğesi sınıfınızdan kaldırmanız gerekir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Office geliştirme yenilikleri](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)
