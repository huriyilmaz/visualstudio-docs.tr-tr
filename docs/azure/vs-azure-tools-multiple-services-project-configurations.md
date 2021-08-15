---
title: Bulut hizmetini birden çok yapılandırmayla yapılandırma
description: ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg ve ServiceConfiguration.Cloud.cscfg dosyalarını değiştirerek bir Azure bulut hizmeti projesini yapılandırmayı öğrenin.
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

Azure'daki bir Azure bulut Visual Studio üç yapılandırma dosyası içerir: `ServiceDefinition.csdef` `ServiceConfiguration.Local.cscfg` , ve `ServiceConfiguration.Cloud.cscfg` :

- `ServiceDefinition.csdef` , bulut hizmetinin ve rollerinin gereksinimlerini açıklamak ve tüm örnekler için geçerli olan ayarları sağlamak için Azure'a dağıtılır. Ayarlar Azure Hizmet Barındırma Çalışma Zamanı API'si kullanılarak çalışma zamanında okunabilir. Bu dosya Yalnızca bulut hizmeti durdurulurken Azure'da güncelleştirilebilir.
- `ServiceConfiguration.Local.cscfg` ve `ServiceConfiguration.Cloud.cscfg` tanım dosyasındaki ayarlar için değerler sağlar ve her rol için çalıştıracak örnek sayısını belirtir. "Yerel" dosyası yerel hata ayıklamada kullanılan değerleri içerir; "Bulut" dosyası olarak Azure'a dağıtılır `ServiceConfiguration.cscfg` ve sunucu ortamı için ayarlar sağlar. Bulut hizmetiniz Azure'da çalışırken bu dosya güncelleştirilebilir.

