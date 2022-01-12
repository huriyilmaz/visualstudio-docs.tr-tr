---
title: Devops için laboratuvar ortamı kullanma
description: Laboratuvar ortamları hakkında bilgi edinmek ve Derleme ve Yayın ile Azure Pipelines veya Team Foundation Server kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: how-to
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 68abf47c04e6b311b48c5b4bf58be4bbcbcd9fab
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517690"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Devops'niz için laboratuvar ortamı kullanma

Laboratuvar ortamı, uygulamaları geliştirmek ve test etmek için kullanabileceğiniz sanal ve fiziksel makinelerden bir koleksiyondur. Laboratuvar ortamında iş istasyonları, web sunucuları ve veritabanı sunucuları gibi çok katmanlı uygulamaları test etmek için gereken birden çok rol olabilir. Ayrıca, uygulamanıza otomatikleştirilmiş testler oluşturma, dağıtma ve çalıştırma sürecini otomatikleştirmek için laboratuvar ortamınız ile bir derleme-dağıtım-test iş akışı kullanabilirsiniz.

* **Otomatikleştirilmiş testleri çalıştırmak için test** planı kullanma - Test planı olarak adlandırılan bir otomatikleştirilmiş test koleksiyonu *çalıştırarak* ilerlemeyi görüntüabilirsiniz.

* **Derleme-dağıtma-test iş akışı kullanma** - Çok katmanlı uygulamaları otomatik olarak test etmek için derleme-dağıtma-test iş akışı kullanabilirsiniz. Tipik bir örnek, derleme başlatan, derleme dosyalarını laboratuvar ortamında uygun makinelere dağıtan ve ardından otomatikleştirilmiş testler gerçekleştiren bir iş akışıdır. Ayrıca, iş akışınızı belirli aralıklarla çalıştıracak şekilde zamanlayabilirsiniz.

* **El ile test sırasında bile tüm makinelerden tanılama verileri toplama** - Aynı anda birden çok makineden tanılama verileri toplayabilirsiniz. Örneğin, tek bir test çalıştırması sırasında bir web sunucusundan, veritabanı sunucusundan ve istemciden IntelliTrace, test etkisi ve diğer veri biçimlerini toplayabilirsiniz.

Yaygın laboratuvar ortamı topolojilerinin örnekleri aşağıda verilmiştir:

| Topoloji | Description |
|---|---|
|![Yalnızca sunucu topolojisi](../media/topology_backend.png)| Bu laboratuvar ortamında genellikle sunucu uygulamalarında el ile testler çalıştırmak için kullanılan ve testçilerin ortamdaki hataları doğrulamak için kendi istemci makinelerini kullanmasına olanak sağlayan bir *sunucu topolojisi* vardır. Arka uç topolojisinde, laboratuvar ortamınız yalnızca sunucuları içerir. Bu tür bir topolojiyi kullanırken, genellikle ortamın parçası olan bir istemci makinesi kullanarak laboratuvar ortamındaki sunuculara bağlanabilirsiniz.|
|![Bulut laboratuvarı ortamı](../media/topology_cloud.png)| Bu laboratuvar ortamı, sunucu _topolojisi_ ile benzer özellikler ve özellikler sağlar, ancak yerel bir ortamda çalışan fiziksel veya sanal makineler gereksinimini ortadan kaldırır; , kurulum süresini düşürerek bakımı basitleştirebilir ve maliyeti en aza indirgeyebilirsiniz. Özel ağ ile birlikte birden çok web sitesi ve sanal makine ayarlama, sanal ağ gibi bir bulut ortamında hızlı ve Microsoft Azure.|
|![İstemci-sunucu laboratuvar ortamı](../media/topology_clientserver.png)| Bu laboratuvar ortamında genellikle sunucu ve istemci bileşenleri olan bir uygulamayı test etmek için kullanılan bir *istemci-sunucu topolojisi* vardır. Bir istemci/sunucu topolojisinde, uygulamalarınızı test etmek için kullanılan tüm istemci ve sunucu makineleri laboratuvar ortamınız içindedir. Bu topolojiyi kullanarak testlerinizi etkileyen her makineden test verilerini toplayabilirsiniz.|

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Derleme ve Yayın Azure Pipelines Team Foundation Server bulutu kullanma

Team Foundation Server (TFS) ve Azure Test Plans'daki derleme [](/azure/devops/pipelines/index?view=vsts&preserve-view=true) ve yayın özelliklerini kullanarak otomatik test ve derleme dağıtımı-test Azure Test Plans. Avantajların bazıları:

