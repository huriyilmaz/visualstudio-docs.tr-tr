---
title: Bulut hizmetini yayımlamaya veya dağıtmaya hazırlanma
description: Bulut ve depolama hesabı hizmetlerini ayarlama ve Azure uygulamanızı yapılandırma yordamlarını öğrenin.
author: ghogen
manager: jillfra
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: a09b8f5c6efacab0f02a445ed78f8a3769031fa0
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399014"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Visual Studio'dan bulut hizmeti yayımlamaya veya dağıtmaya hazırlanma

Bir bulut hizmeti projesi yayımlamak için, aşağıdaki hizmetleri bu makalede açıklandığı gibi ayarlamanız gerekir:

* Azure ortamında rollerinizi çalıştırmak için bir **bulut hizmeti** ve
* Blob, kuyruk ve tablo hizmetlerine erişim sağlayan bir **depolama hesabı** .

## <a name="create-a-cloud-service"></a>Bulut hizmeti oluşturma

Bulut hizmeti, rollerinizi Azure ortamında çalıştırır. Visual Studio 'da ya da aşağıdaki bölümlerde açıklandığı gibi [Azure Portal](https://portal.azure.com/) aracılığıyla bir bulut hizmeti oluşturabilirsiniz.

### <a name="create-a-cloud-service-from-visual-studio"></a>Visual Studio 'dan bir bulut hizmeti oluşturma

1. Daha önce oluşturulmuş bir bulut hizmeti projesiyle, projeye sağ tıklayıp **Yayımla** ' yı seçin.
1. Gerekirse, Azure aboneliğinizle ilişkili Microsoft veya kurumsal hesapla oturum açın ve ardından **Ayarlar** sayfasına Ilerlemek için **İleri** ' yi seçin.
1. **Bulut hizmeti oluştur ve depolama hesabı** iletişim kutusu görüntülenir (yoksa, **bulut hizmeti** listesinden **Yeni oluştur** ' u seçin).
1. URL 'nizin bir parçasını oluşturan ve benzersiz olması gereken bulut hizmetiniz için büyük/küçük harfe duyarsız bir ad girin. Ayrıca bir bölge veya benzeşim grubu seçin ve bir çoğaltma seçeneği belirleyin.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Azure portal aracılığıyla bir bulut hizmeti oluşturun

1. [Azure portalında](https://portal.azure.com/) oturum açın.
1. Sayfanın sol tarafındaki **Cloud Services (klasik)** seçeneğini belirleyin.
1. **+ Ekle** ' yi seçin ve gerekli BILGILERI (DNS adı, abonelik, kaynak grubu ve konum) sağlayın. Bu noktada, daha sonra Visual Studio 'da yaptığınız için bir paketi karşıya yüklemek gerekli değildir.
1. İşlemi gerçekleştirmek için **Oluştur** ' u seçin.

## <a name="create-a-storage-account"></a>Depolama hesabı oluşturma

Depolama hesabı, blob, kuyruk ve tablo hizmetlerine erişim sağlar. Visual Studio veya [Azure Portal](https://portal.azure.com/)aracılığıyla bir depolama hesabı oluşturabilirsiniz.

### <a name="create-a-storage-account-from-visual-studio"></a>Visual Studio 'dan bir depolama hesabı oluşturma

1. Daha önce oluşturulmuş bir bulut hizmeti projesiyle **Çözüm Gezgini** , bir rol projesi Içindeki **bağlı hizmetler** düğümünü bulun, sağ tıklayın ve **bağlı hizmet ekle** ' yi seçin. (Visual Studio 2015 ' de **depolama** düğümüne sağ tıklayın ve **depolama hesabı oluştur** ' u seçin.)
1. Görüntülenen **bağlı hizmetler** listesinde, **Azure depolama ile bulut depolama** ' yı seçin.
1. Görüntülenen Azure depolama iletişim kutusunda, aboneliğinizi belirttiğiniz bir iletişim kutusunu, hesap için bir adı, bir fiyatlandırma katmanını, kaynak grubunu ve konumu gösteren **+ Yeni depolama hesabı oluştur** ' u seçin.
1. İşiniz bittiğinde **Oluştur** ' u seçin. Yeni depolama hesabı, aboneliğinizdeki kullanılabilir depolama hesapları listesinde görüntülenir.
1. Bu hesabı seçin ve **Ekle** ' yi seçin.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Azure portal aracılığıyla bir depolama hesabı oluşturun

1. [Azure portalında](https://portal.azure.com/) oturum açın.
1. Sol üstteki **+ Yeni** ' yi seçin.
1. "Azure Marketi" altında **depolama alanı** ' nı, ardından **depolama hesabı-blob, dosya, tablo, kuyruk** ' u sağ taraftan seçin.
1. Gerekli bilgileri (ad, dağıtım modeli vb.) sağlayın.
1. İşlemi gerçekleştirmek için **Oluştur** ' u seçin.

## <a name="configure-your-app-to-use-the-storage-account"></a>Uygulamanızı depolama hesabını kullanacak şekilde yapılandırma

Bir depolama hesabı oluşturduktan sonra, Visual Studio 'dan bu sunucuya bağlanmak, URL ve erişim anahtarları dahil olmak üzere, proje için hizmet yapılandırmasını otomatik olarak güncelleştirir.

**Bağlı hizmet ekle** ' yi kullanarak Visual Studio 'dan bir bulut hizmeti oluşturduysanız, ve ' i açarak bağlantıları kontrol edebilirsiniz `ServiceConfiguration.Cloud.cscfg` `ServiceConfiguration.Local.cscfg` .

Azure portal aracılığıyla bir bulut hizmeti oluşturduysanız, [Visual Studio 'dan bir depolama hesabı oluşturma](#create-a-storage-account-from-visual-studio) bölümünde aynı adımları izleyin, ancak yeni bir hesap oluşturmak yerine var olan hesabı seçin. Ardından, Visual Studio yapılandırmayı sizin için güncelleştirir.

Ayarları el ile yapılandırmak için, bulut hizmeti projenizde uygulanabilir rol için Visual Studio 'daki özellik sayfalarını kullanın (Role sağ tıklayıp **Özellikler** ' i seçin). Daha fazla bilgi için bkz. bir [depolama hesabına bağlantı dizesi yapılandırma](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Erişim tuşları hakkında

Azure portal, Azure Depolama hizmetlerinin her birinde bulunan kaynaklara erişmek için kullanabileceğiniz URL 'Leri ve ayrıca hesabınız için birincil ve ikincil erişim anahtarlarını gösterir. Depolama hizmetlerinde yapılan isteklerin kimliğini doğrulamak için bu anahtarları kullanırsınız.

İkincil erişim anahtarı, birincil erişim anahtarı olarak depolama hesabınıza aynı erişimi sağlar ve birincil erişim anahtarınızın güvenliğinin aşılmasına karşı bir yedekleme olarak oluşturulur. Ayrıca, erişim anahtarlarınızı düzenli olarak yeniden oluşturmanız önerilir. Birincil anahtarı yeniden oluştururken bir bağlantı dizesi ayarını ikincil anahtarı kullanacak şekilde değiştirebilirsiniz, ardından ikincil anahtarı yeniden oluştururken yeniden üretilen birincil anahtarı kullanacak şekilde değiştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 'dan Azure 'a uygulama yayımlama hakkında daha fazla bilgi edinmek için bkz. [Azure araçlarını kullanarak bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md).
