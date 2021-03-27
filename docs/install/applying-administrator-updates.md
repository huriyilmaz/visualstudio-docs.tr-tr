---
title: Microsoft uç noktası ile Visual Studio 'ya yönetici güncelleştirmeleri uygulama Configuration Manager
titleSuffix: ''
description: Yönetici güncelleştirmelerini Visual Studio 'ya uygulamayı öğrenin.
ms.date: 03/10/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 78c2de8b1d1ffb28cc536b770bf6bd9a4ab0aa35
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2021
ms.locfileid: "105617336"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Microsoft uç noktası kullanan yönetici güncelleştirmelerini uygulama Configuration Manager

Bu belge, Visual Studio yönetici güncelleştirmelerinin farklı türlerini ve özelliklerini açıklamaktadır. Aşağıda, kuruluşunuzun tamamında nasıl ve ne zaman dağıtılacağı, hangi yapılandırma seçeneklerinin kullanılabildiği ve raporların nasıl görüntüleneceği ve nasıl giderileceği hakkında bilgi bulacaksınız. Yönetici güncelleştirmelerini kullanma önkoşulları hakkında daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md).

## <a name="understanding-visual-studio-administrator-updates"></a>Visual Studio Yönetici güncelleştirmelerini anlama 

Microsoft kataloğu ve WSUS tarafından kullanılmak üzere Microsoft Update yayımlanan Visual Studio Yöneticisi güncelleştirme paketi, Configuration Manager güncelleştirmeyi indirip istemci makinelerine dağıtmak için gereken bilgileri içerir. Ayrıca, kuruluş genelinde hangi güncelleştirmelerin dağıtılacağını belirlemek ve ağ düzenlerinin bakımını kolaylaştırmak için BT yöneticisinin ihtiyacı olan bilgileri de içerir. Visual Studio Yönetici güncelleştirme paketleri, ürünün yeni bir yüklemesini yapmak için yeterli bilgi içermez veya Content Delivery Network yayımlanan gerçek ürün ikililerini içerir. Visual Studio yönetici güncelleştirmeleri, normal Visual Studio güncelleştirmelerinde olduğu gibi birikimlidir. Daha yüksek bir ürün sürümü numarası ve daha sonraki bir sürüm tarihi olan herhangi bir Visual Studio güncelleştirmesinin daha eski, daha düşük bir sürümün üst kümesi olduğunu varsayabilirsiniz. 

