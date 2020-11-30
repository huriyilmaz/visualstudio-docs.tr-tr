---
title: DevOps için laboratuvar ortamı kullanma
description: Laboratuvar ortamları ve Azure Pipelines ile bulutu kullanmayı ve Team Foundation Server derleme ve yayınlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: how-to
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: cb25561f70882336a1143918d3cf78849b394065
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328931"
---
# <a name="use-a-lab-environment-for-your-devops"></a>DevOps 'niz için laboratuvar ortamı kullanma

Laboratuvar ortamı, uygulama geliştirmek ve test etmek için kullanabileceğiniz sanal ve fiziksel makinelerin bir koleksiyonudur. Laboratuvar ortamında, iş istasyonları, Web sunucuları ve veritabanı sunucuları gibi çok katmanlı uygulamaları test etmek için gereken birden çok rol bulunabilir. Ayrıca, uygulamanızda otomatikleştirilmiş testler oluşturma, dağıtma ve çalıştırma sürecini otomatik hale getirmek için Laboratuvar ortamınıza sahip bir yapı dağıtımı test iş akışı kullanabilirsiniz.

* **Otomatikleştirilmiş testleri çalıştırmak için bir test planı kullanın** - *test planı* olarak adlandırılan otomatikleştirilmiş testlerin bir koleksiyonunu çalıştırabilir ve ilerleme durumunu görüntüleyebilirsiniz.

* **Yapı-dağıtma-test iş akışı kullanma** -birden çok katmanlı uygulamaları otomatik olarak test etmek için bir yapı dağıtma test iş akışı kullanabilirsiniz. Tipik bir örnek, derleme Başlatan bir iş akışıdır, derleme dosyalarını bir laboratuar ortamında uygun makinelere dağıtır ve ardından otomatikleştirilmiş testleri gerçekleştirir. Ayrıca, iş akışınızı belirli aralıklarda çalışacak şekilde zamanlayabilirsiniz.

* **El ile test sırasında bile tüm makinelerden gelen tanılama verilerini toplayın** . aynı anda birden fazla makineden Tanılama verileri toplayabilirsiniz. Örneğin, tek bir test çalıştırması sırasında IntelliTrace, test etkileri ve diğer veri biçimlerini bir Web sunucusundan, bir veritabanı sunucusundan ve bir istemciden toplayabilirsiniz.

Yaygın laboratuvar ortamı Topolojilerine örnekler aşağıda verilmiştir:

| Topoloji | Açıklama |
|---|---|
|![Yalnızca sunucu topolojisi](../media/topology_backend.png)| Bu laboratuvar ortamında, genellikle sunucu uygulamalarında el ile testleri çalıştırmak için kullanılan ve Test edicilerin ortamdaki hataları doğrulamak için kendi istemci makinelerini kullanmasına izin veren bir *sunucu topolojisi* vardır. Bir arka uç topolojisinde, Laboratuvar ortamınız yalnızca sunucular içerir. Bu tür bir topoloji kullandığınızda, genellikle ortamı parçası olmayan bir istemci makinesini kullanarak Laboratuvar ortamındaki sunuculara bağlanırsınız.|
|![Bulut Laboratuvarı ortamı](../media/topology_cloud.png)| Bu laboratuvar ortamı _sunucu topolojisi_ olarak benzer özellikler ve özellikler sağlar, ancak yerel bir ortamda çalışan fiziksel veya sanal makinelerin gereksinimini ortadan kaldırır; Bu, kurulum süresini azaltabilir, bakımın basitleşebilir ve maliyeti en aza indirir. Özel ağlarla birlikte birden çok Web sitesi ve sanal makine ayarlamak, Microsoft Azure gibi bir bulut ortamında hızlı ve kolaydır.|
|![İstemci-sunucu Laboratuvarı ortamı](../media/topology_clientserver.png)| Bu laboratuvar ortamında, genellikle sunucu ve istemci bileşenlerine sahip bir uygulamayı test etmek için kullanılan bir *istemci-sunucu topolojisi* vardır. Bir istemci/sunucu topolojisinde, uygulamanızı test etmek için kullanılan tüm istemci ve sunucu makineleri Laboratuvar ortamınızda bulunur. Bu topolojiyi kullandığınızda, testlerinizi etkileyen her makineden test verileri toplayabilirsiniz.|

:::row:::
    :::column:::
        ![video için film kamerası simgesi](../../install/media/video-icon.png)
    :::column-end:::
    :::column:::
        Test için laboratuvar ortamlarını yönetme hakkında [bir video izleyin](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) .
    :::column-end:::
:::row-end:::

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Azure Pipelines veya Team Foundation Server derleme ve yayınlama ile bulutu kullanın

