---
title: VSTO Eklentileri Mimarisi
description: VSTO Bu mimaride oluşturulan Visual Studio kararlılık ve güvenliği vurgulayan mimari özelliklere sahiptir ve bu özelliklerle yakın çalışmalarına olanak Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a8c192d9fb6c5f102247f0b38f412b94e3bdb5e6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726728"
---
# <a name="architecture-of-vsto-add-ins"></a>VSTO Eklentileri Mimarisi
  VSTO Visual Studio'daki Office araçları kullanılarak oluşturulan eklentiler, kararlılık ve güvenliği vurgulayan mimari özelliklere sahiptir ve bu özellikleri kullanarak Microsoft Office. Bu konu başlığında, VSTO özellikleri açıklanmıştır:

- [Ek VSTO anlama](#UnderstandingAddIns)

- [VSTO Bileşenleri](#AddinComponents)

- [VSTO uygulamalarıyla nasıl Microsoft Office çalışır?](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  Eklenti oluşturma hakkında genel VSTO için bkz. [Office](../vsto/office-solutions-development-overview-vsto.md) çözüm geliştirmeye genel bakış &#40;VSTO&#41;ve Kullanmaya başlayın programlama [VSTO.](../vsto/getting-started-programming-vsto-add-ins.md)

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a>Ek VSTO anlama
 Office Eklenti Visual Studio derlemek için VSTO geliştirici araçlarını kullanarak bir Microsoft Office uygulaması tarafından yüklenen bir yönetilen kod derlemesi oluşturabilirsiniz. Derleme yüklendikten sonra, VSTO eklenti uygulamada (örneğin, bir kullanıcı bir menü öğesini tıkladığında) olaylara yanıt verir. Uygulama VSTO eklenti, uygulamayı otomatikleştirmek ve genişletmek için nesne modeline çağrı da ekleyebilir ve içinde sınıflardan herhangi birini [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] kullanabilir.

 Derleme, uygulamanın birincil birlikte çalışma derlemesi aracılığıyla uygulamanın COM bileşenleriyle iletişim kurar. Daha fazla bilgi için [bkz. Office birlikte çalışma derlemeleri ve](../vsto/office-primary-interop-assemblies.md) [Office çözüm geliştirmeye genel &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 Bir VSTO birden çok eklenti yüklüyse, her VSTO Eklenti farklı bir uygulama etki alanına yüklenir. Bu, hatalı VSTO bir eklentinin diğer eklenti eklentilerinden birinin başarısız VSTO neden olamayacak olduğu anlamına gelir. Ayrıca, uygulama kapatılan zaman, tüm eklenti derlemelerinin VSTO kaldırıldıklarından emin olmak için yardımcı olur. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [Uygulama etki alanları.](/dotnet/framework/app-domains/application-domains)

> [!NOTE]
> VSTO Visual Studio'daki Office geliştirici araçlarını kullanarak Microsoft Office, yalnızca ana bilgisayar Microsoft Office son kullanıcı tarafından başlatılana kadar kullanılacak şekilde tasarlanmıştır. Uygulama program aracılığıyla (örneğin, Otomasyon kullanılarak) başlatıldı VSTO eklenti beklendiği gibi çalışmayabilirsiniz.

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a>VSTO Bileşenleri
 Eklenti VSTO ana bileşen olsa da, Microsoft Office uygulamalarının eklentilerini bulma ve yükleme konusunda önemli bir rol üst VSTO vardır.

### <a name="registry-entries"></a>Kayıt defteri girdileri
 Microsoft Office uygulamaları VSTO kayıt defteri girdileri arayarak eklentileri keşfeder. VSTO Eklentileri tarafından kullanılan kayıt defteri girdilerinin tam listesi için bkz. VSTO eklentileri için [kayıt defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)

 Çözümlerinizi derlemek için Visual Studio tüm gerekli kayıt defteri girdilerini geliştirme bilgisayarda oluşturur. Böylece, VSTO eklentinizin hata ayıklaması ve çalıştırması için. Daha fazla bilgi için [bkz. Derleme Office.](../vsto/building-office-solutions.md)

 Çözümlerinizi dağıtmak ClickOnce bir çözüm kullanırsanız, yayımlama işlemi tarafından oluşturulan Kurulum programı kayıt defteri anahtarlarını son kullanıcı bilgisayarda otomatik olarak oluşturur. Daha fazla bilgi için [bkz. Office kullanarak bir ClickOnce.](../vsto/deploying-an-office-solution-by-using-clickonce.md)

### <a name="deployment-manifest-and-application-manifest"></a>Dağıtım bildirimi ve uygulama bildirimi
 VSTO Eklentiler, eklenti derlemesi için dağıtım bildirimlerini ve uygulama bildirimlerini kullanarak uygulamanın en güncel VSTO yüklemesini sağlar. Dağıtım bildirimi, geçerli uygulama bildirimini gösterir. Uygulama bildirimi, VSTO eklenti derlemesini işaret ediyor ve derlemede yürütülecek giriş noktası sınıfını belirtir. Daha fazla bilgi için [bkz. Uygulama ve dağıtım bildirimleri Office.](../vsto/application-and-deployment-manifests-in-office-solutions.md)

### <a name="visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları Çalışma zamanı
 VSTO'da Office geliştirici araçları kullanılarak oluşturulan Visual Studio eklentileri çalıştırmak için, son kullanıcı bilgisayarlarında yüklü olması [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gerekir. Çalışma zamanı yönetilemeyen bileşenleri ve bir dizi yönetilen derlemeyi içerir. Unmanaged components load the VSTO add-in assembly. Yönetilen derlemeler, eklenti kodunuzun konak VSTO otomatikleştirmek ve genişletmek için kullandığı nesne modelini sağlar.

 Daha fazla bilgi için bkz. [Office için Visual Studio Araçları genel bakış.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a>VSTO uygulamalarıyla nasıl Microsoft Office çalışır?
 Bir kullanıcı bir Microsoft Office uygulamayı başlatırsa, uygulama, uygulamanın en güncel sürümünü bulmak ve yüklemek için dağıtım bildirimini ve VSTO bildirimini kullanır. Aşağıdaki çizimde bu eklentilerin temel VSTO gösterilmiştir.

 ![2007 Office eklenti mimarisi](../vsto/media/office07addin.png "2007 Office eklenti mimarisi")

> [!NOTE]
> içinde Office veya 'yi hedef alan çözümler, doğrudan PIA'ya çağrı yapmak yerine çözüm derlemesine eklenmiş PIA tür bilgilerini kullanarak konak uygulamanın nesne modeline [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] çağrır. Daha fazla bilgi için, [bkz. Tasarım ve Office çözümleri.](../vsto/designing-and-creating-office-solutions.md)

### <a name="loading-process"></a>Yükleme işlemi
 Kullanıcı bir uygulamayı başlatırken aşağıdaki adımlar gerçekleşir:

1. Uygulama, Office geliştirici araçlarını kullanarak oluşturulan VSTO eklentilerini Office girdileri Visual Studio.

2. Uygulama bu kayıt defteri girdilerini bulursa, uygulama VSTOEE.dll yükler ve VSTOLoader.dll. Bunlar, Office Runtime için Visual Studio 2010 Araçları'nın yükleyici bileşenleri olan Office. Daha fazla bilgi için bkz. [Office için Visual Studio Araçları genel bakış.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

3. *VSTOLoader.dll* yükler ve [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] yönetilen bölümünü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] başlatır.

4. Bildirim [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] güncelleştirmelerini denetler ve en son uygulama ve dağıtım bildirimlerini indirir.

5. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], bir dizi güvenlik denetimi gerçekleştirir. Daha fazla bilgi için [bkz. Güvenli Office çözümleri.](../vsto/securing-office-solutions.md)

6. Uygulama VSTO çalıştırmak için güvenilirse, derleme güncelleştirmelerini kontrol etmek için dağıtım [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bildirimini ve uygulama bildirimini kullanır. Derlemenin yeni bir sürümü kullanılabilirse, çalışma zamanı derlemenin yeni sürümünü istemci [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bilgisayarın önbelleğine indirir. Daha fazla bilgi için [bkz. Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

7. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] eklenti derlemesi için uygulamanın yük VSTO yeni bir uygulama etki alanı oluşturur.

8. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] eklenti VSTO uygulama etki alanına yükler.

9. , yönteminizi geçersiz VSTO eklentinizin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> eklentisinde yöntemini çağırır.

     Bu yöntemi isteğe bağlı olarak geçersiz kılarak VSTO nesnenizi diğer Microsoft Office kullanabilirsiniz. Daha fazla bilgi için [bkz. Diğer VSTO çözümlerinden eklentilerde kod Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

10. , yönteminizi geçersiz VSTO eklentinizin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> eklentisinde yöntemini çağırır.

     Genişletilebilirlik arabirimi uygulayan bir nesneyi döndürerek Microsoft Office özelliğini genişletmek için isteğe bağlı olarak bu yöntemi geçersiz kılabilirsiniz. Daha fazla bilgi için [bkz. Genişletilebilirlik arabirimlerini kullanarak kullanıcı arabirimi özelliklerini özelleştirme.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)

    > [!NOTE]
    > , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] konak uygulama tarafından desteklenen her genişletilebilirlik arabirimi için <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> yöntemine ayrı çağrılar yapar. yöntemine yapılan ilk çağrı genellikle yöntem çağrısının öncesinde gerçekleşir, ancak VSTO Eklentiniz yöntemin ne zaman çağrılacak veya kaç kez çağrılacak olduğuyla ilgili varsayımlarda <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> `ThisAddIn_Startup` <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> bulunmayacaktır.

11. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] `ThisAddIn_Startup` eklentinizin VSTO çağıran. Bu yöntem, olay için varsayılan olay <xref:Microsoft.Office.Tools.AddInBase.Startup> işleyicidir. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Belge düzeyinde özelleştirmelerin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [Office için Visual Studio Araçları çalışma zamanının genel bakışı](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
