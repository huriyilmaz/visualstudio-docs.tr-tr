---
title: 'Nasıl: Kaynak Kontrol Eklentisi Yükleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707987"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Nasıl yapılır: Kaynak denetim eklentisi yükleme
Kaynak denetimi eklentisi oluşturma üç adım içerir:

1. Bu dokümantasyonun Kaynak Denetimi Eklentisi API başvuru bölümünde tanımlanan işlevleri içeren bir DLL oluşturun.

2. Kaynak Denetimi Eklentisi API tanımlı işlevlerini uygulayın. Bunun [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için çağrı yaptığınızda, eklentiden arabirimleri ve iletişim kutularını kullanılabilir hale getirin.

3. Uygun kayıt defteri girişleri yaparak DLL'yi kaydedin.

## <a name="integration-with-visual-studio"></a>Visual Studio ile Tümleştirme
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kaynak Denetimi Eklentisi API'sine uygun kaynak kontrol eklentilerini destekler.

### <a name="register-the-source-control-plug-in"></a>Kaynak kontrol eklentisini kaydedin
 Çalışan tümleşik geliştirme ortamının (IDE) kaynak denetim sistemine çağrılayabilmeleri için önce API'yi dışa akso sokan kaynak denetim eklentisi DLL'yi bulması gerekir.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Kaynak kontrol eklentisi DLL'yi kaydetmek için

1. **Yazılım** alt anahtarında, şirket adınızı alt anahtarınızı ve ardından ürün adınızı alt anahtarınızı belirten **HKEY_LOCAL_MACHINE** anahtarının altına iki giriş ekleyin. Desen **HKEY_LOCAL_MACHINE\SOFTWARE\\\<şirket adı \\ \<>\\ \<ürün adı>giriş>**  =  *değeridir.* İki giriş her zaman **SCCServerName** ve **SCCServerPath**olarak adlandırılır. Her biri normal bir dize.

    Örneğin, şirketinizin adı Microsoft ise ve kaynak denetim ürününuzun adı SourceSafe ise, bu kayıt defteri yolu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**olacaktır. Bu alt anahtarda, ilk giriş, **SCCServerName,** ürününüzü adlandırma kullanıcı tarafından okunabilir bir dizedir. İkinci giriş, **SCCServerPath,** IDE bağlanması gereken kaynak denetim eklentisi DLL tam yoldur. Aşağıda örnek kayıt defteri girişleri sağlar:

   |Örnek Kayıt Defteri girişi|Örnek değer|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath, SourceSafe eklentisine giden tam yoldur. Kaynak denetimi eklentiniz farklı şirket ve ürün adlarını ancak aynı kayıt defteri giriş yollarını kullanır.

2. Aşağıdaki isteğe bağlı kayıt defteri girişleri, kaynak denetim eklentinizin davranışını değiştirmek için kullanılabilir. Bu girişler **SccServerName** ve **SccServerPath**ile aynı alt anahtara gider.

   - **HideInVisualStudioregistry** girişi, kaynak denetim eklentinizin **Plug-in Seçim** listesinde görünmesini istemiyorsanız [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kullanılabilir. Bu giriş, kaynak denetim eklentisine otomatik geçişi de etkiler. Bu giriş için olası kullanımlardan biri, kaynak denetim eklentinizin yerini alan ancak kullanıcının kaynak denetim eklentisini kullanarak kaynak denetim paketine geçiş yapmasını kolaylaştıran bir kaynak denetim paketi sağlamanızdır. Kaynak denetim paketi yüklendiğinde, eklentiyi gizleyen bu kayıt defteri girişini ayarlar.

      **HideInVisualStudio** bir DWORD değeridir ve eklentiyi gizlemek için *1* veya eklentiyi göstermek için *0* olarak ayarlanır. Kayıt defteri girişi görünmüyorsa, varsayılan davranış eklentiyi göstermektir.

   - **DisableSccManager** kayıt defteri girişi, Normalde **Dosya** > **Kaynağı Denetimi** alt menüsüaltında görünen Başlat ** \<Kaynak Denetim Sunucusu>** menü seçeneğini devre dışı kılabilir veya gizlemek için kullanılabilir. Bu menü seçeneğini seçerken [SccRunScc](../../extensibility/sccrunscc-function.md) işlevi çağırır. Kaynak denetimi eklentiniz harici bir programı desteklemeyebilir ve bu nedenle **Başlat** menüsü seçeneğini devre dışı bırakıp gizlemek isteyebilirsiniz.

      **DisableSccManager** bir DWORD değeridir ve **Başlat \<Kaynak Denetim Sunucusu>** menü seçeneğini etkinleştirmek için *0* olarak ayarlanır, menü seçeneğini devre dışı bırakıp *1* olarak ayarlanır ve menü seçeneğini gizlemek için *2* olarak ayarlanır. Bu kayıt defteri girişi görünmüyorsa, varsayılan davranış menü seçeneğini göstermektir.

   | Örnek kayıt defteri girişi | Örnek değer |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. **SOFTWARE** alt anahtarının **HKEY_LOCAL_MACHINE** tuşu altında **SourceCodeControlProvider**alt anahtarını ekleyin.

    Bu alt anahtar altında, kayıt defteri girişi **SağlayıcıRegKey,** 1 adımda kayıt defterine yerleştirdiğiniz alt anahtarı temsil eden bir dize olarak ayarlanır. Desen **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *YAZILIM\\ \> \\<şirket\>adı<ürün adıdır.*

    Aşağıda bu alt anahtar için örnek içerik vereme gösterin.

   |Kayıt defteri girişi|Örnek değer|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|YAZILIM\Microsoft\SourceSafe|

   > [!NOTE]
   > Kaynak denetim eklentiniz aynı alt anahtar ve giriş adlarını kullanır, ancak değer farklı olacaktır.

4. **SourceCodeControlProvider** alt anahtarı altında **InstalledSCCProviders** adında bir alt anahtar oluşturun ve ardından bu alt anahtarın altına bir giriş yerleştirin.

    Bu girişin adı sağlayıcının kullanıcı tarafından okunabilir adıdır (SCCServerName girişi için belirtilen değerle aynıdır) ve değer, bir kez daha, adım 1'de oluşturulan alt anahtardır. Desen **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<şirket\>adı***<ürün adı\\ \> \\ \>* = <yazılım<görüntülemektir.

    Örnek:

   |Örnek kayıt defteri girişi|Örnek değer|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|YAZILIM\Microsoft\SourceSafe|

   > [!NOTE]
   > Bu şekilde kayıtlı birden çok kaynak denetim eklentisi olabilir. Bu şekilde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tüm yüklü Kaynak Denetimi Eklentisi API tabanlı eklentileri bulur.

## <a name="how-an-ide-locates-the-dll"></a>Bir IDE DLL'yi nasıl bulur?
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE kaynak kontrol eklentisi DLL bulma nın iki yolu vardır:

- Varsayılan kaynak denetimi eklentisini bulun ve sessizce bağlanın.

- Kullanıcının seçtiği tüm kayıtlı kaynak denetimi eklentilerini bulun.

  İlk şekilde DLL bulmak için, IDE giriş **SağlayıcıRegKey**için **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** alt anahtarı altında bakar. Bu girişin değeri başka bir alt anahtara işaret. IDE daha sonra **HKEY_LOCAL_MACHINE**altında ikinci alt **anahtarSCcServerPath** adlı bir giriş arar. Bu girişin değeri IDE'yi DLL'ye işaret edin.

> [!NOTE]
> IDE, göreli yollardan DL yüklemez (örneğin, *.\NewProvider.DLL).* DLL'ye tam bir yol belirtilmelidir (örneğin, *c:\Providers\NewProvider.DLL).* Bu, yetkisiz veya taklit edilmiş eklenti DLL'lerin yüklenmesini engelleyerek IDE'nin güvenliğini güçlendirir.

 DLL'yi ikinci şekilde bulmak için, IDE tüm girişler için **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** alt anahtarının altına bakar. Her girişin bir adı ve bir değeri vardır. IDE, bu adların bir listesini kullanıcıya görüntüler. Kullanıcı bir ad seçtiğinde, IDE bir alt anahtara işaret eden seçili ad için değeri bulur. **IDE, HKEY_LOCAL_MACHINE**altındaki bu alt anahtarda **SccServerPath** adında bir giriş arar. Bu girişin değeri IDE'yi doğru DLL'ye işaret edin.

 Bir kaynak denetim eklentisi DLL bulma her iki yolu desteklemek gerekir ve sonuç olarak, **SağlayıcıRegKey**ayarlar , önceki herhangi bir ayarı üzerine. Daha da önemlisi, kullanıcı kullanmak için hangi kaynak denetim eklentisi bir seçim olabilir, böylece **InstalledSccProviders** listesine kendini eklemek gerekir.

> [!NOTE]
> **HKEY_LOCAL_MACHINE** anahtarı kullanıldığından, yalnızca bir kaynak denetim eklentisi belirli bir makinedeki varsayılan kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eklentisi olarak kaydedilebilir (ancak, kullanıcıların belirli bir çözüm için hangi kaynak kontrol eklentisini gerçekten kullanmak istediklerini belirlemelerine olanak tanır). Yükleme işleminiz sırasında, kaynak denetim eklentisi zaten ayarlanmış olup olmadığını kontrol edin; bu durumda, kullanıcıya varsayılan olarak yüklenen yeni kaynak denetim eklentisini ayarlayıp ayarlamamasını isteyin. Yükleme nin kaldırılması sırasında, **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider'daki**tüm kaynak denetim eklentilerinde ortak olan diğer kayıt defteri alt anahtarlarını kaldırmayın; yalnızca belirli SCC alt anahtarınızı kaldırın.

## <a name="how-the-ide-detects-version-1213-support"></a>IDE sürüm 1.2/1.3 desteğini nasıl algılar?
 Bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eklentinin Kaynak Denetimi Eklentisi API sürüm 1.2 ve 1.3 işlevlerini destekleyip desteklemediğini nasıl algılar? Gelişmiş yeteneği bildirmek için kaynak denetim eklentisinin ilgili işlevi uygulaması gerekir:

 İlk [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olarak, [SccGetVersion'u](../../extensibility/sccgetversion-function.md)arayarak döndürülen değeri denetler. 1,2'den büyük veya eşit olmalıdır.

 Ardından, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Belirli yeni `lpSccCaps` [yeteneğin SccInitialize'deki](../../extensibility/sccinitialize-function.md)bağımsız değişkeni inceleyerek desteklenip desteklenmediğini belirler.

 Bu koşulların her ikisi de karşılanırsa, 1.2 ve 1.3 sürümlerinde desteklenen yeni işlevler çağrılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri ile başlayın](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
