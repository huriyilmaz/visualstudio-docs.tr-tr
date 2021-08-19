---
title: Visual Studio Kapsayıcı Araçlarını Yapılandırma
description: Docker kapsayıcıları ile Visual Studio için Visual Studio araçları yapılandırma.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-container-tools
ms.openlocfilehash: 29d1753e8d0c03391d60a4985a922bfb796dc3e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045079"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Visual Studio Container Tools'ları yapılandırma

Bu Visual Studio kullanarak, Docker kapsayıcıları ile çalışırken performansı ve kaynak kullanımını etkileyen ayarlar dahil olmak üzere Visual Studio'nin Docker kapsayıcıları ile nasıl çalıştığıyla ilgili bazı özellikleri kontrol edebilirsiniz.

## <a name="container-tools-settings"></a>Kapsayıcı Araçları ayarları

Ana menüden Araçlar ve **Seçenekler'> Kapsayıcı** Araçları'> Ayarlar.  Kapsayıcı araçları ayarları görüntülenir.

::: moniker range="vs-2017"

![Visual Studio Kapsayıcı Araçları seçenekleri, gösterilen: Proje yükünde gerekli Docker görüntülerini otomatik olarak çekin, Kapsayıcıları arka planda otomatik olarak başlat, Çözüm kapanıyorken kapsayıcıları otomatik olarak sonla ve SSL sertifikasına güvenme isteminde değil.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Kapsayıcı Araçları **Genel** ayarları:

![Visual Studio Kapsayıcı Araçları seçenekleri: Gerekirse Docker Desktop'ı yükleme ve SSL sertifikasına ASP.NET Core yükleme.](./media/configure-container-tools/tools-options-1.png)

Kapsayıcı Araçları **Tek Project** **ve Docker Compose** ayarları:

![Visual Studio Kapsayıcı Araçları seçenekleri, gösterilen: Proje kapanışı üzerinde kapsayıcıları kapatın, Proje açıkken gerekli Docker görüntülerini çekin ve Proje açıkken kapsayıcıları çalıştırın.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Aşağıdaki tablo, bu seçeneklerin nasıl ayarlana karar vermede size yardımcı olabilir.

::: moniker range="vs-2017"
| Name | Varsayılan Ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Proje yükü üzerinde gerekli Docker görüntülerini otomatik olarak çekme | Açık | Docker Compose | Projeleri yüklerken daha yüksek performans için Visual Studio arka planda bir Docker çekme işlemi başlatacak ve böylece kodunuzu çalıştırmaya hazır olduğunda görüntünün indirilmiş veya indirme işlemi sırasında olduğu gibi. Yalnızca proje yükleniyor ve koda göz atıyorsanız, ihtiyacınız olan kapsayıcı görüntülerini indirmekten kaçınmak için bu özelliği kapatabilirsiniz. |
| Kapsayıcıları arka planda otomatik olarak başlatma | Açık | Docker Compose | Daha yüksek performans için Visual Studio derleme ve çalıştırma için hazır birim bağlamaları olan bir kapsayıcı oluşturur. Kapsayıcının ne zaman oluşturulacaklarını kontrol etmek için bunu kapatın. |
| Çözüm kapatılırken kapsayıcıları otomatik olarak sonla | Açık | Docker Compose | Çözümünüz için kapsayıcıların çözümü kapattıktan veya kapattıktan sonra çalışmaya devam etmek Visual Studio. |
| localhost SSL sertifikasına güvenme isteminde değil | Kapalı | ASP.NET Core 2.1 projeleri | localhost SSL sertifikasına güvenilmiyorsa, Visual Studio onay kutusu işaretli olmadığı sürece, projenizi her kez çalıştırarak bu sertifikayı sorabilirsiniz. |
::: moniker-end

::: moniker range=">=vs-2019"

Aşağıdaki tabloda Genel ayarlar **açık** almaktadır:

| Name | Varsayılan Ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Gerekirse Docker Desktop'ı yükleme | Bana sor | Tek Project, Docker Compose | Docker Desktop'ın yüklü olup olmadığının sorulıp sorulmay olmadığını seçin. |
| SSL ASP.NET Core güven | Bana sor | ASP.NET Core 2.x projeleri | Beni İste **olarak ayarlanırsa,** localhost SSL sertifikasına güvenilmiyorsa, Visual Studio projenizi her çalıştırsanız bunu sorabilirsiniz. |

Aşağıdaki tabloda Tekli veri **Project** ve **Docker Compose** açık almaktadır:

| Name | Varsayılan Ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Proje açıkken gerekli Docker görüntülerini çekme | Doğru | Tek Project, Docker Compose | Projeleri yüklerken daha yüksek performans için Visual Studio arka planda bir Docker çekme işlemi başlatacak ve böylece kodunuzu çalıştırmaya hazır olduğunda görüntünün indirilmiş veya indirme işlemi sırasında olduğu gibi. Yalnızca proje yükleniyor ve koda göz atıyorsanız, ihtiyacınız olan kapsayıcı görüntülerini indirmekten kaçınmak için False olarak ayarlayın.  |
| Proje açıkken kapsayıcıları çalıştırma | Doğru | Tek Project, Docker Compose | Daha yüksek performans Visual Studio, kapsayıcınızı derlemek ve çalıştırmak için hazır hale gelecek şekilde bir kapsayıcı oluşturur. Kapsayıcının ne zaman oluşturulacaklarını kontrol etmek için False olarak **ayarlayın.** |
| Proje kapatmada kapsayıcıları durdurma | Doğru | Tek Project ve Docker Compose | Çözümünüz **için** kapsayıcıların çözümü kapattıktan veya kapattıktan sonra çalışmaya devam etmek Visual Studio. |

::: moniker-end
> [!WARNING]
> localhost SSL sertifikasına güvenilmiyorsa ve istemin gizlendiği kutuyu işaret ediyorsanız, HTTPS web istekleri uygulama veya hizmetinizin çalışma zamanında başarısız olabilir. Bu durumda, İstem yapma **onay kutusunun işaretini** kaldırın, projenizi çalıştırın ve isteminde güveni belirtin.

## <a name="next-steps"></a>Sonraki adımlar

Bu genel bakış içinde kapsayıcılarla çalışma hakkında Visual Studio daha fazla bilgi [edinin.](overview.md)