Team Foundation Server (TFS) ve Azure Test Plans içindeki [derleme ve sürüm](/azure/devops/pipelines/index?view=vsts&preserve-view=true) özelliklerini kullanarak otomatik test ve yapı-dağıtma-test Otomasyonu yapabilirsiniz. Bazı avantajlar şunlardır:

* Yapı denetleyicisine veya test denetleyicisine ihtiyacınız yoktur.
* Test Aracısı, derleme veya yayın kapsamında bir görev aracılığıyla yüklenir.
* Dağıtım adımlarının özelleştirilmesi kolaydır. Artık tek bir betiği kullanma yetkiniz yok. Ayrıca, üründe bulunan pek çok görevden ve Visual Studio Market de yararlanabilirsiniz.
* Test paketlerini sürdürmek zorunda değilsiniz. Testleri doğrudan ikili dosyalardan çalıştırabilirsiniz.
* Her derleme veya sürümde çalışan testler için daha zengin bir satır içi raporlama deneyimi alırsınız.
* Hangi varlıkların (Yayın, derleme, iş öğeleri, işlemeler) Şu anda hangi ortamlarda dağıtıldığını ve test edildiğini izleyebilirsiniz.
* Otomasyonu, birden çok test ortamına kolayca dağıtmak ve hatta üretime dağıtmak için genişletebilirsiniz.
* Otomasyonu, her gün bir iade veya tamamlama yapıldığında veya belirli bir saatte gerçekleşecek şekilde zamanlayabilirsiniz.

Daha fazla bilgi için bkz. [derleme veya yayın yönetimi kullanma](use-build-or-rm-instead-of-lab-management.md).

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Microsoft Test Yöneticisi Visual Studio Laboratuvar Yönetimi özelliklerini kullanın

Visual Studio Enterprise sürümünü kullanırken Microsoft Test Yöneticisi Visual Studio Laboratuvar Yönetimi özellikleriyle laboratuvar ortamları oluşturabilir ve yönetebilirsiniz.

Laboratuvar Yönetimi ortamınızdaki her makineye test aracıları otomatik olarak yüklenir.

Laboratuvar Yönetimi System Center Virtual Machine Manager (SCVMM) ile birlikte kullanıyorsanız, laboratuvar ortamları kullandığınızda da bu avantajları elde edersiniz:

* **Makine yapılandırmasını hızlı bir şekilde yeniden oluşturma** -tipik üretim ortamları oluşturmak için yapılandırılmış sanal makine koleksiyonlarını saklayabilirsiniz. Ardından, her bir test çalıştırmasını depolanan bir ortamın yeni bir kopyası üzerinde gerçekleştirebilirsiniz.

* **Bir hatanın tam koşullarını yeniden oluşturma** -bir test çalıştırması başarısız olduğunda, laboratuar ortamınızın durumunun bir kopyasını depolayıp derleme sonuçlarınızdan veya bir iş öğesinden erişebilirsiniz.

* **Laboratuvar ortamının birden çok kopyasını aynı anda çalıştırma** -laboratuar ortamınızın birden çok kopyasını, adlandırma çakışmaları olmadan aynı anda çalıştırabilirsiniz.

### <a name="standard-environments-and-scvmm-environments"></a>Standart ortamlar ve SCVMM ortamları

Visual Studio Laboratuvar Yönetimi: **Standart ortamlar** ve **SCVMM ortamları** ile oluşturabileceğiniz iki tür laboratuvar ortamı vardır. Ancak, her bir ortam türünün özellikleri farklıdır.

**Standart ortamlar:** sanal ve fiziksel makinelerin bir karışımını içerebilir. Ayrıca, üçüncü taraf sanallaştırma çerçeveleri tarafından yönetilen standart bir ortama sanal makineler ekleyebilirsiniz. Ayrıca, standart ortamlar bir SCVMM sunucusu gibi ek sunucu kaynakları gerektirmez.

**SCVMM ortamları:** yalnızca SCVMM tarafından yönetilen sanal makineler içerebilir (System Center Virtual Machine Manager), bu nedenle SCVMM ortamlarındaki sanal makineler yalnızca Hyper-V sanallaştırma çerçevesinde çalıştırılabilir. Ancak, SCVMM ortamları standart ortamlarda kullanılamayan aşağıdaki Otomasyon ve yönetim özelliklerini sağlar:

- **Ortam anlık görüntüleri:** Ortam anlık görüntüleri bir laboratuvar ortamının durumunu içerir, böylece temiz bir ortamı hızlıca geri yükleyebilir veya değiştirilmiş bir ortamın durumunu kaydedebilirsiniz. Ayrıca, ortam anlık görüntülerini kaydetme ve geri yükleme işlemini otomatikleştirmek için bir yapı dağıtma test iş akışı da kullanabilirsiniz.

