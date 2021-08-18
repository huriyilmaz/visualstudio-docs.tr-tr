---
title: Dotfuscator 5'Community yükseltme
ms.date: 07/21/2021
ms.devlang: dotnet
ms.topic: how-to
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio, upgrade, komut satırı
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Visual Studio'a dahil edilen Dotfuscator Community 5'in ücretsiz kopyasını Visual Studio.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: c1a6375a26325ca6f297b78a3024117e6e39132f
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334938"
---
# <a name="upgrade-from-dotfuscator-community-5"></a>Dotfuscator 5'Community yükseltme

PreEmptive Protection ' a yükseltmeyi öğrenin - Dotfuscator Community 6.

Yükleme geçmişinize ve Visual Studio sürümüne bağlı olarak, şu anda önceki ana sürüm olan Dotfuscator Community 5'i çalıştırıyor olabilirsiniz. Öyleyse, kodunuz için en son koruma önlemlerinin verildiğini sağlamak önemli olduğundan [yükseltmeniz gerekir.][always-improving] Yükseltmeler ücretsiz olarak kullanılabilir.

Bu makalede, şu anda hangi sürüme sahip olduğunu belirleme, gerekirse sürüm 6'ya yükseltme ve iki sürüm arasında hangi özelliklerin değiştirıldığı veya kaldırıldığı açıklanmıştır.

## <a name="determine-the-dotfuscator-version"></a>Dotfuscator sürümünü belirleme

Hangi Dotfuscator sürümünü çalıştırabilirsiniz emin değilseniz, aşağıdaki seçeneklerden birini yaparak sürümü belirlenebilirsiniz:

* Visual Studio'nin Araçlar menüsüne gidip **PreEmptive Protection - Dotfuscator**  Community seçeneğini kullanarak Dotfuscator Community grafik kullanıcı [arabirimini][gui] (GUI) Community.

  Dotfuscator GUI'lerinden **Yardım** menüsünü açın ve **Hakkında...** öğesini seçerek Hakkında ekranı açın.
  
  Bu ekranda Dotfuscator'ın sürümü listele gösterilir.

* Derlemenize komut satırı [arabirimiyle][cli] [(Xamarin][xamarin] uygulamaları gibi) tümleştirilmiş Dotfuscator varsa, derleme günlüklerinizi aşağıdaki örnekte olduğu gibi bir satır için de kontrol edin:

  ```no-highlight
  Dotfuscator Community Version 5.42.0.9514-e0e25f754
  ```

  Bu metni görmek için derlemenizin ayrıntılılık sayısını artırmanız gerekir.
  Daha Visual Studio için [bkz. Ayrıntılı Ayarlar.][verbosity]

Sürümün ilk tamsayısı, ilk noktadan önce `.` Dotfuscator'ın ana sürümünü gösterir. İlk tamsayı ise, en son Dotfuscator 6 özelliklerinden ve koruma güncelleştirmelerinden yararlanmak için yükseltme adımlarını bu `5` sayfada gerçekleştirmeniz gerekir.

## <a name="upgrade-instructions"></a>Yükseltme yönergeleri

Bu bölüm, Dotfuscator'ın tipik kullanımlarını sürüm 5'Community 6'ya yükseltmeye ilişkin yönergeler kümelerini içerir.

### <a name="install-dotfuscator-6"></a>Dotfuscator 6'ya yükleme

Dotfuscator Community, uygulamanın uzantısı olarak Visual Studio. Dotfuscator 6'nın yükleme yönergeleri sahip olduğunuz sürüme Visual Studio değişiklik gösterir:

* **Visual Studio 2019** Dotfuscator Community 6, Visual Studio 2019'un sonraki sürümlerinde (sürüm 16.10.0 ve sonrası) yer alır.
  [2019 Visual Studio en son][vs-update] sürüme güncelleştirin. Güncelleştirme Visual Studio, dotfuscator Community 5 yüklemesini otomatik olarak Dotfuscator Community 6'ya yükseltiyor.

    * Dotfuscator'ı henüz yüklememişsinizdir, önce Visual Studio'i güncelleştirin ve yükleme'ye [bakın.][install]

    * Visual Studio sürümlerine ek olarak, [Dotfuscator][download] İndirmeleri sayfasından her zaman Dotfuscator Community en son sürümlerini de edinebilirsiniz.

