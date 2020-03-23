---
title: Visual Studio Konteyner Araçlarını Yapılandır
description: Docker konteynerleriyle çalışmak için Visual Studio'da bulunan araçları yapılandırın.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188778"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Visual Studio Konteyner Araçları nasıl yapılandırılır?

Visual Studio ayarlarını kullanarak, Visual Studio'nun Docker kapsayıcılarıyla nasıl çalıştığını, Docker kapsayıcılarıyla çalışırken performansı ve kaynak kullanımını etkileyen ayarlar da dahil olmak üzere bazı yönlerini denetleyebilirsiniz.

## <a name="container-tools-settings"></a>Konteyner Araçları ayarları

Ana menüden **Araçlar > Seçenekleri'ni**seçin ve Kapsayıcı Araçları **> Ayarları'nı**genişletin. Kapsayıcı araçları ayarları görüntülenir.

::: moniker range="vs-2017"

![Visual Studio Konteyner Araçları seçenekleri: Proje yükünde gerekli Docker görüntülerini otomatik olarak çekin, arka planda kapları otomatik olarak başlatın, çözüm kapanışında kapları otomatik olarak öldürün ve SSL sertifikasına güvenmek için istekte bulunmayın.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Konteyner Araçları **Genel** ayarları:

![Visual Studio Container Tools seçenekleri: Gerekirse Docker Desktop'ı yükleyin ve Core SSL sertifikasına ASP.NET güvenin.](./media/configure-container-tools/tools-options-1.png)

Konteyner Araçları **Tek Proje** ve **Docker Oluşturma** ayarları:

![Visual Studio Konteyner Araçları seçenekleri, gösteren: Proje kapanışında kapları öldürün, proje açıkken gerekli Docker görüntülerini çekin ve proje açıkken kapsayıcıları çalıştırın.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Aşağıdaki tablo, bu seçenekleri nasıl ayarlayacağınınıza karar vermenize yardımcı olabilir.

::: moniker range="vs-2017"
| Adı | Varsayılan Ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Proje yükünde gerekli Docker görüntülerini otomatik olarak çekin | Açık | Docker Oluştur | Proje yüklerken daha yüksek performans için Visual Studio arka planda docker çekme işlemine başlar, böylece kodunuzu çalıştırmaya hazır olduğunuzda görüntü zaten indirilir veya indirme işleminde olur. Projeleri ve gözatma kodunu yüklüyorsanız, ihtiyacınız olmayan kapsayıcı görüntülerini indirmemek için bunu kapatabilirsiniz. |
| Arka planda kapsayıcıları otomatik olarak başlatın | Açık | Docker Oluştur | Yine artan performans için Visual Studio, kapsayıcınızı inşa edip çalıştırdığınızda ses montajlarına hazır bir kapsayıcı oluşturur. Kapsayıcınızın ne zaman oluşturulduğunu denetlemek istiyorsanız, bunu kapatın. |
| Çözelti kapatmada otomatik olarak kapları öldürmek | Açık | Docker Oluştur | Çözümünüzü kapattıktan veya Visual Studio'yu kapattıktan sonra çalışmaya devam etmesini istiyorsanız bunu kapatın. |
| Localhost SSL sertifikasına güvenmek için istekte yok | Kapalı | ASP.NET Core 2.1 projeleri | Localhost SSL sertifikasına güvenilmezse, bu onay kutusu işaretlenmedikçe Visual Studio projenizi her çalıştırdığınızda ister. |
::: moniker-end

::: moniker range=">=vs-2019"

Aşağıdaki **tablogenel** ayarları açıklar:

| Adı | Varsayılan Ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Gerekirse Docker Desktop'ı yükleyin | Beni İste | Tek Proje, Docker Beste | Docker Desktop yüklü değilse istinat isteyip istemediğinizi seçin. |
| Core SSL sertifikasıASP.NET güven | Beni İste | ASP.NET Core 2.x projeleri | **Beni İstet**olarak ayarlandığında, localhost SSL sertifikasına güvenilmezse, Visual Studio projenizi her çalıştırdığınızda ister. |

Aşağıdaki tabloda **Tek Proje** ve Docker **Oluşturma** ayarları açıklanmaktadır:

| Adı | Varsayılan Ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Proje açıkken gerekli Docker görüntülerini çekin | True | Tek Proje, Docker Beste | Proje yüklerken daha yüksek performans için Visual Studio arka planda docker çekme işlemine başlar, böylece kodunuzu çalıştırmaya hazır olduğunuzda görüntü zaten indirilir veya indirme işleminde olur. Projeleri ve gözatma kodunu yüklüyorsanız, ihtiyacınız olmayan kapsayıcı görüntülerini indirmemek için **False** olarak ayarlayabilirsiniz. |
| Proje açık konteynırlarını çalıştırma | True | Tek Proje, Docker Beste | Yine daha yüksek performans için Visual Studio, kabınızı inşa edip çalıştırdığınızda hazır olması için önceden bir konteyner oluşturur. Kapsayıcınızın ne zaman oluşturulduğunu denetlemek istiyorsanız, **False**olarak ayarlayın. |
| Proje deki kapsayıcıları durdurma | True | Tek Proje ve Docker Beste | Çözümünüzü kapattıktan veya Visual Studio'yu kapattıktan sonra çalışmaya devam etmesini istiyorsanız, çözüm için kapsayıcıların çalışmaya devam etmesini istiyorsanız **False** olarak ayarlayın. |

::: moniker-end
> [!WARNING]
> Localhost SSL sertifikasına güvenilmezse ve istek isteni bastırmak için kutuyu işaretleseniz, HTTPS web istekleri uygulamanızda veya hizmetinizde çalışma zamanında başarısız olabilir. Bu durumda, Onay **kutusunu işaretlenin,** projenizi çalıştırın ve istek anında güven belirtin.

## <a name="next-steps"></a>Sonraki adımlar

Bu [genel bakışta](overview.md)Visual Studio'da konteynerlerle çalışma hakkında daha fazla bilgi edinin.