---
title: Yük testleri için test aracılarını/test denetleyicilerini yapılandırma
description: Tek bir Visual Studio daha fazla yük oluşturmak için fiziksel veya sanal makineleri kullanarak sanal yük oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 7c9a85e89e878076302796145c7669e8d5cdd83e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106672"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Yük testlerini çalıştırmaya ilişkin test aracıları ve test denetleyicilerine genel bakış

Visual Studio fiziksel veya sanal makineler kullanarak uygulamanıza yönelik sanal yük oluşturabilirsiniz. Bu makinelerin tek bir test denetleyicisi ve bir veya daha fazla test aracısı olarak ayarlanmış olması gerekir. Tek bir bilgisayarın tek başına oluşturandan daha fazla yük oluşturmak için test denetleyicisini ve test aracılarını kullanabilirsiniz.

> [!NOTE]
> Aynı anda web sitenize erişen çok sayıda kullanıcının yükünü oluşturan sanal makineler sağlamak için bulut tabanlı yük testini de kullanabilirsiniz. Ancak, bulutta barındırılan sanal makinelerde test denetleyicisi/test aracısı kurulumunun kullanımı desteklenmiyor. Bulut tabanlı yük testi hakkında daha fazla bilgi için [Azure Test Plans.](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Yük benzetimi mimarisi

Yük benzetimi mimarisi, Visual Studio, test denetleyicisi ve test aracılarından oluşur.

- İstemci testleri geliştirmek, testleri çalıştırmak ve test sonuçlarını görüntülemek için kullanılır.

- Test denetleyicisi, test aracılarını yönetmek ve test sonuçlarını toplamak için kullanılır.

- Test aracıları testleri çalıştırmak ve sistem bilgileri ve test ayarında tanımlanan profil ASP.NET verileri toplamak için kullanılır.

Bu mimari aşağıdaki avantajları sağlar:

- Bir test denetleyicisine ek test aracıları ekleyerek yük oluşturmanın ölçeğini ölçeklendirebilme.

- İstemci, test denetleyicisi ve test aracısı yazılımını aynı veya farklı bilgisayarlara yükleme esnekliği. Örnek:

   **Yerel yapılandırma:**

  - Machine1: Visual Studio, denetleyici, aracı.

    ![Denetleyici ve aracı kullanan yerel makine](./media/load-test-configa.png)

    **Tipik uzak yapılandırma:**

  - Makine1 ve 2: Visual Studio (birden çok testçi aynı denetleyiciyi kullanabilir).

  - Machine3: Denetleyici (aracılar da yüklü olabilir).

  - Machine4-n: Aracı veya aracıların hepsi Machine3'te denetleyiciyle ilişkilendirildi.

    ![Denetleyici ve aracıları kullanan uzak makineler](./media/load-test-configb.png)

Bir test denetleyicisi genellikle birkaç test aracısını yönetse de, bir aracı yalnızca tek bir denetleyiciyle ilişkilendiril olabilir. Her test aracısı bir geliştirici ekibi tarafından paylaşılır. Bu mimari, test aracılarının sayısını artırmayı ve böylece daha büyük yükler oluşturmayı kolaylaştırır.

## <a name="test-agent-and-test-controller-interaction"></a>Test aracısı ve test denetleyicisi etkileşimi

Test denetleyicisi, testleri çalıştırmak için bir dizi test aracısını yönetir. Test denetleyicisi testleri başlatmak, testleri durdurmak, test aracısı durumunu izlemek ve test sonuçlarını toplamak için test aracıları ile iletişim kurar.

### <a name="test-controller"></a>Test denetleyicisi

Test denetleyicisi testleri çalıştırmaya genel bir mimari sağlar ve yük testlerini çalıştırmaya özel özellikler içerir. Test denetleyicisi yük testini tüm test aracısına gönderir ve tüm test aracıları testi başlatana kadar bekler. Tüm test aracıları hazır olduğunda, test denetleyicisi testi başlatmak için test aracısına bir ileti gönderir.

### <a name="test-agent"></a>Test aracısı

Test aracısı, yeni bir test başlatmak için test denetleyicisinden gelen istekleri dinleyen bir hizmet olarak çalışır. Test aracısı bir istek aldığında, test aracısı hizmeti testleri çalıştırmak için bir işlem başlatır. Her test aracısı aynı yük testini çalıştırır.

Test aracılarının ağırlığı yönetici tarafından atanır ve yük, test aracılarının ağırlığına göre dağıtılır. Örneğin, test aracısı 1'in ağırlığı 30 ise ve test aracısı 2'nin ağırlığı 70 ise ve yük 1000 kullanıcıya ayarlanırsa, test aracısı 1 300 sanal kullanıcının benzetimini, test aracısı 2 ise 700 sanal kullanıcının benzetimini sağlar. Bkz. [Test denetleyicilerini ve test aracılarını Visual Studio.](../test/manage-test-controllers-and-test-agents.md)

Test aracısı giriş olarak bir dizi test ve bir dizi simülasyon parametresi alır. Temel kavramlardan biri, testleri çalıştıracakları bilgisayardan bağımsızdır.

## <a name="test-controller-and-test-agent-connection-points"></a>Test denetleyicisi ve test aracısı bağlantı noktaları

Aşağıdaki çizimde test denetleyicisi, test aracısı ve istemci arasındaki bağlantı noktaları gösterilmiştir. Gelen ve giden bağlantılar için kullanılan bağlantı noktalarının yanı sıra bu bağlantı noktalarında kullanılan güvenlik kısıtlamalarını özetler.

![Test denetleyicisi ve test aracısı bağlantı noktaları ve güvenlik](./media/test-controller-agent-firewall.png)

Daha fazla bilgi için [bkz. Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma.](../test/configure-ports-for-test-controllers-and-test-agents.md)

## <a name="test-controller-and-agent-installation-information"></a>Test denetleyicisi ve aracı yükleme bilgileri

Test denetleyicileri ve test aracıları için donanım ve yazılım gereksinimleri, bunları yükleme yordamları ve ortamınızı en iyi performans için yapılandırma hakkında önemli bilgiler için bkz. Test aracılarını yükleme [ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Birim testleriyle test denetleyicisini ve test aracısını kullanma

Bir test denetleyicisi ve bir ya da daha fazla aracı yükledikten sonra, yük testleriniz için test ayarında test denetleyicisi ile bir uzaktan yürütme kullanılıp kullanılmayacağını belirtebilirsiniz. Ayrıca, test ayarında aracılarla ilişkili rol ile birlikte kullanmak üzere veri ve tanılama bağdaştırıcılarını belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
