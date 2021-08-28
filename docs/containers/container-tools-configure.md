---
title: Visual Studio kapsayıcı araçlarını yapılandırma
description: docker kapsayıcılarıyla çalışmak için Visual Studio bulunan araçları yapılandırın.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-container-tools
ms.openlocfilehash: 91ed17af9900c068af7e81ce3902e68063814d82
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2021
ms.locfileid: "123096925"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Visual Studio kapsayıcı araçlarını yapılandırma

Visual Studio ayarlarını kullanarak, docker kapsayıcılarıyla çalışırken performansı ve kaynak kullanımını etkileyen ayarlar dahil olmak üzere Visual Studio docker kapsayıcılarıyla nasıl çalıştığına ilişkin bazı noktaları kontrol edebilirsiniz.

## <a name="container-tools-settings"></a>Kapsayıcı araçları ayarları

ana menüden **araçlar > seçenekler**' i seçin ve **Ayarlar kapsayıcı araçları**' nı >. Kapsayıcı araçları ayarları görüntülenir.

::: moniker range="vs-2017"

![Visual Studio Kapsayıcı araçları seçenekleri, şunu gösterir: proje yükünde gerekli Docker görüntülerini otomatik olarak çekme, kapsayıcıyı arka planda otomatik olarak Başlat, çözüm kapanındaki kapsayıcıları otomatik olarak sonlandır ve SSL sertifikası için sorma.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Kapsayıcı araçları **genel** ayarları:

![Visual Studio kapsayıcı araçları seçenekleri, şunu gösterir: gerekirse docker Desktop 'ı yükler ve SSL sertifikasına güven ASP.NET Core.](./media/configure-container-tools/tools-options-1.png)

kapsayıcı araçları **tek Project** ve **Docker Compose** ayarları:

![Visual Studio Kapsayıcı araçları seçenekleri, gösterme: proje kapatma üzerinde kapsayıcıları Sonlandır, Project Open 'da gerekli Docker görüntülerini çekin ve proje açıkken kapsayıcıları çalıştırın.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Aşağıdaki tablo, bu seçeneklerin nasıl ayarlanacağına karar vermenize yardımcı olur.

::: moniker range="vs-2017"
| Name | Varsayılan ayar | Uygulanan Öğe | Description |
| -----|:---------------:|:----------:| ----------- |
| Gerekli Docker görüntülerini proje yüküne otomatik olarak çekme | Açık | Docker Compose | projeleri yüklerken daha yüksek performans için Visual Studio arka planda bir docker çekme işlemi başlatacak, böylece kodunuzu çalıştırmaya hazırsanız görüntünün zaten indirilmesi veya indirme sürecinde olması gerekir. Yalnızca projeler ve tarama kodu yüklüyorsanız, gerek duymadığınız kapsayıcı görüntülerini indirmeyi önlemek için bunu kapatabilirsiniz. |
| Kapsayıcıları arka planda otomatik olarak Başlat | Açık | Docker Compose | daha yüksek performans için, Visual Studio kapsayıcınızı oluşturup çalıştırdığınızda, toplu bağlama için hazırlama ile bir kapsayıcı oluşturur. Kapsayıcının ne zaman oluşturulduğunu denetlemek isterseniz, bunu kapatın. |
| Çözüm kapatıldığında kapsayıcıları otomatik olarak Sonlandır | Açık | Docker Compose | Çözümünüze yönelik kapsayıcıların çözümü kapattıktan veya Visual Studio kapattıktan sonra çalışmaya devam etmesini istiyorsanız bunu devre dışı bırakın. |
| Localhost SSL sertifikası için güvenme isteme | Kapalı | ASP.NET Core 2,1 projeleri | localhost SSL sertifikası güvenilir değilse, bu onay kutusu işaretlenmediği takdirde Visual Studio projenizi her çalıştırdığınızda uyarır. |
::: moniker-end

::: moniker range=">=vs-2019"

Aşağıdaki tabloda **genel** ayarları açıklanmaktadır:

| Name | Varsayılan ayar | Uygulanan Öğe | Description |
| -----|:---------------:|:----------:| ----------- |
| Gerekirse Docker Desktop 'ı yükler | Bana sor | tek Project, Docker Compose | Docker Desktop yüklü değilse isteyip istemediğinizi seçin. |
| SSL sertifikası ASP.NET Core güven | Bana sor | ASP.NET Core 2. x projeleri | **bana sor** olarak ayarlandığında, localhost SSL sertifikası güvenilir değilse, projenizi her çalıştırışınızda Visual Studio istenir. |

aşağıdaki tabloda, **tek Project** ve **Docker Compose** ayarları açıklanmaktadır:

| Name | Varsayılan ayar | Uygulanan Öğe | Description |
| -----|:---------------:|:----------:| ----------- |
| Proje açıkken gerekli Docker görüntülerini çekme | Doğru | tek Project, Docker Compose | projeleri yüklerken daha yüksek performans için Visual Studio arka planda bir docker çekme işlemi başlatacak, böylece kodunuzu çalıştırmaya hazırsanız görüntünün zaten indirilmesi veya indirme sürecinde olması gerekir. Yalnızca projeler ve tarama kodu yüklüyorsanız, gerek duymadığınız kapsayıcı görüntülerini indirmemek için **false** olarak ayarlayabilirsiniz. |
| Proje açıkken güncelleştirilmiş Docker görüntülerini çekme | .NET Core projeleri | tek Project, Docker Compose | Bir projeyi açtığınızda, görüntüler için güncelleştirmeleri denetleyin ve varsa indirin. |
| Açık proje üzerinde kapsayıcıları Çalıştır | Doğru | tek Project, Docker Compose | daha yüksek performans için, Visual Studio kapsayıcınızı oluşturup çalıştırdığınızda, daha önce bir kapsayıcı oluşturur. Kapsayıcının ne zaman oluşturulduğunu denetlemek istiyorsanız, **false** olarak ayarlayın. |
| Proje kapatıldığında kapsayıcıları kaldır | Doğru | tek Project, Docker Compose | Çözümünüz kapatıldıktan veya Visual Studio kapatıldıktan sonra çözümünüz için kapsayıcılar bekletilmek istiyorsanız **false** olarak ayarlayın. |

**Kapsayıcılar araç penceresi** ayarları, Docker kapsayıcıları ve görüntüleri hakkında bilgi gösteren **kapsayıcılar** araç penceresi için uygulanan ayarları denetler. Bkz [. kapsayıcılar penceresini kullanma](view-and-diagnose-containers.md)

![Visual Studio Kapsayıcılar araç penceresi için kullanılabilir ayarları gösteren kapsayıcı araçları seçenekleri](media/configure-container-tools/tools-options-3.png)

Aşağıdaki tabloda **kapsayıcılar** penceresi ayarları açıklanmaktadır:


| Name | Varsayılan ayar | Description |
| -----|:---------------:| ----------- |
| Kapsayıcıları Ayıklamadan önce Onayla | Her zaman | Kullanılmayan kapsayıcıları ayıkladığınızda isteyip istemediğinizi denetler. |
| Görüntüleri Ayıklamadan önce Onayla | Her zaman | Kullanılmayan görüntülerin ayıklanması sırasında isteyip istemediğinizi denetler. |
| Kapsayıcıyı kaldırmadan önce Onayla | Her zaman | Bir kapsayıcıyı kaldırırken isteyip istemediğinizi denetler. |
| Görüntüyü kaldırmadan önce Onayla | Her zaman | Bir görüntü kaldırılırken isteyip istemediğinizi denetler. |
| Çok sayıda görüntü çalıştırmadan önce onaylayın | Her zaman | Her seferinde 10 ' dan fazla görüntüden kapsayıcıyı başlatmadan önce isteyip istemediğinizi denetler. |

::: moniker-end
> [!WARNING]
> Localhost SSL sertifikası güvenilir değilse ve sorulmayı önlemek için kutuyu denetederseniz, HTTPS Web istekleri, uygulamanızda veya hizmetinizde çalışma zamanında başarısız olabilir. Bu **durumda, sorma onay kutusunun** işaretini kaldırın, projenizi çalıştırın ve sorulduğunda güveni belirtin.

## <a name="next-steps"></a>Sonraki adımlar

bu [genel bakışta](overview.md)Visual Studio kapsayıcılarla çalışma hakkında daha fazla bilgi edinin.