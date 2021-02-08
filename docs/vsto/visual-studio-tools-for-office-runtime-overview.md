---
title: Office çalışma zamanına genel bakış için Visual Studio Araçları
description: Microsoft Office geliştirici araçları kullanılarak oluşturulan çözümleri çalıştırmak için, Office çalışma zamanı için Visual Studio 2010 araçları 'nın son kullanıcı bilgisayarlarında yüklü olması gerekir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e5d02d7840f1b16098509a6549816746c0a5bfbd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838067"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Office çalışma zamanına genel bakış için Visual Studio Araçları
  Visual Studio 'da Microsoft Office geliştirici araçları kullanılarak oluşturulan çözümleri çalıştırmak için, son kullanıcı bilgisayarlarında Office çalışma zamanı için Visual Studio 2010 araçları 'nın yüklü olması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Office çalışma zamanı için Visual Studio 2010 araçları iki ana bileşenden oluşur:

- .NET Framework için Office uzantıları. Bu bileşenler, çözümünüz ile Microsoft Office uygulaması arasındaki iletişim katmanını sağlayan yönetilen derlemelerdir. Daha fazla bilgi için bkz. [.NET Framework Için Office uzantılarını anlama](#officeextensions).

- Office çözüm yükleyicisi. Bu bileşen, Office uygulamalarının çalışma zamanını ve çözümlerinizi yüklemek için kullandığı bir yönetilmeyen DLL'ler kümesidir. Daha fazla bilgi için bkz. [Office çözüm yükleyicisini anlama](#UnmanagedLoader).

  Çalışma zamanı birkaç farklı yolla yüklenebilir. Bilgisayarın yapılandırmasına bağlı olarak, çalışma zamanını yüklediğinizde farklı çalışma zamanı bileşenlerinin yüklemesi gerçekleşir. Daha fazla bilgi için bkz. [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="understand-the-office-extensions-for-the-net-framework"></a><a name="officeextensions"></a> .NET Framework için Office uzantılarını anlayın
 Office çalışma zamanı için Visual Studio 2010 araçları, ve üzeri .NET Framework 3,5 için Office uzantıları içerir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Her bir .NET Framework sürümünü hedefleyen çözümler, ilgili sürüm için uygun uzantıları kullanır.

 Bu uzantılar, çözümlerinizin Office uygulamalarını otomatikleştirmek ve genişletmek için kullandığı derlemelerden oluşur. Bir Office projesi oluşturduğunuzda, Visual Studio projenin .NET Framework hedefi ve proje türü için kullanılan derlemelerin başvurularını otomatik olarak ekler. Office uzantılarındaki derlemeler hakkında daha fazla bilgi için, bkz. [Office çalışma zamanı için Visual Studio Araçları derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Office uzantılarında tasarım farkları
 .NET Framework 3.5 için Office uzantılarında kullandığınız türlerin çoğu sınıflardır. Bunlar, önceki sürümlerinde bulunan sınıflardır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Buna karşılık, veya üzeri için Office uzantılarında kullandığınız türlerin çoğu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] arayüzlerdir. Örneğin, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümünü hedeflediğinizde, <xref:Microsoft.Office.Tools.Excel.Worksheet> ve <xref:Microsoft.Office.Tools.Word.Document> türleri sınıflar yerine arayüzlerdir.

 Çoğu durumda, Office çözümlerinde yazdığınız kod, çözümünüzün 3,5 .NET Framework veya ' i hedeflemesinden bağımsız olarak aynıdır [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Ancak belirli özellikler, .NET Framework'ün farklı sürümlerini hedeflediğinizde farklı kod gerektirir. Daha fazla bilgi için bkz. [Office çözümlerini .NET Framework 4 veya sonraki bir sürüme geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>.NET Framework 4 veya üzeri için Office uzantılarında arabirimler
 Veya üzeri için Office uzantılarında arabirimlerin çoğunun [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Kullanıcı kodu tarafından uygulanması amaçlanmamıştır. Doğrudan uygulayabileceğiniz tek arabirimler **ı** harfiyle başlayan adlara sahiptir, örneğin <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension> .

 **I** harfiyle başlamayan tüm arabirimler, Office çalışma zamanı Için Visual Studio 2010 araçları tarafından dahili olarak uygulanır ve bu arabirimler gelecek sürümlerde değişebilir. Bu arabirimleri uygulayan nesneler oluşturmak için, projenizdeki nesne tarafından sunulan yöntemleri kullanın `Globals.Factory` . Örneğin, arabirimini uygulayan bir nesne almak için <xref:Microsoft.Office.Tools.Excel.SmartTag> `Globals.Factory.CreateSmartTag` yöntemini kullanın. Hakkında daha fazla bilgi için `Globals.Factory` bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>.NET Framework 4 veya üstünü hedefleyen projelerde tür denklik ve gömülü türleri etkinleştirin
 Veya sonraki bir sürümü için Office uzantılarının nesne modeli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] arabirimlere dayalı olduğundan, içindeki tür bilgilerini çözümünüze eklemek için Visual Studio 'daki tür denklik özelliğini ve Visual Studio 'da Visual Basic kullanabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Bu özellik, Office çözümlerini ve ' [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nin birbirinden bağımsız olarak sürümlerini sağlar. Örneğin, çözümünüz <xref:Microsoft.Office.Tools.Word.Document> arabirimini gömülü bir tür olarak kullanıyorsa ve çalışma zamanının bir sonraki sürümü arabirimine üye eklerse <xref:Microsoft.Office.Tools.Word.Document> , çözümünüz çalışma zamanının sonraki sürümüyle çalışmaya devam edecektir. Çözümünüz <xref:Microsoft.Office.Tools.Word.Document> yerleşik bir tür olarak arabirimini kullanmıyorsa, çözümünüz artık çalışma zamanının sonraki sürümüyle çalışmaz.

 Varsayılan olarak, veya üstünü hedefleyen bir Office projesi oluşturduğunuzda tür denklik özelliği etkin değildir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Bu özelliği etkinleştirmek istiyorsanız, projenizdeki aşağıdaki derleme başvurularının herhangi birinin **birlikte çalışma türlerini katıştır** özelliğini **doğru** olarak ayarlayın:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Bu değişikliği yaptıktan sonra, projeyi oluşturduğunuzda, proje tarafından kullanılan tüm çalışma zamanı türlerine ilişkin tür bilgileri çözüm derlemesine eklenir. Başvurulan derlemelerdeki tür bilgileri yerine bu gömülü tür bilgileri, çalışma zamanında çözüm tarafından kullanılır.

## <a name="understand-the-office-solution-loader"></a><a name="UnmanagedLoader"></a> Office çözüm yükleyicisini anlama
 Office çalışma zamanı Visual Studio Araçları, Office uygulamalarının çalışma zamanını ve Office çözümlerini yüklemek için kullandığı çeşitli yönetilmeyen DLL 'Leri içerir. Hiçbir zaman bu DLL'ler ile doğrudan çalışmanız gerekmese de, bu DLL'lerin amaçlarını bilmeniz, Office çözümlerinin mimarisini daha iyi anlamanıza yardımcı olabilir.

 Yükleme işlemi sırasında bu bileşenlerin nasıl kullanıldığı hakkında bilgi için bkz. [belge düzeyi özelleştirmelerinin](../vsto/architecture-of-document-level-customizations.md) ve [VSTO eklentilerinin mimarisinin](../vsto/architecture-of-vsto-add-ins.md)mimarisi.

### <a name="vstoeedll"></a>VSTOEE.dll
 Bir kullanıcı belge düzeyinde bir özelleştirme açtığında veya VSTO eklentisi başlattığında Office uygulaması, yüklemek için gereken görevleri gerçekleştirmek için *VSTOEE.dll* çağırır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 *VSTOEE.dll* , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözümü ve Office 'in yüklü sürümü için doğru sürümünün yüklü olduğundan emin olur. Uygulamasının birden çok sürümü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aynı bilgisayara yüklenebilse de, aynı anda yalnızca bir *VSTOEE.dll* örneği yüklenir. Bu, bilgisayarda yüklü olan çalışma zamanının en son sürümüne dahil edilen *VSTOEE.dll* . Diğer çözümler için kullanılabilen farklı sürümleri hakkında daha fazla bilgi için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bkz. [Microsoft Office farklı sürümlerinde çözüm çalıştırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 *VSTOEE.dll* uygun sürümünü yükledikten sonra [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , *VSTOLoader.dll* çözüm derlemesini yüklemek için gerekli çalışmanın çoğunu gerçekleştirir. *VSTOLoader.dll* birkaç şeyi yapar:

- Her bir çözüm derlemesi için uygulama etki alanı oluşturur.

- Çözüm derlemesinin çalışma izni olduğunu doğrulamak için bir dizi güvenlik denetimi gerçekleştirir.

- Çözüm için gerekli .NET Framework için Office uzantıları sürümünü yükler.

  Ayrıca, VSTO eklentilerine özgü birkaç şeyi de *VSTOLoader.dll* :

- <xref:Extensibility.IDTExtensibility2>Arabirimini uygular. <xref:Extensibility.IDTExtensibility2> , Microsoft Office uygulamaları için tüm VSTO eklentilerin uygulanması gereken bir COM arabirimidir. Bu arabirim, uygulamanın VSTO eklentisi ile iletişim kurmak için çağırdığı yöntemleri tanımlar.

- IManagedAddin arabirimini uygular. Bu arabirim, Office uygulamaları tarafından VSTO eklentilerinin yüklenmesine yardımcı olmak için kullanılır. Daha fazla bilgi için bkz. [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Çalışma zamanının 32-bit ve 64 bit sürümlerini anlayın
 Office çalışma zamanı için Visual Studio 2010 araçları 'nın ayrı 64-bit ve 32 bit sürümleri vardır. Çalışma zamanının bu sürümleri 64-bit ve 32 bit sürümler ofisinde çözüm çalıştırmak için kullanılır. Aşağıdaki tabloda, her Windows ve Office birleşimi için hangi çalışma zamanı sürümünün gerekli olduğu gösterilmektedir.

|Windows sürümü|Microsoft Office sürümü|Office çalışma zamanı için Visual Studio Araçları'nın gerekli sürümü|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32 bit|32 bit|32 bit|
|64 bit|32 bit|64 bit|
|64 bit|64 bit|64 bit|

 Office 'i yüklediğinizde, gereken sürümü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office ile birlikte yüklenir. Örneğin, Office 'in 64 bit sürümünü Windows 'un 64 bit sürümüne yüklediğinizde, uygulamasının 64 bit sürümü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] de yüklenir. Office ile yükleme hakkında daha fazla bilgi için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bkz. [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 Office 'in 64 bitlik sürümü, Visual Studio 2008 ' de 2007 Microsoft Office sistemi için proje şablonları kullanılarak oluşturulan Office çözümlerini de çalıştırabilir. Ancak Visual Studio 2005 kullanılarak oluşturulan Office çözümlerini veya Visual Studio 2008'de Microsoft Office 2003 proje şablonları kullanılarak oluşturulan Office çözümlerini çalıştıramaz. Daha fazla bilgi için bkz. [Microsoft Office farklı sürümlerinde çözüm çalıştırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio 2010 araçları 'nı onarın
 Çalışma zamanını onarmanız gerekirse, programlar **ve Özellikler** ' i açın veya Denetim Masası 'Nda **Program Ekle veya Kaldır** ' ı seçin, programlar listesinden **Office çalışma zamanı için Microsoft Visual Studio 2010 araçları** ' nı seçin ve ardından **Kaldır**' a tıklayın. Çalıştırılan kurulum programı çalışma zamanını onarmanızı sağlar. **Değiştir**' e tıklarsanız, çalışma zamanını onarmak için bir seçenek verilmemiş demektir.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çalışma zamanı yükleme senaryoları için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Office çalışma zamanı için Visual Studio Araçları derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Visual Studio 'da Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office çözümlerini yükseltme ve geçirme](../vsto/upgrading-and-migrating-office-solutions.md)
