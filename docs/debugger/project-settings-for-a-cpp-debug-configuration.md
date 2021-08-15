---
title: C++ hata ayıklama yapılandırması için Project ayarları
description: Özellik sayfalarında C ve C++ hata ayıklamayı yapılandırın. Bu makale, ayarları açıklar ve kategorilerini size bildirir.
ms.custom: SEO-VS-2020
ms.date: 11/26/2018
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: fedff930798403a8fd24053a2c78a88d9ed60130a0efaa1132db8a4d61d6e243
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121310965"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ hata ayıklama yapılandırması proje ayarları
**Özellik sayfaları** iletişim kutusunda bir C veya C++ hata ayıklama yapılandırması için proje ayarlarını, [nasıl yapılır: ayarlama hata ayıklama ve yayın yapılandırmalarını](../debugger/how-to-set-debug-and-release-configurations.md)açıklandığı gibi değiştirebilirsiniz. Aşağıdaki tablolarda, **Özellik sayfaları** iletişim kutusunda hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir.

> [!NOTE]
> **Yapılandırma özellikleri/hata ayıklama** kategorisindeki hata ayıklama Projesi Ayarları, UWP uygulamaları ve C++ dilinde yazılmış bileşenler için farklıdır. Bkz. [hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Çözümünüzü kaydettiğinizde her hata ayıklama özelliği ayarı otomatik olarak, çözümünüz için "Kullanıcı başına" dosyasına (. vcxproj. User) kaydedilir.

 Aşağıdaki tabloda açıklandığı gibi, **başlatma hata ayıklayıcısında** hangi hata ayıklayıcının kullanılacağını belirtin liste kutusunu seçin. Seçiminiz, hangi özelliklerin görünür olduğunu etkiler.

## <a name="configuration-properties-folder-debugging-category"></a>Yapılandırma özellikleri klasörü (hata ayıklama kategorisi)

| **Ayar** | **Açıklama** |
| - | - |
| **Başlatılacak hata ayıklayıcı** | Aşağıdaki seçimlerle çalıştırılacak hata ayıklayıcıyı belirtir:<br /><br /> -   **yerel Windows hata ayıklayıcı**<br />-   **uzaktan Windows hata ayıklayıcı**<br />-   **Web tarayıcısı hata ayıklayıcı**<br />-   **Web hizmeti hata ayıklayıcısı** |
| **komut** (yerel Windows hata ayıklayıcı) | Yerel bilgisayarda hata ayıklaması yaptığınız programı başlatma komutunu belirtir. |
| **uzak komut** (uzak Windows hata ayıklayıcı) | Uzak bilgisayardaki .exe için yol. Yolu, uzak makineye girdiğiniz gibi girin. |
| **komut bağımsız değişkenleri** (yerel Windows hata ayıklayıcı)<br /><br /> **uzak komut bağımsız değişkenleri** (uzak Windows hata ayıklayıcı) | -Daha önce belirtilen komut için bağımsız değişkenleri belirtir.<br /><br /> Bu kutuda aşağıdaki yeniden yönlendirme işleçlerini kullanabilirsiniz:<br /><br /> < `file`<br /> Dosyadan stdin okur.<br /><br /> > `file`<br /> Stdout dosyasına yazar.<br /><br /> >> `file`<br /> Stdout 'ı dosyaya ekler.<br /><br /> 2> `file`<br /> Dosya için stderr yazar.<br /><br /> 2>> `file`<br /> Stderr 'i dosyaya ekler.<br /><br /> 2> &1<br /> Stderr (2) çıkışını stdout (1) ile aynı konuma gönderir.<br /><br /> 1> &2<br /> Stdout (1) çıkışını stderr (2) ile aynı konuma gönderir.<br /><br /> Çoğu durumda, bu işleçler yalnızca konsol uygulamaları için geçerlidir. |
| **Çalışma dizini** | EXE 'nizin bulunduğu proje dizinine göre, hata ayıklanan programın çalışma dizinini belirtir. Bu alanı boş bırakırsanız, çalışma dizini proje dizinidir. Uzaktan hata ayıklama için, proje dizini uzak sunucuda bulunur. |
| **ekle** (yerel Windows hata ayıklayıcı ve uzaktan Windows hata ayıklayıcı) | Uygulamanın başlatılıp başlatılmayacağını belirtir. Varsayılan ayar Hayır ' dır. |
| **uzak sunucu adı** (uzak Windows hata ayıklayıcı) | Bir uygulamada hata ayıklamak istediğiniz bir bilgisayarın (sizinkinden başka) adını belirtir.<br /><br /> RemoteMachine derleme makrosu, bu özelliğin değerine ayarlanır; daha fazla bilgi için bkz. [derleme komutları ve özellikleri Için makrolar](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **bağlantı** (uzak Windows hata ayıklayıcı) | Uzaktan hata ayıklama için standart ve kimlik doğrulama olmayan bağlantı türleri arasında geçiş yapmanıza olanak sağlar. **Uzak sunucu adı** kutusunda uzak bilgisayar adını belirtin. Bağlantı türleri şunları içerir:<br /><br /> -   **Windows kimlik doğrulaması ile uzaktan**<br />-   **Kimlik doğrulaması olmadan uzak**<br /><br /> **Göz önünde** Kimlik doğrulaması olmadan uzaktan hata ayıklama uzak bilgisayarı güvenlik ihlallerine karşı savunmasız bırakabilir. Windows Kimlik doğrulama modu daha güvenlidir.<br /><br /> Daha fazla bilgi için bkz. [Uzaktan hata ayıklama kurulumu](../debugger/remote-debugging.md). |
| **Http URL 'si** (Web hizmeti hata ayıklayıcısı ve Web tarayıcısı hata ayıklayıcı) | Hata ayıkladığınız projenin bulunduğu URL 'YI belirtir. |
| **Hata ayıklayıcı türü** | Kullanılacak hata ayıklayıcı türünü belirtir: **yalnızca yerel**, yalnızca **yönetilen**, yalnızca **GPU**, **karma**, **Otomatik** (varsayılan) veya **komut dosyası**.<br /><br /> -   **Yalnızca yerel** , yönetilmeyen C++ kodu içindir.<br />-   **Yalnızca yönetilen** , ortak dil çalışma zamanı (yönetilen kod) altında çalışan koda yöneliktir.<br />-   Hem yönetilen hem de yönetilmeyen kod için **karışık** hata ayıklayıcıları çağırır.<br />-   Derleyici ve EXE bilgilerine göre hata ayıklayıcı türünü **Otomatik** olarak belirler.<br />-   **Betik** , betikler için bir hata ayıklayıcı çağırır.<br />-   **yalnızca gpu** , bir gpu aygıtında veya DirectX başvuru tarayıcısı üzerinde çalışan C++ AMP kod içindir. Bkz. [GPU kodunda hata ayıklama](../debugger/debugging-gpu-code.md). |
| **ortam** (yerel Windows hata ayıklayıcı ve uzaktan Windows hata ayıklayıcı) | Hata ayıkladığınız program için ortam değişkenlerini belirtir. Standart ortam değişkeni sözdizimini kullanın (örneğin, `PATH="%SystemRoot%\..."` ). Bu değişkenler, **birleştirme ortamı** ayarına bağlı olarak, sistem ortamını geçersiz kılar veya sistem ortamıyla birleştirilir. Ayarlar sütununda sol tıklattığınızda bir "Düzenle..." görüntülenir. Ortam değişkenlerini düzenlemek için bu bağlantıyı seçin. |
| **birleştirme ortamı** (yerel Windows hata ayıklayıcı) | **Ortam** kutusunda belirtilen değişkenlerin, işletim sistemi tarafından tanımlanan ortamla birleştirilip birleştirilmeyeceğini belirler. Varsayılan ayar Evet ' tir. |
| **SQL hata ayıklama** (tümü, mpı kümesi hata ayıklayıcısı) | SQL yordamların uygulamanızdan hata ayıklamasına izin vermez [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] . Varsayılan ayar Hayır ' dır. |
| **Hata ayıklama Hızlandırıcı türü** (yalnızca GPU hata ayıklama) | Hata ayıklama için kullanılacak GPU cihazını belirtir. Uyumlu GPU cihazları için cihaz sürücülerinin yüklenmesi, ek seçenekler ekler. Varsayılan ayar **GPU-yazılım Emulator**. |
| **GPU Varsayılan kesme noktası davranışı** (yalnızca GPU hata ayıklama) | SıMD warp 'daki her iş parçacığı için bir kesme noktası olayının yapılıp yapılmayacağını belirtir. Varsayılan ayar, kesme noktasını her çarpıtma için yalnızca bir kez tetiklemedir. |
| **Amp varsayılan Hızlandırıcı** | GPU kodunda hata ayıklarken varsayılan AMP hızlandırıcıyı belirtir. Kod yerine donanımdan veya bir sürücüden kaynaklanan bir sorun olup olmadığını araştırmak için **warp yazılım hızlandırıcıyı** seçin. |
| **dağıtım dizini** (uzak Windows hata ayıklayıcı) | Proje çıkışının, başlamadan önce kopyalanacağı uzak bilgisayardaki yolu belirtir. Yol, uzak bilgisayardaki bir ağ paylaşımından olabilir veya uzak bilgisayardaki bir klasörün yolu olabilir. Varsayılan ayar boştur; bu, proje çıkışının bir ağ paylaşımında kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için, Configuration Manager iletişim kutusunda **Dağıt** onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md). |
| **dağıtılacak ek dosyalar** (uzaktan Windows hata ayıklayıcı) | Dağıtım dizini özelliği ayarlanmışsa bu, dağıtım dizinine kopyalanacak ek dosyaların noktalı virgülle ayrılmış listesidir. Varsayılan ayar boştur; bu, dağıtım dizinine hiçbir ek dosya kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için, Configuration Manager iletişim kutusunda **Dağıt** onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md). |
| **Visual C++ hata ayıklama çalışma zamanı kitaplıklarını dağıtma** (uzak Windows hata ayıklayıcı) | Dağıtım dizini özelliği ayarlanmışsa bu, geçerli platform için Visual C++ hata ayıklama çalışma zamanı kitaplıklarının ağ paylaşımında kopyalanıp kopyalanmayacağını belirtir. Varsayılan ayar Evet ' tir. |

