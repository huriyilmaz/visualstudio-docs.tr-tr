---
title: 'Nasıl yapılır: kaynak denetimi eklentisi yüklemesi | Microsoft Docs'
description: kaynak denetimi eklentisini Visual Studio kaynak denetimi eklentisi apı 'siyle tümleştirerek ve DLL 'sini kaydederek Visual Studio nasıl yükleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c1f491bdbf1b27c19f324c2cbee076cb8f9124f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042445"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Nasıl yapılır: kaynak denetimi eklentisi yüklemesi
Kaynak denetimi eklentisi oluşturma üç adımdan oluşur:

1. Bu belgenin kaynak denetimi eklentisi API Başvurusu bölümünde tanımlanan işlevlerle bir DLL oluşturun.

2. Kaynak denetimi eklentisi API tanımlı işlevlerini uygulayın. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Bu, için çağrı yaparken, arabirimleri ve iletişim kutularını eklentiyle kullanılabilir hale getirin.

3. Uygun kayıt defteri girdilerini yaparak DLL 'yi kaydettirin.

## <a name="integration-with-visual-studio"></a>Visual Studio ile Tümleştirme
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kaynak denetimi eklentisi API 'sine uygun kaynak denetimi eklentilerini destekler.

### <a name="register-the-source-control-plug-in"></a>Kaynak denetimi eklentisini kaydetme
 Çalışan bir tümleşik geliştirme ortamı (IDE) kaynak denetim sistemine çağrı yapmadan önce, önce API 'YI dışarı aktaran kaynak denetimi eklentisi DLL 'sini bulmalıdır.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Kaynak denetimi eklentisi DLL 'sini kaydetmek için

1. Şirket adı alt anahtarını ve ardından ürün adı alt anahtarınızı belirten **yazılım** alt anahtarındaki **HKEY_LOCAL_MACHINE** anahtarı altına iki giriş ekleyin. Model **\\ \<company name>HKEY_LOCAL_MACHINE\SOFTWARE\\ \<product name> değerdir \\ . \<entry>**  =   İki giriş her zaman **SccServerName** ve **SccServerPath** olarak adlandırılır. Her biri normal bir dizedir.

    Örneğin, şirketinizin adı Microsoft ise ve kaynak denetimi ürününüz SourceSafe olarak adlandırılmışsa, bu kayıt defteri yolu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe** olacaktır. Bu alt anahtarda, **SccServerName** ilk girdisi, ürününüzü adlandırırken Kullanıcı tarafından okunabilen bir dizedir. İkinci girdi, **SccServerPath**, IDE 'nin bağlanması gereken kaynak denetim eklentisi dll 'inin tam yoludur. Aşağıda örnek kayıt defteri girdileri verilmiştir:

   |Örnek kayıt defteri girdisi|Örnek değer|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath, SourceSafe eklentisinin tam yoludur. Kaynak denetimi eklentiniz farklı şirket ve ürün adlarını, ancak aynı kayıt defteri giriş yollarını kullanacaktır.

2. Aşağıdaki isteğe bağlı kayıt defteri girdileri, kaynak denetimi eklentisinin davranışını değiştirmek için kullanılabilir. Bu girişler **SccServerName** ve **SccServerPath** ile aynı alt anahtara gider.

   - **HideInVisualStudioregistry** girişi, kaynak denetimi eklentisinin ' ın **eklenti seçim** listesinde görünmesini istemiyorsanız kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu giriş, kaynak denetimi eklentisine otomatik değiştirmeyi de etkileyecektir. Bu giriş için olası bir kullanım, kaynak denetimi eklentisinin yerini alan bir kaynak denetimi paketi sağlarsanız ancak kullanıcının kaynak denetimi eklentisini kaynak denetimi paketine kullanmasını kolaylaştırmak istiyorsanız. Kaynak denetim paketi yüklendiğinde, eklentiyi gizleyen bu kayıt defteri girişini ayarlar.

      **HideInVisualStudio** bir DWORD değeridir ve eklentiyi gizlemek için *1* , eklentiyi göstermek için *0* olarak ayarlanır. Kayıt defteri girdisi görünmezse, eklentiyi göstermek varsayılan davranış olur.

   - **DisableSccManager** kayıt defteri girişi, normalde **Dosya** **\<Source Control Server>**  >  **kaynağı denetim** alt menüsünde görüntülenen başlatma menüsü seçeneğini devre dışı bırakmak veya gizlemek için kullanılabilir. Bu menü seçeneğinin belirlenmesi [SccRunScc](../../extensibility/sccrunscc-function.md) işlevini çağırır. Kaynak denetimi eklentiniz bir dış programı desteklemeyebilir, bu nedenle **başlatma** menüsü seçeneğini devre dışı bırakmak veya hatta gizlemek isteyebilirsiniz.

      **DisableSccManager** bir DWORD değeridir ve **Başlat \<Source Control Server>** menüsü seçeneğini etkinleştirmek için *0* olarak ayarlanır, menü seçeneğini devre dışı bırakmak için *1* olarak ayarlayın ve menü seçeneğini gizlemek için *2* olarak ayarlayın. Bu kayıt defteri girdisi görünmezse, varsayılan davranış menü seçeneğini gösterir.

   | Örnek kayıt defteri girdisi | Örnek değer |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. **SourceCodeControlProvider** alt anahtarını, **yazılım** alt anahtarındaki **HKEY_LOCAL_MACHINE** anahtarı altına ekleyin.

    Bu alt anahtar altında, **ProviderRegKey** kayıt defteri girdisi, 1. adımdaki kayıt defterine yerleştirdiğiniz alt anahtarı temsil eden bir dizeye ayarlanır. Bu model **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey**  =  *yazılım \\<şirket adı \> \\<ürün adı \>*' dır.

    Bu alt anahtar için örnek içerik aşağıda verilmiştir.

   |Kayıt defteri girdisi|Örnek değer|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Kaynak denetimi eklentiniz aynı alt anahtarı ve giriş adlarını kullanacaktır, ancak değer farklı olacaktır.

