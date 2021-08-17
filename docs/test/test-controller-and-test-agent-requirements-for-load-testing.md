---
title: Test denetleyicisi/test aracısı gereksinimleri (yük testi)
description: Yük testi için test denetleyicisi ve test aracısı gereksinimleri hakkında bilgi edinebilirsiniz. Visual Studio test türlerini destekler.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 158f18a65c83f52dbe2fa846249da2300fad1508
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106633"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Yük testi için test denetleyicisi ve test aracısı gereksinimleri

Birim, web performansı, yük ve el ile yapılan testler gibi çeşitli test türleri, Visual Studio. Visual Studio Uygulama Visual Studio Yönetimi kullanıcılarının bir test denetleyicisi ve bir veya daha fazla aracı kullanarak uzak bilgisayarlarda testleri çalıştırmasını sağlar. Bkz. [Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Donanım ve yazılım gereksinimleri

Hem test denetleyicisi hem de test aracısı bilgisayarları belirli donanım ve yazılım gereksinimlerine sahiptir. Ayrıca, test denetleyicisini ve test aracısı bilgisayarlarını birden çok dile dağıtmak için, bu dilleri nasıl destekleyebilirsiniz planlamanız gerekir.

### <a name="hardware-requirements"></a>Donanım gereksinimleri

Aşağıdaki tabloda, bir test denetleyicisi ve test aracıları dağıtmak için önerilen donanım gereksinimleri gösterir.

|**Yapılandırma**|**Bileşen**|**CPU**|**HD**|**Bellek**|
|-|-------------------|-|------------|-|
|< 500 sanal kullanıcı|Test aracısı|2,6 GHz|10 GB|2 GB|
|< 1000 sanal kullanıcı|Test aracısı|Çift işlemci 2,6 GHz|10 GB|2 GB|
|N x 1000 sanal kullanıcı|Test aracısı|Her biri İkili 2.6 Ghz ile N aracıya ölçeğini ölçeklendirin|10 GB|2 GB|
|\< Test ortamında 30 bilgisayar. Bu, test altındaki aracıları ve sunucuları içerir.|Test Denetleyicisi|2,6 GHz|||
|Test ortamında N x 30 bilgisayar. Bu, test altındaki aracıları ve sunucuları içerir.|Test Denetleyicisi|N 2,6 GHz işlemci|||

> [!NOTE]
> Sanal kullanıcı sayısı testten teste kadar büyük ölçüde farklılık gösterir. Bu varyansın önemli bir nedeni, *düşünme sürelerinin veya kullanıcı* gecikmelerinin varyansıdır. Daha fazla bilgi için [bkz. Web sitesi insan etkileşimi gecikmelerinin benzetimini yapmak için düşünme sürelerini düzenleme.](../test/edit-think-times-in-load-test-scenarios.md) Yük testinde web testleri genellikle daha verimlidir ve birim testlerinden daha fazla yük üretir. Yukarıdaki tabloda yer alan sayılar, tipik bir web uygulamasında 3-5 saniyelik düşünme süreleriyle web testleri çalıştırma için geçerlidir.

Burada sunulan yönergeler, donanım planlaması için genel yönergeler olarak sağlanır. Test performansı, test verisi miktarına ve test aracılarının sayısına göre büyük ölçüde farklılık gösterir. Test aracıları için kullanılabilir CPU hızı ve bellek, test yükünü sınırlar. Test denetleyicilerinin test aracılarının sayısına ve testlere dahil olan veri miktarına bağlı olarak daha fazla kaynak gerekir.

Visual Studio çalıştıran sunucu, en az 1 Mb/sn bant genişliğine ve en fazla 350 m gecikme süresine sahip güvenilir bir ağ bağlantısına sahip olmalıdır. Test aracıları ile test denetleyicisi arasında güvenlik duvarı olması gerekir. Test performansınız beklentilerinizi karşılayamıyorsa donanım yapılandırmanızı yükseltmeyi göz önünde bulundurabilirsiniz.

### <a name="additional-hardware-considerations"></a>Ek donanımla ilgili dikkat edilmesi gerekenler

Test aracıları, testin süresine ve testin boyutuna bağlı olarak test denetleyicilerinde büyük miktarda veri üretir. Genellikle her 24 saatlik test verileri için 10 GB ek sabit disk depolama alanı planlamanız gerekir.

Burada önerilen donanıma ek olarak, yedekli güç kaynakları ve yedekli fanlar gibi kritik sunucular için ek donanımlar da göz önünde bulundurabilirsiniz.

### <a name="language-requirements"></a>Dil gereksinimleri

Karışıklığı önlemek ve işlemi basitleştirmek için, bir test denetleyicisi ve test aracıları bilgisayarın işletim sistemiyle aynı dili ve bu dili kullanmak üzere Team Foundation Server. Test aracısı ve test denetleyicisi farklı bilgisayarlara yüklenmişse, aynı dili kullanmak üzere yapılandırıldıklarına emin olun. Ancak bu dil, dağıtım sırasında Visual Studio dille eş olduğu sürece İngilizce dil işletim sistemine başka bir dil Team Foundation Server yükleyebilirsiniz.

## <a name="monitor-agent-resources"></a>Aracı kaynaklarını izleme

Testler sırasında yürütülen ve ölçeklendirilen *QTAgent \** işlemlerini gözlemleyerek kaynak ihtiyaçlarını.exearacı makinelerini izleyebilirsiniz. *QTAgent \** ve işlemlerde en yaygın.exeCPU kullanımıdır. CPU kullanımı tutarlı olarak doksanlı doksanlı düzeylerde ise, bu, aracının yoğun olarak yükleniyor olduğunu gösteren bir göstergedir. Bir sonraki yaygın performans sorunu bellek kullanımıdır. Zorlu testler için, bu kaynakların izlenmesi makine kaynaklarını artırmanız veya testlerinizi farklı dağıtmanız gerektiğini belirlemenize yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
