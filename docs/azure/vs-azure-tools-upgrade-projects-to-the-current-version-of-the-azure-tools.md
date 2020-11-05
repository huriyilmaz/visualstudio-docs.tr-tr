---
title: Projeleri Azure Araçları 'nın güncel sürümüne yükseltin
description: Visual Studio 'da bir Azure projesini Azure araçlarının güncel sürümüne nasıl yükselteceğinizi öğrenin
author: ghogen
manager: jillfra
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 4cd9ffac5f668a9f6cd6ab266d38b90658ce9336
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398585"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Projeleri Visual Studio için Azure Araçları'nın güncel sürümüne yükseltme
## <a name="overview"></a>Genel Bakış
Geçerli Azure araçları sürümünü (veya 1,6 'den daha yeni bir sürümü) yükledikten sonra, bir Azure Araçları 1,6 sürümü kullanılarak oluşturulan tüm projeler, siz açarsınız, otomatik olarak yükseltilir (Kasım 2011). Bu araçların 1,6 (Kasım 2011) sürümünü kullanarak projeler oluşturduysanız ve bu sürümü hala yüklüyse, bu projeleri eski sürümde açabilir ve daha sonra bunları yükseltireceğinize karar verebilirsiniz.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Yükselttiğinizde projeniz nasıl değişir
Bir proje otomatik olarak yükseltildiyse veya onu yükseltmek istediğinizi belirtirseniz, projeniz belirli derlemelerin geçerli sürümleriyle çalışacak şekilde değiştirilir ve bu bölümde açıklanan bazı özellikler de değiştirilir. Projeniz diğer değişikliklerin araçların daha yeni sürümü ile uyumlu olmasını gerektiriyorsa, bu değişiklikleri el ile yapmanız gerekir.

* Web rollerinin web.config dosyası ve çalışan rolleri için app.config dosyası, Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll daha yeni sürümüne başvuracak şekilde güncelleştirilir.
* Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll ve Microsoft.WindowsAzure.ServiceRuntime.dll derlemeleri yeni sürümlere yükseltilir.
* Azure proje dosyasında (. ccproj) depolanan yayımlama profilleri, **Yayımla** alt dizininde. azurePubXml uzantılı ayrı bir dosyaya taşınır.
* Yayımla profilindeki bazı özellikler yeni ve değiştirilmiş özellikleri destekleyecek şekilde güncelleştirilir. Dağıtılmış bir bulut hizmetini eşzamanlı olarak veya artımlı olarak güncelleştirebilmeniz için **Allowupgrade** , **Deploymentreplacementmethod** ile değiştirilmiştir.
* **UseIISExpressByDefault** özelliği eklenir ve false olarak ayarlanır, böylece hata ayıklama için kullanılan Web sunucusu otomatik olarak Internet INFORMATION SERVICES (IIS) ' den IIS Express ' e değişmez. IIS Express, araçların yeni sürümleriyle oluşturulan projelere yönelik varsayılan Web sunucusudur.
* Azure önbelleği, projenizin rollerinin bir veya daha fazlasına barındırılıyorsa, bir proje yükseltildiğinde hizmet yapılandırmasındaki (. cscfg dosyası) ve hizmet tanımındaki (. csdef dosyası) bazı özellikler değiştirilir. Proje Azure önbelleğe alma NuGet paketini kullanıyorsa, proje paketin en son sürümüne yükseltilir. web.config dosyasını açmanız ve yükseltme işlemi sırasında istemci yapılandırmasının düzgün şekilde korunduğundan emin olmanız gerekir. Azure önbelleğe alma istemci derlemelerine başvuruları NuGet paketini kullanmadan eklediyseniz, bu derlemeler güncellenmez; Bu başvuruları yeni sürümlere el ile güncelleştirmeniz gerekir.

> [!IMPORTANT]
> F # projeleri için, Azure derlemelerine yapılan başvuruları, bu derlemelerin daha yeni sürümlerine başvuracak şekilde el ile güncelleştirmeniz gerekir.
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Bir Azure projesini geçerli sürüme yükseltme
1. Azure araçlarının güncel sürümünü, yükseltilen proje için kullanmak istediğiniz Visual Studio yüklemesinde yükleme ve ardından yükseltmek istediğiniz projeyi açın. Proje 1,6 (2011 Kasım) öncesi bir Azure araçları sürümü ile oluşturulduysa, proje otomatik olarak geçerli sürüme yükseltilir. Proje Kasım 2011 sürümüyle oluşturulduysa ve bu yayın hala yüklüyse, proje o sürümde açılır.
2. Çözüm Gezgini, proje düğümünün kısayol menüsünü açın, **Özellikler** ' i seçin ve ardından görüntülenen Iletişim kutusunun **uygulama** sekmesini seçin.

    **Uygulama** sekmesi, projeyle ilişkili araçlar sürümünü gösterir. Geçerli Azure araçları sürümü görüntülenirse, proje zaten yükseltilmiştir. Araçların gösterdiği sürümden daha yeni bir sürümünü yüklediyseniz, bir **yükseltme** düğmesi görünür.
3. Bir projeyi araçların güncel sürümüne yükseltmek için **Yükselt** düğmesini seçin.
4. Projeyi derleyin ve ardından API değişikliklerinden kaynaklanan tüm hataları çözün. Yeni sürüm için kodunuzun nasıl değiştirileceği hakkında daha fazla bilgi için, belirli bir API 'nin belgelerine bakın.
