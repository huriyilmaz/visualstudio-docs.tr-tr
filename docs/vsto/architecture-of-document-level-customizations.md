---
title: Belge düzeyi özelleştirmelerin mimarisi
description: Özelleştirme bileşenleri de dahil olmak üzere belge düzeyinde özelleştirmelerin yönleri ve özelleştirmelerin uygulamalarla nasıl Microsoft Office öğrenin.
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
ms.openlocfilehash: ac1fcfaf7a2e5704a82550e31c1d0e2204f52923a4ea8a63fd6360642a1dbb58
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352323"
---
# <a name="architecture-of-document-level-customizations"></a>Belge düzeyinde özelleştirmelerin mimarisi
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]Word ve Microsoft Office için belge düzeyinde özelleştirmeler oluşturmaya yönelik projeleri Microsoft Office Excel. Bu konuda, belge düzeyi özelleştirmelerin aşağıdaki yönleri açıklanmıştır:

- [Özelleştirmeleri anlama](#UnderstandingCustomizations)

- [Özelleştirme bileşenleri](#Components)

- [Özelleştirmeler Microsoft Office çalışır](#HowCustomizationsWork)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Belge düzeyinde özelleştirmeler oluşturma hakkında genel bilgi için bkz. Office çözüm geliştirmesine [genel bakış &#40;VSTO&#41;, ](../vsto/office-solutions-development-overview-vsto.md)Word için [Kullanmaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-word.md)programlama belge düzeyi özelleştirmeleri ve Kullanmaya başlayın için belge düzeyi özelleştirmeleri [programlama Excel.](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

## <a name="understand-customizations"></a><a name="UnderstandingCustomizations"></a> Özelleştirmeleri anlama
 Belge düzeyi özelleştirme Office için Visual Studio geliştirici araçlarını kullanırsanız, belirli bir belgeyle ilişkilendirilmiş bir yönetilen kod derlemesi oluşturmanız gerekir. Bağlantılı derleme içeren bir belgenin veya çalışma kitabının yönetilen kod uzantıları olduğu kabul edildi. Daha fazla bilgi için, [bkz. Tasarım ve Office çözümleri.](../vsto/designing-and-creating-office-solutions.md)

 Kullanıcı belgeyi açtığında derleme, Microsoft Office yüklenir. Derleme yüklendikten sonra, özelleştirme belge açıkken olaylara yanıt verir. Özelleştirme, belge açıkken uygulamayı otomatikleştirmek ve genişletmek için nesne modeline çağrı da kullanabilir ve içinde sınıflardan herhangi birini [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] kullanabilir.

 Derleme, uygulamanın birincil birlikte çalışma derlemesi aracılığıyla uygulamanın COM bileşenleriyle iletişim kurar. Daha fazla bilgi için [bkz. Office birlikte çalışma derlemeleri ve](../vsto/office-primary-interop-assemblies.md) [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 Bir kullanıcı aynı anda birden çok belge düzeyi özelleştirme açarsa, her derleme farklı bir uygulama etki alanına yüklenir. Bu, yanlış davranan bir çözümün diğer çözümlerin başarısız olmasına neden olamayacak anlamına gelir. Belge düzeyinde özelleştirmeler, tek bir uygulama etki alanında tek bir belgeyle çalışacak şekilde tasarlanmıştır. Bunlar, çapraz belge iletişimi için tasarlanmaz. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [Uygulama etki alanları.](/dotnet/framework/app-domains/application-domains)

> [!NOTE]
> Office geliştirici araçlarını kullanarak Visual Studio belge düzeyinde özelleştirmeler, Visual Studio yalnızca uygulama son kullanıcı tarafından başlatılana kadar kullanılacak şekilde tasarlanmıştır. Uygulama program aracılığıyla, örneğin Otomasyon kullanılarak başlatıldı ise, özelleştirme beklendiği gibi çalışmayabilirsiniz.

### <a name="design-time-and-run-time-experiences"></a>Tasarım zamanı ve çalışma zamanı deneyimleri
 Belge düzeyinde özelleştirmelerin mimarisini anlamak için çözüm tasarlama ve çözüm çalıştırma deneyimlerini anlamanıza yardımcı olur.

#### <a name="design-time"></a>Tasarım zamanı
 Tasarım zamanı deneyimi aşağıdaki adımları içerir:

1. Geliştirici içinde belge düzeyinde bir proje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur. Proje, belgeyi ve belgenin arkasında çalışan derlemeyi içerir. Belge zaten mevcut olabilir (tasarımcı tarafından oluşturulmuş olabilir) veya projeyle birlikte yeni bir belge de oluşturulabilir.

2. Tasarımcı (projeyi oluşturan geliştirici veya başka biri) son kullanıcı için belgenin son görünüm ve hissini oluşturur.

#### <a name="runtime"></a>Çalışma Zamanı
 Çalışma zamanı deneyimi aşağıdaki adımları içerir:

1. Son kullanıcı, yönetilen kod uzantılarına sahip bir belge veya çalışma kitabı açar.

2. Belge veya çalışma kitabı derlenmiş derlemeyi yükler.

3. Derleme, kullanıcı belge veya çalışma kitabında çalışırken olaylara yanıt verir.

#### <a name="developer-and-end-user-perspective-compared"></a>Geliştirici ve son kullanıcı perspektifi karşılaştırması
 Geliştirici öncelikli olarak içinde ve son kullanıcı Word veya Excel içinde çalışmalarından dolayı, belge düzeyi özelleştirmeleri anlamanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iki yolu vardır.

|Geliştirici Perspektifi|Son Kullanıcının Perspektifi|
|-----------------------------|----------------------------|
|kullanarak, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] geliştirici Word ve Excel tarafından erişilebilen kodu yazar.<br /><br /> Geliştirici Word veya Excel çalıştıran yürütülebilir bir dosya oluşturuyor gibi görünse de işlem tam olarak tam olarak yolunda ilerler. Belge bir derlemeyle ilişkilendirildi ve bu derlemeye yönelik bir işaretçi içeriyor. Belge açıldığında Word veya Excel derlemeyi bulup tüm işlenmiş olaylara yanıt olarak kodu çalıştırır.|Çözümü kullananlar, diğer tüm belge dosyalarında olduğu gibi belgeyi veya çalışma kitabını açmaları (veya şablondan yeni bir belge oluşturmaları) Microsoft Office olur.<br /><br /> Derleme, belge veya çalışma kitabında, belgeyi otomatik olarak geçerli verilerle doldurmak veya bilgi isteğinde etmek için bir iletişim kutusu göstermek gibi özelleştirmeler sağlar.|

### <a name="supported-document-formats-for-document-level-customizations"></a>Belge düzeyinde özelleştirmeler için desteklenen belge biçimleri
 Bir özelleştirme projesi ekleyebilirsiniz, projede kullanmak istediğiniz belgenin biçimini seçebilirsiniz. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

 Aşağıdaki tabloda, Word ve Word için belge düzeyi özelleştirmelerde kullanabileceğiniz Excel biçimleri listelemektedir.

|Excel|Word|
|-----------|----------|
|Excel çalışma kitabı (*.xlsx*)<br /><br /> Excel etkin çalışma kitabı (*.xlsm*)<br /><br /> Excel ikili çalışma kitabı (*.xlsb*)<br /><br /> Excel 97-2003 çalışma kitabı (*.xls*)<br /><br /> Excel şablonu (*.xltx*)<br /><br /> Excel etkin şablon (*.xltm*)<br /><br /> Excel 97-2003 şablonu (*.xlt*)|Word belgesi (*.docx*)<br /><br /> Word makro özellikli belge (*.docm*)<br /><br /> Word 97-2003 belgesi (*.doc*)<br /><br /> Sözcük şablonu (*.dotx*)<br /><br /> Word makro özellikli şablon (*.dotm*)<br /><br /> Word 97-2003 şablonu (*.dot*)|

 Yönetilen kod uzantılarını yalnızca desteklenen biçimlerde belgeler için tasarlamanız gerekir. Aksi takdirde, belge uygulamada açıldığında bazı olaylar ortaya çıkarılamayabilirsiniz. Örneğin, Excel XML elektronik tablo biçiminde veya web sayfasında <xref:Microsoft.Office.Tools.Excel.Workbook.Open> (.htm;** *.html*) Biçim.

### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Dosya adı uzantılarına sahip word .xml desteği
 Belge düzeyi proje şablonları, aşağıdaki dosya biçimlerini temel alan projeler oluşturmanıza izin vermez:

- Word XML Belgesi (*\* xml*).

- Word 2003 XML Belgesi (*\* xml*).

  Son kullanıcılarının bu dosya biçimlerinde özelleştirmeleri kullanmalarını istiyorsanız, yukarıdaki tabloda belirtilen desteklenen dosya biçimlerinden birini kullanan bir özelleştirmeyi derleme ve dağıtma. Özelleştirmeyi yükledikten sonra, son kullanıcılar belgeyi Word XML Belgesi (*\* xml*) biçiminde veya Word 2003 XML Belgesi (*\* xml*) biçiminde kaydedebilir ve özelleştirme beklendiği gibi çalışmaya devam eder.

## <a name="components-of-customizations"></a><a name="Components"></a> Özelleştirme bileşenleri
 Özelleştirmenin ana bileşenleri belge ve derlemedir. Bu bileşenlere ek olarak, uygulamaların özelleştirmeleri bulma ve yükleme konusunda Microsoft Office önemli bir rol üsten birkaç parça daha vardır.

### <a name="deployment-manifest-and-application-manifest"></a>Dağıtım bildirimi ve uygulama bildirimi
 Özelleştirmeler, özelleştirme derlemenin en güncel sürümünü tanımlamak ve yüklemek için dağıtım bildirimlerini ve uygulama bildirimlerini kullanır. Dağıtım bildirimi, geçerli uygulama bildirimini gösterir. Uygulama bildirimi özelleştirme derlemesini işaret ediyor ve derlemede yürütülecek giriş noktası sınıfını (veya sınıflarını) belirtir. Daha fazla bilgi için [bkz. Uygulama ve dağıtım bildirimleri Office.](../vsto/application-and-deployment-manifests-in-office-solutions.md)

### <a name="visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları Çalışma zamanı
 Visual Studio'de Office geliştirici araçları kullanılarak oluşturulan belge düzeyi özelleştirmeleri çalıştırmak Visual Studio son kullanıcı bilgisayarlarında [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklü olması gerekir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], özelleştirme derlemesi yüken yönetilemeyen bileşenleri ve ayrıca bir dizi yönetilen derlemeyi içerir. Bu yönetilen derlemeler, özelleştirme kodunuzun konak uygulamayı otomatikleştirmek ve genişletmek için kullandığı nesne modelini sağlar.

 Daha fazla bilgi için [bkz. Visual Studio çalışma zamanının Office araçları.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

## <a name="how-customizations-work-with-microsoft-office-applications"></a><a name="HowCustomizationsWork"></a>Özelleştirmeler Microsoft Office çalışır
 Kullanıcı bir özelleştirmenin parçası olan bir Microsoft Office açtığında, uygulama özelleştirme derlemesi'nin en güncel sürümünü bulmak ve yüklemek için belgeye bağlı dağıtım bildirimini kullanır. Dağıtım bildiriminin konumu AssemblyLocation adlı özel bir belge **özelliğinde depolanır.** Bu konumu tanımlayan dize, çözümü derlemek için özelliğine eklenir.

 Dağıtım bildirimi, uygulama bildirimini ve ardından en güncel derlemeyi gösterir. Daha fazla bilgi için [bkz. Uygulama ve dağıtım bildirimleri Office.](../vsto/application-and-deployment-manifests-in-office-solutions.md)

 Aşağıdaki çizimde belge düzeyinde özelleştirmenin temel mimarisi gösterilmiştir.

 ![2007 Office özelleştirme mimarisi](../vsto/media/office07-custom.png "2007 Office özelleştirme mimarisi")

> [!NOTE]
> 'Office çözümlerini hedef alan çözümler, doğrudan PIA'ya çağrı yapmak yerine çözüm derlemesine eklenmiş birincil birlikte çalışma derlemesi (PIA) türü bilgilerini kullanarak konak uygulamanın nesne modeline [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] çağrır. Daha fazla bilgi için, [bkz. Tasarım ve Office çözümleri.](../vsto/designing-and-creating-office-solutions.md)

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
