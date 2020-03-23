---
title: Devops için bir laboratuvar ortamı kullanın
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b02f8bf9542b5de4737d173835c011f59c3fdc86
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75847298"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Devops için bir laboratuvar ortamı kullanın

Laboratuvar ortamı, uygulamaları geliştirmek ve test etmek için kullanabileceğiniz sanal ve fiziksel makinelerin bir koleksiyonudur. Laboratuvar ortamı, iş istasyonları, web sunucuları ve veritabanı sunucuları gibi çok katmanlı uygulamaları sınamak için gereken birden çok rol içerebilir. Ayrıca, uygulamanızda otomatik testler oluşturma, dağıtma ve çalıştırma işlemini otomatikleştirmek için laboratuvar ortamınızla birlikte bir yapı dağıtma-test iş akışı kullanabilirsiniz.

* **Otomatik testleri çalıştırmak için bir test planı kullanın** - Test *planı*adı verilen bir otomatik test koleksiyonu çalıştırabilir ve ilerlemeyi görüntüleyebilirsiniz.

* **Yapı dağıtma testi iş akışı kullanın** - Çok katmanlı uygulamaları otomatik olarak test etmek için yapı dağıtma testi iş akışını kullanabilirsiniz. Tipik bir örnek, yapıyı başlatan, yapı dosyalarını laboratuvar ortamındaki ilgili makinelere dağıtan ve ardından otomatik testler gerçekleştiren bir iş akışıdır. Ayrıca, iş akışınızı belirli aralıklarla çalışacak şekilde zamanlayabilirsiniz.

* **El ile test sırasında bile tüm makinelerden tanılama verileri toplayın** - Aynı anda birden fazla makineden tanılama verileri toplayabilirsiniz. Örneğin, tek bir test çalışması sırasında, bir web sunucusundan, veritabanı sunucusundan ve istemciden IntelliTrace, test etkisi ve diğer veri formlarını toplayabilirsiniz.

Burada ortak laboratuvar ortamı topolojileri örnekleri şunlardır:

| Topoloji | Açıklama |
|---|---|
|![Sunucu sadece topoloji](../media/topology_backend.png)| Bu laboratuvar ortamında, genellikle sunucu uygulamalarında el ile testler yapmak için kullanılan ve test edenlerin çevredeki hataları doğrulamak için kendi istemci makinelerini kullanmalarına olanak tanıyan bir *sunucu topolojisi*vardır. Arka uç topolojisinde, laboratuar ortamınız yalnızca sunucular içerir. Bu tür topoloji kullandığınızda, genellikle ortamın parçası olmayan bir istemci makinesini kullanarak laboratuar ortamındaki sunuculara bağlanırsınız.|
|![Bulut laboratuarı ortamı](../media/topology_cloud.png)| Bu laboratuvar ortamı _sunucu topolojisi_gibi benzer özellikler ve özellikler sağlar, ancak yerel bir ortamda çalışan fiziksel veya sanal makineler için gereksinimi kaldırır; kurulum süresini azaltabilir, bakımı basitleştirebilir ve maliyeti en aza indirebilir. Microsoft Azure gibi bir bulut ortamında, özel ağla birlikte birden çok web sitesi ve sanal makine kurmak hızlı ve kolaydır.|
|![İstemci-sunucu laboratuar ortamı](../media/topology_clientserver.png)| Bu laboratuvar ortamında genellikle sunucu ve istemci bileşenleri olan bir uygulamayı sınamak için kullanılan bir *istemci-sunucu topolojisi*vardır. İstemci/sunucu topolojisinde, uygulamanızı test etmek için kullanılan tüm istemci ve sunucu makineleri laboratuar ortamınızdadır. Bu topolojiyi kullandığınızda, testlerinizi etkileyen her makineden test verileri toplayabilirsiniz.|

