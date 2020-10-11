---
title: Otomatikleştirilmiş test için Azure Pipelines kullanma
ms.date: 10/19/2018
ms.topic: how-to
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 052e2c794ba765573923fba89413e0192c582c15
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928599"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Otomatikleştirilmiş test için Laboratuvar Yönetimi yerine Azure Test Plans kullanın

Otomatik test veya yapı-dağıtma-test otomasyonu için Microsoft Test Yöneticisi ve Laboratuvar Yönetimi kullanırsanız, bu konuda Azure Pipelines ve Team Foundation Server (TFS) içindeki [derleme ve sürüm](/azure/devops/pipelines/index?view=vsts&preserve-view=true) özelliklerini kullanarak aynı hedeflere nasıl ulaştabileceğiniz açıklanmaktadır.

> [!NOTE]
> Microsoft Test Yöneticisi, Visual Studio 2017 ' de kullanımdan kaldırılmıştır ve Visual Studio 2019 ' de kaldırılır.

## <a name="build-deploy-test-automation"></a>Yapı-dağıtma-test Otomasyonu

Microsoft Test Yöneticisi ve Laboratuvar Yönetimi, uygulamalarınızın derleme, dağıtım ve sınamasını otomatik hale getirmek için bir XAML derleme tanımına bağımlıdır. XAML derlemesi, laboratuvar ortamı, test paketleri ve test ayarları gibi Microsoft Test Yöneticisi oluşturulan çeşitli yapılara ve bu amaca ulaşmak için yapı denetleyicisi, derleme aracıları, test denetleyicisi ve test aracıları gibi çeşitli altyapı bileşenlerinde kullanır. Azure Pipelines veya TFS kullanarak daha az adımla aynısını gerçekleştirebilirsiniz.

| Adımlar | XAML derlemesi ile | Bir derlemede veya yayında |
|-------|----------------------|-----------------|
| Derlemeyi dağıtmak ve testleri çalıştırmak için makineleri belirler. | Bu makinelerle Microsoft Test Yöneticisi bir standart laboratuar ortamı oluşturun. | yok |
| Çalıştırılacak Testleri belirler. | Microsoft Test Yöneticisi bir test paketi oluşturun, test çalışmaları oluşturun ve Otomasyonu her test çalışmasıyla ilişkilendirin. Laboratuvar ortamında testlerin çalıştırılması gereken makinelerin rolünü tanımlayan Microsoft Test Yöneticisi test ayarları oluşturun. | Testinizi test planlarına göre yönetmeyi planlıyorsanız, otomatik test paketini Microsoft Test Yöneticisi aynı şekilde oluşturun. Alternatif olarak, testlerinizi doğrudan Derlemelerinizde üretilen test ikilileriyle çalıştırmak istiyorsanız bunu atlayabilirsiniz. Her iki durumda da test ayarları oluşturmaya gerek yoktur. |
| Dağıtımı ve sınamayı otomatikleştirin. | LabDefaultTemplate. *. XAML kullanarak bir XAML derleme tanımı oluşturun. Yapı tanımında yapı, test paketleri ve laboratuvar ortamını belirtin. | Tek bir ortamla [derleme veya yayın işlem hattı](/azure/devops/pipelines/index?view=vsts&preserve-view=true) oluşturun. Komut satırı görevini kullanarak aynı dağıtım betiğini (XAML derleme tanımından) çalıştırın ve test aracısı dağıtımını kullanarak otomatikleştirilmiş testleri çalıştırın ve Işlevsel testler görevlerini çalıştırın. Makinelerin listesini ve kimlik bilgilerini bu görevlere giriş olarak belirtin. |

Bu senaryo için Azure Pipelines veya TFS kullanmanın avantajlarından bazıları şunlardır:

* Yapı denetleyicisine veya test denetleyicisine ihtiyacınız yoktur.
* Test Aracısı, derleme veya yayın kapsamında bir görev aracılığıyla yüklenir.
* Dağıtım adımlarının özelleştirilmesi kolaydır. Artık tek bir betiği kullanma yetkiniz yok. Ayrıca, üründe bulunan pek çok görevden ve Visual Studio Market de yararlanabilirsiniz.
* Test paketlerini sürdürmek zorunda değilsiniz. Testleri doğrudan ikili dosyalardan çalıştırabilirsiniz.
* Her derleme veya yayın içinde çalıştırılan testler için daha zengin bir satır içi raporlama deneyimi alırsınız.
* Hangi varlıkların (Yayın, derleme, iş öğeleri, işlemeler) Şu anda hangi ortamlarda dağıtıldığını ve test edildiğini izleyebilirsiniz.
* Otomasyonu, birden çok test ortamına kolayca dağıtmak ve hatta üretime dağıtmak için genişletebilirsiniz.
* Otomasyonu, her gün bir iade veya tamamlama yapıldığında veya belirli bir saatte gerçekleşecek şekilde zamanlayabilirsiniz.

## <a name="self-service-management-of-scvmm-environments"></a>SCVMM ortamlarının Self Servis Yönetimi

