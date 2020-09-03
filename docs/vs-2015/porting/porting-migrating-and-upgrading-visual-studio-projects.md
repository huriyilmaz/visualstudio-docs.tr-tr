---
title: Projeleri taşıma, geçirme ve yükseltme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 3361b04900e549d037338abfba0911b232c9e1bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919099"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [Visual Studio Için proje geçişi ve yükseltme başvurusu](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Visual Studio 'nun daha yeni bir sürümüne geçiş yapmanız gerekip gerekmediğini düşünürken, bu makaleyi, Visual Studio 2013, Visual Studio 2012 veya Visual Studio 2010 SP1 'de oluşturduğunuz çözümlerin, projelerin, dosyaların ve diğer varlıkların Visual Studio 2013 ve Visual Studio 2015 ' de değişiklik yapılmadan çalışacağını öğrenmek için kullanabilirsiniz. Ya da bu sayfada, açtığınız Visual Studio sürümünde desteklenmeyen bir projeyi açmaya çalışırken veya .NET için Azure SDK gibi bir SDK ya da uzantı gerektiren bir hata iletisiyle karşılaştıysanız bu sayfaya ulaşmış olabilirsiniz.

Yaygın olarak kullanılan birçok varlık, Visual Studio 2015, Visual Studio 2013 ve önceki iki sürümde aynı şekilde davranır. Örneğin, Visual Studio 2015 ' de, Visual Studio 2013 veya Visual Studio 2012 ' de oluşturulmuş bir projeyi açabilir, değiştirebilir ve sonra Visual Studio 2015 ' de yeniden açabilirsiniz. Değişiklikleriniz devam ediyor ve proje, önceki sürümde olduğu gibi davranır. Aynı durum Visual Studio 2010 SP1'de oluşturulmuş birçok varlık için de geçerlidir.

Visual Basic için, Visual Studio 2015 Visual Studio 2013 içinde oluşturulan bir Visual Basic uygulamasının derlenerek bir değişiklik sunmayacak. Visual Studio 2015 kullanılarak yeniden derlenen Visual Basic uygulamaların çalışma zamanı davranışı değişmeyecektir.

Visual Studio 2015 ' i Visual Studio 2013, Visual Studio 2012 veya Visual Studio 2010 SP1 ile birlikte kullanıyorsanız, sürümlerden herhangi birinde projeler ve dosyalar oluşturabilir ve değiştirebilirsiniz. Bir veya daha fazla sürümde desteklenmeyen özellikler eklememiş olduğunuz sürece projeleri ve dosyaları sürümler arasında aktarabilirsiniz.

## <a name="projects"></a><a name="project"></a> Projeyle

Aşağıdaki listede Visual Studio 2015 ' de ve Visual Studio 2012 ya da Visual Studio 2010 SP1 'de oluşturulmuş projeler için Visual Studio 2013 desteği açıklanmaktadır. Projeyi Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 veya Visual Studio 2010 SP1 'de "olduğu gibi" açıp açabildiğinizden emin olmak için bu listeyi kullanın.

