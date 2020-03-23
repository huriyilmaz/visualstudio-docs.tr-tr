---
title: Yük testleri için test aracılarını ve test denetleyicilerini yapılandırın
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8824e1836d8a49de91cf0e3b9cccf2e85a7de18
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597353"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Yük testleri çalıştırmak için test aracılarına ve test denetleyicilerine genel bakış

Visual Studio, fiziksel veya sanal makineleri kullanarak uygulamanız için simüle edilmiş yük oluşturabilir. Bu makineler tek bir test denetleyicisi ve bir veya daha fazla test aracısı olarak ayarlanmalıdır. Tek bir bilgisayarın tek başına oluşturabileceğinden daha fazla yük oluşturmak için test denetleyicisini ve test aracılarını kullanabilirsiniz.

> [!NOTE]
> Ayrıca, web sitenize aynı anda erişen birçok kullanıcının yükünü oluşturan sanal makineler sağlamak için bulut tabanlı yük testi de kullanabilirsiniz. Ancak, bulut barındırılan sanal makinelerde test denetleyicisi/test aracısı kurulumu desteklenmez. [Azure Test Planlarını kullanarak Çalıştır yükleme testlerinde](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)bulut tabanlı yük testi hakkında daha fazla bilgi edinin.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Yük simülasyon mimarisi

Yük simülasyonu mimarisi Visual Studio istemcisi, test denetleyicisi ve test aracılarından oluşur.

- İstemci testler geliştirmek, testleri çalıştırmak ve test sonuçlarını görüntülemek için kullanılır.

- Test denetleyicisi, test aracılarını yönetmek ve test sonuçlarını toplamak için kullanılır.

- Test aracıları testleri çalıştırmak ve sistem bilgileri ve test ayarında tanımlanan profil oluşturma verilerini ASP.NET dahil olmak üzere veri toplamak için kullanılır.

Bu mimari aşağıdaki yararları sağlar:

- Bir test denetleyicisine ek test aracıları ekleyerek yük oluşturmayı ölçeklendirme yeteneği.

- İstemci, test denetleyicisi ve test aracısı yazılımını aynı veya farklı bilgisayarlara yükleme esnekliği. Örnek:

   **Yerel yapılandırma:**

  - Makine1: Visual Studio, denetleyici, ajan.

    ![Denetleyici ve aracıyı kullanan yerel makine](./media/load-test-configa.png)

    **Tipik uzak yapılandırma:**

  - Machine1 ve 2: Visual Studio (birden çok test eden aynı kumandayı kullanabilir).

  - Machine3: Denetleyici (aracılar da kurulabilir).

  - Machine4-n: Machine3'teki kumandayla ilişkili aracı veya aracılar.

    ![Denetleyici ve aracıları kullanan uzak makineler](./media/load-test-configb.png)

Bir test denetleyicisi genellikle birkaç test aracısı yönetir olsa da, bir aracı yalnızca tek bir denetleyici ile ilişkilendirilebilir. Her test aracısı bir geliştirici ekibi tarafından paylaşılabilir. Bu mimari, test aracılarının sayısını artırmayı kolaylaştırır ve böylece daha büyük yükler oluşturur.

## <a name="test-agent-and-test-controller-interaction"></a>Test aracısı ve test denetleyicisi etkileşimi

Test denetleyicisi testleri çalıştırmak için bir dizi test aracısını yönetir. Test denetleyicisi testleri başlatmak, testleri durdurmak, test aracısı durumunu izlemek ve test sonuçlarını toplamak için test aracıları ile iletişim kurar.

### <a name="test-controller"></a>Test denetleyicisi

Test denetleyicisi testleri çalıştırmak için genel bir mimari sağlar ve yük testleri çalıştırmak için özel özellikler içerir. Test denetleyicisi yük testini tüm test ajanlarına gönderir ve tüm test ajanları testi başlatmayı bekleyene kadar bekler. Tüm test aracıları hazır olduğunda, test denetleyicisi testi başlatmak için test aracılarına bir ileti gönderir.

### <a name="test-agent"></a>Test aracısı

Test aracısı, yeni bir test başlatmak için test denetleyicisinden gelen istekleri dinleyen bir hizmet olarak çalışır. Test aracısı bir istek aldığında, test aracısı hizmeti testleri çalıştırmak için bir işlem başlatır. Her test aracısı aynı yük testini çalıştırZ.

Test aracıları yönetici tarafından bir ağırlık atanır ve yük bir test aracısının ağırlığına göre dağıtılır. Örneğin, test aracısı 1'in ağırlığı 30 ve test aracısı 2'nin ağırlığı 70'e sahipse ve yük 1000 kullanıcıya ayarlanmışsa, test aracısı 1 300 sanal kullanıcıyı simüle ederken test aracısı 2 700 sanal kullanıcıyı simüle eder. [Bkz. Visual Studio ile test denetleyicilerini ve test ajanlarını yönetin.](../test/manage-test-controllers-and-test-agents.md)

Test aracısı giriş olarak bir dizi test ve simülasyon parametreleri kümesi alır. Önemli bir kavram, testlerin çalıştırılabildikleri bilgisayardan bağımsız olmasıdır.

## <a name="test-controller-and-test-agent-connection-points"></a>Test denetleyicisi ve test aracısı bağlantı noktaları

Aşağıdaki resimde test denetleyicisi, test aracısı ve istemci arasındaki bağlantı noktaları gösterilmektedir. Gelen ve giden bağlantılar için hangi bağlantı noktalarının kullanıldığını ve bu bağlantı noktalarında kullanılan güvenlik kısıtlamalarını özetler.

![Test denetleyicisi ve test aracısı bağlantı noktaları ve güvenlik](./media/test-controller-agent-firewall.png)

Daha fazla bilgi için test [denetleyicileri ve test aracıları için yapıbağlantı noktalarını yapıya](../test/configure-ports-for-test-controllers-and-test-agents.md)kınızda.

## <a name="test-controller-and-agent-installation-information"></a>Test denetleyicisi ve aracı yükleme bilgileri

Test denetleyicileri ve test aracıları için donanım ve yazılım gereksinimleri, bunları yükleme prosedürleri ve en iyi performans için ortamınızı yapılandırma hakkında önemli bilgiler için, [test aracılarını yükle ve yapılandırma](../test/lab-management/install-configure-test-agents.md)ya bakın.

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Birim testleri ile test denetleyicisini ve test aracısını kullanın

Bir test denetleyicisi ve bir ya da daha fazla aracı yükledikten sonra, yük testleriniz için test ayarında test denetleyicisi ile bir uzaktan yürütme kullanılıp kullanılmayacağını belirtebilirsiniz. Ayrıca, test ayarındaki aracılarla ilişkili rol ile kullanılacak verileri ve tanıbağlayıcıları belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
