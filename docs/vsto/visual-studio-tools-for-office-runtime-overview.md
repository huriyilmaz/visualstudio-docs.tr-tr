---
title: Office için Visual Studio Araçları çalışma zamanının genel bakışı
description: Visual Studio geliştirici araçları kullanılarak oluşturulan çözümleri çalıştırmak için Office için Office 2010 Araçları'nın son kullanıcı bilgisayarlarına Microsoft Office gerekir.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0bf686a1002f3c7de6c3d91ec7e95ac48761e2085e25d62330774dcc31c4db54
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365854"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Office için Visual Studio Araçları çalışma zamanının genel bakışı
  Visual Studio'da Microsoft Office geliştirici araçları kullanılarak oluşturulan çözümleri çalıştırmak için, Office için Visual Studio 2010 Araçları'nın son kullanıcı bilgisayarlarına yüklenmiş olması gerekir. Daha fazla bilgi için, [bkz. How to: Install the Office için Visual Studio Araçları runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio için 2010 Araçları Office iki ana bileşenden oluşur:

- .NET Framework için Office uzantıları. Bu bileşenler, çözümünüz ile Microsoft Office uygulaması arasındaki iletişim katmanını sağlayan yönetilen derlemelerdir. Daha fazla bilgi için [bkz. Office uzantılarının .NET Framework.](#officeextensions)

- Office çözüm yükleyicisi. Bu bileşen, Office uygulamalarının çalışma zamanını ve çözümlerinizi yüklemek için kullandığı bir yönetilmeyen DLL'ler kümesidir. Daha fazla bilgi için [bkz. Office yükleyiciyi anlama.](#UnmanagedLoader)

  Çalışma zamanı birkaç farklı yolla yüklenebilir. Bilgisayarın yapılandırmasına bağlı olarak, çalışma zamanını yüklediğinizde farklı çalışma zamanı bileşenlerinin yüklemesi gerçekleşir. Daha fazla bilgi için [bkz. Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları.](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)

## <a name="understand-the-office-extensions-for-the-net-framework"></a><a name="officeextensions"></a>Dosyanın Office uzantılarını .NET Framework
 Office için Visual Studio 2010 Araçları, Office 3.5 ve sonraki .NET Framework [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] uzantılarını içerir. Her bir .NET Framework sürümünü hedefleyen çözümler, ilgili sürüm için uygun uzantıları kullanır.

 Bu uzantılar, çözümlerinizin Office uygulamalarını otomatikleştirmek ve genişletmek için kullandığı derlemelerden oluşur. Bir Office projesi oluşturduğunuzda, Visual Studio projenin .NET Framework hedefi ve proje türü için kullanılan derlemelerin başvurularını otomatik olarak ekler. Derleme uzantılarında derlemeler hakkında daha fazla Office için bkz. Office için Visual Studio Araçları [çalışma zamanında derlemeler.](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)

### <a name="design-differences-in-the-office-extensions"></a>Uzantılarda tasarım Office farkları
 .NET Framework 3.5 için Office uzantılarında kullandığınız türlerin çoğu sınıflardır. Bunlar, önceki sürümlerine dahil edilen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sınıflardır. Buna karşılık, veya sonraki uzantılarında Office türlerin çoğu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] arabirimdir. Örneğin, veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] hedefle, <xref:Microsoft.Office.Tools.Excel.Worksheet> ve türleri sınıflar yerine <xref:Microsoft.Office.Tools.Word.Document> arabirimler olur.

 Çoğu durumda, çözüm 3.5 veya Office çözümde yazarak .NET Framework aynı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] olur. Ancak belirli özellikler, .NET Framework'ün farklı sürümlerini hedeflediğinizde farklı kod gerektirir. Daha fazla bilgi için [bkz. Office 4 veya sonraki .NET Framework](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)geçirme.

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Office 4 veya sonraki bir .NET Framework arabirimleri
 veya sonraki için Office uzantılarındaki arabirimlerin [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] çoğu kullanıcı kodu tarafından uygulanmaya yönelik değildir. Doğrudan uygulayan arabirimlerin yalnızca **I** harfiyle başlayan adları vardır, <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension> örneğin.

 I harfiyle başlamamış tüm  arabirimler Visual Studio 2010 Tools for Office çalışma zamanı tarafından dahili olarak uygulanır ve bu arabirimler gelecek sürümlerde değişebilir. Bu arabirimleri uygulayan nesneler oluşturmak için projenize nesnesi tarafından `Globals.Factory` sağlanan yöntemleri kullanın. Örneğin, arabirimini uygulayan bir nesnesi <xref:Microsoft.Office.Tools.Excel.SmartTag> almak için yöntemini `Globals.Factory.CreateSmartTag` kullanın. hakkında daha fazla bilgi `Globals.Factory` için [bkz. Office projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>4 veya daha sonraki bir hedefi hedef alan projelerde tür eşdeğerliği .NET Framework ekli türleri etkinleştirme
 veya sonraki için Office uzantılarının nesne modeli arabirimlere dayalı olduğundan, tür bilgilerini çözümünüze eklemek için hem Visual C# hem de Visual Basic Visual Studio'deki tür denkliği özelliğini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanabilirsiniz. Bu özellik, Office ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sürümünden bağımsız olarak birbirinin sürümüne olanak sağlar. Örneğin çözümünüz tümleşik tür olarak arabirimi kullanıyorsa ve çalışma zamanının sonraki sürümü arabirime üye ekliyorsa çözümünüz çalışma zamanının sonraki sürümüyle çalışmaya <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Word.Document> devam ediyor. Çözümünüz arabirimi ekli tür olarak kullanmayacaksa çözümünüz artık çalışma zamanının <xref:Microsoft.Office.Tools.Word.Document> sonraki sürümüyle çalışmaz.

 Varsayılan olarak, veya sonrakini hedef alan bir Office tür denkliği özelliği [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] etkin değildir. Bu özelliği etkinleştirmek için projenize  aşağıdaki derleme başvurularının Birlikte Çalışma Türlerini Katıştır özelliğini True olarak **ayarlayın:**

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Bu değişikliği yaptıktan sonra, projeyi oluşturduğunuzda, proje tarafından kullanılan tüm çalışma zamanı türlerine ilişkin tür bilgileri çözüm derlemesine eklenir. Bu katıştırılmış tür bilgileri, başvurulan derlemelerde tür bilgileri yerine çalışma zamanında çözüm tarafından kullanılır.

## <a name="understand-the-office-solution-loader"></a><a name="UnmanagedLoader"></a>Office çözüm yükleyiciyi anlama
 Çalışma Office için Visual Studio Araçları, uygulamaların çalışma zamanlarını yüklemek ve çözümlerini yüklemek için Office çeşitli Office IÇERIR. Hiçbir zaman bu DLL'ler ile doğrudan çalışmanız gerekmese de, bu DLL'lerin amaçlarını bilmeniz, Office çözümlerinin mimarisini daha iyi anlamanıza yardımcı olabilir.

 Bu bileşenlerin yükleme işlemi sırasında nasıl kullanıldıkları hakkında bilgi için bkz. Belge düzeyinde özelleştirmelerin mimarisi [ve VSTO Mimarisi.](../vsto/architecture-of-vsto-add-ins.md) [](../vsto/architecture-of-document-level-customizations.md)

### <a name="vstoeedll"></a>VSTOEE.dll
 Bir kullanıcı belge düzeyi özelleştirmesi açtığında veya VSTO eklentiyi başlatırsa, Office uygulaması  yüklemesi için gereken görevleri gerçekleştirmekVSTOEE.dlliçinVSTOEE.dll'a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çağrır.

 *VSTOEE.dll* çözüm için doğru sürümünün yüklendiğinden ve çözümün yüklü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sürümünün yüklendiğinden emin Office. aynı bilgisayara birden çok sürümü yüklense de, aynı anda yalnızca [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] *VSTOEE.dll* örneği yüklenir. Bu, *VSTOEE.dll* çalışma zamanının en son sürümüne dahil edilen uygulamadır. diğer çözümler için kullanılmaktadır farklı sürümleri hakkında daha fazla bilgi için, bkz. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Run solutions in different versions in [Microsoft Office.](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 Bu *VSTOEE.dll* uygun sürümünü yükledikten sonraVSTOLoader.dllderlemeyi yüklemek [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] için gereken çalışmaların çoğunu gerçekleştirir.  *VSTOLoader.dll* birçok şey yapar:

- Her bir çözüm derlemesi için uygulama etki alanı oluşturur.

- Çözüm derlemesinin çalışma izni olduğunu doğrulamak için bir dizi güvenlik denetimi gerçekleştirir.

- Çözüm için gerekli .NET Framework için Office uzantıları sürümünü yükler.

  *VSTOLoader.dll* eklentilere özgü birkaç VSTO da yapar:

- Arabirimini <xref:Extensibility.IDTExtensibility2> uygulayan bir uygulamadır. <xref:Extensibility.IDTExtensibility2>, uygulama uygulamanıza gereken VSTO eklentilerin Microsoft Office com arabirimidir. Bu arabirim, uygulamanın uygulamanın Eklenti ile iletişim kurmak VSTO yöntemleri tanımlar.

- IManagedAddin arabirimini uygulama. Bu arabirim, Office yüklemeye yardımcı olmak için VSTO tarafından kullanılır. Daha fazla bilgi için bkz. [IManagedAddin arabirimi.](../vsto/imanagedaddin-interface.md)

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Çalışma zamanının 32 bit ve 64 bit sürümlerini anlama
 Office çalışma zamanı için Visual Studio 2010 Araçları'nın ayrı 64 bit ve 32 bit Office vardır. Çalışma zamanının bu sürümleri, çözümleri 64 bit ve 32 bitlik sürümlerde çalıştırmak için Office. Aşağıdaki tabloda, her bir çalışma zamanı ve çalışma zamanı birleşimi için hangi Windows Office.

|Windows sürümü|Microsoft Office sürümü|Office çalışma zamanı için Visual Studio Araçları'nın gerekli sürümü|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32 bit|32 bit|32 bit|
|64 bit|32 bit|64 bit|
|64 bit|64 bit|64 bit|

 Yükleme Office, gerekli sürümü ile birlikte [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office. Örneğin, Office'nin 64 bit sürümünü Windows'nin 64 bit sürümüne de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklenir. ile yükleme hakkında daha fazla [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bilgi için Office çalışma zamanı Office için Visual Studio Araçları [senaryolarına bakın.](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)

 Office'nin 64 bit sürümü, Office 2008'de 2007 Microsoft Office sistemi için proje şablonları kullanılarak oluşturulan Visual Studio çözümlerini de çalıştırabilirsiniz. Ancak Visual Studio 2005 kullanılarak oluşturulan Office çözümlerini veya Visual Studio 2008'de Microsoft Office 2003 proje şablonları kullanılarak oluşturulan Office çözümlerini çalıştıramaz. Daha fazla bilgi için [bkz. Çözümleri farklı sürümlerde Microsoft Office.](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio 2010 Araçları'Office onarın
 Çalışma zamanını onarmanız gerekirse, Denetim Masası'de Programlar ve Özellikler'i veya Program Ekle veya Kaldır'ı açın, programlar listesinde **Microsoft Visual Studio 2010** Office Çalışma Zamanı için Araçlar'ı seçin ve kaldır'a **tıklayın.**   Çalıştırılan kurulum programı çalışma zamanını onarmanızı sağlar. **Değiştir'e** tıklarsanız, çalışma zamanını onarma seçeneği sağlanmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Office için Visual Studio Araçları çalışma zamanı yükleme senaryoları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Office için Visual Studio Araçları çalışma zamanında derlemeler](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Office çözüm mimarisi Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Belge düzeyinde özelleştirmelerin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Çözümlerini yükseltme Office geçirme](../vsto/upgrading-and-migrating-office-solutions.md)
