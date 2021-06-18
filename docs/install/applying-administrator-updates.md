---
title: Microsoft Endpoint Configuration Manager ile Visual Studio güncelleştirmelerini Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Yöneticilere yönetici güncelleştirmeleri uygulama hakkında Visual Studio.
ms.date: 04/16/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c18c460ebcffdba93279aafec2f3d76503ab2383
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307693"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Yönetici güncelleştirmelerini uygulama Microsoft Endpoint Configuration Manager

Bu belge, yönetici güncelleştirmelerinin farklı Visual Studio özelliklerini açıklar. Aşağıda, bunların kuruluş genelinde nasıl ve ne zaman dağıtılması gerektiği, hangi yapılandırma seçeneklerinin kullanılabilir olduğu ve raporları görüntüleme ve sorun giderme hakkında bilgiler bulabilirsiniz. Yönetici güncelleştirmelerini kullanmanın önkulları hakkında daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini etkinleştirme.](../install/enabling-administrator-updates.md) Yönetici güncelleştirmeleri, Visual Studio bilgisayarda zaten yüklü olduğunu varsayıyor. Yönetici güncelleştirmelerinin uygulanması yepyeni bir yükleme başlatmaz.

## <a name="understanding-visual-studio-administrator-updates"></a>Yönetici Visual Studio güncelleştirmelerini anlama

Microsoft Visual Studio ve WSUS tarafından tüketim için Microsoft Update'da yayımlanan Yapılandırma Yöneticisi yöneticisi güncelleştirme paketi, Yapılandırma Yöneticisi güncelleştirmesini indirerek istemci makinelere Visual Studio gereken bilgileri içerir. Ayrıca, kuruluş genelinde dağıtacak güncelleştirmeleri karar vermek için bir IT yöneticisine gereken bilgileri içerir. Ağ düzenlerinin bakımını kolaylaştırmak için de kullanılabilir. Yönetici Visual Studio güncelleştirme paketleri, ürünün yeni bir yüklemesini yapmak için yeterli bilgi içermez ve üründe yayımlanan gerçek ürün ikililerini Content Delivery Network. Visual Studio yönetici güncelleştirmeleri, normal güncelleştirmeler gibi toplu Visual Studio olur. Daha yüksek bir ürün Visual Studio ve sonraki bir yayın tarihine sahip herhangi bir güncelleştirmenin daha eski ve daha düşük bir sürümün üst kümesi olduğunu varsayabilirsiniz.

Visual Studio güncelleştirmeleri, Visual Studio bakım sürümleri için geçerlidir. Belirli bir zaman çerçevesi Visual Studio hangi hizmet temelleri hala destekte olduğu hakkında daha fazla bilgi için [bkz. Visual Studio Yaşam](/visualstudio/productinfo/vs-servicing-vs)Döngüsü ve Bakım. Tüm desteklenen Visual Studio bakım temelleri güvenli tutulur.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Yönetici güncelleştirmelerinin türleri ve özellikleri

Bu güncelleştirmeler için üç tür yönetici Visual Studio:

