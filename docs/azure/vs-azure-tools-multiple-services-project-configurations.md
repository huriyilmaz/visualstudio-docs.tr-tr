---
title: Azure projesini birden çok hizmet yapılandırmasıyla yapılandırma
description: ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg ve ServiceConfiguration.Cloud.cscfg dosyalarını değiştirerek bir Azure bulut hizmeti projesini nasıl yapılandırabilirsiniz öğrenin.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 7b9df8c5609c92a6b6631d1ed9fdda8d65e9b605
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301701"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Visual Studio'da Azure projenizi birden çok hizmet yapılandırması kullanacak şekilde yapılandırma

Visual Studio'daki bir Azure bulut hizmeti `ServiceDefinition.csdef` `ServiceConfiguration.Local.cscfg`projesi `ServiceConfiguration.Cloud.cscfg`üç yapılandırma dosyası içerir: , , ve:

- `ServiceDefinition.csdef`bulut hizmetinin gereksinimlerini ve rollerini açıklamak ve tüm örnekler için geçerli ayarları sağlamak için Azure'a dağıtılır. Ayarlar, Azure Hizmet Barındırma Çalışma Zamanı API'sini kullanarak çalışma zamanında okunabilir. Bu dosya Yalnızca bulut hizmeti durdurulduğunda Azure'da güncelleştirilebilir.
- `ServiceConfiguration.Local.cscfg`ve `ServiceConfiguration.Cloud.cscfg` tanım dosyasındaki ayarlar için değerler sağlayın ve her rol için çalışacak örnek sayısını belirtin. "Yerel" dosyası yerel hata ayıklama kullanılan değerleri içerir; "Bulut" dosyası Azure'a olarak `ServiceConfiguration.cscfg` dağıtılır ve sunucu ortamı için ayarlar sağlar. Bulut hizmetiniz Azure'da çalışırken bu dosya güncellenebilir.

