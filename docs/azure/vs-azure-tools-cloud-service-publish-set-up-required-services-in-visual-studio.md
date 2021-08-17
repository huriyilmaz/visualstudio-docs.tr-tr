---
title: Bulut Hizmeti yayımlamaya veya dağıtmaya hazırlanma
description: Bulut ve depolama hesabı hizmetlerini ayarlama ve Azure uygulamalarınızı yapılandırma yordamlarını öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 83ee497950383be1ba284f379985d748eac4ea50
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082380"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Visual Studio'dan bulut hizmeti yayımlamaya veya dağıtmaya hazırlanma

Bir bulut hizmeti projesini yayımlamak için, bu makalede açıklandığı gibi aşağıdaki hizmetleri ayarlayabilirsiniz:

* **Rollerinizi** Azure ortamında çalıştırmak için bir bulut hizmeti ve
* **Blob,** Kuyruk ve Tablo hizmetleri için erişim sağlayan bir depolama hesabı.

## <a name="create-a-cloud-service"></a>Bulut hizmeti oluşturma

Bulut hizmeti rollerinizi Azure ortamında çalıştırır. Aşağıdaki bölümlerde açıklandığı gibi Visual Studio veya [Azure portal](https://portal.azure.com/) aracılığıyla bulut hizmeti oluşturabilirsiniz.

### <a name="create-a-cloud-service-from-visual-studio"></a>Visual Studio'dan bulut hizmeti oluşturma

1. Daha önce oluşturulmuş bir Bulut Hizmeti projesiyle projeye sağ tıklayın ve Yayımla'yı **seçin.**
1. Gerekirse, Azure aboneliğiniz ile ilişkilendirilmiş Microsoft veya kuruluş  hesabıyla oturum açın, ardından Sonraki'yi seçerek Ayarlar **geçin.**
1. Bulut **Hizmeti ve Depolama Hesabı Oluştur** iletişim kutusu görüntülenir (yoksa, Bulut Hizmeti **listesinden** Yeni **Oluştur'a** tıklayın).
1. Bulut hizmetiniz için URL'nizin bir bölümünü oluşturan ve benzersiz olması gereken büyük/küçük harfe duyarlı olmayan bir ad girin. Ayrıca bir Bölge veya Benzeşm Grubu seçin ve bir Çoğaltma seçeneği belirleyin.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Azure portal aracılığıyla bulut hizmeti oluşturma

1. [Azure Portal](https://portal.azure.com/)’ında oturum açın.
1. Sayfanın **Cloud Services (klasik)** öğesini seçin.
1. **+ Ekle'yi** seçin, ardından gerekli bilgileri (DNS adı, abonelik, kaynak grubu ve konum) girin. Bu noktada bir paketi karşıya yüklemek gerekli değildir çünkü bunu daha sonra Visual Studio.
1. Süreci **tamamlamak** için Oluştur'a seçin.

## <a name="create-a-storage-account"></a>Depolama hesabı oluşturma

Depolama hesabı Blob, Kuyruk ve Tablo hizmetleri için erişim sağlar. depolama hesabı oluşturmak için Visual Studio veya [Azure portal.](https://portal.azure.com/)

### <a name="create-a-storage-account-from-visual-studio"></a>Depolama hesabından depolama Visual Studio

1. Daha **Çözüm Gezgini** oluşturulmuş bir Bulut Hizmeti projesiyle birlikte, rol projesinin içindeki **Bağlı** Hizmetler düğümünü bulun, sağ tıklayın ve Bağlı Hizmet **Ekle'yi seçin.** (Visual Studio 2015'te, **Depolama** düğümüne sağ tıklayın ve Depolama **Hesabı Oluştur'u seçin.)**
1. Görüntülenen **Bağlı Hizmetler listesinde** Cloud Depolama **with Azure Depolama**.
1. Görüntülenen Azure Depolama iletişim kutusunda **+Yeni Depolama** Hesabı Oluştur'a tıklayın. Abonelik, hesap için bir ad, fiyatlandırma katmanı, kaynak grubu ve konum belirttiğiniz bir iletişim kutusu açılır.
1. **Bitirerek** Oluştur'a seçin. Yeni depolama hesabı, aboneliğinizin kullanılabilir depolama hesapları listesinde görünür.
1. Bu hesabı seçin ve **Ekle'yi seçin.**

### <a name="create-a-storage-account-through-the-azure-portal"></a>Azure portal aracılığıyla depolama hesabı oluşturma

1. [Azure Portal](https://portal.azure.com/)’ında oturum açın.
1. Sol **üst tarafta +** Yeni'yi seçin.
1. **"Depolama"** Azure Market seçin ve ardından Depolama **hesabı ( blob, dosya, tablo, kuyruk)** seçin.
1. Gerekli bilgileri (ad, dağıtım modeli vb.) girin.
1. Süreci **tamamlamak** için Oluştur'a seçin.

## <a name="configure-your-app-to-use-the-storage-account"></a>Depolama hesabını kullanmak için uygulama yapılandırma

Bir depolama hesabı oluşturduktan sonra, Visual Studio url'ler ve erişim anahtarları dahil olmak üzere projenin hizmet yapılandırmalarını otomatik olarak ler.

Bağlı Hizmet Ekle'yi kullanarak Visual Studio hizmeti **oluşturduysanız** ve 'yi açarak bağlantıları kontrol `ServiceConfiguration.Cloud.cscfg` `ServiceConfiguration.Local.cscfg` edin.

Azure portal aracılığıyla bir bulut hizmeti oluşturduysanız, Visual Studio'den depolama hesabı oluşturma'daki adımları [izleyin,](#create-a-storage-account-from-visual-studio) ancak yeni hesap oluşturmak yerine mevcut hesabı seçin. Visual Studio yapılandırmayı sizin için güncelleştirmeleri gerekir.

Ayarları el ile yapılandırmak için, bulut hizmeti Visual Studio ilgili rol için uygulama sayfasındaki özellik sayfalarını kullanın (role sağ tıklayın ve Özellikler'i **seçin).** Daha fazla bilgi için [bkz. Depolama hesabına bağlantı dizesi yapılandırma.](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account)

### <a name="about-access-keys"></a>Erişim anahtarları hakkında

Bu Azure portal Azure depolama hizmetlerinin her bir kaynağına erişmek için kullanabileceğiniz URL'leri ve ayrıca hesabınız için birincil ve ikincil erişim anahtarlarını gösterir. Depolama hizmetlerde yapılan isteklerin kimliğini doğrulamak için bu anahtarları kullanırsiniz.

İkincil erişim anahtarı depolama hesabınıza birincil erişim anahtarıyla aynı erişimi sağlar ve birincil erişim anahtarınız tehlikeye girer ve yedek olarak oluşturulur. Ayrıca, erişim anahtarlarınızı düzenli olarak yeniden oluşturmanız önerilir. Birincil anahtarı yeniden oluşturma sırasında bir bağlantı dizesi ayarını ikincil anahtarı kullanmak üzere değiştirebilirsiniz, ardından bunu, ikincil anahtarı yeniden oluşturulurken yeniden üretilen birincil anahtarı kullanmak üzere değiştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Azure'da uygulama yayımlama hakkında daha fazla bilgi Visual Studio için bkz. [Azure Araçları'Visual Studio Bulut Hizmeti Yayımlama.](vs-azure-tools-publishing-a-cloud-service.md)