4. **SourceCodeControlProvider** alt anahtarı altında **ınstalınstalınstaltıcode** adlı bir alt anahtar oluşturun ve ardından bu alt anahtarın altına bir giriş koyun.

    Bu girdinin adı, sağlayıcının kullanıcı tarafından okunabilen adıdır (SCCServerName girişi için belirtilen değerle aynıdır) ve değer, tekrar, 1. adımda oluşturulan alt anahtar. Bu model, **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\ görünen adı \>**  =  *yazılım \\<şirket adı \> \\<ürün adı \>*<.

    Örnek:

   |Örnek kayıt defteri girdisi|Örnek değer|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Bu şekilde kayıtlı birden fazla kaynak denetimi eklentisi olabilir. Bu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tüm yüklü kaynak denetimi EKLENTISI API tabanlı eklentileri bulur.

## <a name="how-an-ide-locates-the-dll"></a>IDE 'nin DLL 'yi nasıl konumlandırır
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 'nin kaynak denetimi EKLENTISI dll 'sini bulmanın iki yolu vardır:

- Varsayılan kaynak denetimi eklentisini bulun ve sessizce bu eklentiyi bağlayın.

- Kullanıcının bir tane seçtiği tüm kayıtlı kaynak denetim eklentilerini bulun.

  DLL 'yi birinci şekilde bulmak için IDE, **ProviderRegKey** girişinin **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** alt anahtarına bakar. Bu girdinin değeri başka bir alt anahtara işaret eder. Daha sonra IDE, **HKEY_LOCAL_MACHINE** altında bu ikinci alt anahtarda **SccServerPath** adlı bir giriş arar. Bu girdinin değeri, IDE 'yi DLL 'ye yönlendirir.

> [!NOTE]
> IDE, göreli yollardan dll 'Leri yüklemez (örneğin, *.\NewProvider.DLL*). DLL 'nin tam yolu belirtilmelidir (örneğin, *c:\Providers\NewProvider.DLL*). Bu, yetkisiz veya kimliğine bürünülen eklenti dll 'lerinin yüklenmesini önleyecek şekilde IDE 'nin güvenliğini güçlendirir.

 DLL 'yi ikinci şekilde bulmak için, IDE tüm girdilerin **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** alt anahtarına bakar. Her girdinin bir adı ve değeri vardır. IDE, kullanıcıya bu adların bir listesini görüntüler. Kullanıcı bir ad seçtiğinde, IDE bir alt anahtara işaret eden seçili ad için değeri bulur. IDE, **HKEY_LOCAL_MACHINE** altında bu alt anahtarda **SccServerPath** adlı bir giriş arar. Bu girdinin değeri, IDE 'yi doğru DLL 'ye yönlendirir.

 Kaynak denetimi eklentisinin, DLL 'yi bulmanın her iki yolunu desteklemesi gerekir ve sonuç olarak, önceki ayarların üzerine yazarak **ProviderRegKey**' i ayarlar. Daha da önemlisi, kullanıcının hangi kaynak denetimi eklentisinin kullanılacağını tercih etabilmesi için kendisini **ınstalınstalınstalınstaletnbulunan Sccproviders** listesine eklemesi gerekir.

> [!NOTE]
> **HKEY_LOCAL_MACHINE** anahtarı kullanıldığı için, yalnızca bir kaynak denetimi eklentisi belirli bir makinede varsayılan kaynak denetimi eklentisi olarak kaydedilebilir (ancak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcıların belirli bir çözüm için gerçekten hangi kaynak denetimi eklentisini kullanmasını istediğini belirlemesine izin verir). Yükleme işleminiz sırasında, bir kaynak denetimi eklentisinin zaten ayarlanmış olup olmadığını kontrol edin; Bu durumda, kullanıcıdan yeni kaynak denetimi eklentisinin varsayılan olarak yüklenip yüklenmediğini isteyip istemediğini sorar. Kaldırma sırasında, **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; içindeki tüm kaynak denetimi eklentileri için ortak olan diğer kayıt defteri alt anahtarlarını kaldırmayın; yalnızca belirli SCC alt anahtarlarınızı kaldırın.

## <a name="how-the-ide-detects-version-1213-support"></a>IDE 'nin 1.2/1.3 desteğini algılaması
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Eklentinin kaynak denetimi EKLENTISI API sürüm 1,2 ve 1,3 işlevlerini destekleyip desteklemediğini nasıl tespit ediyor? Gelişmiş özelliği bildirmek için, kaynak denetimi eklentisinin ilgili işlevi uygulaması gerekir:

 İlk olarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [SccGetVersion](../../extensibility/sccgetversion-function.md)çağırarak döndürülen değeri denetler. Bu, 1,2 değerinden büyük veya buna eşit olmalıdır.

 Sonra, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] `lpSccCaps` [SccInitialize](../../extensibility/sccinitialize-function.md)'daki bağımsız değişkeni inceleyerek belirli yeni özelliğin desteklenip desteklenmediğini belirler.

 Bu koşulların her ikisi de karşılanırsa, 1,2 ve 1,3 sürümlerinde desteklenen yeni işlevler çağrılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetim eklentilerini kullanmaya başlama](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
