---
title: Otomatik sınama için Azure Ardışık Hatlar'ı kullanma
ms.date: 10/19/2018
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd6e9b2d9ea408e451b7032a00c3c96fb0ef2b58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566832"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Otomatik sınama için Laboratuvar Yönetimi yerine Azure Test Planlarını kullanma

Otomatik sınama veya yapı-dağıtma-test otomasyonu için Microsoft Test Yöneticisi ve Laboratuvar Yönetimi'ni kullanıyorsanız, bu konu Azure Ardışık Hatları ve Team Foundation Server (TFS) geliştirme [ve sürüm](/azure/devops/pipelines/index?view=vsts) özelliklerini kullanarak aynı hedeflere nasıl ulaşabileceğinizi açıklar.

## <a name="build-deploy-test-automation"></a>Yap-dağıt-test otomasyonu

Microsoft Test Yöneticisi ve Laboratuvar Yönetimi, uygulamalarınızın oluşturulmasını, dağıtımını ve testini otomatikleştirmek için xaml yapı tanımına güvenir. XAML yapısı, Microsoft Test Yöneticisi'nde oluşturulan laboratuvar ortamı, test paketleri ve test ayarları gibi çeşitli yapılara ve Yapı denetleyicisi, Yapı aracıları, Test denetleyicisi ve Test aracıları gibi çeşitli altyapı bileşenlerine dayanır. bu hedefe ulaşmak. Azure Ardışık Hatları veya TFS'yi kullanarak aynı adımı daha az adımla gerçekleştirebilirsiniz.

| Adımlar | XAML yapısı ile | Bir yapı da veya sürümde |
|-------|----------------------|-----------------|
| Yapıyı dağıtmak ve testleri çalıştırmak için makineleri tanımlayın. | Bu makinelerle Microsoft Test Yöneticisi'nde standart bir laboratuvar ortamı oluşturun. | yok |
| Çalıştırılacak testleri tanımlayın. | Microsoft Test Yöneticisi'nde bir test paketi oluşturun, test örnekleri oluşturun ve otomasyonu her test çalışmasıyla ilişkilendirin. Microsoft Test Yöneticisi'nde, testlerin çalıştırılması gereken laboratuvar ortamındaki makinelerin rolünü tanımlayan test ayarları oluşturun. | Test planlarınızı yönetmeyi planlıyorsanız, Microsoft Test Yöneticisi'nde de aynı şekilde otomatik test paketi oluşturun. Alternatif olarak, testleri doğrudan yapılarınızın ürettiği test ikililerinden çalıştırmak istiyorsanız bunu atlayabilirsiniz. Her iki durumda da test ayarları oluşturmanıza gerek yoktur. |
| Dağıtımı ve testi otomatikleştirin. | LabDefaultTemplate.*.xaml kullanarak bir XAML yapı tanımı oluşturun. Yapı tanımında yapı, test paketleri ve laboratuar ortamını belirtin. | Tek bir ortamla [bir yapı veya sürüm ardışık hattı](/azure/devops/pipelines/index?view=vsts) oluşturun. Komut satırı görevini kullanarak aynı dağıtım komut dosyasını (XAML yapı tanımından) çalıştırın ve Test Aracısı Dağıtımı ve İşlevsel Testler görevlerini çalıştırarak otomatik testler çalıştırın. Bu görevlere giriş olarak makinelerin listesini ve kimlik bilgilerini belirtin. |

Bu senaryo için Azure Ardışık Hatlar veya TFS kullanmanın avantajlarından bazıları şunlardır:

* Yapı denetleyicisi veya Test denetleyicisi gerekmez.
* Test aracısı, yapı veya sürüm parçası olarak bir görev aracılığıyla yüklenir.
* Dağıtım adımlarını özelleştirmek kolaydır. Artık tek bir komut dosyası kullanmak için sınırlı değildir. Ayrıca, visual studio marketplace'in yanı sıra üründe de bulunan birçok görevden yararlanabilirsiniz.
* Test süitlerini korumak zorunda değilsin. İkili testleri doğrudan çalıştırabilirsiniz.
* Her yapı veya sürüm de çalıştırılabilen testler için daha zengin bir satır içi raporlama deneyimi elde elabilirsiniz.
* Hangi varlıkların (sürüm, oluşturma, iş öğeleri, taahhütler) şu anda dağıtılmış ve her ortamda sınanmış olarak izleyebilirsiniz.
* Otomasyonu, birden çok test ortamına ve hatta üretime kolayca dağıtacak şekilde özelleştirebilir ve genişletebilirsiniz.
* Otomasyonu, check-in veya taahhüt olduğunda veya her gün belirli bir saatte gerçekleşmesi için zamanlayabilirsiniz.

## <a name="self-service-management-of-scvmm-environments"></a>SCVMM ortamlarının self servis yönetimi

