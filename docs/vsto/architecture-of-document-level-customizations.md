---
title: Belge düzeyi özelleştirmelerinin mimarisi
description: özelleştirme bileşenleri ve özelleştirmelerin Microsoft Office uygulamalarla nasıl çalıştığı gibi belge düzeyi özelleştirmelerinin yönleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e7c4792049ee15fc1bc2343a139585cf1308abd4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047276"
---
# <a name="architecture-of-document-level-customizations"></a>Belge düzeyi özelleştirmelerinin mimarisi
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]Microsoft Office Word ve Microsoft Office Excel için belge düzeyi özelleştirmeleri oluşturmaya yönelik projeleri içerir. Bu konuda, belge düzeyi özelleştirmelerinin aşağıdaki yönleri açıklanmaktadır:

- [Özelleştirmeleri anlama](#UnderstandingCustomizations)

- [Özelleştirmelerin bileşenleri](#Components)

- [özelleştirmeler Microsoft Office uygulamalarla nasıl çalışır](#HowCustomizationsWork)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  belge düzeyi özelleştirmeleri oluşturma hakkında genel bilgi için, bkz. [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [Word için belge düzeyi özelleştirmelerini programlamaya](../vsto/getting-started-programming-document-level-customizations-for-word.md)başlayın ve [Excel için belge düzeyi özelleştirmeleri programlamaya](../vsto/getting-started-programming-document-level-customizations-for-excel.md)başlayın.

## <a name="understand-customizations"></a><a name="UnderstandingCustomizations"></a> Özelleştirmeleri anlama
 belge düzeyi özelleştirmesi oluşturmak için Visual Studio Office geliştirici araçlarını kullandığınızda, belirli bir belgeyle ilişkili bir yönetilen kod derlemesi oluşturursunuz. Bağlantılı bütünleştirilmiş koda sahip bir belge veya çalışma kitabı, yönetilen kod uzantılarına sahip olarak kabul edilir. daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

 bir kullanıcı belgeyi açtığında, derleme Microsoft Office uygulaması tarafından yüklenir. Bütünleştirilmiş kod yüklendikten sonra, özelleştirme, belge açıkken olaylara yanıt verebilir. Özelleştirme, belge açıkken uygulamayı otomatikleştirebilmek ve genişletmek için de nesne modelini çağırabilir ve içindeki sınıflardan herhangi birini kullanabilir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 Derleme, uygulamanın COM bileşenleriyle uygulamanın birincil birlikte çalışma derlemesi aracılığıyla iletişim kurar. daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md) ve [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 Bir kullanıcı aynı anda birden çok belge düzeyi özelleştirmesi açarsa, her derleme farklı bir uygulama etki alanına yüklenir. Bu, yanlış bir şekilde davranan bir çözümün diğer çözümlerin başarısız olmasına neden olamayacağı anlamına gelir. Belge düzeyi özelleştirmeleri tek bir uygulama etki alanında tek bir belgeyle çalışmak üzere tasarlanmıştır. Bunlar, belgeler arası iletişim için tasarlanmamıştır. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [uygulama etki alanları](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Visual Studio Office geliştirici araçlarını kullanarak oluşturduğunuz belge düzeyi özelleştirmeleri, yalnızca uygulama bir son kullanıcı tarafından başlatıldığında kullanılmak üzere tasarlanmıştır. Uygulama programlı olarak başlatılırsa (örneğin, Otomasyon kullanılarak), özelleştirme beklendiği gibi çalışmayabilir.

### <a name="design-time-and-run-time-experiences"></a>Tasarım zamanı ve çalışma zamanı deneyimleri
 Belge düzeyi özelleştirmelerinin mimarisini anlamak için, bir çözüm tasarlama ve çözüm çalıştırma deneyimlerini anlamaya yardımcı olur.

#### <a name="design-time"></a>Tasarım zamanı
 Tasarım zamanı deneyimi aşağıdaki adımları içerir:

1. Geliştirici içinde belge düzeyinde bir proje oluşturur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Proje, belgenin arkasında çalışan belgeyi ve derlemeyi içerir. Belge zaten var olabilir (tasarımcı tarafından oluşturulan) veya projeyle birlikte yeni bir belge oluşturulabilir.

2. Tasarımcı — projeyi veya başka birini oluşturan geliştirici, son kullanıcı için belgenin son görünümünü oluşturur.

#### <a name="runtime"></a>Çalışma Zamanı
 Çalışma zamanı deneyimi aşağıdaki adımları içerir:

1. Son Kullanıcı, yönetilen kod uzantılarına sahip bir belge veya çalışma kitabı açar.

2. Belge veya çalışma kitabı derlenen derlemeyi yükler.

3. Kullanıcı belge veya çalışma kitabında çalıştığından, derleme olaylara yanıt verir.

#### <a name="developer-and-end-user-perspective-compared"></a>Geliştirici ve Son Kullanıcı perspektifi karşılaştırması
 geliştirici öncelikle ' de çalıştığından [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve son kullanıcı Word 'de veya Excel çalıştığından, belge düzeyi özelleştirmelerini anlamayı sağlamanın iki yolu vardır.

|Geliştirici perspektifi|Son kullanıcının perspektifi|
|-----------------------------|----------------------------|
|Kullanarak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , geliştirici Word ve Excel erişilebilir kodu yazar.<br /><br /> geliştirici, Word veya Excel çalıştıran bir yürütülebilir dosya oluşturuyor gibi görünse de, işlem aslında başka bir şekilde çalışır. Belge, bir derleme ile ilişkilendirilir ve bu derlemeye yönelik bir işaretçi içerir. belge açıldığında, Word veya Excel derlemeyi bulur ve tüm işlenmiş olaylara yanıt olarak kodu çalıştırır.|çözümü kullanan kişiler, belgeyi veya çalışma kitabını (ya da bir şablondan yeni bir belge oluşturur) yalnızca diğer Microsoft Office dosyaları açtıklarında açar.<br /><br /> Derleme, belge veya çalışma kitabında otomatik olarak geçerli verilerle doldurma veya bilgi istemek için bir iletişim kutusu gösterme gibi özelleştirmeler sağlar.|

### <a name="supported-document-formats-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri için desteklenen belge biçimleri
 Bir özelleştirme projesi oluşturduğunuzda, projede kullanmak istediğiniz belge biçimini seçebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

 aşağıdaki tabloda, Excel ve Word için belge düzeyi özelleştirmelerde kullanabileceğiniz belge biçimleri listelenmektedir.

|Excel|Word|
|-----------|----------|
|Excel çalışma kitabı (*.xlsx*)<br /><br /> Excel makro özellikli çalışma kitabı (*. xlsm*)<br /><br /> Excel ikili çalışma kitabı (*. xlsb*)<br /><br /> Excel 97-2003 çalışma kitabı (*.xls*)<br /><br /> Excel şablonu (*. xltx*)<br /><br /> makro içerebilen şablon Excel (*. xltm*)<br /><br /> Excel 97-2003 şablonu (*. xlt*)|Word belgesi (*.docx*)<br /><br /> Makro içerebilen Word belgesi (*. docm*)<br /><br /> Word 97-2003 belgesi (*.doc*)<br /><br /> Word şablonu (*. dotx*)<br /><br /> Makro içerebilen Word şablonu (*. dotm*)<br /><br /> Word 97-2003 şablonu (*. dot*)|

 Yalnızca desteklenen biçimlerdeki belgeler için yönetilen kod uzantılarını tasarlamanız gerekir. Aksi takdirde, belge uygulamada açıldığında belirli olaylar çıkarılmayabilir. örneğin, <xref:Microsoft.Office.Tools.Excel.Workbook.Open> Excel XML elektronik tablo biçiminde veya web sayfasında (*.htm*; kaydedilmiş çalışma kitapları ile yönetilen kod uzantıları kullandığınızda olay oluşturulmaz. *.html*) formatını.

### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>.xml dosya adı uzantılarına sahip Word belgeleri için destek
 Belge düzeyi proje şablonları, aşağıdaki dosya biçimlerine bağlı olarak proje oluşturmanıza izin vermez:

- Word XML belgesi (*\* XML*).

- Word 2003 XML belgesi (*\* XML*).

  Son kullanıcılarınızın bu dosya biçimlerinde özelleştirmeler kullanmasını istiyorsanız Yukarıdaki tabloda belirtilen desteklenen dosya biçimlerinden birini kullanan bir özelleştirme oluşturun ve dağıtın. Özelleştirmeyi yükledikten sonra, son kullanıcılar belgeyi Word XML belgesi (*\* XML*) biçiminde veya Word 2003 XML belgesi (*\* XML*) biçiminde kaydedebilir ve özelleştirme beklendiği gibi çalışmaya devam eder.

## <a name="components-of-customizations"></a><a name="Components"></a> Özelleştirmelerin bileşenleri
 Bir özelleştirmenin ana bileşenleri belge ve derlemedir. bu bileşenlere ek olarak, Microsoft Office uygulamalarının özelleştirmeleri bulmasına ve yüklemesine ilişkin önemli bir rol oynayan birçok farklı bölüm de vardır.

### <a name="deployment-manifest-and-application-manifest"></a>Dağıtım bildirimi ve uygulama bildirimi
 Özelleştirmeler, özelleştirme derlemesinin en güncel sürümünü tanımlamak ve yüklemek için dağıtım bildirimlerini ve uygulama bildirimlerini kullanır. Dağıtım bildirimi geçerli uygulama bildirimini işaret eder. Uygulama bildirimi, özelleştirme derlemesini işaret eder ve derlemede yürütülecek giriş noktası sınıfını (veya sınıfları) belirtir. daha fazla bilgi için [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)bölümüne bakın.

### <a name="visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları Çalışma zamanı
 Visual Studio ' de Office geliştirici araçları kullanılarak oluşturulan belge düzeyi özelleştirmelerini çalıştırmak için son kullanıcı bilgisayarlarının yüklü olması gerekir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Özelleştirme derlemesini ve ayrıca yönetilen derlemelerin bir kümesini yükleyen yönetilmeyen bileşenleri içerir. Bu yönetilen derlemeler, özelleştirme kodunuzun konak uygulamayı otomatikleştirmek ve genişletmek için kullandığı nesne modelini sağlar.

 daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-customizations-work-with-microsoft-office-applications"></a><a name="HowCustomizationsWork"></a>özelleştirmeler Microsoft Office uygulamalarla nasıl çalışır
 bir kullanıcı Microsoft Office özelleştirmenin parçası olan bir belgeyi açtığında, uygulama özelleştirme derlemesinin en güncel sürümünü bulmak ve yüklemek için belgeye bağlı dağıtım bildirimini kullanır. Dağıtım bildiriminin konumu **AssemblyLocation** adlı bir özel belge özelliğinde depolanır. Bu konumu tanımlayan dize, çözümü oluştururken özelliğine eklenir.

 Dağıtım bildirimi, uygulama bildirimini işaret eder ve daha sonra en güncel derlemeye işaret eder. daha fazla bilgi için [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)bölümüne bakın.

 Aşağıdaki çizimde belge düzeyinde özelleştirmenin temel mimarisi gösterilmektedir.

 ![2007 Office özelleştirme mimarisi](../vsto/media/office07-custom.png "2007 Office özelleştirme mimarisi")

> [!NOTE]
> ' i hedefleyen Office çözümlerinde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , çözümler, pıa 'e doğrudan çağırmak yerine çözüm derlemesine gömülü birincil birlikte çalışma derlemesi (pıa) tür bilgilerini kullanarak ana bilgisayar uygulamasının nesne modeline çağrı yapılır. daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Yükleme işlemi
 Aşağıdaki adımlar, bir kullanıcı bir Microsoft Office çözümün parçası olan bir belgeyi açtığında gerçekleşir.

1. Uygulama Microsoft Office, belgeyle ilişkili yönetilen kod uzantıları olup olmadığını görmek için özel belge özelliklerini denetler. Daha fazla bilgi için [bkz. Özel belge özelliklerine genel bakış.](../vsto/custom-document-properties-overview.md)

2. Yönetilen kod uzantıları varsa, uygulamaVSTOEE.dllyükler *ve* *VSTOLoader.dll.* Bunlar, Office çalışma zamanı için Visual Studio 2010 Araçları'nın yükleyici bileşenleri olan Office. Daha fazla bilgi için bkz. [Office için Visual Studio Araçları genel bakış.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

3. *VSTOLoader.dll* yükler ve [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] yönetilen bölümünü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] başlatır.

4. Belge yerel bilgisayar dışında bir konumdan açılırsa, belge konumunun ilgili uygulama için Güven Merkezi Ayarlar'daki Güvenilen Konumlar listesinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yer Office  doğrular.  Belge konumu güvenilir bir konumda yoksa özelleştirmeye güvenilmiyor ve yükleme işlemi burada durur.

5. Çözümü henüz yüklenmemişse, en son uygulama ve dağıtım bildirimlerini indirir ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bir dizi güvenlik denetimi gerçekleştirir. Daha fazla bilgi için [bkz. Güvenli Office çözümleri.](../vsto/securing-office-solutions.md)

6. Özelleştirmenin çalışması güvenilirse, derleme [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] güncelleştirmelerini kontrol etmek için dağıtım bildirimini ve uygulama bildirimini kullanır. Derlemenin yeni bir sürümü kullanılabilirse, çalışma zamanı derlemenin yeni sürümünü istemci [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bilgisayarın önbelleğine indirir. Daha fazla bilgi için [bkz. Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

7. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] özelleştirme derlemesi yüklemek için yeni bir uygulama etki alanı oluşturur.

8. özelleştirme [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derlemesi uygulama etki alanına yüklenir.

9. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] özelleştirme **derlemenizin Başlangıç** olay işleyicisini çağırıyor. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözüm mimarisi Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office için Visual Studio Araçları çalışma zamanının genel bakışı](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md)
- [Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)
