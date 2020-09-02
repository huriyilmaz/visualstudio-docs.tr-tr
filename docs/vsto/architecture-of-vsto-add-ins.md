---
title: VSTO Eklentileri Mimarisi
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 401ce9b8421cd636fc72c59dcd6641ff4e05d968
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814524"
---
# <a name="architecture-of-vsto-add-ins"></a>VSTO Eklentileri Mimarisi
  Visual Studio 'da Office geliştirici araçları kullanılarak oluşturulan VSTO eklentileri, kararlılığı ve güvenliği vurgulayarak ve Microsoft Office yakından çalışmasını sağlayan mimari özelliklere sahiptir. Bu konuda, VSTO eklentilerinin aşağıdaki yönleri açıklanmaktadır:

- [VSTO Eklentilerini anlama](#UnderstandingAddIns)

- [VSTO eklentilerinin bileşenleri](#AddinComponents)

- [VSTO eklentileri Microsoft Office uygulamalarla nasıl çalışır?](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  VSTO eklentileri oluşturma hakkında genel bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;vsto&#41;](../vsto/office-solutions-development-overview-vsto.md) ve [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md).

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a> VSTO Eklentilerini anlama
 VSTO eklentisi oluşturmak için Visual Studio 'da Office geliştirici araçları 'nı kullandığınızda, bir Microsoft Office uygulaması tarafından yüklenen bir yönetilen kod derlemesi oluşturursunuz. Bütünleştirilmiş kod yüklendikten sonra, VSTO eklentisi uygulamada oluşturulan olaylara yanıt verebilir (örneğin, bir Kullanıcı bir menü öğesini tıkladığında). VSTO eklentisi Ayrıca, uygulamayı otomatikleştirebilmek ve genişletmek için nesne modelini çağırabilir ve içindeki sınıflardan herhangi birini kullanabilir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 Derleme, uygulamanın COM bileşenleriyle uygulamanın birincil birlikte çalışma derlemesi aracılığıyla iletişim kurar. Daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md) ve [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 Bir uygulama için birden çok VSTO eklentisi yüklüyse, her VSTO eklentisi farklı bir uygulama etki alanına yüklenir. Bu, yanlış şekilde davranan bir VSTO eklentisinin diğer VSTO eklentilerinin başarısız olmasına neden olamayacağı anlamına gelir. Ayrıca, uygulama kapatıldığında tüm VSTO eklenti derlemelerinin bellekten bellekten kaldırıldığından emin olmaya de yardımcı olur. Uygulama etki alanları hakkında daha fazla bilgi için bkz. [uygulama etki alanları](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Visual Studio 'da Office geliştirici araçlarını kullanarak oluşturduğunuz VSTO eklentileri yalnızca, ana bilgisayar Microsoft Office uygulaması son kullanıcı tarafından başlatıldığında kullanılmak üzere tasarlanmıştır. Uygulama programlı olarak başlatılırsa (örneğin, Otomasyon kullanılarak), VSTO eklentisi beklendiği gibi çalışmayabilir.

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a> VSTO eklentilerinin bileşenleri
 VSTO eklenti derlemesi ana bileşen olsa da, Microsoft Office uygulamalarının VSTO Eklentilerini bulmasına ve yüklemesine ilişkin önemli bir rol oynayan birçok farklı bileşen vardır.

### <a name="registry-entries"></a>Kayıt defteri girdileri
 Microsoft Office uygulamalar, bir kayıt defteri girişi kümesini arayarak VSTO Eklentilerini bulur. VSTO eklentileri tarafından kullanılan kayıt defteri girdilerinin tam listesi için bkz. [VSTO eklentileri Için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

 Çözümünüzü oluştururken, Visual Studio, VSTO eklentilerinizi hata ayıklamanıza ve çalıştırabilmeniz için geliştirme bilgisayarında gerekli tüm kayıt defteri girişlerini oluşturur. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

 Çözümünüzü dağıtmak için ClickOnce kullanırsanız, yayımlama işlemi tarafından oluşturulan Kurulum programı, son kullanıcı bilgisayarında kayıt defteri anahtarlarını otomatik olarak oluşturur. Daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

### <a name="deployment-manifest-and-application-manifest"></a>Dağıtım bildirimi ve uygulama bildirimi
 VSTO eklentileri, VSTO eklenti derlemesinin en güncel sürümünü tanımlamak ve yüklemek için dağıtım bildirimlerini ve uygulama bildirimlerini kullanır. Dağıtım bildirimi geçerli uygulama bildirimini işaret eder. Uygulama bildirimi, VSTO eklenti derlemesini işaret eder ve derlemede yürütülecek giriş noktası sınıfını belirtir. Daha fazla bilgi için bkz. [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Office çalışma zamanı için Visual Studio Araçları
 Visual Studio 'da Office geliştirici araçları kullanılarak oluşturulan VSTO Eklentilerini çalıştırmak için son kullanıcı bilgisayarlarının yüklü olması gerekir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Çalışma zamanı, yönetilmeyen bileşenleri ve yönetilen derlemelerin bir kümesini içerir. Yönetilmeyen bileşenler VSTO eklenti derlemesini yükler. Yönetilen derlemeler, VSTO eklenti kodunuzun konak uygulamayı otomatikleştirmek ve genişletmek için kullandığı nesne modelini sağlar.

 Daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a> VSTO eklentileri Microsoft Office uygulamalarla nasıl çalışır?
 Bir Kullanıcı bir Microsoft Office uygulaması başlattığında, uygulama, VSTO eklenti derlemesinin en güncel sürümünü bulup yüklemek için dağıtım bildirimini ve uygulama bildirimini kullanır. Aşağıdaki çizimde, bu VSTO eklentilerinin temel mimarisi gösterilmektedir.

 ![2007 Office eklentisi mimarisi](../vsto/media/office07addin.png "2007 Office eklentisi mimarisi")

> [!NOTE]
> Ya da ' i hedefleyen Office çözümlerinde çözüm [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] DERLEMESINE eklenen PIA tür bilgilerini kullanarak doğrudan PIA ' a çağırmak yerine, çözümler ana bilgisayar uygulamasının nesne modeline çağrı yapılır. Daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Yükleme işlemi
 Bir Kullanıcı uygulamayı başlattığında aşağıdaki adımlar oluşur:

1. Uygulama, Visual Studio 'da Office geliştirici araçları kullanılarak oluşturulan VSTO Eklentilerini tanımlayan girişler için kayıt defterini denetler.

2. Uygulama bu kayıt defteri girdilerini bulursa, uygulama VSTOLoader.dll yükleyen VSTOEE.dll yükler. Bunlar, Office çalışma zamanı için Visual Studio 2010 araçları için yükleyici bileşenleri olan yönetilmeyen DLL 'Lerdir. Daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* , [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] ' nin Yönetilen bölümünü yükler ve başlatır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Bildirim güncelleştirmelerini denetler ve en son uygulama ve dağıtım bildirimlerini indirir.

5. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Bir dizi güvenlik denetimi gerçekleştirir. Daha fazla bilgi için bkz. [güvenli Office çözümleri](../vsto/securing-office-solutions.md).

6. VSTO eklentisinin çalışması için güveniliyorsa, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derleme güncelleştirmelerini denetlemek için dağıtım bildirimini ve uygulama bildirimini kullanır. Derlemenin yeni bir sürümü kullanılabiliyorsa, çalışma zamanı derlemenin yeni sürümünü [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] istemci bilgisayardaki önbelleğe indirir. Daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

7. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklenti derlemesinin yükleneceği yeni bir uygulama etki alanı oluşturur.

8. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklenti derlemesini uygulama etki alanına yükler.

9. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> Öğesini geçersiz KıLDıYSANıZ VSTO eklentiinizdeki yöntemi çağırır.

     Bu yöntemi, VSTO eklentiinizdeki bir nesneyi diğer Microsoft Office çözümlerine göstermek için isteğe bağlı olarak geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [VSTO eklentilerindeki kodu diğer Office Çözümlerinden çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

10. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> Öğesini geçersiz KıLDıYSANıZ VSTO eklentiinizdeki yöntemi çağırır.

     İsteğe bağlı olarak, bir genişletilebilirlik arabirimi uygulayan bir nesne döndürerek bir Microsoft Office özelliğini genişletmek için bu yöntemi geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

    > [!NOTE]
    > , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> Ana bilgisayar uygulaması tarafından desteklenen her bir genişletilebilirlik arabirimi için yöntemine ayrı çağrılar yapar. Yönteme yapılan ilk çağrı <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> genellikle yönteme çağrıdan önce gerçekleşse de `ThisAddIn_Startup` , VSTO eklentisi metodun ne zaman <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> çağrılacağını veya kaç kez çağrılacağını hiçbir varsayımda içermemelidir.

11. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] `ThisAddIn_Startup` VSTO eklentiinizdeki yöntemini çağırır. Bu yöntem, olay için varsayılan olay işleyicisidir <xref:Microsoft.Office.Tools.AddInBase.Startup> . Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