[Microsoft Test Yöneticisi'ndeki Test Merkezi,](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) bir [SCVMM sunucusu](/system-center/vmm/overview?view=sc-vmm-1801)kullanarak talep üzerine gelen ortam şablonları kitaplığını ve sağlama ortamlarını yönetme yeteneğini destekler.

Lab Center'ın self servis sağlama özelliklerinin iki farklı hedefi vardır:

* Altyapıyı yönetmek için daha basit bir yol sağlayın. VM ve çevre şablonlarını yönetmek ve ortam klonlarını birbirinden izole etmek için otomatik olarak özel ağlar oluşturmak altyapı yönetimine örnekti.

* Ekiplerin test ve dağıtım etkinliklerinde sanal makineleri kullanmaları için daha basit bir yol sağlayın. Aynı proje güvenlik modeli aracılığıyla laboratuvar ortamlarını erişilebilir hale getirmek ve bu sanal makinelerin test senaryolarında tümleşik kullanımı kolay tüketime örnekti.

Ancak, [Microsoft Azure](https://azure.microsoft.com/) ve Microsoft [Azure Yığını](https://azure.microsoft.com/overview/azure-stack/)gibi daha zengin genel ve özel bulut yönetim sistemlerinin evrimi göz önüne alındığında, TFS 2017 ve ötesinde altyapı yönetimi özelliklerinin evrimi yoktur. Bunun yerine, bu tür bulut altyapıları aracılığıyla yönetilen kaynakların kolay tüketimine odaklanmadevam etmektedir.

Aşağıdaki tablo, Lab Center'da gerçekleştirdiğiniz tipik etkinlikleri ve bunları SCVMM veya Azure (altyapı yönetimi etkinlikleriyse) veya TFS ve Azure DevOps Hizmetleri (test veya dağıtım varsa) aracılığıyla nasıl gerçekleştirebileceğinizi özetler. faaliyetleri):

| Adımlar | Laboratuvar Merkezi ile | Bir yapı da veya sürümde |
|-------|-----------------|-----------------------|
| Ortam şablonları kitaplığı yönetin. | Bir laboratuvar ortamı oluşturun. Sanal makinelere gerekli yazılımları yükleyin. Sysprep ve kitaplıkta bir şablon olarak çevre saklayın. | Sanal makine şablonları veya hizmet şablonları oluşturmak ve yönetmek için doğrudan SCVMM yönetim konsolu'nun kullanın. Azure'u kullanırken Azure [hızlı başlatma şablonlarından](https://azure.microsoft.com/resources/templates/)birini seçin. |
| Bir laboratuvar ortamı oluşturun. | Kitaplıkta bir ortam şablonu seçin ve dağıtın. Sanal makine yapılandırmalarını özelleştirmek için gerekli parametreleri sağlayın. | Şablonlardan VM'ler veya hizmet örnekleri oluşturmak için doğrudan SCVMM yönetim konsolu'nun kullanın. Kaynak oluşturmak için doğrudan Azure portalLarını kullanın. Veya, bir ortamla bir sürüm tanımı oluşturun. Yeni sanal makineler oluşturmak için [SCVMM Tümleştirme uzantısındaki](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) Azure görevlerini veya görevlerini kullanın. Bu tanımın yeni bir sürümü oluşturmak, Lab Center'da yeni bir ortam oluşturmaya eşdeğerdir. |
| Makinelere bağlanın. | Ortam görüntüleyicide laboratuvar ortamını açın. | Sanal makinelere bağlanmak için doğrudan SCVMM yönetim konsolu kullanın. Alternatif olarak, uzak masaüstü oturumlarını açmak için sanal makinelerin IP adresini veya DNS adlarını kullanın. |
| Bir ortamın denetim noktasını alın veya ortamı temiz bir denetim noktasına geri yükleyin. | Ortam görüntüleyicide laboratuvar ortamını açın. Bir denetim noktası almak veya önceki bir denetim noktasına geri yüklemek için seçeneğini belirleyin. | Sanal makinelerde bu işlemleri gerçekleştirmek için doğrudan SCVMM yönetim konsolu kullanın. Veya, daha büyük bir otomasyonun parçası olarak bu adımları gerçekleştirmek için, bir sürüm tanımında ortamın bir parçası olarak [SCVMM Tümleştirme uzantısı](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) gelen denetim noktası görevleri içerir. |

## <a name="create-network-isolated-environments"></a>Ağdan yalıtılmış ortamlar oluşturma

Ağ yalıtılmış laboratuvar ortamı, ağ çakışmalarına neden olmadan güvenli bir şekilde klonlanabilen bir grup SCVMM sanal makinesidir. Bu, MTM'de, özel bir ağdaki sanal makineleri yapılandırmak için bir dizi ağ arabirimi kartı ve ortak ağdaki sanal makineleri yapılandırmak için başka bir ağ arabirimi kartı kümesi kullanılarak yapıldı.

Ancak, Azure Ardışık Hatları ve TFS, SCVMM oluşturma ve dağıtma göreviyle birlikte, SCVMM ortamlarını yönetmek, yalıtılmış sanal ağlar sağlamak ve yapı dağıtma-sınama senaryolarını uygulamak için kullanılabilir. Örneğin, görevi aşağıdakileri için kullanabilirsiniz:

* Denetim noktaları oluşturma, geri yükleme ve silme
* Şablon kullanarak yeni sanal makineler oluşturun
* Sanal makineleri başlatma ve durdurma
* SCVMM için özel PowerShell komut dosyaları çalıştırın

Daha fazla bilgi için [bkz.](/azure/devops/pipelines/targets/create-virtual-network?view=vsts)