Yapılandırma ayarları, geçerli Visual Studio özellik sayfaları kullanılarak yönetiliyor ve değiştiriliyor (role sağ tıklayın ve **Özellikler'i seçin** veya role çift tıklayın). Değişikliklerin kapsamı Hizmet Yapılandırması açılan listesinde hangi yapılandırma **seçilirse seçilmelidir.** Web ve çalışan rollerinin özellikleri, aşağıdaki bölümlerde açıklananlar dışında benzerdir.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Hizmet tanımı ve hizmet yapılandırma dosyaları için temel alınan şemalar hakkında bilgi için [.csdef XML Şeması](/azure/cloud-services/schema-csdef-file) ve [.cscfg XML Şeması makalelerini](/azure/cloud-services/schema-cscfg-file) okuyun. Hizmet yapılandırması hakkında daha fazla bilgi için, [bkz. How to Configure Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Yapılandırma sayfası

### <a name="service-configuration"></a>Hizmet Yapılandırması

Değişikliklerden `ServiceConfiguration.*.cscfg` hangi dosyanın etkilendiğini seçer. Varsayılan olarak, Yerel ve Bulut çeşitlemeleri vardır ve yapılandırma dosyalarını kopyalamak, yeniden adlandırmak ve kaldırmak için **Yönet...** komutunu kullanabilirsiniz. Bu dosyalar bulut hizmeti projenize eklenir ve **Çözüm Gezgini.** Ancak, yapılandırmaları yeniden yeniden ifade etmek veya kaldırmak yalnızca bu denetimden yapılabilir.

### <a name="instances"></a>Örnekler

Örnek **sayısı** özelliğini, hizmetin bu rol için çalıştırması gereken örnek sayısı olarak ayarlayın.

VM boyutu **özelliğini Çok** Küçük, **Küçük,** **Orta,** **Büyük** veya **Çok Büyük** **olarak ayarlayın.**  Daha fazla bilgi için bkz. [Bulut Hizmetlerinin Boyutları](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Başlangıç Eylemi (yalnızca Web rolü)

Hata ayıklamaya başlarken http Visual Studio veya HTTPS uç noktaları için bir web tarayıcısı başlatmanız gerektiğini belirtmek için bu özelliği ayarlayın.

**HTTPS uç noktası** seçeneği yalnızca rolünüz için zaten bir HTTPS uç noktası tanımladıysanız kullanılabilir. Uç noktalar özellik sayfasında bir HTTPS **uç noktası** tanımlayabilirsiniz.

Zaten bir HTTPS uç noktası eklediyseniz HTTPS uç noktası seçeneği varsayılan olarak etkinleştirilir ve Visual Studio, her iki başlatma seçeneğinin de etkinleştirildiğinde HTTP uç noktanız için bir tarayıcıya ek olarak hata ayıklamaya başlarken bu uç nokta için bir tarayıcı başlatıyor.

### <a name="diagnostics"></a>Tanılama

Tanılama varsayılan olarak Web rolü için etkindir. Azure bulut hizmeti projesi ve depolama hesabı, yerel depolama öykünücüsünü kullanmak üzere ayarlanır. Azure'a dağıtmaya hazır olduğunda, bunun yerine Oluşturucu düğmesini (**...**) seçerek Azure depolamayı kullanabilirsiniz. Tanılama verilerini isteğe bağlı olarak veya otomatik olarak zamanlanmış aralıklarla depolama hesabına aktarabilirsiniz. Azure tanılaması hakkında daha fazla bilgi için bkz. Azure Cloud Services [ve Sanal Makinelerde Tanılamayı Etkinleştirme.](/azure/cloud-services/cloud-services-dotnet-diagnostics)

## <a name="settings-page"></a>Ayarlar sayfası

Yapılandırma **Ayarlar,** yapılandırmaya ad-değer çiftleri olarak ayarlar ekleyebilirsiniz. Rolde çalışan kod, özellikle [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) yöntemi olmak üzere [Azure Yönetilen](/previous-versions/azure/dn602775(v=azure.11))Kitaplığı tarafından sağlanan sınıfları kullanarak çalışma zamanında yapılandırma ayarlarınızın değerlerini okuyabilir.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Depolama hesabı için bağlantı dizesi yapılandırma

Bağlantı dizesi, depolama öykünücüsü veya Azure depolama hesabı için bağlantı ve kimlik doğrulama bilgileri sağlayan bir ayardır. Rolde yer alan kodun Azure depolamaya (bloblar, kuyruklar veya tablolar) her erişmesi için bir bağlantı dizesi gerekir.

> [!Note]
> Azure depolama hesabı için bağlantı dizesi tanımlı bir biçim kullanlanmalıdır (bkz. Azure Depolama [Dizelerini Yapılandırma).](/azure/storage/common/storage-configure-connection-string)

Bağlantı dizesini gerektiğinde yerel depolamayı kullanmak üzere, sonra uygulamayı bulut hizmetine dağıtırken bir Azure depolama hesabı olarak ayarlayın. Bağlantı dizesinin düzgün ayarlanmaması, rolünüz başlamama veya başlatma, meşgul ve durdurma durumlarını döngüye alamanıza neden olabilir.

Bağlantı dizesi oluşturmak için Ayar **Ekle'yi seçin ve** Tür'i **"Bağlantı** Dizesi" olarak ayarlayın.

Yeni veya mevcut bağlantı dizeleri için **...** _ _ Değer * alanı sağ *tarafından* Bağlantı Dizesi Oluştur **iletişim Depolama açın:**

1. Kullanarak **Bağlan altında** **Aboneliğiniz seçeneğini belirleyin** ve abonelikten bir depolama hesabı seçin. Visual Studio depolama hesabı kimlik bilgilerini otomatik olarak dosyadan `.publishsettings` edinebilirsiniz.
1. El ile **girilen kimlik bilgileri'nin** seçerek hesap adını ve anahtarını doğrudan hesaptan gelen bilgileri Azure portal. Hesap anahtarını kopyalamak için:
    1. Depolama hesabı üzerinde depolama hesabına gidin ve Azure portal **Yönet'i seçin.**
    1. Hesap anahtarını kopyalamak için, Azure portal depolama hesabına gidin, Ayarlar > anahtarları'Ayarlar > **seçin,** ardından kopyala düğmesini kullanarak birincil erişim anahtarını panoya kopyalayın.
1. Bağlantı seçenekleriden birini belirleyin. **Özel uç noktaları belirtin,** bloblar, tablolar ve kuyruklar için belirli URL'ler belirtmenizi sorar. Özel uç noktalar, özel etki alanlarını [kullanmanızı ve erişimi](/azure/storage/blobs/storage-custom-domain-name) tam olarak denetlemenizi sağlar. Bkz. [Azure Depolama Dizelerini Yapılandırma.](/azure/storage/common/storage-configure-connection-string)
1. Yapılandırmayı **yeni** bağlantı **dizesiyle > için** Tamam'ı ve ardından Dosya Kaydet'i seçin.

Yine, uygulamanızı Azure'da yayımlasanız, bağlantı dizesi için Azure depolama hesabını içeren hizmet yapılandırmasını seçin. Uygulamanız yayımlandıktan sonra, uygulamanın Azure depolama hizmetlerinde beklendiği gibi çalıştığını doğrulayın.

Hizmet yapılandırmalarını güncelleştirme hakkında daha fazla bilgi için Depolama hesapları için [bağlantı dizelerini yönetme bölümüne bakın.](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts)

## <a name="endpoints-page"></a>Uç noktalar sayfası

Web rolü genellikle 80 bağlantı noktası üzerinde tek bir HTTP uç noktasına sahiptir. Öte yandan bir çalışan rolü herhangi bir sayıda HTTP, HTTPS veya TCP uç noktasına sahip olabilir. Uç noktalar, dış istemciler tarafından kullanılabilen giriş uç noktaları veya hizmette çalışan diğer roller tarafından kullanılabilen iç uç noktalar olabilir.

- Bir HTTP uç noktasını dış istemciler ve Web tarayıcıları için kullanılabilir yapmak için uç nokta türünü giriş olarak değiştirerek bir ad ve ortak bağlantı noktası numarası belirtin.
- Bir HTTPS uç noktasını dış istemciler ve Web tarayıcıları için kullanılabilir yapmak için, uç nokta türünü girdi olarak değiştirerek bir ad, ortak bağlantı noktası numarası ve bir yönetim sertifikası adı belirtin. Bir yönetim sertifikası belirtemeden önce **sertifikayı** Sertifikalar özellik sayfasında da tanımlamanız gerekir.
- Bir uç noktayı bulut hizmette diğer roller tarafından iç erişim için kullanılabilir yapmak için, uç nokta türünü iç olarak değiştirebilir ve bu uç nokta için bir ad ve olası özel bağlantı noktaları belirtin.

## <a name="local-storage-page"></a>Yerel depolama sayfası

Yerel depolama Depolama **sayfasını** kullanarak bir rol için bir veya daha fazla yerel depolama kaynağı yedekleyebilirsiniz. Yerel depolama kaynağı, azure sanal makinesinin dosya sistemi içinde bir rol örneğinin çalıştır olduğu ayrılmış bir dizindir.

## <a name="certificates-page"></a>Sertifikalar sayfası

Sertifikalar **özellik** sayfası, hizmet yapılandırmanıza sertifikalarınız hakkında bilgi ekler. Sertifikalarınız hizmetinize paketli değildir; sertifikalarınızı azure'a sertifikalarınızı azure'a [Azure portal.](https://portal.azure.com)

Buraya bir sertifika eklemek, sertifikalar hakkında bilgi ekleyerek hizmet yapılandırmanıza ekler. Sertifikalar hizmetle paketlanmaz; Sertifikalarınızı sertifikalar aracılığıyla ayrı olarak karşıya Azure portal.

Bir sertifikayı rolünüzle ilişkilendirmek için sertifika için bir ad girin. Uç noktalar sayfasında bir HTTPS uç noktası yapılandırıldığında sertifikaya başvurmak için bu **adı kullanırsiniz.** Ardından, sertifika deposun Yerel Makine mi **yoksa Geçerli** **Kullanıcı mı olduğunu ve** depo adını belirtin. Son olarak sertifikanın parmak izini girin. Sertifika Geçerli Kullanıcı\Kişisel (My) depolamada ise, doldurulmuş bir listeden sertifikayı seçerek sertifikanın parmak izini girebilirsiniz. Başka bir konumda yer alan parmak izi değerini el ile girin.

Sertifika depolamadan bir sertifika eklerken, tüm ara sertifikalar sizin için yapılandırma ayarlarına otomatik olarak eklenir. Ayrıca, hizmetinizi SSL için doğru şekilde yapılandırmak için bu ara sertifikaların Azure'a yüklenmeleri gerekir.

Hizmetiniz ile ilişkilendirmeniz gereken tüm yönetim sertifikaları, yalnızca bulutta çalıştır çalıştır durumdayken hizmetinize uygulanır. Hizmetiniz yerel geliştirme ortamında çalışıyorsa, işlem öykünücüsü tarafından yönetilen standart bir sertifika kullanır.
