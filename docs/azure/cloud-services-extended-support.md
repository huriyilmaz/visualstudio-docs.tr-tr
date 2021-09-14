---
title: Cloud Services (genişletilmiş destek) kullanma
description: Visual Studio ile Cloud Services kullanarak Cloud Services (genişletilmiş destek) Azure Resource Manager ve dağıtmayı Visual Studio
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 547c3b6e81ad1df0f0beffec54a25ad7c0b32ed7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633249"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio"></a>Visual Studio'de Cloud Services (genişletilmiş destek) oluşturma ve Visual Studio

Visual Studio [2019 sürüm 16.9'dan](https://visualstudio.microsoft.com/vs/)başlayarak, Azure kaynaklarının bakım ve yönetimini büyük ölçüde basitleştiren ve modernleştiren Azure Resource Manager kullanarak bulut hizmetleriyle çalışabilirsiniz. Bu, Cloud Services *(genişletilmiş destek)* olarak adlandırılan yeni bir Azure hizmeti tarafından etkinleştirilir. Mevcut bir bulut hizmetini Cloud Services (genişletilmiş destek) yayımabilirsiniz. Bu Azure hizmeti hakkında daha fazla bilgi için [Cloud Services (genişletilmiş destek) belgelerine bakın.](/azure/cloud-services-extended-support/overview)

## <a name="publish-to-cloud-services-extended-support"></a>Cloud Services'da yayımlama (genişletilmiş destek)

Mevcut Azure Bulut Hizmeti projenizi Cloud Services (genişletilmiş destek) yayımlarsanız, klasik Bir Azure Bulut Hizmeti'ne yayımlama özelliği korunur. 2019 Visual Studio 16.9 ve sonraki sürümlerde, klasik bulut hizmeti projelerinin Yayımla komutu olan Yayımla **(genişletilmiş destek)** özel bir sürümü vardır.  Bu komut, öğesinin kısayol **menüsünde Çözüm Gezgini.**

Cloud Services'da yayımlama (genişletilmiş destek) arasında bazı farklar vardır. Örneğin, bu dağıtım yuvaları genişletilmiş  destek yayımlama modelinin parçası değildir, çünkü Hazırlama veya Üretim'de yayımlarsanız size sorulanmaz. Bunun yerine, Cloud Services (genişletilmiş destek) ile birden çok dağıtım oluşturabilir ve dağıtımları Azure portal. Visual Studio aracı bunu 16.9'da ayarlamaya izin verir ancak değiştirme özelliği Cloud Services'nin (genişletilmiş destek) sonraki bir sürümüne kadar etkinleştirilmez ve Önizleme sırasında dağıtım zamanında hataya neden olabilir.

Klasik bir Azure Cloud Service'i Cloud Services (genişletilmiş destek) yayımlamadan önce projenizin kullandığı depolama hesaplarını kontrol edin ve V1 veya Depolama V2 Depolama emin olun. Klasik depolama hesabı türleri dağıtım zamanında hata iletisiyle başarısız olur. Tanılama tarafından kullanılan depolama hesabını kontrol edin. Tanılama depolama hesabını kontrol etmek için [bkz. Sanal makineler ve sanal makineler için Azure Cloud Services ayarlama.](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) Hizmetiniz klasik bir depolama hesabı kullanıyorsa, bunu yükseltebilirsiniz; Bkz. [Genel amaçlı v2 depolama hesabına yükseltme.](/azure/storage/common/storage-account-upgrade?tabs=azure-portal)  Depolama hesabı türleri hakkında genel bilgi için bkz. [Depolama genel bakış.](/azure/storage/common/storage-account-overview)

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Klasik bir Azure Cloud Service projesini Cloud Services (genişletilmiş destek)

1. Azure Bulut Hizmeti (klasik) projenizin proje düğümüne sağ tıklayın ve Yayımla **(genişletilmiş destek)... öğesini seçin.** Yayımla **sihirbazı** ilk ekranda açılır.

   ![Menüden Yayımla (genişletilmiş destek) öğesini seçin](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   **Yayımla** sihirbazı görüntülenir.

   ![Oturum açma sayfası](./media/cloud-services-extended-support/publish-step1.png)

1. **Hesap** - Hesap seçin veya **hesap açılan listesinde** Hesap ekle'yi seçin.

1. **Aboneliğinizi seçin** - Dağıtımınız için kullanmak istediğiniz aboneliği seçin.

1. Yeni **sayfayı** seçmek için **Ayarlar** seçin.

   ![Ortak Ayarlar](./media/cloud-services-extended-support/publish-settings.png)

1. **Bulut Hizmeti (genişletilmiş destek)** - Açılan listeden mevcut bir bulut hizmetini (genişletilmiş destek) seçin veya Yeni oluştur'ı seçin ve bir tane oluşturun.  Veri merkezi, her bulut hizmeti (genişletilmiş destek) için parantez içinde görüntülenir. Bulut hizmeti için veri merkezi konumunun (genişletilmiş destek) depolama hesabı için veri merkezi konumuyla aynı olması önerilir.

   Yeni bir hizmet oluşturma seçeneğiniz varsa, Bulut Hizmeti **Oluştur (genişletilmiş destek) iletişim kutusunu** görüntülenir. Bulut hizmeti için kullanmak istediğiniz konumu ve kaynak grubunu belirtin (genişletilmiş destek).

   ![Bulut hizmeti oluşturma (genişletilmiş destek)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Derleme yapılandırması** - Hata Ayıkla **veya Yayın'ı** **seçin.**

1. **Hizmet yapılandırması** - Bulut veya **Yerel'i** **seçin.**

1. **Depolama -** Bu dağıtım için kullanmak üzere depolama hesabını seçin veya Yeni **oluştur'a** bakarak bir depolama hesabı oluşturun. Bölge, her depolama hesabı için parantez içinde görüntülenir. Depolama hesabının veri merkezi konumunun, bulut hizmeti için veri merkezi konumuyla aynı olması önerilir (Common Ayarlar).

   Azure depolama hesabı, uygulama dağıtımı için paketi depolar.

1. **Anahtar kasası** - Bu bulut hizmeti için gizli dizileri içeren anahtar kasasını belirtin (genişletilmiş destek). Bu, uzak masaüstü etkinse veya yapılandırmaya sertifikalar ekleniyorsa etkinleştirilir.

1. **Tüm roller için Uzak Masaüstü'nü** etkinleştir - Hizmete uzaktan bağlanabiliyorsanız bu seçeneği belirleyin. Kimlik bilgilerini belirtmeniz istenir.

   ![Uzak masaüstü ayarları](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Tanılama **ayarları** sayfasına taşımak için **Sonraki'yi** seçin.

   ![Tanılama ayarları](./media/cloud-services-extended-support/diagnostics-settings.png)

   Tanılama, bir Azure bulut hizmetiyle (genişletilmiş destek) ilgili sorunları gidermenize olanak sağlar. Tanılama hakkında bilgi için, [bkz. Configuring Diagnostics for Azure Cloud Services and Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Application Analizler hakkında bilgi için [bkz. Application Analizler?](/azure/application-insights/app-insights-overview).

1. Özet **sayfasına** taşımak için **Sonraki'yi** seçin.

   ![Özet](./media/cloud-services-extended-support/publish-summary.png)

1. **Hedef profil** - Seçtiğiniz ayarlardan bir yayımlama profili oluşturabilirsiniz. Örneğin, bir test ortamı için bir profil ve üretim için başka bir profil oluşturabilirsiniz. Bu profili kaydetmek için Kaydet **simgesini** seçin. Sihirbaz, profili oluşturur ve Visual Studio kaydeder. Profil adını değiştirmek için Hedef profil **listesini açın ve** **Yönet... 'i seçin.**

   > [!Note]
   > Yayımlama profili Çözüm Gezgini içinde Visual Studio ve profil ayarları *.azurePubxml* uzantısına sahip bir dosyaya yazılır. Ayarlar XML etiketlerinin öznitelikleri olarak kaydedilir.

1. Projenizin dağıtımı için tüm ayarları yapılandırdıktan sonra iletişim kutusunun **alt kısmında** Yayımla'yı seçin. İşlem durumunu azure etkinlik günlüğü çıkış **penceresinden** izleyebilirsiniz Visual Studio. Portalda **aç bağlantısını** seçin 

Tebrikler! Bulut hizmeti (genişletilmiş destek) projenizi Azure'da yayımladınız. Aynı ayarlarla yeniden yayımlamak için yayımlama profilini yeniden kullanabilir veya bu adımları tekrar kullanarak yeni bir tane oluşturabilirsiniz. Dağıtım Azure Resource Manager (ARM) şablonu ve parametreleri *bin/ \<configuration\> /Publish klasörüne* kaydedilir.

## <a name="clean-up-azure-resources"></a>Azure kaynaklarını temizleme

Bu öğreticiyi kullanarak oluşturduğunuz Azure kaynaklarını temizlemek için [Azure portal'ye](https://portal.azure.com)gidin, Kaynak grupları'ı **seçin,** bulut hizmetini oluşturmak için kullanılan kaynak grubunu bulun ve açın (genişletilmiş destek) ve Kaynak grubunu sil'i **seçin.**

## <a name="next-steps"></a>Sonraki adımlar

Yayımla ekranındaki Yapılandır düğmesini kullanarak **sürekli tümleştirmeyi** (CI) **ayarlayın.** Daha fazla bilgi için [bkz. Azure Pipelines bakın.](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)
