---
title: Bulut Hizmeti yayınlamaya veya dağıtmaya hazırlanın
description: Bulut ve depolama hesabı hizmetlerini ayarlama ve Azure uygulamanızı yapılandırma yordamlarını öğrenin.
author: ghogen
manager: jillfra
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: f6174f8294f3a9e990893ca9a45d77f2a069692e
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489668"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Visual Studio'dan bulut hizmeti yayımlamaya veya dağıtmaya hazırlanma

Bir bulut hizmeti projesi yayınlamak için, bu makalede açıklandığı şekilde aşağıdaki hizmetleri ayarlamanız gerekir:

* Azure ortamındaki rollerinizi çalıştırmak için bir **bulut hizmeti** ve
* Blob, Sıra ve Tablo hizmetlerine erişim sağlayan bir **depolama hesabı.**

## <a name="create-a-cloud-service"></a>Bulut hizmeti oluşturma

Bir bulut hizmeti, Azure ortamındaki rollerinizi çalıştırAr. Aşağıdaki bölümlerde açıklandığı gibi Visual Studio'da veya [Azure portalı](https://portal.azure.com/) üzerinden bir bulut hizmeti oluşturabilirsiniz.

### <a name="create-a-cloud-service-from-visual-studio"></a>Visual Studio'dan bulut hizmeti oluşturma

1. Daha önce oluşturulmuş bir Bulut Hizmeti projesinde, project'i seç seçeneğini sağ **tıklatın.**
1. Gerekirse, Azure aboneliğinizle ilişkili Microsoft veya kuruluş hesabıyla oturum açın ve **Ayarlar** sayfasına ilerlemek için **İleri'yi** seçin.
1. **Bulut Hizmeti Oluştur ve Depolama Hesabı** oluştur iletişim kutusu görüntülenir (değilse, Bulut **Hizmeti** listesinden **Yeni Oluştur'u** seçin).
1. URL'nizin bir parçasını oluşturan ve benzersiz olması gereken bulut hizmetiniz için bir büyük/küçük harf duyarlı adı girin. Ayrıca bir Bölge veya Affinity Grubu seçin ve bir Çoğaltma seçeneği seçin.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Azure portalı üzerinden bulut hizmeti oluşturma

1. [Azure Portal](https://portal.azure.com/) oturum açın.
1. Sayfanın sol tarafındaki **Bulut Hizmetleri'ni (klasik)** seçin.
1. Seçin **+ Ekle,** ardından gerekli bilgileri (DNS adı, abonelik, kaynak grubu ve konum) sağlayın. Bu noktada bir paket yüklemenize gerek yoktur çünkü bunu daha sonra Visual Studio'da yaparsınız.
1. İşlemi tamamlamak için **Oluştur'u** seçin.

## <a name="create-a-storage-account"></a>Depolama hesabı oluşturma

Depolama hesabı Blob, Sıra ve Tablo hizmetlerine erişim sağlar. Visual Studio veya [Azure portalı](https://portal.azure.com/)aracılığıyla bir depolama hesabı oluşturabilirsiniz.

### <a name="create-a-storage-account-from-visual-studio"></a>Visual Studio'dan depolama hesabı oluşturma

1. Daha önce oluşturulmuş bir Bulut Hizmeti projesiyle **Solution Explorer'da,** Bağlı **Hizmetler** düğümünü bir rol projesi içinde bulun, sağ tıklatın ve Bağlı Hizmet **Ekle'yi**seçin. (Visual Studio 2015'te **Depolama** düğümüne sağ tıklayın ve **Depolama Hesabı Oluştur'u**seçin.)
1. Görünen **Bağlı Hizmetler** listesinde Azure **Depolama ile Bulut Depolama'yı**seçin.
1. Görünen Azure Depolama iletişim kutusunda, aboneliğinizi, hesabı belirten bir ad, fiyatlandırma katmanı, kaynak grubu ve konumu belirttiğiniz bir iletişim kutusunu oluşturan **+Yeni Depolama Hesabı Oluştur'u**seçin.
1. İşi bittiğinde **Oluştur'u** seçin. Yeni depolama hesabı, aboneliğinizdeki kullanılabilir depolama hesapları listesinde görünür.
1. Bu hesabı seçin ve **Ekle'yi**seçin.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Azure portalı üzerinden bir depolama hesabı oluşturma

1. [Azure Portal](https://portal.azure.com/) oturum açın.
1. Sol üstte **+ Yeni'yi** seçin.
1. "Azure Marketi" altında **Depolama'yı** seçin, ardından **Depolama hesabı - blob, dosya, tablo,** sağ taraftan sıra.
1. Gerekli bilgileri (ad, dağıtım modeli vb.) sağlayın.
1. İşlemi tamamlamak için **Oluştur'u** seçin.

## <a name="configure-your-app-to-use-the-storage-account"></a>Uygulamanızı depolama hesabını kullanacak şekilde yapılandırın

Bir depolama hesabı oluşturduktan sonra, Visual Studio'dan ona bağlanmak, URL'ler ve erişim anahtarları da dahil olmak üzere projenin hizmet yapılandırmalarını otomatik olarak güncelleştirir.

**Bağlı Ekle Hizmetini**kullanarak Visual Studio'dan bir bulut hizmeti oluşturduysanız, `ServiceConfiguration.Cloud.cscfg` `ServiceConfiguration.Local.cscfg`bağlantıları açarak ve .

Azure portalı üzerinden bir bulut hizmeti oluşturduysanız, [Visual Studio'dan bir depolama hesabı oluştur'da](#create-a-storage-account-from-visual-studio) aynı adımları izleyin, ancak yeni bir hizmet oluşturmak yerine varolan hesabı seçin. Visual Studio daha sonra yapılandırmayı sizin için günceller.

Ayarları el ile yapılandırmak için, bulut hizmeti projenizdeki geçerli rol için Visual Studio'daki özellik sayfalarını kullanın (rolü sağ tıklatın ve **Özellikler'i**seçin). Daha fazla bilgi için [bkz.](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account)

### <a name="about-access-keys"></a>Erişim tuşları hakkında

Azure portalı, Azure depolama hizmetlerinin her birinde kaynaklara erişmek için kullanabileceğiniz URL'leri ve ayrıca hesabınızın birincil ve ikincil erişim anahtarlarını gösterir. Bu anahtarları depolama hizmetlerine karşı yapılan istekleri doğrulamak için kullanırsınız.

İkincil erişim anahtarı, birincil erişim anahtarıyla depolama hesabınıza aynı erişimi sağlar ve birincil erişim anahtarınızın tehlikeye atılması halinde yedek olarak oluşturulur. Ayrıca, erişim anahtarlarınızı düzenli olarak yeniden oluşturmanız önerilir. Birincil anahtarı yeniden oluştururken ikincil anahtarı kullanmak için bir bağlantı dize ayarını değiştirebilir, sonra ikincil anahtarı yeniden oluştururken yeniden oluşturulan birincil anahtarı kullanmak üzere değiştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio'dan Uygulamaları Azure'a yayımlama hakkında daha fazla bilgi edinmek için Azure [Araçlarını kullanarak Bulut Hizmeti Yayımlama'ya](vs-azure-tools-publishing-a-cloud-service.md)bakın.
