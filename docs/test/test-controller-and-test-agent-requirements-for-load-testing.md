---
title: Test denetleyicisi/test aracısı gereksinimleri (yük testi)
description: Yük testi için test denetleyicisi ve test aracısı gereksinimleri hakkında bilgi edinin. Visual Studio çeşitli test türlerini destekler.
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
ms.openlocfilehash: dfdc7e48c5d2b1c3064192340cf7729c4e9d728563296aeed03b0e9569595450
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424820"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Yük testi için test denetleyicisi ve test aracısı gereksinimleri

Birim, Web performansı, yük ve el ile testler de dahil olmak üzere çeşitli test türleri Visual Studio tümleşiktir. Visual Studio, Visual Studio uygulama yaşam döngüsü yönetimi kullanıcılarının bir test denetleyicisi ve bir veya daha fazla aracı kullanarak uzak bilgisayarlarda testler çalıştırmasına olanak sağlar. Bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Donanım ve yazılım gereksinimleri

Test denetleyicisi ve test aracısı bilgisayarlarının belirli donanım ve yazılım gereksinimleri vardır. Ayrıca, test denetleyicisi ve test aracısı bilgisayarlarını birden çok dilde dağıtmak istiyorsanız, bu dilleri nasıl destekleyecağınızı planlamanız gerekir.

### <a name="hardware-requirements"></a>Donanım gereksinimleri

Aşağıdaki tabloda bir test denetleyicisi ve test aracıları dağıtmak için önerilen donanım gereksinimleri gösterilmektedir.

|**Yapılandırma**|**Bileşen**|**CPU**|**HD**|**Bellek**|
|-|-------------------|-|------------|-|
|< 500 sanal kullanıcıları|Test Aracısı|2,6 GHz|10 GB|2 GB|
|< 1000 sanal kullanıcıları|Test Aracısı|Çift işlemci 2,6 GHz|10 GB|2 GB|
|N x 1000 Sanal Kullanıcı|Test Aracısı|Her biri Iki 2,6 GHz ile N aracıya ölçeklendirin|10 GB|2|
|\< test ortamında 30 bilgisayar. Bu, test edilen aracıları ve sunucuları içerir.|Test denetleyicisi|2,6 GHz|||
|Test ortamında N x 30 bilgisayar. Bu, test edilen aracıları ve sunucuları içerir.|Test denetleyicisi|N 2,6 GHz işlemcileri|||

> [!NOTE]
> Sanal Kullanıcı sayısı testten test 'e göre farklılık gösterir. Bu farkın önemli bir nedeni, *düşünme süreleriyle* veya Kullanıcı gecikmelerinden sapmaktır. Daha fazla bilgi için bkz. [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme zamanlarını düzenleme](../test/edit-think-times-in-load-test-scenarios.md). Bir yük testinde, Web testleri genellikle daha etkilidir ve birim testlerinden daha fazla yük oluşturur. Yukarıdaki tabloda yer alan sayılar, tipik bir Web uygulamasındaki 3-5 saniyelik düşünme süreleriyle Web testlerini çalıştırmak için geçerlidir.

Burada sunulan yönergeler, donanım planlaması için genel kılavuz olarak sunulmaktadır. Test performansı, test verileri miktarına ve test aracılarının sayısına göre büyük ölçüde farklılık gösterir. Test aracıları için, CPU hızı ve kullanılabilir bellek, test yükünü sınırlayacaktır. Test denetleyicilerinin, test aracılarının sayısına ve testlerde yer alan veri miktarına bağlı olarak daha fazla kaynağı olması gerekir.

Visual Studio çalıştıran sunucu, en az 1 Mbps bant genişliğine ve en fazla 350ms gecikme süresine sahip güvenilir bir ağ bağlantısına sahip olmalıdır. Test aracıları ve test denetleyicisi arasında bir güvenlik duvarı olmaması gerekir. Sınama performanslarınız beklentilerinizi karşılamıyorsa, donanım yapılandırmanızı yükseltmeyi düşünün.

### <a name="additional-hardware-considerations"></a>Ek donanım konuları

Test aracıları testin süresine ve test boyutuna bağlı olarak test denetleyicileri üzerinde büyük miktarda veri oluşturur. Genellikle, her 24 saat test verisi için 10 GB 'lık ek sabit disk depolaması planlamanız gerekir.

Burada önerilen donanıma ek olarak, yedekli güç kaynakları ve gereksiz fanlar gibi kritik sunucular için ek donanımlar göz önünde bulundurmanız gerekir.

### <a name="language-requirements"></a>Dil gereksinimleri

Karışıklıkları önlemek ve işlemi basitleştirmek için, bir test denetleyicisi ve test aracısının bilgisayarın işletim sistemiyle aynı dili kullanacak şekilde yapılandırılması gerekir ve bu Team Foundation Server. Test Aracısı ve test denetleyicisi farklı bilgisayarlara yüklenirse, aynı dili kullanacak şekilde yapılandırılması gerekir. ancak, bu dilin Team Foundation Server dağıtımının eşleştiği sürece, ingilizce bir işletim sistemine Visual Studio başka bir dil sürümünü de yükleyebilirsiniz.

## <a name="monitor-agent-resources"></a>Aracı kaynaklarını izleme

Testler sırasında yürütülen ve ölçeklendirilen *QTAgent \*.exe* süreçlerini gözlemleyerek, kaynak ihtiyaçlarını tespit etmek için aracı makinelerini izleyebilirsiniz. *QTAgent \*.exe* işlemlerinde en YAYGıN performans sorunu CPU kullanımdır. CPU kullanımı sürekli olarak yüksek bir şekilde yüksekse, aracının yoğun olarak yüklenmekte olduğunun bir göstergesidir. Sonraki yaygın performans sorunu, bellek kullanımından kaynaklanıyor. Yoğun sınamalar için, bu kaynakları izlemek makineler kaynaklarını artırmanız veya testlerinizi farklı şekilde dağıtmanız gerekip gerekmediğini belirlemenize yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
