---
title: Microsoft Endpoint Configuration Manager ile Visual Studio yönetici güncelleştirmelerini uygulama
titleSuffix: ''
description: Visual Studio için yönetici güncelleştirmelerini uygulamayı öğrenin.
ms.date: 04/16/2021
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 755bfb09826ec168228fbea16db26abc2a232a8c
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453390"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager kullanan yönetici güncelleştirmelerini uygulama

bu belge Visual Studio yönetici güncelleştirmelerinin farklı türlerini ve özelliklerini açıklamaktadır. Aşağıda, kuruluşunuzun tamamında nasıl ve ne zaman dağıtılacağı, hangi yapılandırma seçeneklerinin kullanılabildiği ve raporların nasıl görüntüleneceği ve nasıl giderileceği hakkında bilgi bulacaksınız. Yönetici güncelleştirmelerini kullanma önkoşulları hakkında daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md). yönetici güncelleştirmeleri Visual Studio bilgisayarda zaten yüklü olduğunu varsayar. Yönetici güncelleştirmelerinin uygulanması, yepyeni bir yükleme başlatmaz.

## <a name="understanding-visual-studio-administrator-updates"></a>Visual Studio yönetici güncelleştirmelerini anlama

Microsoft kataloğu ve WSUS tarafından kullanılmak üzere Microsoft Update yayımlanan Visual Studio yönetici güncelleştirme paketi, Configuration Manager Visual Studio güncelleştirmesini indirip istemci makinelere dağıtabilmesi için gereken bilgileri içerir. Ayrıca, kuruluş genelinde hangi güncelleştirmelerin dağıtılacağını belirlemek için bir BT yöneticisinin ihtiyacı olan bilgileri de içerir. Ayrıca, ağ düzenlerinin bakımını kolaylaştırmak için de kullanılabilir. Visual Studio yönetici güncelleştirme paketleri, ürünün yeni bir yüklemesini yapmak için yeterli bilgi içermez ve Content Delivery Network yayımlanan gerçek ürün ikililerini içerir. Visual Studio yönetici güncelleştirmeleri, düzenli Visual Studio güncelleştirmelerinde olduğu gibi birikimlidir. daha yüksek ürün sürüm numarasına sahip Visual Studio güncelleştirme ve daha sonraki bir sürüm tarihi daha eski, daha düşük bir sürümün üst kümesi olduğunu varsayabilirsiniz.

Visual Studio yönetici güncelleştirmeleri, destek altında olan Visual Studio bakım sürümleri için geçerlidir. belirli bir zaman çerçevesi içinde hala destek sunan Visual Studio hizmet temelleri hakkında daha fazla bilgi için bkz. [Visual Studio ürün yaşam döngüsü ve bakımı](/visualstudio/productinfo/vs-servicing-vs). desteklenen tüm Visual Studio hizmet temelleri güvenli tutulacak.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Yönetici güncelleştirmelerinin türleri ve özellikleri

Visual Studio için üç tür yönetici güncelleştirmesi vardır:

