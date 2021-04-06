---
title: Cloud Services kullan (genişletilmiş destek)
description: Visual Studio ile Azure Resource Manager kullanarak Cloud Services (genişletilmiş destek) oluşturup dağıtmayı öğrenin
author: ghogen
manager: jmartens
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 289bc88d9aef40fdc260ce84395b1c4b9237c689
ms.sourcegitcommit: 2a50f4c1705baeee5c05580f04e3f468550f44e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106381613"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio"></a>Visual Studio 'da Cloud Services oluşturma ve dağıtma (genişletilmiş destek)

[Visual Studio 2019 sürüm 16,9](https://visualstudio.microsoft.com/vs/)' den Itibaren, Azure kaynaklarının bakımını ve yönetimini büyük ölçüde kolaylaştıran ve destekleyen Azure Resource Manager kullanarak bulut hizmetleriyle çalışabilirsiniz. Bu, *Cloud Services (genişletilmiş destek)* olarak adlandırılan yeni bir Azure hizmeti tarafından etkinleştirilir. Mevcut bir bulut hizmetini Cloud Services (genişletilmiş destek) olarak yayımlayabilirsiniz. Bu Azure hizmeti hakkında daha fazla bilgi için bkz. [Cloud Services (genişletilmiş destek) belgeleri](/azure/cloud-services-extended-support/overview).

## <a name="publish-to-cloud-services-extended-support"></a>Cloud Services yayımlama (genişletilmiş destek)

Mevcut Azure bulut hizmeti projenizi Cloud Services (genişletilmiş destek) ' a yayımladığınızda, klasik bir Azure bulut hizmetine yayımlama özelliğini yine de koruyabilirsiniz. Visual Studio 2019 sürüm 16,9 ve sonrasında, klasik bulut hizmeti projelerinin **Yayımla** komutunun özel bir sürümü **(genişletilmiş destek)** vardır. Bu komut **Çözüm Gezgini** kısayol menüsünde görüntülenir.

Cloud Services (genişletilmiş destek) yayımladığınızda bazı farklılıklar vardır. Örneğin, bu dağıtım yuvaları genişletilmiş destek yayımlama modelinin parçası olmadığından, **hazırlama** veya **üretime** yayımladıysanız sizden sorulmaz. Bunun yerine, Cloud Services (genişletilmiş destek) ile birden çok dağıtım ayarlayabilir ve dağıtım Azure portal. Visual Studio Araçları, 16,9 ' de bu ayarı ayarlamaya izin veriyorsa, değiştirme özelliği Cloud Services (genişletilmiş destek) ' in daha yeni bir sürümüne kadar etkinleştirilmez ve Önizleme sırasında dağıtım zamanında bir hata oluşmasına neden olabilir.

Cloud Services (genişletilmiş destek) için klasik bir Azure bulut hizmetini yayımlamadan önce, projenizin kullandığı depolama hesaplarını denetleyin ve bunların Storage v1 veya Storage v2 hesapları olduklarından emin olun. Klasik depolama hesabı türleri, dağıtım zamanında bir hata iletisiyle başarısız olur. Tanılama tarafından kullanılan depolama hesabını denetlediğinizden emin olun. Tanılama depolama hesabını denetlemek için bkz. [Azure Cloud Services için tanılamayı ayarlama ve sanal makineler](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Hizmetiniz klasik bir depolama hesabı kullanıyorsa, bunu yükseltebilirsiniz; bkz. [genel amaçlı v2 depolama hesabına yükseltme](/azure/storage/common/storage-account-upgrade?tabs=azure-portal).  Depolama hesabı türleri hakkında genel bilgi için bkz. [depolama hesabına genel bakış](/azure/storage/common/storage-account-overview).

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Cloud Services için klasik bir Azure bulut hizmeti projesi yayımlamak için (genişletilmiş destek)

1. Azure bulut hizmeti (klasik) projenizdeki proje düğümüne sağ tıklayın ve Yayımla ' yı **(genişletilmiş destek) seçin...** **Yayımla Sihirbazı** ilk ekranda açılır.

   ![Menüden Yayımla (genişletilmiş destek) öğesini seçin](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   **Yayımla** Sihirbazı görüntülenir.

   ![Oturum açma sayfası](./media/cloud-services-extended-support/publish-step1.png)

1. **Hesap** -hesap açılır listesinden bir hesap seçin veya hesap **Ekle** ' yi seçin.

1. **Aboneliğinizi seçin** -dağıtımınız için kullanılacak aboneliği seçin.

1. **Ayarlar** sayfasına gitmek için **İleri ' yi** seçin.

   ![Ortak ayarlar](./media/cloud-services-extended-support/publish-settings.png)

1. **Bulut hizmeti (genişletilmiş destek)** -açılan menüyü kullanarak var olan bir bulut hizmeti seçin (genişletilmiş destek) veya **Yeni oluştur**' u seçin ve bir tane oluşturun. Veri merkezi her bir bulut hizmeti (genişletilmiş destek) için parantez içinde görüntülenir. Bulut hizmeti için veri merkezi konumunun (genişletilmiş destek) depolama hesabı için veri merkezi konumuyla aynı olması önerilir.

   Yeni bir hizmet oluşturmayı seçerseniz, **bulut hizmeti oluştur (genişletilmiş destek)** iletişim kutusunu görürsünüz. Bulut hizmeti (genişletilmiş destek) için kullanmak istediğiniz konumu ve kaynak grubunu belirtin.

   ![Bulut hizmeti oluşturma (genişletilmiş destek)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Derleme yapılandırması** - **Hata Ayıkla** veya **Yayınla**' yı seçin.

1. **Hizmet yapılandırması** - **bulut** ya da **Yerel**' i seçin.

1. **Depolama hesabı** -bu dağıtım için kullanılacak depolama hesabını seçin veya depolama hesabı oluşturmak Için **Yeni oluştur** ' u seçin. Bölge, her depolama hesabı için parantez içinde görüntülenir. Depolama hesabı için veri merkezi konumunun, bulut hizmeti için veri merkezi konumuyla aynı olması önerilir (ortak ayarlar).

   Azure depolama hesabı, uygulama dağıtımı için paketi depolar.

1. **Anahtar Kasası** -bu bulut hizmeti için gizli dizileri içeren anahtar kasasını belirtin (genişletilmiş destek). Bu, uzak masaüstü etkinleştirilmişse veya yapılandırmaya sertifikalar eklendiyse etkinleştirilir.

1. **Tüm roller Için uzak masaüstünü etkinleştir** -hizmete uzaktan bağlanabiliyor olmanız için bu seçeneği belirleyin. Kimlik bilgilerini belirtmeniz istenecektir.

   ![Uzak Masaüstü ayarları](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. **Tanılama ayarları** sayfasına gitmek için **İleri ' yi** seçin.

   ![Tanılama ayarları](./media/cloud-services-extended-support/diagnostics-settings.png)

   Tanılama, bir Azure bulut hizmetinde (genişletilmiş destek) sorun gidermenize olanak sağlar. Tanılama hakkında daha fazla bilgi için bkz. [Azure Cloud Services ve sanal makineler Için tanılamayı yapılandırma](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Application Insights hakkında daha fazla bilgi için bkz. [Application Insights nedir?](/azure/application-insights/app-insights-overview).

1. **Özet** sayfasına geçmek için **İleri ' yi** seçin.

   ![Özet](./media/cloud-services-extended-support/publish-summary.png)

1. **Hedef profil** -seçtiğiniz ayarlardan bir yayımlama profili oluşturmayı tercih edebilirsiniz. Örneğin, bir test ortamı için bir profil ve bir üretim için başka bir profil oluşturabilirsiniz. Bu profili kaydetmek için **Kaydet** simgesini seçin. Sihirbaz profili oluşturur ve Visual Studio projesine kaydeder. Profil adını değiştirmek için, **hedef profil** listesini açın ve ardından **Yönet...** öğesini seçin.

   > [!Note]
   > Yayımlama profili, Visual Studio 'da Çözüm Gezgini görüntülenir ve profil ayarları *. azurePubxml* uzantılı bir dosyaya yazılır. Ayarlar, XML etiketlerinin öznitelikleri olarak kaydedilir.

1. Projenizin dağıtımı için tüm ayarları yapılandırdıktan sonra, iletişim kutusunun alt kısmında **Yayımla** ' yı seçin. İşlem durumunu Visual Studio 'daki **Azure etkinlik günlüğü** çıkışı penceresinde izleyebilirsiniz. **Portala aç** bağlantısını seçin 

Tebrikler! Bulut hizmeti (genişletilmiş destek) projenizi Azure 'da yayımladınız. Aynı ayarlarla yeniden yayımlamak için, yayımlama profilini yeniden kullanabilir veya yeni bir tane oluşturmak için bu adımları yineleyebilirsiniz. Dağıtım için kullanılan Azure Resource Manager (ARM) şablonu ve parametreleri *bin/ \<configuration\> /Publish* klasörüne kaydedilir.

## <a name="clean-up-azure-resources"></a>Azure kaynaklarını Temizleme

Bu öğreticiyi izleyerek oluşturduğunuz Azure kaynaklarını temizlemek için [Azure Portal](https://portal.azure.com)gidin, **kaynak grupları**' nı seçin, bulut hizmetini oluşturmak için kullandığınız kaynak grubunu bulun ve açın (genişletilmiş destek) ve **kaynak grubunu sil**' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

**Yayımla** ekranında **Yapılandır** düğmesini kullanarak sürekli tümleştirme (CI) ayarlayın. Daha fazla bilgi için bkz. [Azure Pipelines belgeleri](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).