|Proje Türü|Uyumluluk|
|---------------------|-------------------|
|Evrensel Windows Platformu uygulamalar|Araçlar Evrensel Windows uygulamaları yüklemek için, Visual Studio Kurulumu 'nda **özel** veya **Değiştir**' i seçin ve ardından **Evrensel Windows uygulaması geliştirme araçları**' nı seçin.<br /><br /> Windows 10 için Evrensel Windows Platformu (UWP) uygulama geliştirmesi yalnızca Windows 10 veya üzerinde Visual Studio 2015 ' de desteklenir [!INCLUDE[win81](../includes/win81-md.md)] .|
|Windows Mağazası uygulamaları|Windows 8.1 ve Windows Phone 8,1 ' i hedefleyen evrensel uygulamalar da dahil olmak üzere Windows Mağazası uygulaması geliştirme, [!INCLUDE[win81](../includes/win81-md.md)] ve Windows 10 ' da desteklenir. Mevcut [!INCLUDE[win8](../includes/win8-md.md)] Projeler hizmet verilmeye devam edebilir, ancak yeni [!INCLUDE[win8](../includes/win8-md.md)] Projeler oluşturulamaz. [!INCLUDE[win81](../includes/win81-md.md)] projeler yalnızca belirli başvuru türlerine bağlı olabilir. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md). **Note:** [!INCLUDE[win81](../includes/win81-md.md)] Visual Studio 2015 veya Visual Studio 2013 kullanarak oluşturduğunuz projeler Visual Studio 2012 ' de açılamaz.   Bunun nedeni, [!INCLUDE[win81](../includes/win81-md.md)] Visual studio 2015 kullanılarak oluşturulan ve Visual Studio 2013 bu sürümleri hedefleyerek ve Visual Studio 2012 ' nin yalnızca hedef projeleri desteklediği bir olanlardır [!INCLUDE[win8](../includes/win8-md.md)] [!INCLUDE[win8](../includes/win8-md.md)] .|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Bu projeleri Visual Studio 2015 ' de oluşturabilir ve kullanabilirsiniz ve uygun Çoklu hedefleme paketini yükledikten sonra Visual Studio 2013. Bu projeler Visual Studio 2010 SP1 sürümünde desteklenmez.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Visual Studio 2015, Visual Studio 2013 ve Visual Studio 2012 ' de bu projeleri oluşturabilir ve açabilirsiniz, ancak Visual Studio 2010 SP1 'de kullanamazsınız.|
|BizTalk|BizTalk Server projeleri Visual Studio 2015 veya Visual Studio 2013 uyumlu değildir.|
|C#/Visual Basic Silverlight 4 Uygulaması veya Sınıf Kitaplığı|Visual Studio 'Nun projeyi otomatik olarak güncelleştirmesine izin verirseniz, Visual Studio 2013 ya da Visual Studio 2012 ' de açabilirsiniz.|
|C#/Visual Basic Webform veya Windows Form|Projeyi Visual Studio 2013 ve Visual Studio 2012 ' de açabilirsiniz.|
|Visual Basic 6 ve Visual C++ 6|Visual Studio 2012 ve Visual Studio 2013 Visual Basic 6 veya Visual C++ 6 ile oluşturulmuş uygulamalarda hata ayıklamayı desteklemez; Bu uygulamalarda hata ayıklamak için Visual Studio 'nun önceki sürümlerini kullanın.|
|Kodlanmış UI testi|Visual Studio 'Nun projeyi otomatik olarak güncelleştirmesine izin verirseniz, Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|F#|Visual Studio 'Nun Visual Studio 2010 SP1 'de oluşturulmuş bir projeyi yükseltmesine izin verirseniz, Visual Studio 2013 ve Visual Studio 2012 ' de açabilirsiniz. Ancak, Visual Studio 'nun daha eski bir sürümünde oluşturulmuş bir Silverlight projesini Visual Studio 2013 için yükseltemezsiniz. Bunun yerine, Visual Studio 2013 bir Silverlight projesi oluşturmanız ve ardından kodunuzu buna kopyalamanız gerekir. Visual Studio 2013 hedef Silverlight 5 ' te oluşturduğunuz Silverlight projeleri.|
|LightSwitch|Visual Studio 'Nun projeyi otomatik olarak yükseltmesine izin verirseniz, yalnızca Visual Studio 2013 ' de açabilirsiniz.|
|Yerel Veritabanı Önbelleği|Yerel veritabanı önbelleği şablonu ve **veri eşitlemesini Yapılandır** iletişim kutusu Visual Studio 2013 ' de bulunmaz. Microsoft Eşitleme Hizmetleri v 1.0 yüklüyse içinde oluşturulan projeleri açmak ve çalıştırmak için Visual Studio 2013 kullanabilirsiniz [!INCLUDE[vs2010](../includes/vs2010-md.md)] , ancak bunları Visual Studio 2013 güncelleştirmek istiyorsanız, tüm değişiklikleri kodda el ile yapmanız gerekir. Alternatif olarak, [!INCLUDE[vs2010](../includes/vs2010-md.md)] Bu projeleri sürdürmek ve güncelleştirmek için kullanmaya devam edebilirsiniz.  Yeni geliştirme için Microsoft Sync Framework tarafından sağlanan yeni eşitleme modelini hedef alın. Bilgi için bkz. [Microsoft Sync Framework Geliştirici Merkezi](https://msdn.microsoft.com/sync/default)|
|Model-Görünüm-Denetleyici çerçevesi|Visual Studio 2010 SP1 yalnızca MVC 2 ve MVC 3 ' ü destekler, Visual Studio 2012 yalnızca MVC 3 ve MVC 4 ' ü destekler ve Visual Studio 2013 yalnızca MVC 4 ' ü destekler. MVC 2 ' den MCV 3 ' e otomatik olarak yükseltme hakkında daha fazla bilgi için bkz. [ASP.NET MVC 3 uygulama yükseltme](https://aspnet.codeplex.com/releases/view/59008). MVC 2 ' den MVC 3 ' e el ile yükseltme hakkında bilgi için, bkz. [ASP.NET MVC 2 projesini ASP.NET MVC 3 araç güncelleştirmesine yükseltme](https://aspnet.codeplex.com/releases/view/59008). MVC3 'ten MVC 4 ' e el ile yükseltme hakkında bilgi için bkz. [ASP.NET MVC 3 projesini ASP.NET MVC 4 ' e yükseltme](/aspnet/whitepapers/mvc4-release-notes). Projeniz .NET Framework 3.5 SP1'i hedefliyorsa, .NET Framework 4 kullanacak şekilde yeniden hedef belirlemeniz gerekir.|
|Modelleme|Visual Studio 'Nun projeyi otomatik olarak güncelleştirmesine izin verirseniz, Visual Studio 2013, Visual Studio 2012 veya Visual Studio 2010 SP1 içinde açabilirsiniz.<br /><br /> Team Foundation bir modelleme projesi oluşturduğunda proje içindeki katmanları doğrulamaya çalışır. Visual Studio 2013, Team Foundation derlemesi, Visual Studio 2010 SP1 'de oluşturulan bir modelleme projesi için katmanları doğrulayamaz. Ancak, Visual Studio 2010 SP1 'de, Team Foundation derlemesi, Visual Studio 2013 oluşturulan bir modelleme projesindeki katmanları doğrulayabilir.|
|MPI/Küme Hata Ayıklama|Visual Studio 2013, Visual Studio 2012 veya Visual Studio 2010 SP1 çalıştıran bilgisayarlarda aynı çalışma zamanının veya araçların sürümü yüklüyse, bu projeyi üç sürümde de açabilirsiniz.|
|MSI kurulumu (.vdproj)|Bu proje, bu proje türünü desteklemediğinden Visual Studio 2013 açılamaz. Çoğu Windows platformunu ve uygulama çalışma zamanını doğrudan destekleyen ücretsiz bir dağıtım çözümü olarak Visual Studio için InstallShield Limited Edition (ISLE) kullanmanızı öneririz. Visual Studio Yükleyicisi projelerinden verileri ve ayarları içeri aktarmak için de ISLE kullanabilirsiniz. .|
|Office 2007 VSTO|Projeyi Office 2013 ve .NET Framework 4 ' ü hedefleyecek şekilde yükseltirseniz, bu projeyi Visual Studio 2013, Visual Studio 2012 veya Visual Studio 2010 SP1 içinde açabilirsiniz.|
|Office 2010 VSTO|Proje .NET Framework 4 ' ü hedefliyorsa, bu dosyayı Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz. Tüm diğer projeler tek yönlü yükseltme gerektirir.|
|Zengin Internet Uygulamaları|Projeyi yükseltirseniz, Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|SharePoint 2007|Bu proje Visual Studio 2013 açılamaz. Ancak, projeyi SharePoint 2010 'ye el ile yükseltirseniz, Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 'de açabilirsiniz. SharePoint 2007 ' i yükseltme hakkında daha fazla bilgi için bkz. SharePoint [2007 ' den sharepoint 2010 'e geçiş](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) , [SharePoint Server 2010 için BT uzmanı ve SharePoint kurumsal arama geçiş aracı](/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Projeyi Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|SketchFlow|Visual Studio 'Nun projeyi WPF 4.5/Silverlight 5 ' e yükseltmesine izin verirseniz, Visual Studio 2012 ' de açabilir ve Visual Studio 2013.|
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] veritabanı|Projeyi Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz. SQL Server önceki bir sürümünde oluşturulmuş bir veritabanı dosyanız (. mdf) varsa, bunu [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] SQL Server Express LocalDB ile kullanabilmeniz için önce sürümüne yükseltmeniz gerekir, ancak veritabanı artık SQL Server önceki sürümleriyle uyumlu olmaz. Yükseltmezseniz, aynı bilgisayara yükleyerek ve kullanarak Visual Studio 2013 veritabanı ile çalışmaya devam edebilirsiniz [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] . Daha fazla bilgi için bkz [.. mdf dosyalarını yükseltme](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Çaba|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)]Visual Studio 2013, Visual studio 2012 ve Visual studio 2010 SP1 çalıştıran bilgisayarlarda Express yüklüyse, projeyi üç sürümde de açabilirsiniz.|
|SQL Server Rapor Projesi|Projeyi Visual Studio 2013 ve Visual Studio 2012 ' de açabilirsiniz. Yalnızca yerel mod için (yani, SQL Server bağlı olmadığında), içindeki görüntüleyiciyle ilişkili denetimler için tasarım zamanı deneyimini almazsınız [!INCLUDE[vs2010](../includes/vs2010-md.md)] , ancak proje çalışma zamanında düzgün şekilde çalışır. **Dikkat:**  Visual Studio 2013 özgü bir özellik eklerseniz, rapor şeması otomatik olarak yükseltilir ve artık projeyi Visual Studio 2012 ' de açamazsınız.|
|Birim testleri|[!INCLUDE[TCMext](../includes/tcmext-md.md)]Bu sürümlerde oluşturulan testleri açmak için Visual Studio 2013, Visual studio 2012 ve Visual studio 2010 SP1 içinde kullanabilirsiniz.|
|Visual C++|Visual Studio 2012 veya Visual Studio 2010 SP1 'de oluşturulan bir C++ projesini açmak için Visual Studio 2013 kullanabilirsiniz. Visual Studio 2012 ' de oluşturulmuş bir proje oluşturmak için Visual Studio 2013 derleme ortamını kullanmak istiyorsanız, Visual Studio 'nun her iki sürümünün de aynı bilgisayarda yüklü olması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual C++ projelerini Visual Studio 2015 'ye yükseltme](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) ve [Visual C++ taşıma ve Yükseltme Kılavuzu](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Visual Studio 2010 web|Visual Studio 'Nun projeyi otomatik olarak yükseltmesine izin verirseniz, Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|Visual Studio 2010 Veritabanı (.dbproj)|Projeyi bir SQL Server Veri Araçları veritabanı projesine dönüştürürseniz, bunu Visual Studio 2013 açabilirsiniz. Ancak Visual Studio 2013 bu yapıtları desteklemez:<br /><br /> -birim testleri<br />-veri oluşturma planları<br />-veri karşılaştırma dosyaları<br />-Statik kod analizi için özel kural uzantıları<br />-Server. sqlsettings<br />-. sqlcmd dosyaları<br />-Özel dağıtım uzantıları<br />-kısmi projeler (. Files)<br /><br /> SQL Server Veri Araçlarını yüklerseniz, dönüştürme işleminden sonra Visual Studio 2010 SP1 ile projeyi açabilirsiniz. Daha fazla bilgi için bkz. [Microsoft SQL Server veri araçları](https://msdn.microsoft.com/data/tools.aspx).|
|Visual Studio 2010 Görsel Veritabanı Araçları|Bu projeyi Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|Visual Studio Laboratuvar Yönetimi|[!INCLUDE[TCMext](../includes/tcmext-md.md)]Bu sürümlerde oluşturulan ortamları açmak için, Visual Studio 2013, Visual studio 2012 ve Visual studio 2010 SP1 'i kullanabilirsiniz. Ancak, ortamları oluşturmadan önce Microsoft Test Yöneticisi sürümünüzün Team Foundation Server sürümünüz ile eşleşmesi gerekir.|
|Visual Studio Makrosu|Bu proje, proje türünü desteklemediğinden Visual Studio 2013 açılamaz.|
|Visual Studio SDK/VSIX|Visual Studio SDK projesini Visual Studio 2013 sürümüne yükselttikten sonra, Visual Studio 2012 ' de açılamaz. Daha fazla bilgi için bkz. [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2015 'ye geçirme](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Visual Studio için Microsoft Azure Araçları|Visual Studio sürüm 2,1 için Microsoft Azure araçları kullanıyorsanız, projeyi Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz. Önceki sürümleri hedefleyen projeler için, Visual Studio 'Nun projeyi 2,1 sürümüne yükseltmesine izin verirseniz, Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|Windows Communication Foundation, Windows Presentation Foundation|Bu projeyi Visual Studio 2013, Visual Studio 2012 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|Windows Mobile|Bu proje, proje türünü desteklemediğinden Visual Studio 2013 açılamaz.|
|Windows Phone 7,1|Visual Studio 'Nun projeyi Windows Phone 8,0 ' e yükseltmesine izin verirseniz, Visual Studio 2012 ' de açabilir ve Visual Studio 2013.|
|Diğer|Visual Studio 2012, Visual Studio 2013 ve Visual Studio 2010 SP1 'de diğer birçok proje türünü açabilirsiniz.|
|FrontPage Web Siteleri|Bu proje, proje türünü desteklemediğinden Visual Studio 2013 açılamaz.|
|Taşınabilir Sınıf Kitaplığı|Visual Studio 'Nun projeyi otomatik olarak güncelleştirmesine izin verirseniz, Visual Studio 2013, Visual Studio 2012 veya Visual Studio 2010 SP1 içinde açabilirsiniz.<br /><br /> -Silverlight 4 ' ü hedefleyen projeler Silverlight 5 ' i hedefleyecektir.<br />-7,0 veya Windows Phone 7,5 Windows Phone hedeflenen projeler 8 ' i hedefleyecek Windows Phone.<br />-Xbox 360 hedeflenen projeler artık Xbox 360 ' i hedeflemiyor.|
|. Deployproj uzantılı bulut hizmeti projeleri (. ccproj uzantısı) ve Azure Resource Manager projeleri (bulut dağıtım projeleri) gibi Azure projeleri|Bu proje türlerini açmak için önce [.net Için Azure SDK](https://azure.microsoft.com/downloads/)'yı yükledikten sonra projeyi açın.|

## <a name="troubleshooting-project-compatibility-issues"></a>Proje uyumluluk sorunlarını giderme
 Bu, bir proje Visual Studio 2015 veya Visual Studio 2013 'de açılmayabilmeniz gereken bazı şeyler aşağıda verilmiştir:

- Visual Studio 2015 veya Visual Studio 2013 desteklenmeyen bir projeyi açmayı denerseniz ve Visual Studio 'nun ilişkili sürümü yüklü değilse, proje türünün desteklenmediği bir ileti görünebilir ve proje türü, **desteklenmeyen projeler**altındaki **Proje ve çözüm değişikliklerini gözden geçir** iletişim kutusunda listelenmiş olabilir. Bu sorunu çözmek için, Windows **Denetim Masası**'ndaki programlar ve Özellikler sayfasını açın, **Visual Studio**' yı seçin ve ardından **Değiştir**, **Onar**' ı seçin. Bunun ardından eksik sürümü yükleyebilirsiniz.

- İçindeki bir masaüstü uygulaması için bir projeyi açmayı denerseniz [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] , bir hata oluşur ve bu iletilerden biri görüntülenir: "Visual Studio 'Nun bu sürümü yalnızca [!INCLUDE[win81](../includes/win81-md.md)] uygulamaları destekler" veya "Bu proje, geçerli Visual Studio sürümü ile uyumlu değil." [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] , Windows 8.1 için tasarlanan Windows Mağazası uygulamalarının geliştirilmesi, sınanması ve dağıtımı ile kısıtlıdır. Bir masaüstü uygulaması projesini açmak için, bu proje türünü destekleyen bir Visual Studio sürümünü kullanmanız gerekir.

   Visual Studio sürümleri hakkında daha fazla bilgi için bkz. [Microsoft Visual Studio Products](https://visualstudio.microsoft.com/products/)

- Masaüstünde bir Windows Mağazası uygulama projesi açmaya çalışırsanız [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] bir hata oluşur. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Masaüstü, Windows Mağazası uygulamaları oluşturmak için kullanılamaz. Windows Mağazası uygulamaları oluşturmak istiyorsanız, ' yi de yükleyebilirsiniz [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] . Ya da tüm Microsoft platformlarına ve web'e yönelik uygulamalar geliştirmek için, Visual Studio Professional 2013'ü deneyin.

- Bir proje, Visual Studio 2013 özgü özellikler gerektiriyorsa, önceki bir sürümde açılamaz.

- Visual Studio 2012 kullanıyorsanız ve Visual Studio 2013 oluşturduğunuz bir projeyi açmak istiyorsanız, proje sistemini Visual Studio 2013 özelliklerini içerecek şekilde özelleştirebilirsiniz. Bunun nasıl yapılacağı hakkında bilgi için bkz. [özel proje sürümü duyarlı hale getirme](../misc/making-custom-projects-version-aware.md).

  Ek sorun giderme bilgileri için [Visual Studio 2013 uyumluluk](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) KB makalesine bakın.

## <a name="files"></a><a name="file"></a> Dosyalarý

Aşağıdaki liste, Visual Studio 2013 her dosya türünü destekleyip desteklemediğini tanımlar. dosyayı Visual Studio 2012 ve Visual Studio 2010 SP1 'de açıp açamayacağını ve uyumluluğu sağlamak için değiştirip değiştirmeyeceğinizi belirtir.

|Dosya Türü|Uyumluluk|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (.xml dosyaları)|Bu dosyaları Visual Studio 2012, Visual Studio 2013 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|BizTalk düz dosya şemaları|Bu şemaları, Visual Studio 2013 bir BizTalk 2013 projesine ekleyebilirsiniz. Düz dosya şemaları olan BizTalk 2010 projeleriyle Visual Studio 2013 kullanmak için, Visual Studio 2013 olan bilgisayara BizTalk 2013 ' yi yüklersiniz. BizTalk 2010 projesini ilk açışınızda, otomatik olarak BizTalk 2013 veya Visual Studio 2013 proje sistemine yükseltilir.|
|İstemci Rapor Tanımı (.rdlc) dosyaları|Bu dosyaları Visual Studio 2013 açabilirsiniz ve Visual Studio 2013 özellikleri ve denetimleri eklerseniz şema otomatik olarak yükseltilir.|
|Kod analizi kural kümeleri|Bu dosyaları Visual Studio 2012, Visual Studio 2013 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|Veri katmanı uygulama paketi dosyaları|Bu dosyaları, sürüm 2,0 veya sürüm 2,5 ise Visual Studio 2013 açabilirsiniz.|
|Hata ayıklayıcı döküm dosyaları|Bu dosyaları Visual Studio 2012, Visual Studio 2013 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|Yönlendirilmiş Grafik Biçimlendirme Dili (DGML) diyagram dosyaları|Dosyayı değiştirmeden Visual Studio 2012, Visual Studio 2013 ve Visual Studio 2010 SP1 içinde bu dosyaları açabilirsiniz.|
|Varlık Veri Modeli (EDMX) dosyaları|Visual Studio 2013, dosyayı değiştirmeden .NET Framework 4,5 veya .NET Framework 4 ' ü hedefleyen bir EDMX dosyasını açabilirsiniz.|
|Profil Oluşturucu rapor dosyaları|Visual Studio 2012 ve Visual Studio 2013 profil Oluşturucu rapor dosyalarını (. vsp. vsps,. psess ve. vspf) açabilirsiniz. .vspx dosyası Visual Studio 2010 SP1'de açılamaz.|
|Çözüm (.suo) dosyası|Visual Studio 2012 veya Visual Studio 2010 SP1 'de oluşturulan bir çözüm dosyasını açmak için Visual Studio 2013 kullanabilirsiniz|
|SQL Server Compact Edition|Visual Studio 2013 SQL Server Compact sürümünü desteklemez.|
|SQLX dosyaları|Bu dosyaları Visual Studio 2013 açmak için tek yönlü bir yükseltme gerçekleştirmeniz, Visual Studio 'nun hedef sürümünde. sqlx dosyasını dağıtmanız ve ardından dosyayı. dacpac biçiminde yeniden oluşturmanız gerekir.|
|IntelliTrace günlük dosyaları [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Bu dosyaları Visual Studio 2012, Visual Studio 2013 ve Visual Studio 2010 SP1 içinde açabilirsiniz.|
|JavaScript Bellek Çözümleyicisi (.diagsession) dosyaları|Visual Studio 'nun eski sürümleri tarafından oluşturulan dosyalar Visual Studio 2013 ' de görüntülenebilir. Ancak, toplanan bilgilere bağlı olarak Visual Studio 2013 içinde oluşturulan dosyalar Visual Studio 2012 veya Visual Studio 2010 SP1 'de açılmayabilir.|

## <a name="integration-assets"></a><a name="integration"></a> Tümleştirme varlıkları

Visual Studio Team Foundation Server ürününün farklı sürümlerine ait istemciler ve sunucular kullanırsanız uyumluluk sorunlarıyla karşılaşabilirsiniz.

|Tümleştirme Türü|Uyumluluk|
|-------------------------|-------------------|
|Kod İncelemesi ve Çalışmam|Bir istemcisini ' a bağladığınızda kod Incelemesi ve çalışmam özellikleri çalışmaz [!INCLUDE[esprfound](../includes/esprfound-md.md)] [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] .|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|[!INCLUDE[esprbuild](../includes/esprbuild-md.md)]İçinde oluşturulan uygulamaları derlemek Için MSBuild veya gibi 64 bitlik bir ortam kullanılamaz [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] .|

## <a name="see-also"></a>Ayrıca bkz.

- [Özel proje sürümü duyarlı hale getirme](../misc/making-custom-projects-version-aware.md)