| | |
|---|---|
| ![video için film kamera simgesi](../../install/media/video-icon.png) | Test için laboratuvar ortamlarını yönetme yle ilgili [bir video izleyin.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Bulutu Azure Pipelines veya Team Foundation Server Build and Release ile kullanma

Team Foundation Server (TFS) ve Azure Test Planları'ndaki [yapı ve sürüm](/azure/devops/pipelines/index?view=vsts) özelliklerini kullanarak otomatik sınama ve geliştirme-dağıtma-test otomasyonu gerçekleştirebilirsiniz. Bazı faydaları şunlardır:

* Yapı denetleyicisi veya Test denetleyicisi gerekmez.
* Test aracısı, yapı veya sürüm parçası olarak bir görev aracılığıyla yüklenir.
* Dağıtım adımlarını özelleştirmek kolaydır. Artık tek bir komut dosyası kullanmak için sınırlı değildir. Ayrıca, visual studio marketplace'in yanı sıra üründe de bulunan birçok görevden yararlanabilirsiniz.
* Test süitlerini korumak zorunda değilsin. İkili testleri doğrudan çalıştırabilirsiniz.
* Her yapı veya sürüm de çalışan testler için daha zengin bir satır içi raporlama deneyimi elde elabilirsiniz.
* Hangi varlıkların (sürüm, oluşturma, iş öğeleri, taahhütler) şu anda dağıtılmış ve her ortamda sınanmış olarak izleyebilirsiniz.
* Otomasyonu, birden çok test ortamına ve hatta üretime kolayca dağıtacak şekilde özelleştirebilir ve genişletebilirsiniz.
* Otomasyonu, check-in veya taahhüt olduğunda veya her gün belirli bir saatte gerçekleşmesi için zamanlayabilirsiniz.

Daha fazla bilgi için Yapı [kullan veya yayın yönetimini kullan'a](use-build-or-rm-instead-of-lab-management.md)bakın.

## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Microsoft Test Yöneticisi'nin Visual Studio Lab Management özelliklerini kullanma

Visual Studio Enterprise sürümünü kullandığınızda Microsoft Test Yöneticisi'nin Visual Studio Lab Management özellikleriyle laboratuvar ortamları oluşturabilir ve yönetebilirsiniz.

Laboratuvar Yönetimi, ortamınızdaki her makineye test aracılarını otomatik olarak yükler.

Sistem Merkezi Sanal Makine Yöneticisi (SCVMM) ile birlikte Laboratuvar Yönetimi kullanıyorsanız, laboratuvar ortamlarını kullandığınızda da şu avantajlardan yararlanırsınız:

* **Makine yapılandırmalarını hızla yeniden üretin** - Tipik üretim ortamlarını yeniden oluşturmak üzere yapılandırılan sanal makine koleksiyonlarını depolayabilirsiniz. Daha sonra, depolanan ortamın yeni bir kopyasıüzerinde her test çalışmasını gerçekleştirebilirsiniz.

* **Hatanın tam koşullarını yeniden üretin** - Bir test çalışması başarısız olduğunda, laboratuvar ortamınızın durumunun bir kopyasını depolayabilir ve yapı sonuçlarınızdan veya iş öğenizden erişebilirsiniz.

* **Bir laboratuar ortamının birden çok kopyasını aynı anda çalıştırın** - Çakışmaları adlandırmadan aynı anda birden çok kopyayı çalıştırabilirsiniz.

### <a name="standard-environments-and-scvmm-environments"></a>Standart Ortamlar ve SCVMM Ortamları

Visual Studio Lab Management ile oluşturabileceğiniz iki tür laboratuvar ortamı vardır: **standart ortamlar** ve **SCVMM ortamları.** Ancak, her ortam türünün yetenekleri farklıdır.

**Standart ortamlar:** sanal ve fiziksel makinelerin bir karışımını içerebilir. Ayrıca, üçüncü taraf sanallaştırma çerçeveleri tarafından yönetilen standart bir ortama sanal makineler ekleyebilirsiniz. Buna ek olarak, standart ortamlar SCVMM sunucusu gibi ek sunucu kaynakları gerektirmez.

**SCVMM ortamları:** yalnızca SCVMM (System Center Virtual Machine Manager) tarafından yönetilen sanal makineler içerebilir, böylece SCVMM ortamlarında sanal makineler yalnızca Hyper-V sanallaştırma çerçevesinde çalıştırılabilir. Ancak, SCVMM ortamları standart ortamlarda bulunmayan aşağıdaki otomasyon ve yönetim özelliklerini sağlar:

- **Ortam anlık görüntüleri:** Ortam anlık görüntüleri, temiz bir ortamı hızla geri yükleyebilmeniz veya değiştirilen ortamın durumunu kaydedebilirsiniz. Ayrıca, ortam anlık görüntülerini kaydetme ve geri verme işlemini otomatikleştirmek için bir yapı dağıtma-sınt-test iş akışı da kullanabilirsiniz.

- **Depolanan ortamlar:** Bir SCVMM ortamının kopyasını depolayabilir ve sonra bu ortamın birden çok kopyasını dağıtabilirsiniz.

- **Ağ yalıtımı:** Ağ yalıtımı, bilgisayar adı çakışmaları olmadan bir SCVMM ortamının birden çok aynı kopyasını aynı anda çalıştırmanızı sağlar.

- **Sanal makine şablonları:** Sanal makine şablonu, adını ve diğer tanımlayıcıları kaldırılmış olan sanal bir makinedir. Bir VM şablonu Bir SCVMM ortamında dağıtıldığında, Microsoft Test Yöneticisi yeni tanımlayıcılar oluşturur. Bu, sanal bir makinenin birden çok kopyasını aynı ortamda veya birden çok ortamda dağıtmanıza ve sanal makineleri aynı anda çalıştırmanıza olanak tanır.

- **Saklanan Sanal Makineler:** Proje kitaplığınızda depolanan ve benzersiz tanımlayıcılar içeren sanal bir makine.

> [!NOTE]
> Laboratuvar Yönetimi SCVMM 2016'yı desteklemez.

SCVMM hakkında daha fazla bilgi için [Virtual Machine Manager'a](/azure/devops/pipelines/?view=vsts)bakın.

Standart ortamlar ve SCVMM ortamları aynı özelliklerin çoğunu destekler. Ancak, göz önünde bulundurulması gereken bazı önemli farklılıklar vardır. Aşağıdaki tablo, standart ortamlar ve SCVMM ortamları için kullanılabilen özellikleri karşılaştırmaktadır.

|Özellik|SCVMM Ortamları|Standart Ortamlar|
|-|------------------------|-|
|**Sınama**|||
|El ile testler çalıştırın|Destekleniyor|Destekleniyor|
|Kodlanmış UI ve diğer otomatik testleri çalıştırma|Destekleniyor|Destekleniyor|
|Tanılama bağdaştırıcılarını kullanarak zengin hataları dosyala|Destekleniyor|Destekleniyor|
|**Dağıtım oluşturma**|||
|Otomatik yapı dağıtma-test iş akışları|Destekleniyor|Destekleniyor|
|**Çevre oluşturma ve yönetimi**|||
|Sanal makinelere ek olarak fiziksel makineler kullanın|Desteklenmiyor|Destekleniyor|
|Üçüncü taraf sanal makineleri kullanma|Desteklenmiyor|Destekleniyor|
|Test ajanlarını laboratuvar ortamındaki makinelere otomatik olarak töşen|Destekleniyor|Destekleniyor|
|Ortam anlık görüntülerini kullanarak laboratuvar ortamının durumunu kaydetme ve dağıtma|Destekleniyor|Desteklenmiyor|
|VM şablonlarından laboratuvar ortamları oluşturma|Destekleniyor|Desteklenmiyor|
|Başlat/durdur/anlık görüntü ortamı|Destekleniyor|Desteklenmiyor|
|Çevre Görüntüleyici'yi kullanarak ortama bağlanma|Destekleniyor|Destekleniyor|
|Ağ yalıtımını kullanarak aynı anda ortamın birden çok kopyasını çalıştırma|Destekleniyor|Desteklenmiyor|

### <a name="lab-management-concepts"></a>Laboratuvar yönetimi kavramları

Devam etmeden önce aşina olmanızı gereken bazı ek kavramlar şunlardır:

|Sözleşme Dönemi|Açıklama|
|-|-----------------|
|Laboratuvar Merkezi|Microsoft Test Yöneticisi'nin laboratuvar ortamlarını oluşturduğunuz ve yönettiğiniz alanı.|
|Azure Devops Proje Laboratuvarı|Onlara bağlanabilmeniz ve sanal makinelerini çalıştırabilmeniz için ayarlanmış laboratuvar ortamları koleksiyonu.|
|Azure Devops Proje Kütüphanesi|Projenizin ana bilgisayar grubuna aktarılan depolanmış sanal makinelerin, şablonların ve depolanmış laboratuvar ortamlarının arşivi. Kitaplığınızdaki öğeleri SCVMM ortamları ile kullanabilirsiniz; ancak, bunları doğrudan standart bir ortama ekemezsiniz. Kitaplığınızdaki öğeleri çalıştıramazsınız; bunun yerine bunları yeni bir ortam dağıtmak için kullanırsınız.|
|Dağıtılan Ortam|Proje laboratuarınıza dağıtılan bir laboratuvar ortamı, böylece ona bağlanabilmeniz ve makinelerini çalıştırabilmeniz için.|

Laboratuvar yönetimi hakkında daha fazla bilgi için bkz:

* [Laboratuvarınızı planlayın](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Laboratuvarınızı yönetin](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [SCVMM ortamları için ayarlama](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [İzinleri yönetme](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Kurulumu değiştir](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Sorun giderme](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Ortamlar ayarlama hakkında bilgi için bkz:

* [Bulut ortamları oluşturma ve serbest bırakma](use-build-or-rm-instead-of-lab-management.md)
* [Standart laboratuvar ortamları](https://msdn.microsoft.com/library/ee390842.aspx)
* [SCVMM (sanal) ortamları](https://msdn.microsoft.com/library/ee943322.aspx)
* [Ağ yalıtılmış ortam oluşturma ve kullanma](https://msdn.microsoft.com/library/ee518924.aspx)

## <a name="see-also"></a>Ayrıca bkz.

* [Test aracılarını yükleme ve yapılandırma](../../test/lab-management/install-configure-test-agents.md)
* [Visual Studio Lab Yönetim Rehberi](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2015/04/22/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions/)
* [Microsoft DevOps Blogu](https://devblogs.microsoft.com/devops/)