- **Depolanan ortamlar:** Bir SCVMM ortamının bir kopyasını depolayıp daha sonra bu ortamın birden çok kopyasını dağıtabilirsiniz.

- **Ağ yalıtımı:** Ağ yalıtımı, bilgisayar adı çakışması olmadan bir SCVMM ortamının birden fazla özdeş kopyasını aynı anda çalıştırmanızı sağlar.

- **Sanal makine şablonları:** Bir sanal makine şablonu, adı ve diğer tanımlayıcıları kaldırılmış bir sanal makinedir. Bir VM şablonu bir SCVMM ortamında dağıtıldığında, Microsoft Test Yöneticisi yeni tanımlayıcılar oluşturur. Bu, aynı ortamda veya birden çok ortamda bir sanal makinenin birden çok kopyasını dağıtmanızı sağlar ve ardından sanal makineleri eşzamanlı olarak çalıştırabilir.

- **Depolanan sanal makineler:** Proje kitaplığınızda depolanan ve benzersiz tanımlayıcılar içeren bir sanal makine.

> [!NOTE]
> Laboratuvar Yönetimi, SCVMM 2016 ' i desteklemez.

SCVMM hakkında daha fazla bilgi için bkz. [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts&preserve-view=true).

Standart ortamlar ve SCVMM ortamları, aynı özelliklerin birçoğunu destekler. Ancak göz önünde bulundurmanız gereken bazı önemli farklılıklar vardır. Aşağıdaki tabloda, standart ortamlar ve SCVMM ortamları için kullanılabilen özellikler karşılaştırılır.

|Özellik|SCVMM ortamları|Standart ortamlar|
|-|------------------------|-|
|**Test etme**|||
|El ile testleri çalıştırma|Desteklenir|Desteklenir|
|Kodlanmış UI ve diğer otomatikleştirilmiş testleri çalıştırma|Desteklenir|Desteklenir|
|Tanılama bağdaştırıcılarını kullanarak dosya zengin hatalar|Desteklenir|Desteklenir|
|**Derleme dağıtımı**|||
|Otomatik derleme-dağıtma-test iş akışları|Desteklenir|Desteklenir|
|**Ortam oluşturma ve yönetme**|||
|Sanal makinelere ek olarak fiziksel makineleri kullanma|Desteklenmez|Desteklenir|
|Üçüncü taraf sanal makineleri kullanma|Desteklenmez|Desteklenir|
|Laboratuvar ortamındaki makinelere test aracılarını otomatik olarak yükler|Desteklenir|Desteklenir|
|Ortam anlık görüntülerini kullanarak laboratuvar ortamının durumunu kaydetme ve dağıtma|Desteklenir|Desteklenmez|
|VM şablonlarından laboratuvar ortamları oluşturma|Desteklenir|Desteklenmez|
|Başlat/Durdur/anlık görüntü ortamı|Desteklenir|Desteklenmez|
|Ortam Görüntüleyicisi 'ni kullanarak ortama bağlanma|Desteklenir|Desteklenir|
|Ağ yalıtımı kullanarak bir ortamın birden çok kopyasını aynı anda çalıştırma|Desteklenir|Desteklenmez|

### <a name="lab-management-concepts"></a>Laboratuvar yönetimi kavramları

Devam etmeden önce bilmeniz gereken bazı ek kavramlar aşağıda verilmiştir:

|Süre|Açıklama|
|-|-----------------|
|Laboratuvar Merkezi|Laboratuvar ortamlarını oluşturduğunuz ve yönettiğiniz Microsoft Test Yöneticisi alanı.|
|Azure DevOps proje Laboratuvarı|Kendilerine bağlanıp sanal makinelerini çalıştırabilmeniz için ayarlanmış laboratuvar ortamları koleksiyonu.|
|Azure DevOps proje kitaplığı|Projenizin konak grubuna aktarılmış olan depolanan sanal makineler, şablonlar ve depolanan laboratuvar ortamları arşivi. Kitaplığınızdaki öğeleri SCVMM ortamlarıyla kullanabilirsiniz; Ancak, bunları doğrudan standart bir ortama ekleyemezsiniz. Kitaplığınızdaki öğeleri çalıştıramazsınız; Bunun yerine, bunları yeni bir ortam dağıtmak için kullanırsınız.|
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
* [Visual Studio Laboratuvar Yönetimi Kılavuzu](/archive/blogs/visualstudioalmrangers/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions)
* [Microsoft DevOps Blogu](https://devblogs.microsoft.com/devops/)