* Derleme denetleyicisine veya Test denetleyicisine ihtiyacınız yok.
* Test aracısı derlemenin veya sürümün bir parçası olarak bir görev aracılığıyla yüklenir.
* Dağıtım adımlarını özelleştirmek kolaydır. Artık tek bir betik kullanmak için kısıtlanmamış oluruz. Ayrıca üründe ve Market'te bulunan birçok görevden de Visual Studio.
* Test paketlerini sürdürmeye gerek yok. Testleri doğrudan ikililerden çalıştırabilirsiniz.
* Her derleme veya yayında çalıştıran testler için daha zengin bir satır içi raporlama deneyimi elde edin.
* Her ortamda şu anda hangi varlıkların (yayın, derleme, iş öğeleri, işlemeler) dağıtıldı ve test edildiklerini izleyebilirsiniz.
* Otomasyonu özelleştirebilir ve genişletebilir, birden çok test ortamına ve hatta üretim ortamına kolayca dağıtabilirsiniz.
* Her iade veya işleme olduğunda veya her gün belirli bir zamanda gerçekleşecek şekilde otomasyon zamanlayabilir.

Daha fazla bilgi için [bkz. Derleme veya Yayın yönetimini kullanma.](use-build-or-rm-instead-of-lab-management.md)

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Özelliklerin Visual Studio Laboratuvar Yönetimi özelliklerini Microsoft Test Yöneticisi

Visual Studio Enterprise sürümünü kullanarak Visual Studio Laboratuvar Yönetimi'nin Microsoft Test Yöneticisi özellikleriyle laboratuvar Visual Studio Enterprise oluşturabilir ve yönetebilirsiniz.

Laboratuvar Yönetimi ortamınız içinde her makineye test aracılarını otomatik olarak yüklür.

Laboratuvar Yönetimi (SCVMM) System Center Virtual Machine Manager birlikte kullanırsanız, laboratuvar ortamlarını kullanırken de şu avantajlara sahip olursanız:

* **Makine yapılandırmalarını hızla** yeniden oluşturma - Tipik üretim ortamlarını yeniden oluşturmak için yapılandırılmış sanal makine koleksiyonlarını depolayın. Daha sonra her test çalıştırması, depolanan bir ortamın yeni bir kopyası üzerinde gerçekleştirin.

* **Hatanın tam** koşullarını yeniden oluşturma - Test çalıştırması başarısız olduğunda laboratuvar ortamının durumunun bir kopyasını depolayıp derleme sonuçlarınıza veya iş öğesinden erişebilirsiniz.

* **Bir laboratuvar ortamının birden çok** kopyasını aynı anda çalıştırma - Adlandırma çakışmaları olmadan laboratuvar ortamının birden çok kopyasını aynı anda çalıştırabilirsiniz.

### <a name="standard-environments-and-scvmm-environments"></a>Standart Ortamlar ve SCVMM Ortamları

Standart ortamlar ve SCVMM ortamları olmak Visual Studio Laboratuvar Yönetimi **iki** **tür laboratuvar ortamları oluşturabilirsiniz.** Ancak, her ortam türünün özellikleri farklıdır.

**Standart ortamlar:** Sanal ve fiziksel makinelerin bir karışımını içerebilir. Ayrıca, üçüncü taraf sanallaştırma çerçeveleri tarafından yönetilen standart bir ortama sanal makineler eklemek de gerekir. Ayrıca, standart ortamlar SCVMM sunucusu gibi ek sunucu kaynakları gerektirmez.

**SCVMM ortamları:** Yalnızca SCVMM (System Center Virtual Machine Manager) tarafından yönetilen sanal makineler içerebilir, bu nedenle SCVMM ortamlarındaki sanal makineler yalnızca Hyper-V sanallaştırma çerçevesinde çalışır. Ancak SCVMM ortamları, standart ortamlarda mevcut olmayan aşağıdaki otomasyon ve yönetim özelliklerini sağlar:

- **Ortam anlık görüntüleri:** Ortam anlık görüntüleri bir laboratuvar ortamının durumunu içerir, bu nedenle temiz bir ortamı hızla geri yükleyebilir veya değiştirilmiş bir ortamın durumunu kaydedebilirsiniz. Ortam anlık görüntülerini kaydetme ve geri yükleme işlemini otomatikleştirmek için derleme-dağıtma-test iş akışı da kullanabilirsiniz.

- **Depolanan ortamlar:** SCVMM ortamının bir kopyasını depolayıp bu ortamın birden çok kopyasını dağıtabilirsiniz.

- **Ağ yalıtımı:** Ağ yalıtımı, bilgisayar adı çakışması olmadan bir SCVMM ortamının aynı anda birden çok kopyasını çalıştırmaya olanak sağlar.

- **Sanal makine şablonları:** Sanal makine şablonu, adı ve diğer tanımlayıcıları kaldırılmış bir sanal makinedir. SCVMM ortamında bir VM şablonu dağıtıldığında, Microsoft Test Yöneticisi tanımlayıcılar oluşturur. Bu, bir sanal makinenin birden çok kopyasını aynı ortama veya birden çok ortama dağıtmaya ve ardından sanal makineleri aynı anda çalıştırmaya olanak tanır.

- **Depolanan Sanal Makineler:** Proje kitaplığınıza depolanan ve benzersiz tanımlayıcılar içeren bir sanal makine.