## <a name="cc-folder-general-category"></a>C/C++ klasörü (genel kategori)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata ayıklama bilgi biçimi** ([/Z7,/ZD, Zi,/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format))|Proje için oluşturulacak hata ayıklama bilgilerinin türünü belirtir.<br /><br /> Varsayılan seçenek (/ZI) Düzenle ve devam et uyumlu biçimde bir program veritabanı (PDB) oluşturur. Daha fazla bilgi için bkz. [/Z7,/ZD,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>C/C++ klasörü (Iyileştirme kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**İyileştirme**|Derleyicinin ürettiği kodu iyileştiregerekip gerekmediğini belirtir. İyileştirme, yürütülen kodu değiştirir. İyileştirilmiş kod artık kaynak kodla eşleşmez, bu da hata ayıklamayı daha zor hale getirir.<br /><br /> Varsayılan seçenek (**devre dışı (/0d)**) iyileştirme 'yi bastırır. İyileştirme bastırıldığınızda geliştirme yapabilir ve sonra kodunuzun üretim sürümünü oluştururken bunu açabilirsiniz.|

## <a name="linker-folder-debugging-category"></a>Bağlayıcı klasörü (hata ayıklama kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata ayıklama bilgisi oluştur** ([/Debug](/cpp/build/reference/debug-generate-debug-info))|Bağlayıcının [/Z7,/ZD, Zi veya/ZI](/cpp/build/reference/z7-zi-zi-debug-information-format)tarafından belirtilen biçime sahip hata ayıklama bilgilerini içermesini söyler.|
|**Program veritabanı dosyası oluştur** ([/pdb: ad](/cpp/build/reference/pdb-use-program-database))|Bu kutudaki program veritabanı (PDB) dosyasının adını belirtin. Hata ayıklama bilgileri biçimi için ZI veya/Zi seçmeniz gerekir.|
|**Özel sembolleri** çıkar ([/pdbçıkarıldı: filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|PDB dosyasına özel semboller eklemek istemiyorsanız, bu kutudaki PDB dosyasının adını belirtin. Bu seçenek, program görüntünüzü,/DEBUG,/Z7,/Zdgibi bir PDB dosyası üreten derleyici veya bağlayıcı seçeneklerinden biriyle oluşturduğunuzda ikinci bir PDB dosyası oluşturur. Ya da/Zi. Bu ikinci PDB dosyası, müşterilerinize göndermek istemediğiniz sembolleri atlar. Daha fazla bilgi için bkz. [/Pdbçıkarıldı (özel sembolleri Strip)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Eşleme dosyası oluştur** ([/map](/cpp/build/reference/map-generate-mapfile))|Bağlayıcının bağlama sırasında bir eşleme dosyası oluşturmasını söyler. Varsayılan ayar Hayır ' dır. Daha fazla bilgi için bkz. [/Map (mapfile üret)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme dosyası adı** ([/map:](/cpp/build/reference/map-generate-mapfile)*ad*)|Eşleme dosyası oluştur ' u seçerseniz, bu kutuda eşleme dosyasını belirtebilirsiniz. Daha fazla bilgi için bkz. [/Map (mapfile üret)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme dışarı aktarmaları** ([/MapInfo: dışarı aktarmalar](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Eşleme dosyasına aktarılmış işlevleri içerir. Varsayılan ayar Hayır ' dır. Daha fazla bilgi için bkz. [/MapInfo (mapfile Içine bilgi ekleme)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Hata ayıklanabilir derlemesi** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Bağlayıcı/ASSEMBLYDEBUG seçeneğinin ayarlarını belirtir. Olası değerler şunlardır:<br /><br /> -   **Hata ayıklanabilir özniteliği yayılmadı**.<br />-   **Çalışma zamanı izleme ve devre dışı bırakma (/ASSEMBLYDEBUG)**. Bu, varsayılan ayardır,<br />-   **Çalışma zamanı Izleme yok ve iyileştirmeleri etkinleştir (/ASSEMBLYDEBUG: DISABLE)**.<br />-   **\<inherit from parent or project defaults>**.<br />-Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (hata ayıklama Ggableattribute Ekle)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Yapılandırma özellikleri klasöründeki (hata ayıklama kategorisi) bu ayarları, Microsoft. VisualStudio. VCProjectEngine. VCDebugSettings arabirimini kullanarak programlı bir şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Diğer proje ayarları

statik kitaplıklar ve dll 'ler gibi proje türlerinde hata ayıklamak için Visual Studio projenizin doğru dosyaları bulabilmeleri gerekir. Kaynak kodu kullanılabilir olduğunda, hata ayıklamayı daha kolay hale getirmek için aynı çözüme ayrı projeler olarak statik kitaplıklar ve DLL 'Ler ekleyebilirsiniz. Bu proje türlerini oluşturma hakkında bilgi için, bkz. [dinamik bağlantı kitaplığı (dll) oluşturma ve kullanma](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) ve [statik kitaplık kullanarak oluşturma](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). kaynak kodu kullanılabilir olduğunda,   >    >  **mevcut koddan yeni Project** dosya ' yı seçerek yeni bir Visual Studio projesi de oluşturabilirsiniz.

Projenizin dışındaki dll 'Lerde hata ayıklamak için bkz. [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Kendi DLL projenizde hata ayıklaması yapmanız, ancak çağıran uygulama için projeye erişiminiz yoksa, bkz. [DLL projesinden hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [C++ projeleri oluşturma ve yönetme](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (DebuggableAttribute Ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Derleme komutları ve özellikleri için genel makrolar](/cpp/ide/common-macros-for-build-commands-and-properties)