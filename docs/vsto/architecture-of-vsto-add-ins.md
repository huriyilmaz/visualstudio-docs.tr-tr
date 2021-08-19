---
title: VSTO Eklentileri Mimarisi
description: VSTO Visual Studio oluşturulan eklentilerde, kararlılık ve güvenlik vurgularken mimari özellikler vardır ve bunların Microsoft Office yakından çalışmasını sağlayabilirsiniz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059926"
---
# <a name="architecture-of-vsto-add-ins"></a>VSTO Eklentileri Mimarisi
  VSTO Visual Studio Office geliştirici araçları kullanılarak oluşturulan eklentiler, kararlılık ve güvenliği vurgulayarak mimari özelliklerine sahiptir ve Microsoft Office yakından çalışmasını sağlar. bu konuda VSTO eklentilerin aşağıdaki yönleri açıklanmaktadır:

- [VSTO eklentilerini anlayın](#UnderstandingAddIns)

- [VSTO eklentilerin bileşenleri](#AddinComponents)

- [VSTO eklentileri Microsoft Office uygulamalarla nasıl çalışır](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  VSTO eklentiler oluşturma hakkında genel bilgi için, bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) ve [VSTO eklentileri programlamayı kullanmaya başlama](../vsto/getting-started-programming-vsto-add-ins.md).

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a>VSTO eklentilerini anlayın
 bir VSTO eklentisi oluşturmak için Visual Studio Office geliştirici araçları 'nı kullandığınızda, bir Microsoft Office uygulaması tarafından yüklenen bir yönetilen kod derlemesi oluşturursunuz. derleme yüklendikten sonra, VSTO eklentisi uygulamada oluşturulan olaylara yanıt verebilir (örneğin, bir kullanıcı bir menü öğesine tıkladığında). VSTO eklenti, uygulamayı otomatikleştirebilmek ve genişletmek için nesne modeline da çağrı yapabilir ve içindeki sınıflardan herhangi birini kullanabilir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 Derleme, uygulamanın COM bileşenleriyle uygulamanın birincil birlikte çalışma derlemesi aracılığıyla iletişim kurar. daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md) ve [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 bir uygulama için birden çok VSTO eklentisi yüklüyse, her bir VSTO eklentisi farklı bir uygulama etki alanına yüklenir. yani, yanlış şekilde davranan bir VSTO eklentisinin diğer VSTO eklentilerin başarısız olmasına neden olamaz. ayrıca, uygulama kapatıldığında tüm VSTO eklenti derlemelerinin bellekten kaldırıldığından emin olmaya de yardımcı olur. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [uygulama etki alanları](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> VSTO Visual Studio Office geliştirici araçlarını kullanarak oluşturduğunuz eklentiler, yalnızca host Microsoft Office uygulaması son kullanıcı tarafından başlatıldığında kullanılmak üzere tasarlanmıştır. uygulama programlı olarak başlatılırsa (örneğin, otomasyonu kullanarak) VSTO eklenti beklendiği gibi çalışmayabilir.

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a>VSTO eklentilerin bileşenleri
 VSTO eklenti derlemesi ana bileşen olsa da, Microsoft Office uygulamalarının VSTO eklentileri bulmasına ve yüklemesine ilişkin önemli bir rol oynayan birkaç farklı bileşen vardır.

### <a name="registry-entries"></a>Kayıt defteri girdileri
 Microsoft Office uygulamalar, bir kayıt defteri girişi kümesini arayarak VSTO eklentileri bulur. VSTO eklentileri tarafından kullanılan kayıt girdilerinin tam listesi için, bkz. [VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

 çözümünüzü oluşturduğunuzda Visual Studio, VSTO eklentilerinizi hata ayıklamanıza ve çalıştırabilmeniz için geliştirme bilgisayarında gerekli tüm kayıt defteri girişlerini oluşturur. daha fazla bilgi için bkz. [derleme Office çözümleri](../vsto/building-office-solutions.md).

 çözümünüzü dağıtmak için ClickOnce kullanıyorsanız, yayımlama işlemi tarafından oluşturulan kurulum programı, son kullanıcı bilgisayarında kayıt defteri anahtarlarını otomatik olarak oluşturur. daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

### <a name="deployment-manifest-and-application-manifest"></a>Dağıtım bildirimi ve uygulama bildirimi
 VSTO eklentiler, VSTO eklentisi derlemesinin en güncel sürümünü tanımlamak ve yüklemek için dağıtım bildirimlerini ve uygulama bildirimlerini kullanır. Dağıtım bildirimi geçerli uygulama bildirimini işaret eder. uygulama bildirimi VSTO eklentisi derlemesine işaret eder ve derlemede yürütülecek giriş noktası sınıfını belirtir. daha fazla bilgi için [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)bölümüne bakın.

### <a name="visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları Çalışma zamanı
 Visual Studio Office geliştirici araçları kullanılarak oluşturulan VSTO eklentilerini çalıştırmak için son kullanıcı bilgisayarlarının yüklü olması gerekir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Çalışma zamanı, yönetilmeyen bileşenleri ve yönetilen derlemelerin bir kümesini içerir. yönetilmeyen bileşenler VSTO eklentisi derlemesini yükler. yönetilen derlemeler, ana bilgisayar uygulamasını otomatikleştirmek ve genişletmek için VSTO eklentisi kodunun kullandığı nesne modelini sağlar.

 daha fazla bilgi için bkz. [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a>VSTO eklentileri Microsoft Office uygulamalarla nasıl çalışır
 kullanıcı Microsoft Office bir uygulama başlattığında, uygulama dağıtım bildirimini ve uygulama bildirimini kullanarak VSTO eklenti derlemesinin en güncel sürümünü bulur ve yükler. aşağıdaki çizimde bu VSTO eklentilerin temel mimarisi gösterilmektedir.

 ![2007 Office eklentisi mimarisi](../vsto/media/office07addin.png "2007 Office eklentisi mimarisi")

> [!NOTE]
> ya da ' i hedefleyen Office çözümlerinde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , çözüm derlemesine katıştırılmış pıa tür bilgilerini kullanarak doğrudan pıa ' a çağırmak yerine, çözümler ana bilgisayar uygulamasının nesne modeline çağrı yapılır. daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Yükleme işlemi
 Bir Kullanıcı uygulamayı başlattığında aşağıdaki adımlar oluşur:

1. uygulama, Visual Studio Office geliştirici araçları kullanılarak oluşturulan VSTO eklentilerini tanımlayan girişler için kayıt defterini denetler.

2. Uygulama bu kayıt defteri girdilerini bulursa, uygulama VSTOLoader.dll yükleyen VSTOEE.dll yükler. bunlar, Office çalışma zamanına yönelik Visual Studio 2010 araçları için yükleyici bileşenleri olan yönetilmeyen dll 'lerdir. daha fazla bilgi için bkz. [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* , [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] ' nin Yönetilen bölümünü yükler ve başlatır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Bildirim güncelleştirmelerini denetler ve en son uygulama ve dağıtım bildirimlerini indirir.

5. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Bir dizi güvenlik denetimi gerçekleştirir. daha fazla bilgi için bkz. [Secure Office solutions](../vsto/securing-office-solutions.md).

6. VSTO eklentisi çalıştırılmak üzere güvenilirse, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derleme güncelleştirmelerini denetlemek için dağıtım bildirimini ve uygulama bildirimini kullanır. Derlemenin yeni bir sürümü kullanılabiliyorsa, çalışma zamanı derlemenin yeni sürümünü [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] istemci bilgisayardaki önbelleğe indirir. daha fazla bilgi için bkz. [Office çözüm dağıtma](../vsto/deploying-an-office-solution.md).

7. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisi derlemesinin yükleneceği yeni bir uygulama etki alanı oluşturur.

8. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisi derlemesini uygulama etki alanına yükler.

9. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> öğesini geçersiz kıldıysanız VSTO eklenti içindeki yöntemi çağırır.

     isteğe bağlı olarak, VSTO eklentisi içindeki bir nesneyi diğer Microsoft Office çözümlerine göstermek için bu yöntemi geçersiz kılabilirsiniz. daha fazla bilgi için bkz. [diğer Office çözümlerdeki VSTO eklentilerdeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

10. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> öğesini geçersiz kıldıysanız VSTO eklenti içindeki yöntemi çağırır.

     isteğe bağlı olarak, bir genişletilebilirlik arabirimi uygulayan bir nesne döndürerek bir Microsoft Office özelliğini genişletmek için bu yöntemi geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

    > [!NOTE]
    > , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> Ana bilgisayar uygulaması tarafından desteklenen her bir genişletilebilirlik arabirimi için yöntemine ayrı çağrılar yapar. yöntemine yapılan ilk çağrı <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> genellikle yönteme çağrıdan önce gerçekleşse de `ThisAddIn_Startup` VSTO eklentisi metodun ne zaman <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> çağrılacağını veya kaç kez çağrılacağını hiçbir varsayımda içermemelidir.

11. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] `ThisAddIn_Startup` VSTO eklentisinin yöntemini çağırır. Bu yöntem, olay için varsayılan olay işleyicisidir <xref:Microsoft.Office.Tools.AddInBase.Startup> . daha fazla bilgi için bkz. [Office projelerindeki olaylar](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Office çözümlerin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