Visual Studio yönetici güncelleştirmeleri, destek altında olan Visual Studio bakım sürümleri için geçerlidir. Belirli bir zaman çerçevesi sırasında hangi Visual Studio bakım temellerinin hala DESTEKDE olduğu hakkında daha fazla bilgi için bkz. [Visual Studio ürün yaşam döngüsü ve bakımı](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Desteklenen tüm Visual Studio bakım temelleri güvenli tutulacak.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Yönetici güncelleştirmelerinin türleri ve özellikleri 

Visual Studio 'Da üç tür yönetici güncelleştirmesi vardır:

* **Güvenlik güncelleştirmeleri** tüm Visual Studio sürümleri için geçerlidir (örneğin, Enterprise, Professional, Community, vb.) ve sınırlı, yüksek oranda hedeflenmiş ve uyumlu hizmet düzeyi değişiklikleri içerir. Güvenlik güncelleştirmeleri, bir istemciyi daha sonraki bir ikincil sürüme ilerlemez; Bunlar, zaten belirli bir alt sürüm düzeyinde olan bir istemciye güvenlik açıklarına yönelik düzeltmeler sunacak şekilde tasarlanmıştır. Güvenlik güncelleştirmelerinde en az bir güvenlik düzeltme olacaktır, ancak güvenlik düzeltme, istemci makinesine yüklenmiş bir bileşen veya iş yükü içinde olabilir veya olmayabilir. Örneğin, .NET bileşenlerinde bir güvenlik açığını çözebiliriz ve güncelleştirmeyi güvenlik güncelleştirmesi olarak etiketliyoruz, ancak aslında yalnızca C++ bileşenlerinin yüklü olduğu bir istemci makinesine gerçekten anlamlı bir etkiye sahip değildir. Güvenlik güncelleştirmeleri, diğer güvenilirlik düzeltmelerini veya diğer gerekli bileşen güncelleştirmelerini de içerebilir. Güvenlik güncelleştirmeleri, hem [Microsoft Update kataloğunda](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) hem de [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)'da yayımlanır ve burada "güvenlik güncelleştirmeleri" olarak sınıflandırılır.
 
* **Özellik güncelleştirmeleri** , BT yöneticilerinin kuruluştaki bilgisayarları, Visual Studio 2019 ' nin daha yeni bir alt sürümüne ilerlemelerini sağlar. Özellik güncelleştirmeleri, yalnızca kuruluşlarda kurumsal, profesyonel ve derleme araçları SKU 'Ları gibi yaygın olarak bulunan Visual Studio sürümleri için geçerlidir. Tüm özellik güncelleştirmeleri, Microsoft Update kataloğunda "özellik paketleri" olarak yayımlanacak ve isteğe bağlı olarak, [Microsoft Update kataloğundan el ile Configuration Manager içeri aktarmaları](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)sağlanır. Özellik güncelleştirmeleri birikimlidir ve ek kalite ve önceki güvenlik düzeltmelerini içerir. Bir istemci makinenin bir hizmet taban çizgisinde kalacak şekilde nasıl yapılandırılacağı ve özellik güncelleştirmelerinin belirli istemcilere teslim edilmesini önleyen yönergeler için aşağıdaki [yapılandırma seçenekleri bölümüne](#understanding-configuration-options) bakın. 

* **Kalite güncelleştirmeleri** , yalnızca kuruluşlarda yaygın olarak bulunan Visual Studio sürümleri için de geçerlidir ve sınırlı, yüksek oranda hedeflenmiş ve uyumlu hizmet düzeyi değişiklikleri içerirler. Kalite güncelleştirmeleri, bir istemciyi daha sonraki bir ikincil sürüme ilerlemez; Bunlar, zaten belirli bir alt sürüm düzeyinde olan bir istemciye performans ve güvenilirlik düzeltmeleri veya diğer gerekli bileşen güncelleştirmelerini sunacak şekilde tasarlanmıştır. Kalite güncelleştirmeleri güvenlik güncelleştirmeleriyle birlikte birikir ve bu nedenle yalnızca güvenlik düzeltmesi bağımsız olarak zaten yayımlanmışsa güvenlik düzeltmelerini içerir. Kalite güncelleştirmeleri, Microsoft Update kataloğunda "Güncelleştirmeler" olarak yayımlanır ve isteğe bağlı olarak Configuration Manager el ile [içeri aktarmak](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)için de kullanılabilir.

### <a name="decoding-the-titles-of-administrator-updates"></a>Yönetici güncelleştirmeleri başlıklarının kodunu çözme

Her yönetici güncelleştirmesinin başlığı, hem ilgili sürüm aralığını hem de güncelleştirmenin sonuç sürümünü açıklar.Örneğin,

* **Visual studio 2019 sürüm 16.7.0 to 16.7.12 Update** "Security Update" olarak sınıflandırılır, istemcideki 16.7.0 ile 16.7.12 arasındaki sürümler arasında tüm Visual Studio sürümleri için geçerlidir ve bu istemci sürümlerini 16.7.12 olarak güncelleştirir.  

* "Özellik paketi" olarak sınıflandırılan **Visual studio 2019 16.0.0 to 16.9.0 Update** , Istemcideki Visual Studio sürümleri için 16.0.0 ile 16.9.0 arasındaki tüm ürün sürümü aralığı arasında ve bu istemci sürümlerini (önceki bir hizmet ana bilgisayarında kalacak şekilde yapılandırılmamış), 16.9.0 olarak güncelleştirecek şekilde güncelleştirecektir. 

* **Visual studio 2019 sürüm 16.8.0 to 16.8.7 Update** , istemci üzerindeki 16.8.0 ile 16.8.7 arasındaki sürümler arasında Visual Studio sürümlerini seçme için geçerlidir ve bu istemci sürümlerini 16.8.7 olarak güncelleştirir. 

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Visual Studio güncelleştirmelerini dağıtmak için Configuration Manager kullanma

### <a name="understanding-configuration-options"></a>Yapılandırma seçeneklerini anlama

Visual Studio Yönetici güncelleştirmelerini, kuruluşunuzun dağıtım gereksinimleriyle uyumlu ve uyumlu olacak şekilde uyarlamak için kullanılabilecek birkaç yapılandırma seçeneği vardır. En yaygın seçenekler aşağıda listelenmiştir.  Yönetici güncelleştirmeleri tarafından desteklenen tüm komut satırı parametrelerinin ayrıntılı bir listesi için, [Visual Studio belgelerini yüklemek üzere komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) ve yalnızca "Güncelleştir" eylemine karşılık gelen eylemlere ödeme yapma bölümüne bakın.

* **Yönetici güncelleştirmesi kabul etme**: istemci makinenin yönetici güncelleştirmelerini alması için [yönetici güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md) bölümünde açıklanan bu kayıt defteri anahtarı gereklidir. Bu, bir makine genelindeki anahtardır ve bu, kutuda yüklü olan tüm Visual Studio örnekleri için geçerli olduğu anlamına gelir. 
 
* **Geliştirici geri çevirme**: geliştiriciler,    Visual Studio Yönetici güncelleştirmelerini almayı *devre dışı* bırakmak için ayrı bir makine genelinde AdministratorUpdatesOptOut anahtarı kullanabilir. Bu anahtarın amacı, Visual Studio kullanıcısının amacını kodlayamaktır. İstemci bilgisayarı yönetici güncelleştirmelerini engelleyecek şekilde yapılandırmak için, **AdministratorUpdatesOptOut**   REG_DWORD anahtarını **1** olarak ayarlayın. Anahtarın yokluğu veya **0** kümesi değeri, Visual Studio kullanıcısının Visual Studio 'ya yönetici güncelleştirmelerini almak istediği anlamına gelir.

     ****   BT Yöneticisi hedefini kodlayan, AdministratorUpdatesOptOut anahtarının (örneğin Geliştirici amacı Için), **tınupdatesenabled** anahtarı üzerinden önceliklendirildiğine unutmayın   .  **AdministratorUpdatesOptOut**    **1** olarak ayarlandıysa, \Administrators istemci üzerinde engelleniyordu, ancak **admupdatesenabled**   anahtarı da **1** olarak ayarlanmış olsa bile.Bu eylem, BT yöneticilerinin hangi geliştiricilerin kabul etmek istediğinizi ve bu kişilerin ne kadar önemli olduğunu anlatabileceği anlamına gelir.BT yöneticileri her zaman istedikleri zaman her iki anahtarı da değiştirebilir.
 
* **Güncelleştirilmiş ürün bitlerinin konumu**: çoğu zaman, Istemci MAKINELERI Microsoft CDN aracılığıyla Internet 'ten güncelleştirilmiş ürün bitlerini indirir. Bu senaryo, istemci makinelerin internet erişimine sahip olmasını gerektirir. Bununla birlikte, bazı kuruluşlar, istemci makinelerini yalnızca bir iç ağ düzeni konumundan BITS yüklemek ve güncelleştirmek üzere kısıtlar. Yönetici güncelleştirmelerinin bir iç ağ konumundan uygulanabileceğini sağlamak için aşağıdaki koşulların doğru olması gerekir: 

  - İstemci makinenin, ürünü bir ağ düzeni konumundan (örn. yerel yükleme önbelleği) yüklemiş olması gerekir. 
  - Bu ağ düzeni konumu (istemcinin başlangıçta yüklendiği), yönetici güncelleştirmesi tarafından belirtilen [Güncelleştirilmiş ürün bitlerini içerecek şekilde güncelleştirilmiştir](../install/update-a-network-installation-of-visual-studio.md) . 
 
* **Visual Studio kullanımda olsa bile güncelleştirmenin oluşmasını zorla**: güncelleştirmeyi yüklemeden önce Visual Studio kapatılmalıdır. Visual Studio açıksa veya kullanılıyorsa, güncelleştirme yüklemesi iptal edilir. Visual Studio 'Nun kapalı olduğundan emin olmanın kolay bir yolu, bir makine yeniden başlatıldıktan sonra güncelleştirme hakkını uygulamak için onay yöneticisini yapılandırmaktır. `--force`Visual Studio 'yu kapatmayı zorlamak için parametresini de kullanabilirsiniz. Visual Studio 'Nun kapatılmasını zorlamak iş kaybına neden olabilir, bu nedenle dikkatli olun. Varsayılan sistem bağlamında bir yönetici güncelleştirmesi çalıştırıldığında bayrağı yok sayılacak, bu `–-force` nedenle yönetici güncelleştirmesini kullanıcı bağlamında çalıştırılacak şekilde yapılandırmanız gerekir.
 
* **Hizmet ana hat sürekliliği**: yukarıda açıklanan şekilde, özellik güncelleştirmeleri olan yönetici güncelleştirmeleri bir Visual Studio yüklemesini ürünün daha güncel bir alt sürümüne ilerledi. Ancak bazı durumlarda, geliştirme ekipleri belirli bir kararlı ve güvenli hizmet temeli düzeyinde kalmak ve istemcilerinin daha güncel bir alt sürüme ne zaman ilerledikleri hakkında kontrol etmek gibi. Bir istemci makinesini bir hizmet ana makinesinde kalacak ve kendisine gönderilen istenmeyen yönetici Özellik güncelleştirmelerini yoksayacak şekilde yapılandırmak için, **BaselineStickinessVersions2019** REG_SZ veri değerini oluşturmanız ve istemci makinesinin üzerinde kalabileceğini izin verilen taban çizgilerini temsil eden bir dizeye ayarlamanız gerekir.  Dize, **16.4.0, 16.7.0** gibi virgülle ayırarak bir hizmet ana hat sürümü dizisi içerebilir. Herhangi bir sayıda hizmet temeli sürümü, dizeye dahil edilebilir ve tüm desteklenen hizmet temellerine başvurmak için toplu olan **Tüm** sözcük de desteklenir. 

     `BaselineStickinessVersions2019`Kayıt defteri değeri hatalı biçimlendirilmişse, tüm özellik güncelleştirmelerinin makineye yüklenmesi engellenir. Ayrıca, lütfen [Visual Studio özellik güncelleştirmelerine yönelik desteklenen zaman çerçevelerine](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)dikkat edin. Yaşam sürelerinin sonuna ulaşan Özellik güncelleştirmelerini uygulamak teknik olarak mümkün olsa da, destek dışı ve bu nedenle güvensiz olabilecek özellikler için önerilmez.

### <a name="methods-for-configuring-an-administrator-update"></a>Yönetici Güncelleştirmesi yapılandırma yöntemleri

Yönetici güncelleştirmelerini yapılandırmanın üç ana yöntemi vardır: bir kayıt defteri anahtarı, istemci makinesindeki bir yapılandırma dosyası veya Configuration Manager dağıtım paketinin kendisi üzerinde değişiklik.   

* **Kayıt defteri anahtarı**: yönetici güncelleştirmeleri, [kurumsal dağıtımlar Için Varsayılanları Ayarla] belgelerinde açıklandığı gibi standart Visual Studio konumlarından herhangi birinde belirli kayıt defteri anahtarlarına bakar. Kayıt defteri anahtarları tarafından denetlenen seçenekler, **AdministratorUpdatesOptOut** REG_DWORD, **AdministratorUpdatesOptOut**   REG_DWORD ve **BaselineStickinessVersions2019** REG_SZ gibi öğelerdir. İstemci bilgisayarda yönetici erişimi, kayıt defteri anahtarlarının değerini oluşturmak ve ayarlamak için gereklidir. 
 
* **Yapılandırma dosyası**: bazı ayarlar, istemci makinesinde, yalnızca bir kez ayarlamaya ve gelecekteki tüm yönetici güncelleştirmelerine uygulanmasını sağlayan isteğe bağlı bir yapılandırma dosyasında korunabilir. Yapılandırma dosyası yaklaşımı bir kayıt defteri anahtarı gibi davranır ve makine genişliğinde olur ve bu, istemci makinesine yüklenen tüm Visual Studio yüklemelerine uygulanacak anlamına gelir. Yapılandırma dosyası için standart konum: `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Ancak, dosyayı depolamak için başka bir konum kullanmak istiyorsanız, **Updateconfigurationfile** adlı bir REG_SZ kayıt defteri anahtarı oluşturarak ve bu anahtarın değerini yapılandırma dosyanızın yoluna ayarlayarak bunu yapabilirsiniz. Bu kayıt defteri anahtarı, [Kurumsal dağıtımlarda ayarlanan varsayılanlar](../install/set-defaults-for-enterprise-deployments.md)bölümünde açıklandığı gibi, Visual Studio kayıt defteri konumlarından herhangi birine yer alabilir. Özel yapılandırma dosyası konumu için bir kayıt defteri değeri eklemeyi seçerseniz, bu dosya için arama yapılır; Dosya yoksa, bir özel durum oluşturulur ve güncelleştirme başarısız olur.    
 
JSON biçimindeki yapılandırma dosyası, `installerUpdateArgs` Visual Studio yükleyicisine geçirebilmeniz için daha fazla anahtar belirten virgüller ile ayrılmış bir dize dizisi olan seçeneği destekler. Dosyanın içeriği geçersiz bir alan veya desteklenmeyen bir seçenek içeriyorsa, güncelleştirme başarısız olur. Daha fazla bilgi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md).
 
Örnek bir yapılandırma dosyası aşağıda verilmiştir: 

```
“installerUpdateArgs” : [“--quiet”, “--noWeb”], 

“checkPendingReboot” :  “true” 
```

* **SCCM 'de yönetici güncelleştirmeleri paketini el ile güncelleştirme**: SCCM 'de tek yönetici güncelleştirme paketinin komut satırı parametreleri de el ile değiştirilebilir.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Doğrulama, raporlar ve sorun giderme hata kodları

### <a name="determining-that-visual-studio-was-updated"></a>Visual Studio 'Nun güncelleştirildiğini belirleme

Yönetici güncelleştirmesinin doğru şekilde yüklendiğini doğrulamak için aşağıdaki yöntemlerden birini kullanabilirsiniz: 

* İstemci bilgisayarda, Visual Studio 2019 ' u başlatın, **Yardım**   >  **hakkında**' yı seçin ve sürüm numarasının hedeflenen güncelleştirmenin başlığındaki Son numarayla eşleştiğini doğrulayın. 

* Bilgisayardaki Visual Studio 'nun çeşitli sürümlerini tanımlamak için istemci makinesinde **vswhere** aracını kullanın. Daha fazla bilgi için bkz. [Visual Studio örneklerini algılamak ve yönetmek Için Araçlar](../install/tools-for-managing-visual-studio-instances.md). 

* Her Yönetimsel güncelleştirme denemesi, istemci makinesi `%temp%` dizininde güncelleştirme işleminin ilerlemesini yakalayan birkaç günlük dosyası oluşturur.Klasörü tarihe göre sıralayın ve  `dd_updatedriver`  `dd_bootstrapper`  `dd_client`  `dd_setup`   Yönetim güncelleştirmeleri, önyükleyici, Visual Studio yükleyicisi ve kurulum altyapısı için sırasıyla,,, ve için başlayan dosyaları arayın.Bu günlük dosyalarının, güncelleştirmenin başarıyla uygulandığını belirten 0 içerdiğini doğrulayın. Bu günlük dosyalarının, yapılandırma dosyasının kullanıldığını doğrulamak için de kullanılabilir olduğunu unutmayın. Daha fazla ayrıntı için [Visual Studio günlük toplama aracına](https://www.microsoft.com/download/details.aspx?id=12493) bakın.     

### <a name="error-codes-and-conditions"></a>Hata kodları ve koşulları

>[!IMPORTANT]
> Güncelleştirmeyi yüklemeden önce Visual Studio 'Nun kapatılması gerektiğini unutmayın. Visual Studio açıksa veya kullanılıyorsa, güncelleştirme yüklemesi iptal edilir.

Yönetim güncelleştirmeleri aşağıdaki dönüş kodlarını döndürebilir:  

| Hata kodu | Tanım |
|--|:-|
| 0 | Yönetimsel güncelleştirme başarıyla yüklendi. |
| 1001 | Visual Studio Yükleyicisi veya ilgili bir kurulum işlemi çalışıyor. Güncelleştirme uygulanmadı. |
| 1002 | Visual Studio Yükleyicisi duraklatıldı. Güncelleştirme uygulanmadı. |
| 1003 | Visual Studio çalışıyor. Güncelleştirme uygulanmadı. Bu koşul bayrağı kullanılarak geçersiz kılınabilir `--force` . |
| 1004 | Algılanan internet yok.Güncelleştirme, güncelleştirilmiş dosyaları tutan Internet konumuyla iletişim kuramadı. Güncelleştirme uygulanmadı. |
| 1005 |  **Tınupdatesenabled**   kayıt defteri değeri **0** olarak ayarlanmış veya hiç ayarlanmamış. Güncelleştirme uygulanmadı. |
| 1006 |  **AdministratorUpdatesOptOut**   kayıt defteri değeri **1** olarak ayarlanır. Güncelleştirme uygulanmadı. Anahtar, yönetici tarafından güncelleştirilmemiş istemci bilgisayarlara yöneliktir. |
| 1007 | Visual Studio Yükleyicisi yüklenmedi. |
| 1008 | **BaselineStickinessVersions2019** kayıt defteri değeri okunabilir bir biçimde değil. Kayıt defteri değeri, derleme numarası 0 olarak ayarlanmış **Tüm** veya geçerli sürümleri içermelidir, örneğin, X. Y. 0. |
| 3010 | Sistemin yeniden başlatılması gerekiyor.Güncelleştirme veya uygulanmamış olabilir. Bilgisayarı yeniden başlatın ve güncelleştirmeyi yeniden deneyin. |
| Diğer | Güncelleştirme uygulanmaya çalışılırken hata oluştu.Güncelleştirme uygulanmadı. |

İstemci hata kodlarının ayrıntılı bir listesi için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md). 

## <a name="feedback-and-support"></a>Geri bildirim ve destek
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Visual Studio yönetici güncelleştirmeleri hakkında geri bildirim sağlamak veya güncelleştirmeleri etkileyen sorunları bildirmek için aşağıdaki yöntemleri kullanabilirsiniz:
* [Visual Studio yükleme ve yükseltme sorunlarını giderme](../install/troubleshooting-installation-issues.md) kılavuzuna bakın.
* [Visual Setup soru-cevap&](https://docs.microsoft.com/answers/topics/vs-setup.html)topluluğa soru sorabilirsiniz.
* [Visual Studio destek sayfasına](https://visualstudio.microsoft.com/vs/support/)gidin ve sorunun SSS bölümünde listelenip listelenmediğini denetleyin.  Sohbet yardımı için [destek bağlantısı](https://visualstudio.microsoft.com/vs/support/#talktous) düğmesini de seçebilirsiniz.
* Bu deneyim için [özellik geri bildirimi sağlayın veya Visual Studio ekibine bir sorun bildirin](https://aka.ms/vs/wsus/feedback) .
* Microsoft için kuruluşunuzun teknik hesap yöneticisiyle iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.
* [Yönetici güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md)    
* [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)
* [Visual Studio Ürün Yaşam Döngüsü ve Bakım](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 Sürüm Notları](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 Sürüm Notları](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio'yu yükleme](../install/install-visual-studio.md)
* [Visual Studio 'Yu yüklemek için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](../install/tools-for-managing-visual-studio-instances.md)
* [Visual Studio 'nun ağ yüklemesi oluşturma](../install/create-a-network-installation-of-visual-studio.md)
* [Yanıt dosyasındaki ayarları tanımlama](../install/automated-installation-with-response-file.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](../install/controlling-updates-to-visual-studio-deployments.md)
* [Microsoft Update Catalog hakkında SSS](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft uç nokta Configuration Manager (SCCM) belgeleri](https://docs.microsoft.com/mem/configmgr)
* [Güncelleştirmeleri Microsoft kataloğundan Configuration Manager içine aktarın](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) belgeleri](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