[Microsoft Test Yöneticisi 'Daki test merkezi](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts&preserve-view=true) , bir dizi ortam şablonu yönetme ve bir [SCVMM sunucusu](/system-center/vmm/overview?view=sc-vmm-1801&preserve-view=true)kullanarak isteğe bağlı ortamlar sağlama yeteneğini destekler.

Laboratuvar Merkezi 'nin Self Servis sağlama özellikleri iki farklı hedefle sahiptir:

* Altyapıyı yönetmenin daha basit bir yolunu sağlayın. VM 'leri ve ortam şablonlarını yönetme ve ortamların klonlarını yalıtmak için özel ağları otomatik olarak oluşturma altyapı yönetimi örnekleri.

* Takımların test ve dağıtım etkinliklerinde sanal makineleri tüketmesi için daha basit bir yol sağlayın. Laboratuvar ortamlarının aynı proje güvenlik modeliyle erişilebilir hale getirilmesi ve test senaryolarında bu sanal makinelerin tümleşik kullanımı, kolay tüketim örneğidir.

Ancak, [Microsoft Azure](https://azure.microsoft.com/) ve [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/)gibi daha zengin ortak ve özel bulut yönetim sistemlerinin EVRIMI verildiğinde, TFS 2017 ve dışındaki altyapı yönetimi özelliklerinin bir gelişimi yoktur. Bunun yerine, bu tür bulut altyapıları aracılığıyla yönetilen kaynakların kolay tüketimine odaklanmaya devam edilir.

Aşağıdaki tabloda, Laboratuvar Merkezi 'nde gerçekleştirdiğiniz tipik etkinlikler ve bunları SCVMM ya da Azure (altyapı yönetimi etkinlikleriniz) veya TFS ve Azure DevOps Services (test veya dağıtım etkinlikleri) aracılığıyla nasıl gerçekleştirebileceğiniz özetlenmektedir.

| Adımlar | Laboratuvar Merkezi ile | Bir derlemede veya yayında |
|-------|-----------------|-----------------------|
| Ortam şablonlarının bir kitaplığını yönetin. | Laboratuvar ortamı oluşturun. Gerekli yazılımları sanal makinelere yükler. Sysprep ve ortamı kitaplıkta şablon olarak depolayın. | Sanal makine şablonlarını veya hizmet şablonlarını oluşturmak ve yönetmek için doğrudan SCVMM Yönetim konsolunu kullanın. Azure 'u kullanırken [Azure hızlı başlangıç şablonlarından](https://azure.microsoft.com/resources/templates/)birini seçin. |
| Laboratuvar ortamı oluşturun. | Kitaplıkta bir ortam şablonu seçin ve dağıtın. Sanal makine yapılandırmasını özelleştirmek için gerekli parametreleri sağlayın. | Şablonlardan VM 'Ler veya hizmet örnekleri oluşturmak için doğrudan SCVMM Yönetim konsolunu kullanın. Kaynakları oluşturmak için doğrudan Azure portal kullanın. Ya da, bir ortamla birlikte bir yayın tanımı oluşturun. Yeni sanal makineler oluşturmak için [SCVMM Tümleştirme Uzantısı](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) ' ndan Azure görevlerini veya görevlerini kullanın. Bu tanımın yeni bir sürümünü oluşturmak, Laboratuvar Merkezi 'nde yeni bir ortam oluşturmaya eşdeğerdir. |
| Makinelere bağlanın. | Ortam Görüntüleyicisinde laboratuvar ortamını açın. | Sanal makinelere bağlanmak için doğrudan SCVMM Yönetim konsolunu kullanın. Alternatif olarak, uzak masaüstü oturumlarını açmak için sanal makinelerin IP adresini veya DNS adlarını kullanın. |
| Bir ortamın denetim noktasını alın veya bir ortamı temiz bir kontrol noktasına geri yükleyin. | Ortam Görüntüleyicisinde laboratuvar ortamını açın. Bir denetim noktası alma veya önceki bir kontrol noktasına geri yükleme seçeneğini belirleyin. | Bu işlemleri sanal makinelerde gerçekleştirmek için doğrudan SCVMM Yönetim konsolunu kullanın. Ya da bu adımları daha büyük bir Otomasyon kapsamında gerçekleştirmek için, bir yayın tanımındaki ortamın bir parçası olarak, [SCVMM tümleştirme uzantısından](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) denetim noktası görevlerini dahil edin. |

## <a name="create-network-isolated-environments"></a>Ağ yalıtımlı ortamlar oluşturma

Ağ yalıtımlı laboratuvar ortamı, ağ çakışmalarına neden olmadan güvenli bir şekilde kopyalanabilen bir SCVMM sanal makine grubudur. Bu, özel bir ağdaki sanal makineleri yapılandırmak için bir dizi ağ arabirim kartı ve bir ortak ağdaki sanal makineleri yapılandırmak için başka bir ağ arabirimi kartı kullanan bir dizi yönerge kullanılarak MTM 'de yapılır.

Ancak, SCVMM derleme ve dağıtma göreviyle birlikte Azure Pipelines ve TFS, SCVMM ortamlarını yönetmek, yalıtılmış sanal ağlar sağlamak ve yapı dağıtma test senaryolarını uygulamak için kullanılabilir. Örneğin, görevi şu şekilde kullanabilirsiniz:

* Denetim noktaları oluşturma, geri yükleme ve silme
* Şablon kullanarak yeni sanal makineler oluşturma
* Sanal makineleri başlatma ve durdurma
* SCVMM için özel PowerShell betikleri çalıştırma

Daha fazla bilgi için bkz. [yapı-dağıtma-test senaryoları için sanal ağ yalıtılmış ortam oluşturma](/azure/devops/pipelines/targets/create-virtual-network?view=vsts&preserve-view=true).