* **Güvenlik güncelleştirmeleri** tüm Visual Studio sürümleri (Enterprise, Professional, Community vb.) için geçerlidir ve sınırlı, yüksek oranda hedeflenen ve uyumlu bakım düzeyi değişiklikleri içerir. Güvenlik güncelleştirmeleri istemciyi sonraki bir ikincil sürüme ilerletecek değildir; zaten belirli bir ikincil sürüm düzeyinde olan bir istemciye güvenlik açıklarına yönelik düzeltmeler sunmak için tasarlanmıştır. Güvenlik güncelleştirmelerinde en az bir güvenlik düzeltmesi vardır, ancak güvenlik düzeltmesi istemci makinede yüklü bir bileşende veya iş yükünde olabilir veya bu düzeltmede yer alamayacak olabilir. Örneğin, .NET bileşenlerinde bir güvenlik açığını düzeltebilir ve güncelleştirmeyi bir güvenlik güncelleştirmesi olarak etiketleyene, ancak yalnızca C++ bileşenlerinin yüklü olduğu bir istemci makinesi üzerinde anlamlı bir etkisi olmaz. Güvenlik güncelleştirmeleri, diğer güvenilirlik düzeltmelerini veya diğer gerekli bileşen güncelleştirmelerini de içerebilir. Güvenlik güncelleştirmeleri, ["Güvenlik Güncelleştirmeleri" olarak](https://www.catalog.update.microsoft.com/Home.aspx) sınıflandırılan Microsoft Update Kataloğu (MUC) ve [Windows Server Update Services'de](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)yayımlanır.
* **Özellik güncelleştirmeleri,** IT yöneticilerinin kuruluşlarında bilgisayarları daha yeni bir ikincil sürüme Visual Studio. Özellik güncelleştirmeleri yalnızca enterprise Visual Studio, Professional ve Build Tools SKUS gibi kuruluşlarda yaygın olarak bulunan sürümler için geçerlidir. Tüm özellik güncelleştirmeleri Microsoft Update Kataloğu'Microsoft Update "Özellik Paketleri" olarak yayımlanır ve isteğe bağlı olarak Yapılandırma Yöneticisi Kataloğu'Microsoft Update [içeri aktarılabilir.](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog) Özellik güncelleştirmeleri topludur ve ek kalite ve önceki güvenlik düzeltmelerini içerir. bir istemci [makinesini bakım](#understanding-configuration-options) temel çizgisi üzerinde kalacak şekilde yapılandırma ve özellik güncelleştirmelerinin belirli istemcilere teslimini önleme hakkında yönergeler için aşağıdaki yapılandırma seçenekleri bölümüne bakın.
* **Kalite güncelleştirmeleri** yalnızca kuruluşlarda yaygın Visual Studio olan ve sınırlı, yüksek oranda hedeflenen ve uyumlu bakım düzeyi değişiklikleri içeren sürümler için de geçerlidir. Kalite güncelleştirmeleri istemciyi sonraki bir ikincil sürüme ilerletecek değildir; zaten belirli bir ikincil sürüm düzeyinde olan bir istemciye performans ve güvenilirlik düzeltmeleri veya gerekli diğer bileşen güncelleştirmeleri sunmak için tasarlanmıştır. Kalite güncelleştirmeleri, güvenlik güncelleştirmeleriyle birlikte birikerek yalnızca güvenlik düzeltmesi daha önce bağımsız olarak yayınlandı ise güvenlik düzeltmeleri içerir. Kalite güncelleştirmeleri Microsoft Update Kataloğu'Microsoft Update" olarak yayımlanır ve isteğe bağlı olarak [Yapılandırma Yöneticisi.](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)

### <a name="decoding-the-titles-of-administrator-updates"></a>Yönetici güncelleştirmelerinin başlıklarının kodunu çözme

Her yönetici güncelleştirmenin başlığı, hem geçerli sürüm aralığını hem de güncelleştirmenin sonuç sürümünü açıklar.Örneğin,

::: moniker range="vs-2017"

* **Visual Studio 2017 sürüm 15.9.0 ile 15.9.35** arasında bir "Güvenlik Güncelleştirmesi" olarak sınıflandırılan güncelleştirme, istemcide 15.9.0 ile 15.9.35 arasındaki tüm Visual Studio 2017 sürümleri için geçerli olacaktır ve bu istemci sürümlerini 15.9.35 sürümüne güncelleştirecek.
* "Özellik Paketi" olarak sınıflandırılan **Visual Studio 2017 sürüm 15.0.0 ile 15.9.0** arasındaki tüm ürün sürümü aralığı boyunca istemcide kurumsal kullanım için lisanslı Visual Studio 2017 sürümleri için geçerli olacak ve bu istemci sürümleri 15.9.0 sürümüne güncelleştirilecek. Bu özellik paketinin uygulanması, temel olarak istemcilerin güvenlik güncelleştirmelerini almalarına olanak sağlar. 
* yalnızca "Güncelleştirmeler" olarak sınıflandırılan **Visual Studio 2017 sürüm 15.9.0 ile 15.9.37** arası sürümler, istemcide kurumsal kullanım için lisanslı Visual Studio 2017 sürümleri için geçerli olacak ve bu istemci sürümlerini 15.9.37 sürümüne güncelleştirecek.

::: moniker-end

::: moniker range="vs-2019"

* **Visual Studio 2019 sürüm 16.7.0 ile 16.7.12** arası bir "Güvenlik Güncelleştirmesi" olarak sınıflandırılan güncelleştirme, istemcinin 16.7.0 ile 16.7.12 sürümleri arasındaki tüm Visual Studio 2019 sürümleri için geçerli olacak ve bu istemci sürümlerini 16.7.12 sürümüne güncelleştirecek.  
* **"Özellik Paketi" olarak sınıflandırılan Visual Studio 2019 sürüm 16.0.0 ile 16.9.0** arasındaki tüm ürün sürümü aralığı ile 16.9.0 arasında istemcide kurumsal kullanım için lisanslı Visual Studio 2019 sürümleri için geçerli olacaktır. ve bu istemci sürümleri (daha önceki bir bakım temeli üzerinde kalacak şekilde yapılandırılmamış) 16.9.0 sürümüne güncelleştirecek. 
* yalnızca "Güncelleştirmeler" olarak sınıflandırılan **Visual Studio 2019 sürüm 16.8.0 ile 16.8.7** arası sürümler, istemcide kurumsal kullanım için lisanslı Visual Studio 2019 sürümleri için geçerli olacak ve bu istemci sürümlerini 16.8.7 sürümüne güncelleştirecek.

::: moniker-end

::: moniker range=">=vs-2022"

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Yapılandırma Yöneticisi güncelleştirmelerini dağıtmak Visual Studio kullanma

### <a name="understanding-configuration-options"></a>Yapılandırma seçeneklerini anlama

Visual Studio yönetici güncelleştirmelerini, kuruluş dağıtım tercihleri ve gereksinimleriyle uyumlu olacak şekilde uyarlamak için kullanılmaktadır. En yaygın yapılandırma seçenekleri aşağıda listelenmiştir. Desteklenen tüm yönetici güncelleştirme davranışlarının kapsamlı bir listesi [](../install/use-command-line-parameters-to-install-visual-studio.md) için bkz. Visual Studio'i yüklemek için komut satırı parametrelerini kullanma ve yalnızca "güncelleştirme" eylemine karşılık gelenlere dikkat.

* **[Yönetici güncelleştirmesi kabul:](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)** bu kayıt defteri anahtarı, istemci makinesinin yönetici güncelleştirmelerini alsı için gereklidir. Makine genelindeki bir anahtardır, yani kutuya yüklenmiş tüm Visual Studio örnekleri için geçerlidir.
* **Visual Studio geri** alma: Visual Studio, yönetici güncelleştirmelerini almayı geri almak için makine genelindeki ayrı  bir **AdministratorUpdatesOptOut** kayıt defteri Visual Studio kullanabilir. Bu anahtarın amacı, kullanıcıya Visual Studio güncelleştirmelerin makineye otomatik olarak uygulanması üzerinde denetim sahibi olmasına izin vermektir. İstemci bilgisayarı yönetici güncelleştirmelerini engellemek üzere yapılandırmak için **AdministratorUpdatesOptOut**   REG_DWORD **1 olarak ayarlayın.** Anahtarın olmaması veya **0** değerinin ayarlanmış olmaması, Visual Studio kullanıcının Visual Studio için yönetici güncelleştirmeleri almak istediği anlamına gelir.
    Kodlama kullanıcı **tercihi için AdministratorUpdatesOptOut** anahtarının, IT yöneticisi amacını kodlayan    **AdministratorUpdatesEnabled** anahtarına göre   önceliklendirmesi olduğunu unutmayın.  **AdministratorUpdatesOptOut**    **1** olarak ayarlanırsa, **AdministratorUpdatesEnabled** anahtarı da 1 olarak ayarlanmış olsa bile istemcide   güncelleştirme **engellenir.**Bu eylem, IT yöneticilerinin hangi geliştiricilerin geri almayı tercih etme kararına sahip olduğunu ve bu geliştiricilerin daha sonra kimin ihtiyaçlarının daha önemli olduğunu tartışacaklarını varsayıyor.IT yöneticileri her zaman her iki anahtarı da her zaman değiştirebilir.
* **Güncelleştirilmiş ürün bitlerinin konumu:** Çoğu zaman istemci makineleri güncelleştirilmiş ürün bitlerini Microsoft CDN aracılığıyla İnternet'den indirir. Bu senaryo, istemci makinelerinin İnternet erişimine sahip olduğunu gerektirir. Ancak bazı kuruluşlar, istemci makinelerini yalnızca iç ağ düzeni konumlarından bitleri yükp güncelleştiracak şekilde kısıtlar. Yönetici güncelleştirmelerinin bir iç ağ konumu üzerinde güncelleştirilmiş bitler kullanılarak uygulana olduğundan emin olmak için, yönetici güncelleştirmesi başarıyla dağıtılamadan önce aşağıdaki koşulların doğru olması gerekir: 
  * İstemci makinenin bir noktada önyükleyiciyi bu ağ düzeni konumdan çalıştırması gerekir. İdeal olarak, özgün istemci yüklemesi ağ düzeninden önyükleyici kullanılarak olmuş olabilir, ancak aynı ağ konumu içinde güncelleştirilmiş bir önyükleyici kullanarak bir güncelleştirme yüklemek de mümkündür. Bu eylemlerden biri, istemci makinesine, bu belirli düzen konumuyla bir bağlantı katıştırabilirsiniz.
  * Ağ düzeni konumu (istemcinin bağlı olduğu konum), yönetici güncelleştirmenin dağıtmak istediği [güncelleştirilmiş](../install/update-a-network-installation-of-visual-studio.md) ürün bitlerini içermesi için güncelleştirilmiş olmalıdır.

::: moniker range=">=vs-2019"

* **Bakım temeli bağlı kalma durumu:** Yukarıda açıklandığı gibi, yönetici özelliği güncelleştirmeleri Visual Studio sürümün daha güncel ikincil bir sürümüne doğru ilerler. Ancak bazen Visual Studio belirli bir kararlı ve güvenli bakım temeli düzeyinde kalması ve makinelerinin daha güncel bir ikincil sürüme ne zaman ilerler olduğunu denetlemesi gerekir. Bir istemci makinesini hizmet temeli üzerinde kalacak şekilde yapılandırmak ve buna gönderilen isteksiz yönetici özelliği güncelleştirmelerini yoksaymak için **BaselineStickinessVersions2019** Reg_SZ veri değerini, istemci makinesinin yaslaması ve devam ettiği tercih edilen temeli temsil eden bir dize olarak ayarlamanız gerekir. Dize, **16.7.0** gibi izin verilebilir bir bakım temel sürümü içerebilir.  
     Kayıt `BaselineStickinessVersions2019` defteri değeri yanlış biçimlendirilmişse, tüm yönetici özellik güncelleştirmelerinin makineye yüklemesi engellenir. özellik güncelleştirmeleri için desteklenen [zaman çerçevelerini Visual Studio olun.](/visualstudio/productinfo/vs-servicing-vs) Ayrıca, anahtarın varlığına veya değerine bakılmaksızın, teknik olarak yaşam sürelerinin sonuna ulaşan yönetici özellik güncelleştirmeleri uygulamak mümkünken, destekleri sona erer ve bu nedenle güvensiz olabilecekleri için bunu `BaselineStickinessVersions2019` önerilmez.

::: moniker-end

* **Güncelleştirmeyi, şu Visual Studio bile gerçekleşmesini zorlar:** Visual Studio yüklemeden önce kapatılacak bir güncelleştirme gerekir. Bu Visual Studio açıksa veya kullanılıyorsa, güncelleştirme yüklemesi iptal edilir. Güncelleştirmenin kapatıldığından emin Visual Studio kolay bir yol, Onay Yöneticisi'ni makine yeniden başlatıldıktan hemen sonra güncelleştirmeyi uygulayacak şekilde yapılandırmaktır. Ayrıca parametresini kullanarak `--force` da sistemi kapatmaya Visual Studio. Bir Visual Studio zorlayarak çalışma kaybına neden olabilir, bu nedenle dikkatli kullanın. Varsayılan sistem bağlamında bir yönetici güncelleştirmesi çalıştırmak bayrağını yoksayar, bu nedenle yönetici Güncelleştirmesini kullanıcı bağlamında `–-force` çalıştıracak şekilde yapılandırmanız gerekir.

### <a name="methods-for-configuring-an-administrator-update"></a>Yönetici güncelleştirmesini yapılandırma yöntemleri

Yönetici güncelleştirmelerini yapılandırmanın üç ana yöntemi vardır: kayıt defteri anahtarı, istemci makinede bir yapılandırma dosyası veya dağıtım paketinin Yapılandırma Yöneticisi değişikliği.   

* **Kayıt defteri anahtarı:** Yönetici güncelleştirmeleri, Kurumsal dağıtımlar için varsayılanları ayarlama konusunda açıklandığı gibi standart Visual Studio konumlardan herhangi birsinde belirli [kayıt defteri anahtarlarını arama.](../install/set-defaults-for-enterprise-deployments.md) Kayıt defteri anahtarları tarafından denetlenen seçenekler **AdministratorUpdatesOptOut** Reg_DWORD, **AdministratorUpdatesOptOut**   Reg_DWORD ve **BaselineStickinessVersions2019** gibi Reg_SZ. Kayıt defteri anahtarlarının değerini oluşturmak ve ayarlamak için istemci bilgisayarda yönetici erişimi gerekir.

* **Yapılandırma dosyası:** Bazı ayarlar, istemci makinede isteğe bağlı bir yapılandırma dosyasında korunarak yalnızca bir kez ayarlanabilecek ve gelecekteki tüm yönetici güncelleştirmeleri için geçerli olacak şekilde kullanılabilir. Yapılandırma dosyası yaklaşımı bir kayıt defteri anahtarı gibi davranır ve makine genelindedir; bu da istemci makinede yüklü olan tüm Visual Studio yüklemeleri için geçerli olduğu anlamına gelir. Yapılandırma dosyasının standart konumu şu `C:\ProgramData\Microsoft\VisualStudio\updates.config` konumdadır: . Ancak, dosyayı depolamak için başka bir konum kullanmak isterseniz, **UpdateConfigurationFile** adlı bir Reg_SZ kayıt defteri anahtarı oluşturarak ve bu anahtarın değerini yapılandırma dosyanız yoluna ayarerek bunu kullanabilirsiniz. Bu kayıt defteri anahtarı, Kurumsal dağıtımlar için varsayılanları Visual Studio kayıt defteri [konumlarının herhangi bir yerine yer değiştirebilir.](../install/set-defaults-for-enterprise-deployments.md) Özel yapılandırma dosyası konumu için bir kayıt defteri değeri eklemeyi seçerseniz, bu dosya için bir değere bakar; Dosya yoksa bir özel durum oluşturur ve güncelleştirme başarısız olur.

     JSON biçimindeki yapılandırma dosyası, bu yükleyiciye geçebilirsiniz daha fazla anahtar belirten virgülle ayrılmış bir dize dizisi `installerUpdateArgs` olan Visual Studio destekler. Dosyanın içeriği geçersiz bir alan veya desteklenmiyor bir seçenek içeriyorsa, güncelleştirme başarısız olur. Daha fazla bilgi için [bkz. Komut satırı parametrelerini kullanarak Visual Studio.](../install/use-command-line-parameters-to-install-visual-studio.md)

   Örnek bir yapılandırma dosyası şöyledir:

  ```json
  "installerUpdateArgs" : ["--quiet", "--noWeb"], 
  "checkPendingReboot" :  "true" 
  ```

* **SCCM'de Yönetici** Güncelleştirme Paketini el ile güncelleştirme: SCCM'de tek bir yönetici güncelleştirme paketinin komut satırı parametreleri de el ile değiştirilebilir.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Doğrulama, raporlar ve sorun giderme hata kodları

### <a name="determining-that-visual-studio-was-updated"></a>Güncelleştirmenin Visual Studio belirleme

Yönetici güncelleştirmesini doğru şekilde yüklemiş olduğunu doğrulamak için aşağıdaki yöntemlerden birini kullanabilirsiniz:

* İstemci bilgisayarda, Visual Studio hakkında Yardım'ı **** seçin ve sürüm numarasının hedeflenen güncelleştirmenin başlığında yer alan son sayıyla   >  **** eş olduğunu doğrulayın.
* Bilgisayarın çeşitli sürümlerini tanımlamak için istemci makinede **vswhere** aracını Visual Studio kullanın. Daha fazla bilgi için, [bkz. Tools for detecting and managing Visual Studio instances](../install/tools-for-managing-visual-studio-instances.md).
* Her yönetim güncelleştirme girişimi, istemci makinesinin dizininde güncelleştirme işlemi `%temp%` ilerlemesini yakalayan birkaç günlük dosyası üretir.Klasörü tarihe göre sırala ve sırasıyla yönetim güncelleştirmeleri, önyükleyici, Visual Studio Yükleyicisi ve kurulum altyapısı için , , ve başlayan  `dd_updatedriver`  `dd_bootstrapper` dosyaları  `dd_client`  `dd_setup`   arama.Bu günlük dosyalarının 0 içerdiğini ve güncelleştirmenin başarıyla uygulandığını doğrulayın. Bu günlük dosyalarının, yapılandırma dosyasının çalıştığını doğrulamak için de kullanılal olduğunu unutmayın. Diğer ayrıntılar için [Visual Studio Günlük Toplama Aracı'nı](https://www.microsoft.com/download/details.aspx?id=12493) kullanın.

### <a name="error-codes-and-conditions"></a>Hata kodları ve koşulları

>[!IMPORTANT]
> Güncelleştirmeyi Visual Studio önce uygulamanın kapat gerektiğini unutmayın. Bu Visual Studio açıksa veya kullanılıyorsa, güncelleştirme yüklemesi iptal edilir.

Yönetim güncelleştirmeleri aşağıdaki dönüş kodlarını iade ediyor olabilir:  

| Hata kodu | Tanım                                                                                                                                                                                                  |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0          | Yönetim güncelleştirmesi başarıyla yüklendi.                                                                                                                                                       |
| 1001       | Visual Studio Yükleyicisi veya ilgili bir kurulum işlemi çalışıyor. Güncelleştirme uygulanmaz.                                                                                                                   |
| 1002       | Visual Studio Yükleyicisi duraklatıldı. Güncelleştirme uygulanmaz.                                                                                                                                               |
| 1003       | Visual Studio çalışıyor. Güncelleştirme uygulanmaz. Bu koşul, bayrağı kullanılarak `--force` reddedildi.                                                                                              |
| 1004       | İnternet algılanmadı.Güncelleştirme, güncelleştirilen dosyaların bulunduğu İnternet konumuyla iletişim kuramıyor. Güncelleştirme uygulanmaz.                                                                          |
| 1005       |  **AdministratorUpdatesEnabled**   kayıt defteri değeri **0** olarak ayarlanır veya hiç ayarlanmaz. Güncelleştirme uygulanmaz.                                                                                            |
| 1006       |  **AdministratorUpdatesOptOut kayıt**   defteri değeri **1 olarak ayarlanır.** Güncelleştirme uygulanmaz. Anahtar, yönetici tarafından güncelleştirilmez istemci bilgisayarlara yöneliktir.                     |
| 1007       | Visual Studio Yükleyicisi yüklü değil.                                                                                                                                                               |
| 1008       | **BaselineStickinessVersions2019** kayıt defteri değeri okunabilir bir biçimde değil. Kayıt defteri değeri, **derleme** numarası açıkça 0 olarak ayarlanmış Tüm veya geçerli sürümleri (örneğin, X.Y.0) içermeli. |
| 3010       | Sistemin yeniden başlatılması gerekir.Güncelleştirme uygulanmış olabilir veya uygulanmaymalıdır. Bilgisayarı yeniden başlatın ve güncelleştirmeyi yeniden deneyin.                                                                                |
| Diğer      | Güncelleştirme uygulanırken hata oluştu.Güncelleştirme uygulanmaz.                                                                                                                                   |

İstemci hata kodlarının kapsamlı bir listesi için [bkz. Komut satırı parametrelerini kullanarak](use-command-line-parameters-to-install-visual-studio.md)Visual Studio.

## <a name="feedback-and-support"></a>Geri bildirim ve destek

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Yönetici güncelleştirmeleri hakkında geri bildirim sağlamak veya Visual Studio sorunları rapor etmek için aşağıdaki yöntemleri kullanabilirsiniz:

* Yükleme ve yükseltme [Visual Studio sorunlarını giderme kılavuzuna](../install/troubleshooting-installation-issues.md) bakın.
* Soru-Cevap Kurulumu'nda [Visual Studio topluluk&sorun.](/answers/topics/vs-setup.html)
* Destek Visual Studio [sayfasına gidin ve](https://visualstudio.microsoft.com/vs/support/)soruna SSS sayfasında listelenmiş olup olmadığını kontrol edin.  Sohbet yardımı için Destek [Bağlantısı düğmesini](https://visualstudio.microsoft.com/vs/support/#talktous) de seçin.
* [Yönetici güncelleştirmelerini uygulama deneyimiyle ilgili olarak](https://aka.ms/vs/wsus/feedback) özellik geri bildirimi Visual Studio sorun bildirin.
* Microsoft için kuruluşun teknik hesap yöneticisine ulaşın.

## <a name="see-also"></a>Ayrıca bkz.

* [Yönetici güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md)
* [Visual Studio yönetici kılavuzu](../install/visual-studio-administrator-guide.md)
* [Visual Studio Ürün Yaşam Döngüsü ve Bakım](/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 Sürüm Notları](/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 Sürüm Notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Komut Satırı Parametrelerini kullanarak Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](../install/tools-for-managing-visual-studio-instances.md)
* [Ağ yüklemesi oluşturma Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Yanıt dosyasında ayarları tanımlama](../install/automated-installation-with-response-file.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](../install/controlling-updates-to-visual-studio-deployments.md)
* [Microsoft Update Kataloğu hakkında SSS](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM) belgeleri](/mem/configmgr)
* [Güncelleştirmeleri Microsoft Kataloğu'Yapılandırma Yöneticisi](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) belgeleri](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
