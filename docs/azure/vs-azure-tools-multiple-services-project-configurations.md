---
title: Bulut hizmetini birden çok yapılandırmayla yapılandırma
description: ServiceDefinition. csdef, ServiceConfiguration. Local. cscfg ve ServiceConfiguration. Cloud. cscfg dosyalarını değiştirerek bir Azure bulut hizmeti projesini nasıl yapılandıracağınızı öğrenin.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 7d2c0c7e54bb57f199579716499ee02901ae58c16dadf773dc4e5513bb28484d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348759"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Visual Studio'da Azure projenizi birden çok hizmet yapılandırması kullanacak şekilde yapılandırma

Visual Studio bir Azure bulut hizmeti projesi üç yapılandırma dosyası içerir: `ServiceDefinition.csdef` , `ServiceConfiguration.Local.cscfg` ve `ServiceConfiguration.Cloud.cscfg` :

- `ServiceDefinition.csdef` , bulut hizmeti ve rollerinin gereksinimlerini ve tüm örneklere uygulanan ayarları sağlamak üzere Azure 'a dağıtılır. Ayarlar, Azure hizmeti barındırma çalışma zamanı apı 'si kullanılarak çalışma zamanında okunabilir. Bu dosya, Azure 'da yalnızca bulut hizmeti durdurulduğunda güncelleştirilir.
- `ServiceConfiguration.Local.cscfg` ve `ServiceConfiguration.Cloud.cscfg` tanım dosyasındaki ayarlar için değerler sağlayın ve her bir rol için çalıştırılacak örneklerin sayısını belirtin. "Yerel" dosya, yerel hata ayıklamada kullanılan değerleri içerir; "bulut" dosyası Azure 'a olarak dağıtılır `ServiceConfiguration.cscfg` ve sunucu ortamı için ayarları sağlar. Bu dosya, bulut hizmetiniz Azure 'da çalışırken güncelleştirilemeyebilir.

