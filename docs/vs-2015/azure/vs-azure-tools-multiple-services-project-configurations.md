---
title: Azure projenizi birden çok hizmet yapılandırması kullanarak yapılandırma | Microsoft Docs
description: ServiceDefinition. csdef, ServiceConfiguration. Local. cscfg ve ServiceConfiguration. Cloud. cscfg dosyalarını değiştirerek bir Azure bulut hizmeti projesini nasıl yapılandıracağınızı öğrenin.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 59996180661806eee60d18ab4b7b5fd26f4a2e7b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410063"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Visual Studio'da Azure projenizi birden çok hizmet yapılandırması kullanacak şekilde yapılandırma

Visual Studio 'da bir Azure bulut hizmeti projesi üç yapılandırma dosyası içerir: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg`ve `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef`, bulut hizmeti ve rollerinin gereksinimlerini ve tüm örneklere uygulanan ayarları sağlamak için Azure 'a dağıtılır. Azure hizmeti barındırma çalışma zamanı API 'SI kullanılarak çalışma zamanında ayarlar okunabilir. Bu dosya, Azure 'da yalnızca bulut hizmeti durdurulduğunda güncelleştirilir.
- `ServiceConfiguration.Local.cscfg` ve `ServiceConfiguration.Cloud.cscfg`, tanım dosyasındaki ayarlar için değerler sağlar ve her bir rol için çalıştırılacak örneklerin sayısını belirtir. "Yerel" dosya, yerel hata ayıklamada kullanılan değerleri içerir; "bulut" dosyası Azure 'a `ServiceConfiguration.cscfg` olarak dağıtılır ve sunucu ortamı için ayarlar sağlar. Bu dosya, bulut hizmetiniz Azure 'da çalışırken güncelleştirilemeyebilir.

