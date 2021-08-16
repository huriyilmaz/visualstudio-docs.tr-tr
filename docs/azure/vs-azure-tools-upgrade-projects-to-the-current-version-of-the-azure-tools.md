---
title: Projeleri Azure araçlarının geçerli sürümüne yükseltme
description: Azure'daki bir Azure projesini Visual Studio Azure araçlarının geçerli sürümüne yükseltmeyi öğrenin
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 2fbe048d232c7129709ed1655bcb0dc86b11eb8d9b497c859fffdd921db9fa52
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363214"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Projeleri Visual Studio için Azure Araçları'nın güncel sürümüne yükseltme
## <a name="overview"></a>Genel Bakış
Azure Araçları'nın geçerli sürümünü (veya 1.6'dan yeni bir sürümü) yükledikten sonra, 1.6 'dan (Kasım 2011) önceki bir Azure Araçları sürümü kullanılarak oluşturulan tüm projeler, siz bunları açar açmaz otomatik olarak yükseltilir. Projeleri bu araçların 1.6 (Kasım 2011) sürümüyle oluşturduysanız ve bu sürüm hala yüklüyse, bu projeleri eski sürümde açabilir ve daha sonra yükseltip yükseltmey karar veyebilirsiniz.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Projenizi yükseltinca nasıl değişir?
Bir proje otomatik olarak yükseltilirse veya bunu yükseltmek istediğiniz belirtirse, projeniz belirli derlemelerin geçerli sürümleriyle çalışacak şekilde değiştirilir ve bu bölümde anlatıldıklarına göre bazı özellikler de değiştirilir. Projeniz diğer değişikliklerin araçların daha yeni sürümüyle uyumlu olması gerektiriyorsa, bu değişiklikleri el ile de yapabilirsiniz.

* Web web.config ve çalışan rolleri için app.config dosyası, web rollerinin yeni sürümüne başvuracak şekilde Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll.
* Derlemeler Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll ve Microsoft.WindowsAzure.ServiceRuntime.dll yeni sürümlere yükseltilir.
* Azure proje dosyasında (.ccproj) depolanan yayımlama profilleri Yayımla alt dizininde .azurePubXml uzantısına sahip ayrı bir **dosyaya** taşınır.
* Yayımlama profilinde bazı özellikler yeni ve değiştirilmiş özellikleri destekleyecek şekilde güncelleştirilir. Dağıtılan bir bulut hizmetini aynı anda veya artımlı olarak güncelleştiremeniz nedeniyle **AllowUpgrade,** **DeploymentReplacementMethod** ile değiştirilir.
* **UseIISExpressByDefault** özelliği eklenir ve hata ayıklama için kullanılan web sunucusunun Internet Information Services (IIS) olan web sunucusunun otomatik olarak hata IIS Express. IIS Express, araçların yeni sürümleriyle oluşturulan projeler için varsayılan web sunucusudur.
* Azure Önbelleğe Alma projenizin rollerinden biri veya daha fazlası içinde barındırıldısa, bir proje yükseltilirken hizmet yapılandırması (.cscfg dosyası) ve hizmet tanımı (.csdef dosyası) bazı özellikler değiştirilir. Proje Azure Önbelleğe Alma NuGet paketini kullanıyorsa, proje paketin en son sürümüne yükseltilir. İstemci yapılandırma dosyasını web.config ve istemci yapılandırmasının yükseltme işlemi sırasında düzgün şekilde korunarak koruna olduğunu doğrulamanız gerekir. NuGet paketini kullanmadan Azure Önbelleğe Alma istemci derlemelerine başvurular eklediysanız, bu derlemeler güncelleştirilmez; Bu başvuruları yeni sürümlere el ile güncelleştirmeniz gerekir.

> [!IMPORTANT]
> F# projeleri için, bu derlemelerin daha yeni sürümlerine başvuracak şekilde Başvuruları Azure derlemelerine el ile güncelleştirmeniz gerekir.
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Azure projesini geçerli sürüme yükseltme
1. Yükseltilen proje için kullanmak istediğiniz Visual Studio Azure Araçları'nın geçerli sürümünü yükleyin ve ardından yükseltmek istediğiniz projeyi açın. Proje 1.6 'dan (Kasım 2011) önce bir Azure Araçları sürümüyle oluşturulmuşsa, proje otomatik olarak geçerli sürüme yükseltilir. Proje Kasım 2011 sürümüyle oluşturulmuşsa ve bu sürüm hala yüklüyse, proje bu sürümde açılır.
2. Bu Çözüm Gezgini proje düğümünün kısayol menüsünü açın, Özellikler'i seçin ve ardından görüntülenen **iletişim** kutusunun Uygulama sekmesini seçin.

    Uygulama **sekmesi,** projeyle ilişkili araç sürümünü gösterir. Azure Araçları'nın geçerli sürümü görünürse proje zaten yükseltilmiştir. Araçların sekmede görünenden daha yeni bir sürümünü yüklemişsanız Yükselt **düğmesi** görüntülenir.
3. Projeyi **araçların** geçerli sürümüne yükseltmek için Yükselt düğmesini seçin.
4. Projeyi derleme ve ardından API değişikliklerinden gelen hataları giderme. Kodunuzu yeni sürüm için değiştirme hakkında bilgi için ilgili API'nin belgelerine bakın.