* **güvenlik güncelleştirmeleri** tüm Visual Studio sürümleri için geçerlidir (örn. Enterprise, Professional, Community, vb.) ve sınırlı, yüksek oranda hedeflenmiş ve uyumlu hizmet düzeyi değişiklikleri içerir. Güvenlik güncelleştirmeleri, bir istemciyi daha sonraki bir ikincil sürüme ilerlemez; Bunlar, zaten belirli bir alt sürüm düzeyinde olan bir istemciye güvenlik açıklarına yönelik düzeltmeler sunacak şekilde tasarlanmıştır. Güvenlik güncelleştirmelerinde en az bir güvenlik düzeltme olacaktır, ancak güvenlik düzeltme, istemci makinesine yüklenmiş bir bileşen veya iş yükü içinde olabilir veya olmayabilir. Örneğin, .NET bileşenlerinde bir güvenlik açığını çözebiliriz ve güncelleştirmeyi güvenlik güncelleştirmesi olarak etiketliyoruz, ancak aslında yalnızca C++ bileşenlerinin yüklü olduğu bir istemci makinesine gerçekten anlamlı bir etkiye sahip değildir. Güvenlik güncelleştirmeleri, diğer güvenilirlik düzeltmelerini veya diğer gerekli bileşen güncelleştirmelerini de içerebilir. güvenlik güncelleştirmeleri, hem [Microsoft Update kataloğunda](https://www.catalog.update.microsoft.com/Home.aspx) (muc) hem de [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)'da yayımlanır ve burada "güvenlik güncelleştirmeleri" olarak sınıflandırılır.
* **Özellik güncelleştirmeleri** , BT yöneticilerinin kuruluştaki bilgisayarları Visual Studio daha güncel bir alt sürümüne ilerlemelerini sağlar. özellik güncelleştirmeleri yalnızca kurumda, Enterprise, Professional ve derleme araçları sku 'ları gibi yaygın olarak bulunan Visual Studio sürümleri için geçerlidir. Tüm özellik güncelleştirmeleri, Microsoft Update kataloğunda "özellik paketleri" olarak yayımlanacak ve isteğe bağlı olarak, [Microsoft Update kataloğundan el ile Configuration Manager içeri aktarmaları](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)sağlanır. Özellik güncelleştirmeleri birikimlidir ve ek kalite ve önceki güvenlik düzeltmelerini içerir. Bir istemci makinenin bir hizmet taban çizgisinde kalacak şekilde nasıl yapılandırılacağı ve özellik güncelleştirmelerinin belirli istemcilere teslim edilmesini önleyen yönergeler için aşağıdaki [yapılandırma seçenekleri bölümüne](#understanding-configuration-options) bakın.
* **kalite güncelleştirmeleri** , yalnızca kurumda yaygın olarak bulunan Visual Studio sürümleri için geçerlidir ve sınırlı, yüksek oranda hedeflenmiş ve uyumlu hizmet düzeyi değişiklikleri içerirler. Kalite güncelleştirmeleri, bir istemciyi daha sonraki bir ikincil sürüme ilerlemez; Bunlar, zaten belirli bir alt sürüm düzeyinde olan bir istemciye performans ve güvenilirlik düzeltmeleri veya diğer gerekli bileşen güncelleştirmelerini sunacak şekilde tasarlanmıştır. Kalite güncelleştirmeleri güvenlik güncelleştirmeleriyle birlikte birikir ve bu nedenle yalnızca güvenlik düzeltmesi bağımsız olarak zaten yayımlanmışsa güvenlik düzeltmelerini içerir. Kalite güncelleştirmeleri, Microsoft Update kataloğunda "Güncelleştirmeler" olarak yayımlanır ve isteğe bağlı olarak Configuration Manager el ile [içeri aktarmak](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)için de kullanılabilir.

### <a name="decoding-the-titles-of-administrator-updates"></a>Yönetici güncelleştirmeleri başlıklarının kodunu çözme

Her yönetici güncelleştirmesinin başlığı, hem ilgili sürüm aralığını hem de güncelleştirmenin sonuç sürümünü açıklar.Örneğin,

::: moniker range="vs-2017"

* **Visual Studio 2017 sürüm 15.9.0 to 15.9.35 update** "Security update", istemcideki 15.9.0 ile 15.9.35 arasındaki sürümler arasında herhangi bir Visual Studio 2017 sürümü için geçerlidir ve bu istemci sürümlerini 15.9.35 olarak güncelleştirir.
* **Visual Studio 2017 sürüm 'sının 15.0.0 to 15.9.0 update** "Feature Pack" olarak sınıflandırılan Visual Studio 2017 sürümleri, istemci üzerinde 'sının 15.0.0 aracılığıyla tüm ürün sürümü aralığı ile, bu istemci sürümlerini 15.9.0 olarak güncelleştirecek şekilde uygulanır. Bu özellik paketinin uygulanması, istemcilerin güvenlik güncelleştirmelerini almasını sağlar. 
* **Visual Studio 2017 sürüm 15.9.0 to 15.9.37 update** , istemci üzerinde 15.9.0 ile 15.9.37 arasındaki sürümler arasında kurumsal kullanım için lisanslı Visual Studio 2017 sürümleri için geçerlidir ve bu istemci sürümlerini 15.9.37 olarak güncelleştirir.

::: moniker-end

::: moniker range="vs-2019"

* **Visual Studio 2019 sürüm 16.7.0 to 16.7.12 update** "Security update", istemcideki 16.7.0 ile 16.7.12 arasındaki sürümler arasında herhangi bir Visual Studio 2019 sürümü için geçerlidir ve bu istemci sürümlerini 16.7.12 olarak güncelleştirir.  
* **Visual Studio 2019 sürüm 16.0.0 to 16.9.0 update** "Feature Pack" olarak sınıflandırılan Visual Studio 2019 sürümleri, istemci üzerinde 16.0.0 ile 16.9.0 arasındaki tüm ürün sürümü aralığı arasında kurumsal kullanım için lisanslanır ve bu istemci sürümlerini (daha önceki bir hizmet tabanında kalacak şekilde yapılandırılmamış) 16.9.0 olarak güncelleştirir. 
* **Visual Studio 2019 sürüm 16.8.0 to 16.8.7 update** , istemci üzerinde 16.8.0 ile 16.8.7 arasındaki sürümler arasında kurumsal kullanım için lisanslı Visual Studio 2019 sürümleri için geçerlidir ve bu istemci sürümlerini 16.8.7 olarak güncelleştirir.

::: moniker-end

::: moniker range=">=vs-2022"

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Visual Studio güncelleştirmelerini dağıtmak için Configuration Manager kullanma

### <a name="understanding-configuration-options"></a>Yapılandırma seçeneklerini anlama

Visual Studio yönetici güncelleştirmelerini kuruluşunuzun dağıtım tercihleri ve gereksinimleriyle uyumlu olacak şekilde uyarlamak için kullanılabilecek birkaç yapılandırma seçeneği vardır. En yaygın yapılandırma seçenekleri aşağıda listelenmiştir. desteklenen tüm yönetici güncelleştirme davranışlarının ayrıntılı bir listesi için, bkz. [Visual Studio yüklemek için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) ve yalnızca "güncelleştir" eylemine karşılık gelen bir uyarı ödeme.

* **[Yönetici güncelleştirme katılımı](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)**: Bu kayıt defteri anahtarı, istemci makinenin yönetici güncelleştirmelerini alması için gereklidir. bu, bir makine genelindeki anahtardır ve bu, kutuda yüklü olan tüm Visual Studio örneklerine uygulanmasıdır.
* **Visual Studio kullanıcı geri çevirme**: Visual Studio kullanıcılar, Visual Studio yönetici güncelleştirmelerini almayı *devre dışı* bırakmak için ayrı bir makine genelinde **AdministratorUpdatesOptOut** kayıt defteri anahtarı kullanabilir. bu anahtarın amacı, Visual Studio kullanıcının makineye güncelleştirmelerin otomatik olarak uygulanmasını sağlamak için bir denetime sahip olmasına izin versağlamaktır. İstemci bilgisayarı yönetici güncelleştirmelerini engelleyecek şekilde yapılandırmak için, **AdministratorUpdatesOptOut**   REG_DWORD anahtarını **1** olarak ayarlayın. anahtarın yokluğu veya **0** kümesi değeri, Visual Studio kullanıcının Visual Studio için yönetici güncelleştirmelerini almak istediği anlamına gelir.
     ****   Kullanıcı tercihini kodlamaya yönelik ADMINISTRATORUPDATESOPTOUT anahtarının, BT Yöneticisi hedefini kodlayan **tınupdatesenabled** anahtarı üzerinden önceliklendirildiğini unutmayın   .  **AdministratorUpdatesOptOut**    **1** olarak ayarlandıysa, \Administrators istemci üzerinde engelleniyordu, ancak **admupdatesenabled**   anahtarı da **1** olarak ayarlanmış olsa bile.Bu eylem, BT yöneticilerinin hangi geliştiricilerin kabul etmek istediğinizi ve bu kişilerin ne kadar önemli olduğunu anlatabileceği anlamına gelir.BT yöneticileri her zaman istedikleri zaman her iki anahtarı da değiştirebilir.
* **Güncelleştirilmiş ürün bitlerinin konumu**: çoğu zaman, Istemci makineleri Microsoft CDN aracılığıyla Internet 'ten güncelleştirilmiş ürün bitlerini indirir. Bu senaryo, istemci makinelerin internet erişimine sahip olmasını gerektirir. Bununla birlikte, bazı kuruluşlar, istemci makinelerini yalnızca bir iç ağ düzeni konumundan BITS yüklemek ve güncelleştirmek üzere kısıtlar. Yönetici güncelleştirmelerinin dahili bir ağ konumunda bulunan güncelleştirilmiş bitler kullanılarak uygulanabileceğini sağlamak için, yönetici güncelleştirmesinin başarıyla dağıtılması için aşağıdaki koşulların doğru olması gerekir: 
  * İstemci makinenin bir noktada zaten bu ağ düzeni konumundan bir önyükleyiciyi çalıştırması gerekir. İdeal olarak, özgün istemci yüklemesi ağ düzeninden önyükleyici kullanılarak gerçekleşmiş olur, ancak aynı ağ konumunda güncelleştirilmiş bir önyükleyici kullanarak yalnızca bir güncelleştirme yüklemek de mümkündür. Bu eylemlerden biri, söz konusu düzen konumuyla bir bağlantı olan istemci makinesine katıştırılabilir.
  * Ağ düzeni konumunun (istemcinin bağlandığı yer), yönetici güncelleştirmesinin dağıtmak istediği [Güncelleştirilmiş ürün bitlerini içerecek şekilde güncelleştirilmesi](../install/update-a-network-installation-of-visual-studio.md) gerekir.

::: moniker range=">=vs-2019"

* **hizmet ana hat sürekliliği**: yukarıda açıklanan şekilde, yönetici özelliği güncelleştirmeleri ürünün daha güncel bir alt sürümüne Visual Studio bir yükleme ilerledi. ancak, bazı durumlarda Visual Studio kullanıcıların belirli bir kararlı ve güvenli hizmet temeli düzeyinde kalması ve makinelerinden daha güncel bir alt sürüme ne zaman ilerledikleri üzerinde kontrol olmaları gerekir. Bir istemci makinesini bir hizmet ana makinesinde kalacak ve kendisine gönderilen istenmeyen yönetici Özellik güncelleştirmelerini yoksaymaya yönelik olarak yapılandırmak için, **BaselineStickinessVersions2019** REG_SZ veri değerini oluşturmanız ve istemci makinenin üzerinde kalması gereken tercih edilen taban çizgisini temsil eden bir dizeye ayarlamanız gerekir. Dize, **16.7.0** gibi, izin verilen bir hizmet temeli sürümü içerebilir.  
     `BaselineStickinessVersions2019`Kayıt defteri değeri hatalı biçimlendirilmişse, tüm yönetici özelliği güncelleştirmelerinin makineye yüklenmesi engellenir. [Visual Studio özellik güncelleştirmeleri için desteklenen zaman çerçevelerine](/visualstudio/productinfo/vs-servicing-vs)dikkat edin. Ayrıca, anahtarın varlığı veya değeri ne olursa olsun, `BaselineStickinessVersions2019` yaşam sürelerinin sonuna ulaşan yönetici özelliği güncelleştirmelerinin uygulanması teknik olarak mümkün olsa da, destek dışı ve bu nedenle güvensiz olabilir.

::: moniker-end

* **Visual Studio kullanımda olsa bile güncelleştirmenin gerçekleşmesini zorla**: güncelleştirme yüklenmeden önce Visual Studio kapatılmalıdır. Visual Studio açıksa veya kullanılıyorsa, güncelleştirme yüklemesi iptal edilir. Visual Studio kapanmanın kolay bir yolu, bir makine yeniden başlatıldıktan sonra güncelleştirme hakkını uygulamak için onay yöneticisini yapılandırmaktır. Ayrıca, `--force` Visual Studio kapatmayı zorlamak için parametresini kullanabilirsiniz. Visual Studio kapanmaya zorlamak iş kaybına neden olabilir, bu nedenle dikkatli olun. Varsayılan sistem bağlamında bir yönetici güncelleştirmesi çalıştırıldığında bayrağı yok sayılacak, bu `–-force` nedenle yönetici güncelleştirmesini kullanıcı bağlamında çalıştırılacak şekilde yapılandırmanız gerekir.

### <a name="methods-for-configuring-an-administrator-update"></a>Yönetici Güncelleştirmesi yapılandırma yöntemleri

Yönetici güncelleştirmelerini yapılandırmanın üç ana yöntemi vardır: bir kayıt defteri anahtarı, istemci makinesindeki bir yapılandırma dosyası veya Configuration Manager dağıtım paketinin kendisi üzerinde değişiklik.   

* **kayıt defteri anahtarı**: yönetici güncelleştirmeleri, [kurumsal dağıtımlar için varsayılanları ayarlama](../install/set-defaults-for-enterprise-deployments.md)bölümünde açıklandığı gibi standart Visual Studio konumlarından herhangi birinde belirli kayıt defteri anahtarlarını arar. Kayıt defteri anahtarları tarafından denetlenen seçenekler, **AdministratorUpdatesOptOut** REG_DWORD, **AdministratorUpdatesOptOut**   REG_DWORD ve **BaselineStickinessVersions2019** REG_SZ gibi öğelerdir. İstemci bilgisayarda yönetici erişimi, kayıt defteri anahtarlarının değerini oluşturmak ve ayarlamak için gereklidir.

* **Yapılandırma dosyası**: bazı ayarlar, istemci makinesinde, yalnızca bir kez ayarlamaya ve gelecekteki tüm yönetici güncelleştirmelerine uygulanmasını sağlayan isteğe bağlı bir yapılandırma dosyasında korunabilir. yapılandırma dosyası yaklaşımı bir kayıt defteri anahtarı gibi davranır ve makine genişliğinde olduğundan, istemci makinesinde yüklü olan tüm Visual Studio yüklemeleri için geçerli olacaktır. Yapılandırma dosyası için standart konum: `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Ancak, dosyayı depolamak için başka bir konum kullanmak istiyorsanız, **Updateconfigurationfile** adlı bir REG_SZ kayıt defteri anahtarı oluşturarak ve bu anahtarın değerini yapılandırma dosyanızın yoluna ayarlayarak bunu yapabilirsiniz. bu kayıt defteri anahtarı, [kurumsal dağıtımlar için varsayılanları ayarlama](../install/set-defaults-for-enterprise-deployments.md)bölümünde açıklandığı gibi Visual Studio kayıt defteri konumlarından birine yer alabilir. Özel yapılandırma dosyası konumu için bir kayıt defteri değeri eklemeyi seçerseniz, bu dosya için arama yapılır; Dosya yoksa, bir özel durum oluşturulur ve güncelleştirme başarısız olur.

     JSON biçimindeki yapılandırma dosyası, `installerUpdateArgs` Visual Studio yükleyiciye geçirebilmeniz için daha fazla anahtar belirten virgüller ile ayrılmış bir dize dizisi olan seçeneği destekler. Dosyanın içeriği geçersiz bir alan veya desteklenmeyen bir seçenek içeriyorsa, güncelleştirme başarısız olur. Daha fazla bilgi için bkz. [Visual Studio yüklemek için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md).

   Örnek bir yapılandırma dosyası aşağıda verilmiştir:

  ```json
  "installerUpdateArgs" : ["--quiet", "--noWeb"], 
  "checkPendingReboot" :  "true" 
  ```

* **SCCM 'de yönetici güncelleştirmeleri paketini el ile güncelleştirme**: SCCM 'de tek yönetici güncelleştirme paketinin komut satırı parametreleri de el ile değiştirilebilir.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Doğrulama, raporlar ve sorun giderme hata kodları

### <a name="determining-that-visual-studio-was-updated"></a>Visual Studio güncelleştirildiğini belirleme

Yönetici güncelleştirmesinin doğru şekilde yüklendiğini doğrulamak için aşağıdaki yöntemlerden birini kullanabilirsiniz:

* istemci bilgisayarda Visual Studio başlatın, **yardım**   >  **hakkında**' yı seçin ve sürüm numarasının hedeflenen güncelleştirmenin başlığındaki son numarayla eşleştiğini doğrulayın.
* bilgisayardaki çeşitli Visual Studio sürümlerini belirlemek için istemci makinesinde **vswhere** aracını kullanın. daha fazla bilgi için bkz. [Visual Studio örnekleri algılama ve yönetme araçları](../install/tools-for-managing-visual-studio-instances.md).
* Her Yönetimsel güncelleştirme denemesi, istemci makinesi `%temp%` dizininde güncelleştirme işleminin ilerlemesini yakalayan birkaç günlük dosyası oluşturur.klasörü tarihe göre sıralayın ve  `dd_updatedriver`  `dd_bootstrapper`  `dd_client`  `dd_setup`   yönetim güncelleştirmeleri, önyükleyici, Visual Studio Yükleyicisi ve kurulum altyapısı için sırasıyla,,, ve için başlayan dosyaları arayın.Bu günlük dosyalarının, güncelleştirmenin başarıyla uygulandığını belirten 0 içerdiğini doğrulayın. Bu günlük dosyalarının, yapılandırma dosyasının kullanıldığını doğrulamak için de kullanılabilir olduğunu unutmayın. daha fazla ayrıntı için [Visual Studio günlük toplama aracına](https://www.microsoft.com/download/details.aspx?id=12493) bakın.

### <a name="error-codes-and-conditions"></a>Hata kodları ve koşulları

>[!IMPORTANT]
> güncelleştirmeyi yüklemeden önce Visual Studio kapatılması gerektiğini unutmayın. Visual Studio açıksa veya kullanılıyorsa, güncelleştirme yüklemesi iptal edilir.

Yönetim güncelleştirmeleri aşağıdaki dönüş kodlarını döndürebilir:  

| Hata kodu | Tanım                                                                                                                                                                                                  |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0          | Yönetimsel güncelleştirme başarıyla yüklendi.                                                                                                                                                       |
| 1001       | Visual Studio ınstaller veya ilgili bir kurulum işlemi çalışıyor. Güncelleştirme uygulanmadı.                                                                                                                   |
| 1002       | Visual Studio Yükleyicisi duraklatıldı. Güncelleştirme uygulanmadı.                                                                                                                                               |
| 1003       | Visual Studio çalışıyor. Güncelleştirme uygulanmadı. Bu koşul bayrağı kullanılarak geçersiz kılınabilir `--force` .                                                                                              |
| 1004       | Algılanan internet yok.Güncelleştirme, güncelleştirilmiş dosyaları tutan Internet konumuyla iletişim kuramadı. Güncelleştirme uygulanmadı.                                                                          |
| 1005       |  **Tınupdatesenabled**   kayıt defteri değeri **0** olarak ayarlanmış veya hiç ayarlanmamış. Güncelleştirme uygulanmadı.                                                                                            |
| 1006       |  **AdministratorUpdatesOptOut**   kayıt defteri değeri **1** olarak ayarlanır. Güncelleştirme uygulanmadı. Anahtar, yönetici tarafından güncelleştirilmemiş istemci bilgisayarlara yöneliktir.                     |
| 1007       | Visual Studio Yükleyicisi yüklenmedi.                                                                                                                                                               |
| 1008       | **BaselineStickinessVersions2019** kayıt defteri değeri okunabilir bir biçimde değil. Kayıt defteri değeri, derleme numarası 0 olarak ayarlanmış **Tüm** veya geçerli sürümleri içermelidir, örneğin, X. Y. 0. |
| 3010       | Sistemin yeniden başlatılması gerekiyor.Güncelleştirme veya uygulanmamış olabilir. Bilgisayarı yeniden başlatın ve güncelleştirmeyi yeniden deneyin.                                                                                |
| Diğer      | Güncelleştirme uygulanmaya çalışılırken hata oluştu.Güncelleştirme uygulanmadı.                                                                                                                                   |

İstemci hata kodlarının ayrıntılı bir listesi için bkz. [Visual Studio yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md).

## <a name="feedback-and-support"></a>Geri bildirim ve destek

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Visual Studio yönetici güncelleştirmeleri hakkında geri bildirim sağlamak veya güncelleştirmeleri etkileyen sorunları raporlamak için aşağıdaki yöntemleri kullanabilirsiniz:

* [yükleme ve yükseltme sorunları Visual Studio sorun giderme](../install/troubleshooting-installation-issues.md) kılavuzuna bakın.
* [Visual Studio kurulum Q ile bir Forum&](/answers/topics/vs-setup.html)topluluğa soru sorun.
* [Visual Studio destek sayfasına](https://visualstudio.microsoft.com/vs/support/)gidin ve sorunun sss bölümünde listelenip listelenmediğini denetleyin.  Sohbet yardımı için [destek bağlantısı](https://visualstudio.microsoft.com/vs/support/#talktous) düğmesini de seçebilirsiniz.
* Visual Studio ekibine, yönetici güncelleştirmelerini uygulama hakkında bu deneyimle ilgili [bir sorun bildirin veya özellik geri bildirimi sağlayın](https://aka.ms/vs/wsus/feedback) .
* Microsoft için kuruluşunuzun teknik hesap yöneticisiyle iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.

* [Yönetici güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md)
* [Visual Studio yönetici kılavuzu](../install/visual-studio-administrator-guide.md)
* [Visual Studio Ürün Yaşam Döngüsü ve Bakım](/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 Sürüm Notları](/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 Sürüm Notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Visual Studio yüklemek için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](../install/tools-for-managing-visual-studio-instances.md)
* [Visual Studio ağ yüklemesi oluşturma](../install/create-a-network-installation-of-visual-studio.md)
* [Yanıt dosyasındaki ayarları tanımlama](../install/automated-installation-with-response-file.md)
* [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](../install/controlling-updates-to-visual-studio-deployments.md)
* [Microsoft Update Catalog hakkında SSS](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM) belgeleri](/mem/configmgr)
* [Güncelleştirmeleri Microsoft kataloğundan Configuration Manager içine aktarın](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) belgeleri](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)
