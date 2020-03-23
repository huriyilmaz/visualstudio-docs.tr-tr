---
title: Yük Testi için Test Denetleyicisi ve Test Aracısı Gereksinimleri
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39b174b0b134fdfdf26570565aa6aa756ba43c92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588648"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Yük testi için test denetleyicisi ve test aracısı gereksinimleri

Birim, web performansı, yük ve manuel testler dahil olmak üzere çeşitli test türleri Visual Studio'ya entegre edilmiştir. Visual Studio, Visual Studio Application Lifecycle Management kullanıcılarının bir test denetleyicisi ve bir veya daha fazla aracı kullanarak uzak bilgisayarlarda testler çalıştırmasını sağlar. Bkz. [Test aracılarını yükle ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Donanım ve yazılım gereksinimleri

Hem test denetleyicisi hem de test aracısı bilgisayarların belirli donanım ve yazılım gereksinimleri vardır. Ayrıca, test denetleyicisi ve test aracısı bilgisayarlarını birden çok dilde dağıtmak istiyorsanız, bu dilleri nasıl destekleyeceğinizi planlamanız gerekir.

### <a name="hardware-requirements"></a>Donanım gereksinimleri

Aşağıdaki tablo, bir test denetleyicisi ve test aracıları dağıtmak için önerilen donanım gereksinimlerini gösterir.

|**Yapılandırma**|**Bileşen**|**CPU**|**HD**|**Bellek**|
|-|-------------------|-|------------|-|
|500 sanal kullanıcı<|Test aracısı|2.6 GHz|10 GB|2 GB|
|1000 sanal kullanıcı<|Test aracısı|Çift işlemci 2.6 GHz|10 GB|2 GB|
|N x 1000 sanal kullanıcı|Test aracısı|Her biri Çift 2,6 Ghz'li N ajanlarına ölçeklendirin|10 GB|2 GB|
|\<Test ortamında 30 bilgisayar. Bu, test altındaki aracıları ve sunucuları içerir.|Test Denetleyicisi|2.6 GHz|||
|Test ortamında N x 30 bilgisayar. Bu, test altındaki aracıları ve sunucuları içerir.|Test Denetleyicisi|N 2.6 GHz işlemciler|||

> [!NOTE]
> Sanal kullanıcı sayısı testten teste büyük farklılıklar gösterir. Bu varyans önemli bir nedeni *düşünmek kez*varyans veya kullanıcı gecikmeleri. Daha fazla bilgi için, [web sitesi insan etkileşimi gecikmeleri simüle etmek için düşünmek kez edit](../test/edit-think-times-in-load-test-scenarios.md)bakın. Bir yük testinde, web testleri genellikle daha verimlidir ve birim testlerinden daha fazla yük oluşturur. Önceki tablodaki sayılar, tipik bir web uygulamasında 3-5 saniyelik düşünme süreleri ile web testlerini çalıştırmak için geçerlidir.

Burada sunulan yönergeler donanım planlaması için genel kılavuz olarak sağlanmaktadır. Test performansı, test verilerinin miktarına ve test aracılarının sayısına bağlı olarak büyük ölçüde değişir. Test aracıları için, kullanılabilir CPU hızı ve bellek test yükünü sınırlandıracaktır. Test denetleyicileri, test aracılarının sayısına ve testlerde yer alan veri miktarına bağlı olarak daha fazla kaynağa ihtiyaç duyar.

Visual Studio'yu çalıştıran sunucu, en az 1 Mbps bant genişliğine ve en fazla 350 m gecikme ye sahip güvenilir bir ağ bağlantısına sahip olmalıdır. Test aracıları ve test denetleyicisi arasında güvenlik duvarı olmamalıdır. Test performansınız beklentilerinizi karşılamıyorsa, donanım yapılandırmanızı yükseltmeyi düşünün.

### <a name="additional-hardware-considerations"></a>Ek donanım konuları

Test aracıları, testin süresine ve testin boyutuna bağlı olarak test denetleyicilerinde büyük miktarda veri oluşturur. Genellikle, her 24 saatlik test verileri için 10 GB ek bir sabit disk depolama alanı planlamanız gerekir.

Burada önerilen donanıma ek olarak, gereksiz güç kaynakları ve yedek fanlar gibi kritik sunucular için ek donanım ı da göz önünde bulundurmalısınız.

### <a name="language-requirements"></a>Dil gereksinimleri

Karışıklığı önlemek ve işlemi basitleştirmek için, bir test denetleyicisi ve test aracıları bilgisayarın işletim sistemiyle ve Team Foundation Server ile aynı dili kullanacak şekilde yapılandırılmalıdır. Test aracısı ve test denetleyicisi farklı bilgisayarlara yüklenmişse, aynı dili kullanacak şekilde yapılandırılmaları gerekir. Ancak, Visual Studio'nun başka bir dil sürümünü, Bu dil Team Foundation Server dağıtımıyla eşleştirdiği sürece, İngilizce bir işletim sistemine yükleyebilirsiniz.

## <a name="monitor-agent-resources"></a>Aracı kaynaklarını izleme

Testler sırasında yürüten ve ölçeklendiren *QTAgent\*.exe* işlemlerini gözlemleyerek kaynak gereksinimlerini belirlemek için aracı makineleri izleyebilirsiniz. *QTAgent\*.exe* süreçlerinde en sık karşılaşılan darboğaz CPU kullanımıdır. CPU kullanımı sürekli yüksek doksanlı ise o zaman aracı ağır yüklenen bir göstergesidir. Bir sonraki yaygın darboğaz bellek kullanımıdır. Zorlu testler için, bu kaynakları izlemek, makine kaynaklarını artırmanız veya testlerinizi farklı şekilde dağıtmanız gerektirebilip dağıtılamamanız gerektiğini belirlemenize yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