Yapılandırma ayarları Visual Studio'da geçerli rol için özellik sayfaları kullanılarak yönetilir ve değiştirilir (rolü sağ tıklatın ve **Özellikler'i**seçin veya rolü çift tıklatın). Değişiklikler, **Hizmet Yapılandırması** açılır açılır arasında hangi yapılandırma seçilirse seçilsin kapsama alanı olabilir. Web ve çalışan rollerinin özellikleri, aşağıdaki bölümlerde açıklanan durumlar dışında benzerdir.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Hizmet tanımı ve hizmet yapılandırma dosyalarının temel şemaları hakkında bilgi için [.csdef XML Schema](/azure/cloud-services/schema-csdef-file) ve [.cscfg XML Schema](/azure/cloud-services/schema-cscfg-file) makalelerine bakın. Hizmet yapılandırması hakkında daha fazla bilgi için [Bulut Hizmetlerinin Nasıl Yapılandırıldığı'na](/azure/cloud-services/cloud-services-how-to-configure-portal)bakın.

## <a name="configuration-page"></a>Yapılandırma sayfası

### <a name="service-configuration"></a>Hizmet Yapılandırması

Hangi `ServiceConfiguration.*.cscfg` dosyanın değişikliklerden etkilendiğini seçer. Varsayılan olarak, Yerel ve Bulut türevleri vardır ve yapılandırma dosyalarını kopyalamak, yeniden adlandırmak ve kaldırmak için **Yönet...** komutunu kullanabilirsiniz. Bu dosyalar bulut hizmeti projenize eklenir ve **Solution Explorer'da**görünür. Ancak, yapılandırmaları yeniden adlandırma veya kaldırma yalnızca bu denetimden yapılabilir.

### <a name="instances"></a>Örnekler

**Örnek** sayısı özelliğini, hizmetin bu rol için çalıştırması gereken örnek sayısına ayarlayın.

**VM boyutu** özelliğini **Ekstra Küçük,** **Küçük,** **Orta,** **Büyük**veya **Ekstra Büyük**olarak ayarlayın.  Daha fazla bilgi için bkz. [Bulut Hizmetlerinin Boyutları](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Başlangıç Eylemi (yalnızca Web rolü)

Visual Studio'nun HTTP uç noktaları veya HTTPS uç noktaları veya hata ayıklamaya başladığınızda her ikisi için bir web tarayıcısı başlatması gerektiğini belirtmek için bu özelliği ayarlayın.

**HTTPS bitiş noktası** seçeneği yalnızca rolünüz için zaten bir HTTPS bitiş noktası tanımladıysanız kullanılabilir. **Bitiş Noktaları** özelliği sayfasında bir HTTPS bitiş noktası tanımlayabilirsiniz.

Zaten bir HTTPS bitiş noktası eklediyseniz, https uç noktası seçeneği varsayılan olarak etkinleştirilir ve Visual Studio hata ayıklamaya başladığınızda, her iki başlangıç seçeneğinin de etkin olduğunu varsayarak, http uç noktanız için bir tarayıcıya ek olarak bu uç nokta için bir tarayıcı başlatır.

### <a name="diagnostics"></a>Tanılama

Varsayılan olarak, Web rolü için tanılama etkinleştirilir. Azure bulut hizmeti projesi ve depolama hesabı yerel depolama emülatörü kullanacak şekilde ayarlanmıştır. Azure'a dağıtmaya hazır olduğunuzda, azure depolama alanını kullanmak için oluşturucu düğmesini **(...**) seçebilirsiniz. Tanılama verilerini isteğe bağlı olarak veya otomatik olarak zamanlanan aralıklarla depolama hesabına aktarabilirsiniz. Azure tanılama hakkında daha fazla bilgi için [bkz.](/azure/cloud-services/cloud-services-dotnet-diagnostics)

## <a name="settings-page"></a>Ayarlar sayfası

**Ayarlar** sayfasında, yapılandırmaya ad değeri çiftleri olarak ayarlar ekleyebilirsiniz. Rolde çalışan kod, özellikle [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) yöntemi olan Azure [Yönetilen Kitaplığı](/previous-versions/azure/dn602775(v=azure.11))tarafından sağlanan sınıfları kullanarak yapılandırma ayarlarınızın değerlerini çalışma zamanında okuyabilir.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Depolama hesabı için bağlantı dizesi yapılandırma

Bağlantı dizesi, depolama emülatörü veya Azure depolama hesabı için bağlantı ve kimlik doğrulama bilgileri sağlayan bir ayardır. Bir roldeki kod Azure depolama alanına (blobs, kuyruklar veya tablolar) erişse, bir bağlantı dizesi gerekir.

> [!Note]
> Azure depolama hesabı için bir bağlantı dizesi tanımlı bir biçim kullanmalıdır [(bkz.](/azure/storage/common/storage-configure-connection-string)

Bağlantı dizesini gerektiğinde yerel depolamayı kullanacak şekilde ayarlayabilir ve bulut hizmetini uygulamaya dağıttığınızda bir Azure depolama hesabına ayarlayabilirsiniz. Bağlantı dizesinin düzgün ayarlanmaması, rolünüzün başlamamasına veya başlatma, meşgul ve durdurma durumları arasında geçiş yapmamasına neden olabilir.

Bağlantı dizesi oluşturmak için **Ayar Ekle'yi** seçin ve **Türü** "Bağlantı Dizesi" olarak ayarlayın.

Yeni veya varolan bağlantı dizeleri için **...** * **Depolama Bağlantı String oluştur** iletişim kutusunu açmak için **Değer** alanının sağında:

1. **Connect kullanarak Bağlan'ın**altında, abonelikten bir depolama hesabı seçmek için **aboneliğiniz** seçeneğini seçin. Visual Studio daha sonra `.publishsettings` dosyadan otomatik olarak depolama hesabı kimlik bilgilerini alır.
1. El **ile girilen kimlik bilgilerini** seçmek, Azure portalındaki bilgileri kullanarak hesap adını ve anahtarı doğrudan belirtmenize olanak tanır. Hesap anahtarını kopyalamak için:
    1. Azure portalındaki depolama hesabına gidin ve **Anahtarları Yönet'i**seçin.
    1. Hesap anahtarını kopyalamak için Azure portalındaki depolama hesabına gidin, **Ayarlar > Erişim tuşlarını**seçin ve ardından panodaki birincil erişim anahtarını kopyalamak için kopyala düğmesini kullanın.
1. Bağlantı seçeneklerinden birini seçin. **Özel uç noktaları belirtin,** lekeler, tablolar ve kuyruklar için belirli URL'ler belirtmenizi ister. Özel uç noktalar, [özel etki alanlarını](/azure/storage/blobs/storage-custom-domain-name) kullanmanıza ve erişimi daha tam olarak denetlemenize olanak sağlar. Bkz. [Azure Depolama Bağlantı Dizelerini Yapılandırma.](/azure/storage/common/storage-configure-connection-string)
1. Yapılandırmayı yeni bağlantı dizesiyle güncelleştirmek için **Tamam,** ardından **Dosya >** Kaydet'i seçin.

Yine, uygulamanızı Azure'da yayımladığınızda, bağlantı dizesi için Azure depolama hesabını içeren hizmet yapılandırmasını seçin. Uygulamanız yayımlandıktan sonra, uygulamanın Azure depolama hizmetlerine karşı beklendiği gibi çalıştığından doğrulayın.

Hizmet yapılandırmalarının nasıl güncelleştirilenhakkında daha fazla bilgi için, [depolama hesapları için bağlantı dizelerini yönet bölümüne](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts)bakın.

## <a name="endpoints-page"></a>Uç noktalar sayfası

Bir web rolü genellikle bağlantı noktası 80 üzerinde tek bir HTTP bitiş noktası vardır. Diğer taraftan, bir alt rolünde herhangi bir sayıda HTTP, HTTPS veya TCP uç noktası olabilir. Uç noktalar, dış istemciler için kullanılabilen giriş uç noktaları veya hizmette çalışan diğer rolleriçin kullanılabilen dahili uç noktalar olabilir.

- Bir HTTP bitiş noktasını dış istemciler ve Web tarayıcıları için kullanılabilir hale getirmek için, bitiş noktası türünü girişe değiştirin ve bir ad ve ortak bağlantı noktası numarası belirtin.
- Bir HTTPS bitiş noktasını dış istemciler ve Web tarayıcıları için kullanılabilir hale getirmek için, bitiş noktası türünü **giriş ekiolarak**değiştirin ve bir ad, ortak bağlantı noktası numarası ve yönetim sertifikası adı belirtin. Yönetim sertifikası belirtemeden önce **sertifikaları Sertifikalar** özelliği sayfasında da tanımlamanız gerekir.
- Bulut hizmetindeki diğer rollertarafından dahili erişim için bir uç noktası kullanılabilir hale getirmek için, uç nokta türünü dahili olarak değiştirin ve bu bitiş noktası için bir ad ve olası özel bağlantı noktaları belirtin.

## <a name="local-storage-page"></a>Yerel depolama sayfası

Bir rol için bir veya daha fazla yerel depolama kaynağı ayırmak için **Yerel Depolama** özelliği sayfasını kullanabilirsiniz. Yerel depolama kaynağı, bir rolün bir örneğinin çalıştırıldığı Azure sanal makinesinin dosya sisteminde ayrılmış bir dizindir.

## <a name="certificates-page"></a>Sertifikalar sayfası

**Sertifikalar** özelliği sayfası, hizmet yapılandırmanıza sertifikalarınız hakkında bilgi ekler. Sertifikalarınızın hizmetinizle birlikte paketlenmemiş olduğunu unutmayın; sertifikalarınızı [Azure portalı](https://portal.azure.com)üzerinden Azure'a ayrı ayrı yüklemeniz gerekir.

Buraya sertifika eklemek, hizmet yapılandırmanıza sertifikalarınız hakkında bilgi ekler. Sertifikalar hizmetle birlikte paketlenmemiştir; sertifikalarınızı Azure portalı üzerinden ayrı olarak yüklemeniz gerekir.

Bir sertifikayı rolünüzle ilişkilendirmek için sertifika için bir ad sağlayın. **Bitiş Noktaları** sayfasında bir HTTPS bitiş noktası yapılandırDığınızda sertifikaya başvurmak için bu adı kullanırsınız. Ardından, sertifika deposunun **Yerel Makine** mi yoksa **Geçerli Kullanıcı** mı olduğunu ve mağazanın adını belirtin. Son olarak, sertifikanın parmak izini girin. Sertifika Geçerli Kullanıcı\Kişisel (Benim) mağazasındaysa, doldurulan bir listeden sertifikayı seçerek sertifikanın parmak izini girebilirsiniz. Başka bir konumda yaşıyorsa, parmak izi değerini elle girin.

Sertifika deposundan bir sertifika eklediğinizde, ara sertifikalar sizin için yapılandırma ayarlarına otomatik olarak eklenir. Ayrıca, ssl için hizmetinizi doğru şekilde yapılandırmak için bu ara sertifikaların Azure'a yüklenmesi gerekir.

Hizmetinizle ilişkilendirdiğiniz tüm yönetim sertifikaları, hizmetiniz için yalnızca bulutta çalışırken geçerlidir. Hizmetiniz yerel geliştirme ortamında çalışırken, bilgi işlem emülatörü tarafından yönetilen standart bir sertifika kullanır.