* **Visual Studio 2017** Bu sürüm Visual Studio yalnızca Dotfuscator Community 5 ile gönderilir.
  Ancak [Dotfuscator İndirmeleri][download] sayfasına gidip uygun indirme bağlantısını seçerek Dotfuscator Community 6'ya yükleyebilir veya yükseltebilirsiniz.

  İndirilen dosyayı çalıştırın ve istemleri takip edin `.vsix` ve Dotfuscator Community 6'Visual Studio. Mevcut Dotfuscator Community 5 yüklemesi de yükseltilecek.

* **Visual Studio'nin önceki sürümleri** Dotfuscator Community 6, bu sürümlerde Visual Studio.
  Daha yeni bir Visual Studio sürümüne yükseltmenizi veya [Dotfuscator Community'den Dotfuscator'a yükseltmenizi Professional.][pro]

[Dotfuscator'Community][register] 5'i daha önce kaydettiyebilirsiniz. Bu kayıt, Dotfuscator'Community 6'ya ilk kez Community.

<a name="steps-cli"></a>

### <a name="update-paths-to-the-cli"></a>CLI yollarını güncelleştirme

Daha önce, uygulamanızı korumak için Dotfuscator 5'in komut satırı [arabirimini][cli] (CLI) kullandıysanız, tüm projelerde CLI yolunu güncelleştirmeniz ve buna başvurulan betikler derlemeniz gerekir. Dotfuscator kullanan projeleri ve Community [Xamarin tümleştirmesi içerir.][xamarin]

Dotfuscator'ın CLI'sine giden yolun artık geçersiz olması, Dotfuscator Community dotfuscator 6'da yüklü olan yürütülebilir dosyalardan bazılarının adlarının değişmesi olabilir. Bu değişiklik, bu yürütülebilir adların Dotfuscator Community ve Dotfuscator dosyalarında aynı Professional.

| Yürütülebilir dosya...                     | Dotfuscator 5         | Dotfuscator 6         |
|---------------------------------------|-----------------------|-----------------------|
| [GUI][gui] | `dotfuscator.exe`     | `dotfuscatorUI.exe`   |
| [CLI][cli]   | `dotfuscatorCLI.exe`  | `dotfuscator.exe`     |

> [!NOTE]
> Dotfuscator CLI, Visual Studio'ın yükleme dizininde yüklü olduğu için Visual Studio veya switch Visual Studio sürümleri arasında yükseltme yaptısanız CLI yolu Visual Studio geçersiz olabilir.
Aşağıda listelenen belirtiler ve çözüm de bu senaryo için geçerlidir.

Derlemeniz geçersiz bir Dotfuscator CLI yolu kullanıyorsa, aşağıdaki örneklerden biri gibi hatalar elde edersiniz:

`'"[...]\PreEmptiveSolutions\DotfuscatorCE\dotfuscatorCLI.exe"' is not recognized as an internal or external command,
operable program or batch file.`

`The command ""[...]\PreEmptiveSolutions\DotfuscatorCE\dotfuscatorCLI.exe" Dotfuscator.xml" exited with code 9009.`

`When the DotfuscatorXamarinEnabled property is 'true', the Dotfuscator command line interface specified by
DotfuscatorXamarinCliPath ('[...]\DotfuscatorCE\dotfuscatorCLI.exe') must exist.`

Derlemenizi doğru CLI yolunu kullanmak üzere güncelleştirmek için:

1. Visual Studio'nin Community Araçlar menüsüne [][gui] gidip **PreEmptive Protection - Dotfuscator** Community. 
   
2. Dotfuscator Community GUI'sinde Araçlar menüsüne gidin ve **Dotfuscator Komut İstemi'ne tıklayın.** 

3. Açılan komut istemine `where dotfuscator.exe` yazın.
   Görüntülenen ilk yolu daha sonra başvuru için düz metin belgesine kopyalayın. Bu yol, 6'nın CLI'sini Community Dotfuscator'ın yeni yoludur.

4. Projeyi veya derleme yapılandırmasını derleme sisteminiz için uygun şekilde açın.

    * Proje Visual Studio proje dosyasını ( , veya ) düz `.csproj` `.vbproj` metin olarak `.fsproj` açmanız gerekir. [Bir proje dosyasını Visual Studio.](../solutions-and-projects-in-visual-studio.md#project-file)
    
    * Daha önce bir [Xamarin][xamarin] uygulamasını korumak için Dotfuscator Community'nin Xamarin tümleştirmesini kullandıysanız, Dotfuscator'ın paylaşılan kitaplık projelerine değil ayrı ayrı her uygulama projesine (ve gibi) tümleştiril olduğunu `MyProject.Android.csproj` `MyProject.iOS.csproj` hatırlayın.
      Şu anda Dotfuscator kullanan tüm uygulama projelerini güncelleştirmeniz gerekir.

5. Projenizin içinde veya 5 CLI'sı için eski bir Dotfuscator yolunun Community herhangi bir yer bulun.
   Bu genellikle ile biten bir `dotfuscatorCLI.exe` yoldur.

    * Dotfuscator kullanarak Community [Xamarin][xamarin] tümleştirmesini güncelleştiriyorsanız, eski yol ve etiketleri arasında `<DotfuscatorXamarinCliPath>` `</DotfuscatorXamarinCliPath>` bulunur.

6. 5. adımda yer alan eski yolları, 3. adımda not not alan yeni yol ile değiştirin.
   
   Eski yollardan biri mutlak bir yol yoksa, yeni yolu bağlama göre uygun şekilde ayarlamanız gerekir.
   Aşağıdaki örnekte, eski `VSInstallDir` yolda ortam değişkeni kullanılmıştır, bu nedenle buna karşılık gelen yeni yol da bunu yapar.

    * 3. adımdan yeni yol: `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\Common7\IDE\Extensions\PreEmptiveSolutions\DotfuscatorCE\dotfuscator.exe`
    * Proje dosyasındaki eski yol: `%VSInstallDir%\Common7\IDE\Extensions\PreEmptiveSolutions\DotfuscatorCE\dotfuscatorCLI.exe`
    * Proje dosyasındaki yeni yol: `%VSInstallDir%\Common7\IDE\Extensions\PreEmptiveSolutions\DotfuscatorCE\dotfuscator.exe`

7. Git gibi bir kaynak denetim sistemi kullanıyorsanız, 6. adımda yapılan değişikliklerin bu sisteme yansıtıldıklarından emin olun.
   Sisteminize ve organizasyona uygun olması için bu değişiklikleri takımınıza dağıtin.

> [!WARNING]
> `dotfuscator.exe`Dotfuscator 5'te grafik kullanıcı arabirimine (GUI) başvurduğu, ancak Dotfuscator 6'daki komut satırı arabirimine (CLI) başvurduğu için, birden çok makine arasında paylaşılan derleme betiklerini güncelleştiriyorken dikkatli olun.
>
> Dotfuscator 6 için güncelleştirilmiş bir betik çalıştıran Dotfuscator 5 yüklü bir makine, betiğin hedeflenen komut satırı arabirimi yerine grafik kullanıcı arabirimini başlatmasına neden olur. **Bu, Dotfuscator'ın korumasını uygulamamalarına rağmen derlemenin başarılı olmasına neden olabilir, yani çıkış paketleriniz KORUNMAZ.**
>
> Diğer durumlarda, bunun yerine bir derleme hatasına neden olabilir.
>
> Bu senaryoları önlemek için Tüm makineleriniz genelinde Dotfuscator Community sürüm 5'den sürüm 6'ya yükseltin ve aynı anda betikler derlemeniz gerekir.

<a name="steps-config-files"></a>

### <a name="upgrade-dotfuscator-config-files"></a>Dotfuscator yapılandırma dosyalarını yükseltme

*Tüm* `Dotfuscator.xml`Dotfuscator 6'dan önce oluşturulan Dotfuscator yapılandırma dosyalarının (örneğin) yükseltilleri gerekir.

Dotfuscator CLI'sini eski bir yapılandırma dosyasıyla çalıştırmayı denersanız aşağıdaki örneklerde olduğu gibi hatalar elde edersiniz:

`Dotfuscator Engine Initialization error: PreEmptive Analytics, Authenticode signing, and the Introduce Explicit Method Overrides
setting are no longer supported. Please open your Dotfuscator config in the Config Editor which will automatically upgrade it.`

> [!IMPORTANT]
> Bu hatayı alırsınız ve belirtilen özellikleri kullanmasanız bile yapılandırma dosyanızı yükseltmeniz gerekir.

Bir yapılandırma dosyasını yükseltmek için:

1. Visual Studio'nin Araçlar menüsüne gidip **PreEmptive Protection - Dotfuscator**  Community seçeneğini kullanarak Dotfuscator Community grafik kullanıcı [arabirimini][gui] (GUI) Community.

2. Söz konusu Dotfuscator yapılandırma dosyasını açın (Ctrl+O).

3. Derleme Çıkışı sekmesinde aşağıdaki *ileti* görüntülenir:

    `PreEmptive Analytics, Authenticode signing, and the Introduce Explicit Method Overrides setting are no longer supported.
   The associated settings have been removed. Please save your upgraded Dotfuscator config.`

4. Güncelleştirilmiş Dotfuscator yapılandırma dosyasını (Ctrl+S) kaydedin.

5. Git gibi bir kaynak denetim sistemi kullanıyorsanız Dotfuscator yapılandırma dosyasındaki değişikliklerin bu sisteme yansıtıldıklardan emin olun.
   Sisteminize ve organizasyona uygun olması için bu değişiklikleri takımınıza dağıtin.

### <a name="update-xamarin-integration"></a>Xamarin Tümleştirmesini Güncelleştirme

Dotfuscator Community 5'i [Xamarin][xamarin] projenize tümleştirilmenizi [sağlarsanız,][xamarin-download] adımlardan biri gibi özel MSBuild hedeflerini ve görevlerini indirmenizi gerekli kıldı. `PreEmptive.Dotfuscator.Xamarin.targets` Bu hedefler ve görevler Dotfuscator Community 6'da güncelleştirilmiştir, bu nedenle eski sürümleri yeni sürümlerle değiştirmeniz gerekir.

Xamarin tümleştirme dosyalarınızı güncelleştirmek için:

1. Bu dosyaları ilk kez indirdiğiniz dizini bulun.
   Yönergelerde verilen [örnekte][xamarin-download] adlı bir alt dizin kullanılır, ancak dosyaları farklı bir dizine indirilmiş olabilir ve `PreEmptive.Dotfuscator.Xamarin` bu dizinde Dotfuscator ile ilgili olmayan dosyalar da olabilir.

2. 1. adımda bulunan dizinde, Dotfuscator Xamarin tümleştirmesi ile ilgili dosyaları silin.

3. Aşağıdaki Kullanıcı Kılavuzu bölümünün geçerli sürümünde bağlantılı ZIP dosyasını indirin: Dotfuscator için özel MSBuild ve [Görevler'i indirin.][xamarin-download]

4. ZIP dosyasının içeriğini 1. adımda not edilen dizine ayıklar.

5. Git gibi bir kaynak denetim sistemi kullanıyorsanız, eski dosyaların kaldırılmasının ve yeni dosyaların bu sisteme yansıtıldıklarının doğru olduğundan emin olun.
   Sistemin türüne bağlı olarak, bu değişiklikler dosyalarda değişiklik olarak görünebilir ve bunlar değiştirilene kadar değişir.
   Sisteminize ve organizasyona uygun olması için bu değişiklikleri takımınıza dağıtin.

Bu sayfada yer alan diğer alt bölüm Xamarin projeleri için de geçerlidir, bu nedenle bu sayfanın yönergelerinin geri kalanını da gözden geçirmeyi de bekleyin.

### <a name="update-references-to-attribute-libraries"></a>Öznitelik kitaplıklarına başvurular güncelleştirildi

Dotfuscator, kaynak kodundaki [.NET][dotnet-attributes] öznitelikleri aracılığıyla belirli özellikleri yapılandırmanıza olanak sağlar.
Projeleriniz bu tür öznitelikleri kullanıyorsa, Bunları Dotfuscator 6'daki değişiklikleri ele alan şekilde güncelleştirmeniz gerekir.

#### <a name="obfuscation-attributes"></a>Karartma öznitelikleri

Karartma [Özniteliklerinde hiçbir değişiklik yok.][attributes-obfuscation] Bu öznitelikler .NET temel sınıf kitaplıklarında tanımlanır ve Dotfuscator Community 6 bunları uygulamaya devam eder.

<a name="steps-attrs-check"></a>

#### <a name="check-attributes"></a>Öznitelikleri Denetleme

Denetim Özniteliklerini [içeren kitaplık][attributes-checks] değişti. Dotfuscator Community 5'te, Dotfuscator'ın kendisiyle birlikte bir dosya olarak dağıtılmıştır. Dotfuscator Community 6'dan başlayarak, bunun yerine genel bir NuGet olarak dağıtılır.

Hala eski konuma başvuru Visual Studio bir proje derlemeye çalışmanız, aşağıdaki örnekler gibi hatalara neden olabilir:

`The type or namespace name 'PreEmptive' could not be found
(are you missing a using directive or an assembly reference?)`

`The type or namespace name 'TamperCheckAttribute' could not be found
(are you missing a using directive or an assembly reference?)`

Ayrıca şu uyarıyı da almak için:

`Could not resolve this reference. Could not locate the assembly "PreEmptive.Attributes". Check to make sure the assembly exists
on disk. If this reference is required by your code, you may get compilation errors.`

Projenizi yeni konumu kullanmak üzere güncelleştirmek için:

1. Projenin derleme başvurularını `PreEmptive.Attributes.dll` kaldırın.

2. NuGet paketi `PreEmptive.Protection.Checks.Attributes` başvurularını projeye ekleyin.
    Paket, varsayılan NuGet akışında kullanılabilir, [nuget.org.][nuget-org]

Her Check Özniteliğinin `ExtendedKey` parametreleri de kaldırılmıştır.
Bu parametreler Dotfuscator Community 5'te yoksayıldı, ancak kaynak kodunuz bunları ne olursa olsun kullandısa, projenizin derleyene kadar bu kullanımları kaldırmanız gerekir.

<a name="steps-attrs-analytics"></a>

#### <a name="instrumentation-attributes"></a>Ölçüm özniteliklerini

Ölçüm araçları, Dotfuscator 5'te PreEmptive Analytics özelliğini yapılandırmak için kullanıldı. Ancak PreEmptive Analytics, Dotfuscator 6'da kaldırılmıştır; Bkz. Kaldırılan Özellik alt bölüm [PreEmptive Analytics](#removed-analytics). Sonuç olarak, ölçüm özniteliklerini de kaldırılmıştır.

Ölçüm özniteliklerini kullanılan bir Visual Studio projesi derlemeyi denersiniz, öznitelik adları farklı olsa da (örneğin, yerine), Öznitelikleri Denetleme konusunda not alınan hata ve uyarı türleriyle aynı türlerde hatalar ve uyarılar elde [](#steps-attrs-check) `FeatureAttribute` edersiniz. `TamperCheckAttribute`

Ölçüm araçları özniteliklerinin kullanımlarını içeren önceden yerleşik derlemelerde Dotfuscator çalıştırmayı denersiniz, aşağıdaki örnekler gibi hatalar elde edersiniz:

`The PreEmptive.Attributes.FeatureAttribute attribute (annotating SomeNamespace.SomeType::SomeMethod) is not recognized
by this version of Dotfuscator.`

Bu sorunları çözmek için kaynak kodunuzdan tüm ölçümleme öznitelikleri kullanımını kaldırmanız gerekir.
Ayrıca özniteliklerini tanımlandığı kitaplıma yapılan derleme başvurularını da kaldırmanız `PreEmptive.Attributes.dll` gerekir.
(Bu kitaplıkta tanımlanan Denetim Özniteliklerini de kullanıyorsanız, bunlar taşınmıştır; yukarıdaki [Öznitelikleri Denetleme'ye](#steps-attrs-check) bakın.)

## <a name="removed-features"></a>Kaldırılan özellikler

Dotfuscator Community 6, Dotfuscator 5'in Community değişikliklere neden olur. Dotfuscator Community 5 kullanıyorsanız, bu bölümde derleme değişiklikleri gerektirip Dotfuscator'ın çıkışını etkileyebilecek değişikliklerle nasıl ilgilenilebilirsiniz?

Değişikliklerin tam listesi değişiklik günlüğünde [mevcuttur.][changelog]

<a name="removed-analytics"></a>

### <a name="preemptive-analytics"></a>PreEmptive Analytics

Dotfuscator 6, Telemetri Denetimi de dahil olmak üzere PreEmptive Analytics'i desteklemez. Ancak, [Denetimler][checks-overview] [(Uygulama Bildirimi ve][checks-notification] Denetim Eylemleri [dahil)][checks-actions]hala de desteklemektedir.

Dotfuscator 6'ı kullanmak için, PreEmptive Analytics ayarlarını kaldırmak için yapılandırma dosyanızı yükseltmeniz gerekir. [](#steps-config-files)

PreEmptive Analytics'i yapılandırmak için kod içinde öznitelikler kullanıyorsanız, Dotfuscator 6'nın bu derlemeleri koruyamadan önce bunları kaynak kodunuzdan kaldırmanız ve giriş derlemelerinizi yeniden derlemeniz gerekir. [](#steps-attrs-analytics)

Check (Denetim) geçersiz bir durum algılandığında (örneğin kurcalama [][tamper]algılandığında) telemetriyi denetlemeyi kullanıyorsanız, olayı [Azure Application Analizler'ye][application-insights] veya tercih edilen başka bir hizmete raporlayan özel bir Uygulama Bildirimi ile değiştirebilirsiniz. [][checks-notification]

### <a name="unsupported-application-types"></a>Desteklenmeyen uygulama türleri

Dotfuscator 6'da aşağıdaki uygulama türleri artık desteklenmiyor:

* Windows Phone
* WinRT (Windows 8 uygulamalar)
* Silverlight
* Unity (oyun altyapısı)

Buna ek olarak, Universal Windows Platformu (UWP) uygulamaları yalnızca [Xamarin senaryoları][xamarin] için de de kullanılabilir.

Diğer UWP uygulamalarını korumak için [Dotfuscator'a][pro] yükseltme Professional Ve Uygulamanızı Koruma [yönergelerini][pro-pya] izleyin.

### <a name="unsupported-inputs"></a>Desteklenmeyen girişler

Dotfuscator Community artık Universal Windows Platform (UWP) paketlerini `.appx` girdi olarak [desteklememektedir.][inputs] Xamarin tümleştirmesi ile UWP'i hedef alan [Xamarin][xamarin] uygulamalarını korumaya devam edin. Diğer UWP uygulamalarını korumak için [Dotfuscator'a][pro] yükseltme Professional Ve Uygulamanızı Koruma [yönergelerini][pro-pya] izleyin.

Buna ek `.xap` olarak, Silverlight artık destekçi olmadığı için paketler artık giriş olarak kullanılamaz.

### <a name="introduce-explicit-method-overrides"></a>Açık yöntem geçersiz kılmalarını tanıtma

Belirtik yöntem geçersiz kılmalarını tanıtmak için Yeniden Anlama seçeneği Dotfuscator'dan kaldırıldı. Dotfuscator 6'ı kullanmak için yapılandırma [dosyanızı yükseltip bu](#steps-config-files) ayarı kaldırmanız gerekir.

[changelog]: https://www.preemptive.com/support/dotfuscator-support/dotfuscator-ce-change-log
[download]: https://www.preemptive.com/products/dotfuscator/downloads
[always-improving]: https://www.preemptive.com/always-improving
[vs-update]: ../../install/update-visual-studio.md

[install]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
[register]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_register.html
[pro]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[pro-pya]: https://www.preemptive.com/dotfuscator/pro/userguide/en/getting_started_protect.html

[gui]:  https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_gui.html
[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[xamarin]: https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_xamarin.html
[xamarin-download]: https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_xamarin.html#pctoc-download-the-custom-set-of-msbuild-targets-and-tasks-for-dotfuscator

[inputs]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_inputs.html

[checks-overview]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[checks-notification]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#pctoc-application-notification
[checks-actions]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#pctoc-check-actions
[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html

[attributes-checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/attributes_checks.html
[attributes-obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/attributes_obfuscation.html

[verbosity]: ../how-to-view-save-and-configure-build-log-files.md#to-change-the-amount-of-information-included-in-the-build-log
[dotnet-attributes]: /dotnet/standard/attributes
[application-insights]: /azure/azure-monitor/app/app-insights-overview
[nuget-org]: https://www.nuget.org/