> [!NOTE]
> Laboratuvar Yönetimi SCVMM 2016'ya sahip değildir.

SCVMM hakkında bilgi için [bkz. Virtual Machine Manager.](/azure/devops/pipelines/?view=vsts&preserve-view=true)

Standart ortamlar ve SCVMM ortamları aynı özelliklerin çoğunu destekler. Ancak dikkat etmek gereken bazı önemli farklılıklar vardır. Aşağıdaki tabloda standart ortamlar ve SCVMM ortamları için kullanılabilen özellikler karşılaştırmaktadır.

|Özellik|SCVMM Ortamları|Standart Ortamlar|
|-|------------------------|-|
|**Test etme**|||
|El ile test çalıştırma|Desteklenir|Desteklenir|
|Kodlanmış kullanıcı arabirimini ve diğer otomatikleştirilmiş testleri çalıştırma|Desteklenir|Desteklenir|
|Tanılama bağdaştırıcılarını kullanarak zengin hatalar dosyala|Desteklenir|Desteklenir|
|**Derleme dağıtımı**|||
|Otomatik derleme-dağıtma-test iş akışları|Desteklenir|Desteklenir|
|**Ortam oluşturma ve yönetim**|||
|Sanal makinelere ek olarak fiziksel makineleri kullanma|Desteklenmez|Desteklenir|
|Üçüncü taraf sanal makineleri kullanma|Desteklenmez|Desteklenir|
|Test aracılarını laboratuvar ortamındaki makinelere otomatik olarak yükleme|Desteklenir|Desteklenir|
|Ortam anlık görüntülerini kullanarak laboratuvar ortamının durumunu kaydetme ve dağıtma|Desteklenir|Desteklenmez|
|VM şablonlarından laboratuvar ortamları oluşturma|Desteklenir|Desteklenmez|
|Başlat/Durdur/anlık görüntü ortamı|Desteklenir|Desteklenmez|
|ortam görüntüleyicisi 'ni kullanarak ortama Bağlan|Desteklenir|Desteklenir|
|Ağ yalıtımı kullanarak bir ortamın birden çok kopyasını aynı anda çalıştırma|Desteklenir|Desteklenmez|

### <a name="lab-management-concepts"></a>Laboratuvar yönetimi kavramları

Devam etmeden önce bilmeniz gereken bazı ek kavramlar aşağıda verilmiştir:

|Süre|Açıklama|
|-|-----------------|
|Laboratuvar Merkezi|Laboratuvar ortamlarını oluşturduğunuz ve yönettiğiniz Microsoft Test Yöneticisi alanı.|
|Azure DevOps Project laboratuvarı|Kendilerine bağlanıp sanal makinelerini çalıştırabilmeniz için ayarlanmış laboratuvar ortamları koleksiyonu.|
|Azure DevOps Project kitaplığı|Projenizin konak grubuna aktarılmış olan depolanan sanal makineler, şablonlar ve depolanan laboratuvar ortamları arşivi. Kitaplığınızdaki öğeleri SCVMM ortamlarıyla kullanabilirsiniz; Ancak, bunları doğrudan standart bir ortama ekleyemezsiniz. Kitaplığınızdaki öğeleri çalıştıramazsınız; Bunun yerine, bunları yeni bir ortam dağıtmak için kullanırsınız.|
|Dağıtılan ortam|Bu sunucuya bağlanıp makinelerini çalıştırabilmeniz için proje laboratuvarınıza dağıtılan bir laboratuvar ortamı.|

Laboratuvar Yönetimi hakkında daha fazla bilgi için bkz.

* [Laboratuvarınızı planlayın](/previous-versions/ff756575(v=vs.140))
* [Laboratuvarınızı yönetin](/previous-versions/dd936084(v=vs.140))
* [SCVMM ortamları için ayarlama](/previous-versions/dd380687(v=vs.140))
* [İzinleri yönetme](/previous-versions/dd380760(v=vs.140))
* [Değişiklik kurulumu](/previous-versions/ee704508(v=vs.140))
* [Sorun giderme](/previous-versions/ee853230(v=vs.140))

Ortamları ayarlama hakkında daha fazla bilgi için bkz.:

* [Bulut ortamlarını derleme ve yayınlama](use-build-or-rm-instead-of-lab-management.md)
* [Standart laboratuar ortamları](/previous-versions/ee390842(v=vs.140))
* [SCVMM (sanal) ortamları](/previous-versions/ee943322(v=vs.140))
* [Ağ yalıtımlı ortam oluşturma ve kullanma](/previous-versions/ee518924(v=vs.140))
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

* [Test aracılarını yükleme ve yapılandırma](../../test/lab-management/install-configure-test-agents.md)
* [Visual Studio Laboratuvar Yönetimi kılavuzu](/archive/blogs/visualstudioalmrangers/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions)
* [Microsoft DevOps Blogu](https://devblogs.microsoft.com/devops/)