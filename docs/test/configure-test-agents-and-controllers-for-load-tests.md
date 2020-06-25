---
title: Yük testleri için test aracılarını ve test denetleyicilerini yapılandırma
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8fa44ffd75cd64f3ce745524ecdcf6ccb7b9a9b5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288812"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Yük testlerini çalıştırmak için Test aracılarına ve test denetleyicilerine genel bakış

Visual Studio fiziksel veya sanal makineler kullanarak uygulamanız için benzetimli yük oluşturabilir. Bu makinelerin tek bir test denetleyicisi ve bir veya daha fazla test aracısı olarak ayarlanması gerekir. Test denetleyicisini ve test aracılarını, tek bir bilgisayardan yalnızca bir bilgisayarın oluşturabileceğinden daha fazla yük oluşturmak için kullanabilirsiniz.

> [!NOTE]
> Ayrıca, Web sitenize aynı anda erişen birçok kullanıcının yükünü üreten sanal makineler sağlamak için bulut tabanlı yük testi de kullanabilirsiniz. Ancak, bulutta barındırılan sanal makinelerde test denetleyicisi/test Aracısı kurulumu kullanılması desteklenmez. [Azure test Plans kullanarak yük testlerini Çalıştır](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)' da bulut tabanlı yük testi hakkında daha fazla bilgi edinin.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Yük Simülasyon mimarisi

Yük Simülasyon mimarisi, Visual Studio istemcisi, test denetleyicisi ve test aracılarından oluşur.

- İstemci, testlerin geliştirilmesi, testlerin çalıştırılması ve test sonuçlarını görüntülemek için kullanılır.

- Test denetleyicisi test aracılarını yönetmek ve test sonuçlarını toplamak için kullanılır.

- Test aracıları, testleri çalıştırmak için kullanılır ve test ayarında tanımlanan sistem bilgileri ve ASP.NET profil oluşturma verileri dahil olmak üzere verileri toplar.

Bu mimari aşağıdaki avantajları sağlar:

- Test denetleyicisine ek test aracıları ekleyerek yük oluşturmayı ölçeklendirebilme özelliği.

- Aynı veya farklı bilgisayarlara istemci, test denetleyicisi ve test Aracısı yazılımı yükleme esnekliği. Örneğin:

   **Yerel yapılandırma:**

  - Machine1: Visual Studio, denetleyici, aracı.

    ![Denetleyiciyi ve aracıyı kullanan yerel makine](./media/load-test-configa.png)

    **Tipik uzak yapılandırma:**

  - Machine1 ve 2: Visual Studio (aynı denetleyiciyi birden çok Sınayıcılar kullanabilir).

  - Machine3: denetleyici (aracıların yüklü olması de olabilir).

  - Machine4-n: tüm aracı veya aracıları, Machine3 üzerinde denetleyicisiyle ilişkili.

    ![Denetleyiciyi ve aracıları kullanan uzak makineler](./media/load-test-configb.png)

Bir test denetleyicisi genellikle birkaç test aracısını yönetse de bir aracı yalnızca tek bir denetleyiciyle ilişkilendirilebilir. Her test aracısı, bir geliştirici ekibi tarafından paylaşılabilir. Bu mimari, test aracılarının sayısını arttırmayı kolaylaştırır ve bu sayede daha büyük yüklemeler oluşturulmasını kolaylaştırır.

## <a name="test-agent-and-test-controller-interaction"></a>Test Aracısı ve test denetleyicisi etkileşimi

Test denetleyicisi, testleri çalıştırmak için bir test aracıları kümesini yönetir. Test denetleyicisi, testleri başlatmak, testleri durdurmak, test Aracısı durumunu izlemek ve test sonuçlarını toplamak için test aracılarıyla iletişim kurar.

### <a name="test-controller"></a>Test denetleyicisi

Test denetleyicisi, testleri çalıştırmak için genel bir mimari sağlar ve yük testlerini çalıştırmaya yönelik özel özellikler içerir. Test denetleyicisi, yük testini tüm test aracılarına gönderir ve tüm test aracıları testi başlattığını kadar bekler. Tüm test aracıları hazırsa, test denetleyicisi testi başlatmak için Test aracılarına bir ileti gönderir.

### <a name="test-agent"></a>Test Aracısı

Test Aracısı, test denetleyicisinden yeni bir test başlatmak üzere istekleri dinleyen bir hizmet olarak çalışır. Test Aracısı bir istek aldığında, test Aracısı hizmeti testlerin çalıştırılacağı bir işlem başlatır. Her test Aracısı aynı yük testini çalıştırır.

Test aracılarına yönetici tarafından bir ağırlık atanır ve yükleme bir test aracısının ağırlığına göre dağıtılır. Örneğin, test aracısı 1, 30 ağırlığa sahipse ve test Aracısı 2 70 ağırlığa sahipse ve yük 1000 ' e ayarlanmışsa, test aracısı 1, 300 sanal kullanıcılarına benzeirken test Aracısı 2, 700 sanal kullanıcılarına benzetir. Bkz. [Visual Studio ile test denetleyicilerini ve test aracılarını yönetme](../test/manage-test-controllers-and-test-agents.md).

Test Aracısı bir dizi testi ve bir benzetim parametreleri kümesini giriş olarak alır. Önemli bir kavram, testlerin çalıştırıldığı bilgisayardan bağımsızdır.

## <a name="test-controller-and-test-agent-connection-points"></a>Test denetleyicisi ve test Aracısı bağlantı noktaları

Aşağıdaki çizimde, test denetleyicisi, test aracısı ve istemci arasındaki bağlantı noktaları gösterilmektedir. Gelen ve giden bağlantılar için hangi bağlantı noktalarının kullanıldığını ve bu bağlantı noktalarında kullanılan güvenlik kısıtlamalarını özetler.

![Test denetleyicisi ve test Aracısı bağlantı noktaları ve güvenliği](./media/test-controller-agent-firewall.png)

Daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Test denetleyicisi ve aracı yükleme bilgileri

Test denetleyicileri ve test aracıları için donanım ve yazılım gereksinimleri, bunları yükleme yordamları ve ortamınızı en iyi performansa göre yapılandırma hakkında önemli bilgiler için, bkz. [test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Birim testleriyle test denetleyicisini ve test aracısını kullanma

Bir test denetleyicisi ve bir ya da daha fazla aracı yükledikten sonra, yük testleriniz için test ayarında test denetleyicisi ile bir uzaktan yürütme kullanılıp kullanılmayacağını belirtebilirsiniz. Ayrıca, test ayarındaki aracılarla ilişkili rolüyle birlikte kullanılacak veri ve tanılama bağdaştırıcılarını de belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