Yapılandırma ayarları, geçerli rolün Özellik sayfaları kullanılarak Visual Studio 'da yönetilir ve değiştirilir (Role sağ tıklayıp **Özellikler**' i seçin ya da role çift tıklayın). Değişiklikler, **hizmet yapılandırması** açılır penceresinde hangi yapılandırmanın seçiltiğine göre kapsamlandırılır. Web ve çalışan rollerinin özellikleri, aşağıdaki bölümlerde açıklananlar dışında benzerdir.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Hizmet tanımı ve hizmet yapılandırma dosyaları için temel alınan şemalar hakkında daha fazla bilgi için, bkz [. CSDEF XML şeması](/azure/cloud-services/schema-csdef-file) ve [. cscfg XML şeması](/azure/cloud-services/schema-cscfg-file) makaleleri. Hizmet yapılandırması hakkında daha fazla bilgi için bkz. [nasıl yapılandırılır Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Yapılandırma sayfası

### <a name="service-configuration"></a>Hizmet yapılandırması

Değişikliklerden etkilenen `ServiceConfiguration.*.cscfg` dosyasını seçer. Varsayılan olarak, yerel ve bulut çeşitleri vardır ve yapılandırma dosyalarını kopyalamak, yeniden adlandırmak ve kaldırmak için **Yönet...** komutunu kullanabilirsiniz. Bu dosyalar, bulut hizmeti projenize eklenir ve **Çözüm Gezgini**görüntülenir. Ancak, yapılandırmaların yeniden adlandırılması veya kaldırılması yalnızca bu denetimden yapılabilir.

### <a name="instances"></a>Örnekler

**Örnek** sayısı özelliğini hizmetin bu rol için çalışması gereken örnek sayısına ayarlayın.

**VM boyutu** özelliğini **çok küçük**, **küçük**, **Orta**, **büyük**veya çok **büyük**olarak ayarlayın.  Daha fazla bilgi için bkz. [Bulut Hizmetlerinin Boyutları](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Başlangıç eylemi (yalnızca Web rolü)

Bu özelliği, Visual Studio 'Nun HTTP uç noktaları veya HTTPS uç noktaları için bir Web tarayıcısı başlatması gerektiğini belirtmek için veya hata ayıklamayı başlattığınızda her iki durumda da ayarlayın.

**Https uç noktası** seçeneği, yalnızca rolünüz IÇIN bir HTTPS uç noktası tanımladıysanız kullanılabilir. **Uç noktalar** Özellik SAYFASıNDA bir HTTPS uç noktası tanımlayabilirsiniz.

Zaten bir HTTPS uç noktası eklediyseniz, HTTPS uç noktası seçeneği varsayılan olarak etkindir ve Visual Studio, hata ayıklamaya başladığınızda, HTTP uç noktanızın bir tarayıcısına ek olarak, her iki başlatma seçeneğinin de etkinleştirildiğinden bu uç nokta için bir tarayıcı başlatır.

### <a name="diagnostics"></a>Tanılama

Varsayılan olarak, Web rolü için tanılama etkindir. Azure bulut hizmeti projesi ve depolama hesabı yerel depolama öykünücüsünü kullanacak şekilde ayarlanır. Azure 'a dağıtmaya hazırsanız, bunun yerine Azure Storage 'ı kullanmak için Oluşturucu düğmesini ( **...** ) seçebilirsiniz. Tanılama verilerini depolama hesabına isteğe bağlı olarak veya otomatik olarak zamanlanmış aralıklarla aktarabilirsiniz. Azure Tanılama hakkında daha fazla bilgi için bkz. [azure Cloud Services ve sanal makinelerde tanılamayı etkinleştirme](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Ayarlar sayfası

**Ayarlar** sayfasında bir yapılandırmaya ad-değer çiftleri olarak ayarlar ekleyebilirsiniz. Rol içinde çalışan kod, [Azure yönetilen Kitaplığı](/previous-versions/azure/dn602775(v=azure.11))tarafından sunulan sınıfları kullanarak çalışma zamanında yapılandırma ayarlarınızın değerlerini okuyabilir, özellikle [Getconfigurationsettingvalue](/previous-versions/azure/reference/ee772857(v=azure.100)) yöntemi.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Depolama hesabı için bağlantı dizesi yapılandırma

Bağlantı dizesi, depolama öykünücüsü veya bir Azure depolama hesabı için bağlantı ve kimlik doğrulama bilgileri sağlayan bir ayardır. Bir roldeki kod, Azure depolama (blob 'lar, kuyruklar veya tablolar) ile eriştiğinde bir bağlantı dizesine ihtiyaç duyuyor.

> [!Note]
> Azure depolama hesabı bağlantı dizesi tanımlı bir biçim kullanmalıdır (bkz. [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)).

Bağlantı dizesini, gerektiğinde yerel depolamayı kullanacak şekilde ayarlayabilir ve uygulamayı bulut hizmeti dağıtırken bir Azure depolama hesabına ayarlayabilirsiniz. Bağlantı dizesinin düzgün şekilde ayarlanamaması, rolünüzün başlamamasına veya başlatma, meşgul ve durdurma durumlarında geçiş yapılmasına neden olabilir.

Bir bağlantı dizesi oluşturmak için **Ayar ekle** ' yi seçin ve **türü** "bağlantı dizesi" olarak ayarlayın.

Yeni veya mevcut bağlantı dizeleri için... seçeneğini belirleyin **.** * **depolama bağlantı dizesi oluştur** iletişim kutusunu açmak için **değer** alanının sağında:

1. **Kullanarak bağlan**altında, aboneliğinizden bir depolama hesabı seçmek için **abonelik** seçeneğini belirleyin. Daha sonra Visual Studio, depolama hesabı kimlik bilgilerini `.publishsettings` dosyasından otomatik olarak alır.
1. **El ile girilen kimlik bilgilerinin** seçilmesi, Azure Portal bilgileri kullanarak doğrudan hesap adı ve anahtarı belirtmenize olanak tanır. Hesap anahtarını kopyalamak için:
    1. Azure portal depolama hesabına gidin ve **anahtarları Yönet**' i seçin.
    1. Hesap anahtarını kopyalamak için Azure portal depolama hesabına gidin, **ayarlar > erişim anahtarları**' nı seçin ve ardından Kopyala düğmesini kullanarak birincil erişim anahtarını panoya kopyalayın.
1. Bağlantı seçeneklerinden birini belirleyin. **Özel uç noktaları belirtin** , Bloblar, tablolar ve kuyruklar Için belirli URL 'leri belirtmenizi ister. Özel uç noktalar [özel etki alanlarını](/azure/storage/blobs/storage-custom-domain-name) kullanmanıza ve erişimi daha tam olarak denetlemenize olanak tanır. Bkz. [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string).
1. **Tamam**' ı ve ardından yeni bağlantı dizesiyle yapılandırmayı güncelleştirmek için **Dosya > Kaydet** ' i seçin.

Uygulamanızı Azure 'da yayımladığınızda, bağlantı dizesinin Azure Depolama hesabını içeren hizmet yapılandırmasını seçin. Uygulamanız yayımlandıktan sonra, uygulamanın Azure Storage hizmetlerinde beklendiği gibi çalıştığını doğrulayın.

Hizmet yapılandırmalarının nasıl güncelleştirilmesi hakkında daha fazla bilgi için bkz. [depolama hesapları için bağlantı dizelerini yönetme](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts)bölümü.

## <a name="endpoints-page"></a>Uç noktalar sayfası

Bir Web rolünün genellikle bağlantı noktası 80 üzerinde tek bir HTTP uç noktası vardır. Diğer yandan bir çalışan rolünün herhangi bir sayıda HTTP, HTTPS veya TCP uç noktası olabilir. Uç noktalar, dış istemciler için kullanılabilir olan giriş uç noktaları veya hizmette çalışan diğer roller için kullanılabilir iç uç noktalar olabilir.

- Bir HTTP uç noktasını dış istemciler ve Web tarayıcıları için kullanılabilir hale getirmek için, uç nokta türünü giriş olarak değiştirin ve bir ad ve genel bağlantı noktası numarası belirtin.
- HTTPS uç noktasını dış istemciler ve Web tarayıcıları için kullanılabilir hale getirmek için, uç nokta türünü **giriş**olarak değiştirin ve bir ad, genel bağlantı noktası numarası ve bir yönetim sertifikası adı belirtin. Ayrıca, bir yönetim sertifikası belirttıklamadan önce **Sertifikalar** Özellik sayfasında sertifikayı tanımlamanız gerekir.
- Bir uç noktayı bulut hizmetindeki diğer roller tarafından iç erişim için kullanılabilir hale getirmek için, uç nokta türünü iç olarak değiştirin ve bu uç nokta için bir ad ve olası özel bağlantı noktaları belirtin.

## <a name="local-storage-page"></a>Yerel depolama sayfası

Bir rol için bir veya daha fazla yerel depolama kaynağı ayırmak üzere **yerel depolama** özellik sayfasını kullanabilirsiniz. Yerel depolama kaynağı, bir rolün örneğinin çalıştırıldığı Azure sanal makinesinin dosya sistemindeki ayrılmış bir dizindir.

## <a name="certificates-page"></a>Sertifikalar sayfası

**Sertifikalar** Özellik sayfası, hizmet yapılandırmanıza sertifikalarınızı hakkında bilgi ekler. Sertifikalarınızın hizmetinize paketlenmemiş olduğunu unutmayın; [Azure Portal](https://portal.azure.com)aracılığıyla sertifikalarınızı Azure 'a ayrı olarak yüklemeniz gerekir.

Buraya bir sertifika eklendiğinde, hizmet yapılandırmanıza sertifikanız hakkında bilgiler eklenir. Sertifikalar, hizmetle paketlenmez; sertifikalarınızı Azure portal aracılığıyla ayrı olarak yüklemeniz gerekir.

Bir sertifikayı rolünüzün ilişkilendirilmesi için, sertifika için bir ad sağlayın. Bu adı, **uç noktalar** SAYFASıNDA bir HTTPS uç noktası yapılandırdığınızda sertifikaya başvurmak için kullanırsınız. Ardından, sertifika deposunun **yerel makine** mı yoksa **Geçerli Kullanıcı** ve deponun adı mı olduğunu belirtin. Son olarak, sertifikanın parmak izini girin. Sertifika geçerli User\Personal (My) depolduysa, doldurulmuş bir listeden sertifikayı seçerek sertifikanın parmak izini girebilirsiniz. Başka bir konumda yer alıyorsa, parmak izi değerini el ile girin.

Sertifika deposundan bir sertifika eklediğinizde, tüm ara sertifikalar sizin için yapılandırma ayarlarına otomatik olarak eklenir. Ayrıca, bu ara sertifikaların, hizmetinizi SSL için doğru şekilde yapılandırması için Azure 'a yüklenmesi gerekir.

Hizmetinize ilişkilendirdiğiniz tüm yönetim sertifikaları hizmetinize yalnızca bulutta çalışırken uygulanır. Hizmetiniz yerel geliştirme ortamında çalışırken, işlem öykünücüsü tarafından yönetilen standart bir sertifika kullanır.