yapılandırma ayarları, uygulanabilir rolün özellik sayfaları kullanılarak Visual Studio yönetilir ve değiştirilir (role sağ tıklayıp **özellikler**' i seçin ya da role çift tıklayın). Değişiklikler, **hizmet yapılandırması** açılır penceresinde hangi yapılandırmanın seçiltiğine göre kapsamlandırılır. Web ve çalışan rollerinin özellikleri, aşağıdaki bölümlerde açıklananlar dışında benzerdir.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Hizmet tanımı ve hizmet yapılandırma dosyaları için temel alınan şemalar hakkında daha fazla bilgi için, bkz [.. CSDEF XML şeması](/azure/cloud-services/schema-csdef-file) ve [. cscfg XML şeması](/azure/cloud-services/schema-cscfg-file) makaleleri. Hizmet yapılandırması hakkında daha fazla bilgi için bkz. [nasıl yapılandırılır Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Yapılandırma sayfası

### <a name="service-configuration"></a>Hizmet yapılandırması

Hangi `ServiceConfiguration.*.cscfg` dosyanın değişikliklerden etkilendiğini seçer. Varsayılan olarak, yerel ve bulut çeşitleri vardır ve yapılandırma dosyalarını kopyalamak, yeniden adlandırmak ve kaldırmak için **Yönet...** komutunu kullanabilirsiniz. Bu dosyalar, bulut hizmeti projenize eklenir ve **Çözüm Gezgini** görüntülenir. Ancak, yapılandırmaların yeniden adlandırılması veya kaldırılması yalnızca bu denetimden yapılabilir.

### <a name="instances"></a>Örnekler

**Örnek** sayısı özelliğini hizmetin bu rol için çalışması gereken örnek sayısına ayarlayın.

**VM boyutu** özelliğini **çok küçük**, **küçük**, **Orta**, **büyük** veya çok **büyük** olarak ayarlayın.  Daha fazla bilgi için bkz. [Bulut Hizmetlerinin Boyutları](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Başlangıç eylemi (yalnızca Web rolü)

bu özelliği, Visual Studio HTTP uç noktaları veya HTTPS uç noktaları için bir web tarayıcısı ya da hata ayıklamayı başlattığınızda her ikisi için de başlatması gerektiğini belirtmek için ayarlayın.

**Https uç noktası** seçeneği, yalnızca rolünüz IÇIN bir HTTPS uç noktası tanımladıysanız kullanılabilir. **Uç noktalar** Özellik SAYFASıNDA bir HTTPS uç noktası tanımlayabilirsiniz.

zaten bir https uç noktası eklediyseniz, https uç noktası seçeneği varsayılan olarak etkindir ve hata ayıklamayı başlattığınızda, her iki başlatma seçeneğinin etkin olduğu varsayıldığında, HTTP uç noktası için bir tarayıcıya ek olarak, bu uç nokta için bir tarayıcı başlatır Visual Studio.

### <a name="diagnostics"></a>Tanılama

Varsayılan olarak, Web rolü için tanılama etkindir. Azure bulut hizmeti projesi ve depolama hesabı yerel depolama öykünücüsünü kullanacak şekilde ayarlanır. Azure 'a dağıtmaya hazırsanız, bunun yerine Azure Storage 'ı kullanmak için Oluşturucu düğmesini (**...**) seçebilirsiniz. Tanılama verilerini depolama hesabına isteğe bağlı olarak veya otomatik olarak zamanlanmış aralıklarla aktarabilirsiniz. Azure Tanılama hakkında daha fazla bilgi için bkz. [azure Cloud Services ve sanal makinelerde tanılamayı etkinleştirme](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Ayarlar sayfası

**Ayarlar** sayfasında, yapılandırmaya ad-değer çiftleri olarak ayarlar ekleyebilirsiniz. Rol içinde çalışan kod, [Azure yönetilen Kitaplığı](/previous-versions/azure/dn602775(v=azure.11))tarafından sunulan sınıfları (özellikle [Getconfigurationsettingvalue](/previous-versions/azure/reference/ee772857(v=azure.100)) yöntemi) kullanarak çalışma zamanında yapılandırma ayarlarınızın değerlerini okuyabilir.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Depolama hesabı için bağlantı dizesi yapılandırma

Bağlantı dizesi, depolama öykünücüsü veya bir Azure depolama hesabı için bağlantı ve kimlik doğrulama bilgileri sağlayan bir ayardır. Bir roldeki kod, Azure depolama (blob 'lar, kuyruklar veya tablolar) ile eriştiğinde bir bağlantı dizesine ihtiyaç duyuyor.

> [!Note]
> azure depolama hesabı için bir bağlantı dizesinde tanımlı bir biçim kullanılmalıdır (bkz. [azure Depolama bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)).

Bağlantı dizesini, gerektiğinde yerel depolamayı kullanacak şekilde ayarlayabilir ve uygulamayı bulut hizmeti dağıtırken bir Azure depolama hesabına ayarlayabilirsiniz. Bağlantı dizesinin düzgün şekilde ayarlanamaması, rolünüzün başlamamasına veya başlatma, meşgul ve durdurma durumlarında geçiş yapılmasına neden olabilir.

Bir bağlantı dizesi oluşturmak için **Ayar ekle** ' yi seçin ve **türü** "bağlantı dizesi" olarak ayarlayın.

Yeni veya mevcut bağlantı dizeleri için... seçeneğini belirleyin **.** _ *değer** alanının sağ tarafındaki _. **Depolama bağlantı dizesi oluştur** iletişim kutusunu açmak için:

1. **Bağlan kullanarak**, aboneliğinizden bir depolama hesabı seçmek için **abonelik** seçeneğini belirleyin. Visual Studio daha sonra depolama hesabı kimlik bilgilerini dosyadan otomatik olarak alır `.publishsettings` .
1. **El ile girilen kimlik bilgilerinin** seçilmesi, Azure Portal bilgileri kullanarak doğrudan hesap adı ve anahtarı belirtmenize olanak tanır. Hesap anahtarını kopyalamak için:
    1. Azure portal depolama hesabına gidin ve **anahtarları Yönet**' i seçin.
    1. hesap anahtarını kopyalamak için Azure portal depolama hesabına gidin, **Ayarlar > erişim anahtarları**' nı seçin ve ardından kopyala düğmesini kullanarak birincil erişim anahtarını panoya kopyalayın.
1. Bağlantı seçeneklerinden birini belirleyin. **Özel uç noktaları belirtin** , Bloblar, tablolar ve kuyruklar Için belirli URL 'leri belirtmenizi ister. Özel uç noktalar [özel etki alanlarını](/azure/storage/blobs/storage-custom-domain-name) kullanmanıza ve erişimi daha tam olarak denetlemenize olanak tanır. bkz. [Azure Depolama bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string).
1. **Tamam**' ı ve ardından yeni bağlantı dizesiyle yapılandırmayı güncelleştirmek için **Dosya > kaydet** ' i seçin.

Uygulamanızı Azure 'da yayımladığınızda, bağlantı dizesinin Azure Depolama hesabını içeren hizmet yapılandırmasını seçin. Uygulamanız yayımlandıktan sonra, uygulamanın Azure Storage hizmetlerinde beklendiği gibi çalıştığını doğrulayın.

Hizmet yapılandırmalarının nasıl güncelleştirilmesi hakkında daha fazla bilgi için bkz. [depolama hesapları için bağlantı dizelerini yönetme](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts)bölümü.

## <a name="endpoints-page"></a>Uç noktalar sayfası

Bir Web rolünün genellikle bağlantı noktası 80 üzerinde tek bir HTTP uç noktası vardır. Diğer yandan bir çalışan rolünün herhangi bir sayıda HTTP, HTTPS veya TCP uç noktası olabilir. Uç noktalar, dış istemciler için kullanılabilir olan giriş uç noktaları veya hizmette çalışan diğer roller için kullanılabilir iç uç noktalar olabilir.

- Bir HTTP uç noktasını dış istemciler ve Web tarayıcıları için kullanılabilir hale getirmek için, uç nokta türünü giriş olarak değiştirin ve bir ad ve genel bağlantı noktası numarası belirtin.
- HTTPS uç noktasını dış istemciler ve Web tarayıcıları için kullanılabilir hale getirmek için, uç nokta türünü **giriş** olarak değiştirin ve bir ad, genel bağlantı noktası numarası ve bir yönetim sertifikası adı belirtin. Ayrıca, bir yönetim sertifikası belirttıklamadan önce **Sertifikalar** Özellik sayfasında sertifikayı tanımlamanız gerekir.
- Bir uç noktayı bulut hizmetindeki diğer roller tarafından iç erişim için kullanılabilir hale getirmek için, uç nokta türünü iç olarak değiştirin ve bu uç nokta için bir ad ve olası özel bağlantı noktaları belirtin.

## <a name="local-storage-page"></a>Yerel depolama sayfası

bir rol için bir veya daha fazla yerel depolama kaynağı ayırmak üzere **yerel Depolama** özellik sayfasını kullanabilirsiniz. Yerel depolama kaynağı, bir rolün örneğinin çalıştırıldığı Azure sanal makinesinin dosya sistemindeki ayrılmış bir dizindir.

## <a name="certificates-page"></a>Sertifikalar sayfası

**Sertifikalar** Özellik sayfası, hizmet yapılandırmanıza sertifikalarınızı hakkında bilgi ekler. Sertifikalarınızın hizmetinize paketlenmemiş olduğunu unutmayın; [Azure Portal](https://portal.azure.com)aracılığıyla sertifikalarınızı Azure 'a ayrı olarak yüklemeniz gerekir.

Buraya bir sertifika eklendiğinde, hizmet yapılandırmanıza sertifikanız hakkında bilgiler eklenir. Sertifikalar, hizmetle paketlenmez; sertifikalarınızı Azure portal aracılığıyla ayrı olarak yüklemeniz gerekir.

Bir sertifikayı rolünüzün ilişkilendirilmesi için, sertifika için bir ad sağlayın. Bu adı, **uç noktalar** SAYFASıNDA bir HTTPS uç noktası yapılandırdığınızda sertifikaya başvurmak için kullanırsınız. Ardından, sertifika deposunun **yerel makine** mı yoksa **Geçerli Kullanıcı** ve deponun adı mı olduğunu belirtin. Son olarak, sertifikanın parmak izini girin. Sertifika geçerli User\Personal (My) depolduysa, doldurulmuş bir listeden sertifikayı seçerek sertifikanın parmak izini girebilirsiniz. Başka bir konumda yer alıyorsa, parmak izi değerini el ile girin.

Sertifika deposundan bir sertifika eklediğinizde, tüm ara sertifikalar sizin için yapılandırma ayarlarına otomatik olarak eklenir. Ayrıca, bu ara sertifikaların, hizmetinizi SSL için doğru şekilde yapılandırması için Azure 'a yüklenmesi gerekir.

Hizmetinize ilişkilendirdiğiniz tüm yönetim sertifikaları hizmetinize yalnızca bulutta çalışırken uygulanır. Hizmetiniz yerel geliştirme ortamında çalışırken, işlem öykünücüsü tarafından yönetilen standart bir sertifika kullanır.
