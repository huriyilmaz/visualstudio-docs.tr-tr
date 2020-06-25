---
title: Visual Studio kapsayıcı araçlarını yapılandırma
description: Visual Studio 'da bulunan araçları Docker kapsayıcılarıyla çalışmak üzere yapılandırın.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: d2b3e2821e7697ad53b10a7148c22140aa1a07af
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283222"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Visual Studio kapsayıcı araçlarını yapılandırma

Visual Studio ayarlarını kullanarak, Docker kapsayıcılarıyla çalışırken performansı ve kaynak kullanımını etkileyen ayarlar dahil olmak üzere Visual Studio 'nun Docker kapsayıcılarıyla nasıl çalıştığı hakkında bazı yönleri denetleyebilirsiniz.

## <a name="container-tools-settings"></a>Kapsayıcı araçları ayarları

Ana menüden **araçlar > seçenekler**' i seçin ve **kapsayıcı araçları > ayarlar**' ı genişletin. Kapsayıcı araçları ayarları görüntülenir.

::: moniker range="vs-2017"

![Visual Studio kapsayıcı araçları seçenekleri, şunu gösterir: proje yükünde gerekli Docker görüntülerini otomatik olarak çekme, kapsayıcıları otomatik olarak arka planda başlatma, çözüm kapanındaki kapsayıcıları otomatik olarak sonlandırma ve SSL sertifikası için istem sorma.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Kapsayıcı araçları **genel** ayarları:

![Visual Studio kapsayıcı araçları seçenekleri, şunu gösterir: gerekirse Docker Desktop 'ı yükler ve SSL sertifikasına güven ASP.NET Core.](./media/configure-container-tools/tools-options-1.png)

Kapsayıcı araçları **tek proje** ve **Docker Compose** ayarları:

![Visual Studio kapsayıcı araçları seçenekleri, gösterme: proje kapatma üzerinde kapsayıcıları Sonlandır, proje açık ' de gerekli Docker görüntülerini çekin ve proje aç üzerinde kapsayıcıları çalıştırın.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Aşağıdaki tablo, bu seçeneklerin nasıl ayarlanacağına karar vermenize yardımcı olur.

::: moniker range="vs-2017"
| Name | Varsayılan ayar | Uygulanan Öğe | Description |
| -----|:---------------:|:----------:| ----------- |
| Gerekli Docker görüntülerini proje yüküne otomatik olarak çekme | Açık | Docker Compose | Projeleri yüklerken daha yüksek performans için, Visual Studio arka planda bir Docker çekme işlemi başlatır, böylece kodunuzu çalıştırmaya hazırsanız görüntü zaten indirilmeye devam eder ve indirme sürecinde olur. Yalnızca projeler ve tarama kodu yüklüyorsanız, gerek duymadığınız kapsayıcı görüntülerini indirmeyi önlemek için bunu kapatabilirsiniz. |
| Kapsayıcıları arka planda otomatik olarak Başlat | Açık | Docker Compose | Daha yüksek performans için, Visual Studio, kapsayıcınızı oluşturup çalıştırdığınızda, toplu takmaya hazırlama ile bir kapsayıcı oluşturur. Kapsayıcının ne zaman oluşturulduğunu denetlemek isterseniz, bunu kapatın. |
| Çözüm kapatıldığında kapsayıcıları otomatik olarak Sonlandır | Açık | Docker Compose | Çözümünüzü kapattıktan veya Visual Studio 'Yu kapattıktan sonra çözümünüz için kapsayıcıların çalışmaya devam etmesini istiyorsanız bunu kapatın. |
| Localhost SSL sertifikası için güvenme isteme | Kapalı | ASP.NET Core 2,1 projeleri | Localhost SSL sertifikası güvenilir değilse, bu onay kutusu işaretlenmediği takdirde, Visual Studio projenizi her çalıştırdığınızda sorar. |
::: moniker-end

::: moniker range=">=vs-2019"

Aşağıdaki tabloda **genel** ayarları açıklanmaktadır:

| Name | Varsayılan ayar | Uygulanan Öğe | Description |
| -----|:---------------:|:----------:| ----------- |
| Gerekirse Docker Desktop 'ı yükler | Bana sor | Tek proje, Docker Compose | Docker Desktop yüklü değilse isteyip istemediğinizi seçin. |
| SSL sertifikası ASP.NET Core güven | Bana sor | ASP.NET Core 2. x projeleri | **Bana sor**olarak ayarlandığında, localhost SSL sertifikası güvenilir değilse, projenizi her çalıştırdığınızda Visual Studio sorar. |

Aşağıdaki tabloda **tek proje** ve **Docker Compose** ayarları açıklanmaktadır:

| Name | Varsayılan ayar | Uygulanan Öğe | Description |
| -----|:---------------:|:----------:| ----------- |
| Proje açıkken gerekli Docker görüntülerini çekme | True | Tek proje, Docker Compose | Projeleri yüklerken daha yüksek performans için, Visual Studio arka planda bir Docker çekme işlemi başlatır, böylece kodunuzu çalıştırmaya hazırsanız görüntü zaten indirilmeye devam eder ve indirme sürecinde olur. Yalnızca projeler ve tarama kodu yüklüyorsanız, gerek duymadığınız kapsayıcı görüntülerini indirmemek için **false** olarak ayarlayabilirsiniz. |
| Açık proje üzerinde kapsayıcıları Çalıştır | True | Tek proje, Docker Compose | Daha yüksek performans için, Visual Studio, kapsayıcınızı oluşturup çalıştırdığınızda, daha önce bir kapsayıcı oluşturur. Kapsayıcının ne zaman oluşturulduğunu denetlemek istiyorsanız, **false**olarak ayarlayın. |
| Proje kapatıldığında kapsayıcıları durdur | True | Tek proje ve Docker Compose | Çözümünüzü kapattıktan veya Visual Studio 'Yu kapattıktan sonra çözümünüz için kapsayıcıların çalışmaya devam etmesini istiyorsanız, **false** olarak ayarlayın. |

::: moniker-end
> [!WARNING]
> Localhost SSL sertifikası güvenilir değilse ve sorulmayı önlemek için kutuyu denetederseniz, HTTPS Web istekleri, uygulamanızda veya hizmetinizde çalışma zamanında başarısız olabilir. Bu **durumda, sorma onay kutusunun** işaretini kaldırın, projenizi çalıştırın ve sorulduğunda güveni belirtin.

## <a name="next-steps"></a>Sonraki adımlar

Bu [genel bakışta](overview.md)Visual Studio 'da kapsayıcılarla çalışma hakkında daha fazla bilgi edinin.