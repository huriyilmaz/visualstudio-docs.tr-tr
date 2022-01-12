---
title: Project C++ hata ayıklama yapılandırması için yapılandırma ayarları
description: Özellik Sayfalarında C ve C++ hata ayıklamasını yapılandırma. Bu makalede ayarlar açıklanmıştır ve size kategorilerini anlatabilirsiniz.
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
ms.openlocfilehash: ae7a976ad66cddf9ad4ce2167570b429b1166055
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803251"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ hata ayıklama yapılandırması proje ayarları
Özellik Sayfaları iletişim kutusunda bir C veya C++  hata ayıklama yapılandırması için proje ayarlarını, Nasıl kullanılır: Hata ayıklama ve sürüm yapılandırmalarını ayarlama içinde ele [alınarak değiştirebilirsiniz.](../debugger/how-to-set-debug-and-release-configurations.md) Aşağıdaki tablolarda, Özellik Sayfaları iletişim kutusunda hata ayıklayıcıyla ilgili **ayarların nerede bulunamaz olduğu** gösterir.

> [!NOTE]
> Yapılandırma **Özellikleri/Hata** Ayıklama kategorisindeki hata ayıklama projesi ayarları, UWP uygulamaları ve C++ ile yazılmış bileşenler için farklıdır. Bkz. [Hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Her hata ayıklama özelliği ayarı otomatik olarak yazılır ve çözümlerinizi kaydeden çözümünüz için "kullanıcı başına" dosyasına (.vcxproj.user) kaydedilir.

 Aşağıdaki tabloda açıklandığı gibi, Hata **Ayıklayıcı'da** hangi hata ayıklayıcının liste kutusunu başlatacaklarını belirtin. Hangi özelliklerin görünür olduğunu sizin seçiminiz etkiler.

## <a name="configuration-properties-folder-debugging-category"></a>Yapılandırma Özellikleri klasörü (Hata ayıklama kategorisi)

| **Ayar** | **Açıklama** |
| - | - |
| **Başlat için hata ayıklayıcı** | Çalıştıracak hata ayıklayıcısını aşağıdaki seçeneklerle belirtir:<br /><br /> -   **Yerel Windows Hata Ayıklayıcısı**<br />-   **Uzak Windows Hata Ayıklayıcısı**<br />-   **Web Tarayıcısı Hata Ayıklayıcısı**<br />-   **Web Hizmeti Hata Ayıklayıcısı** |
| **Komut** (Yerel Windows Hata Ayıklayıcısı) | Yerel bilgisayarda hata ayıklarken program başlatma komutunu belirtir. |
| **Uzaktan Komut** (Uzak Windows Hata Ayıklayıcısı) | Uzak bilgisayarda .exe için yol. Yolu, uzak makineye girer gibi girin. |
| **Komut Bağımsız Değişkenleri** (Yerel Windows Hata Ayıklayıcısı)<br /><br /> **Uzak Komut Bağımsız Değişkenleri** (Uzak Windows Hata Ayıklayıcısı) | - Daha önce belirtilen komutun bağımsız değişkenlerini belirtir.<br /><br /> Bu kutuda aşağıdaki yeniden yönlendirme işleçlerini kullanabilirsiniz:<br /><br /> < `file`<br /> dosyadan stdin okur.<br /><br /> > `file`<br /> stdout dosyasını dosyaya yazar.<br /><br /> >> `file`<br /> dosyaya stdout ekler.<br /><br /> 2> `file`<br /> stderr dosyasını dosyaya yazar.<br /><br /> 2>> `file`<br /> Dosyaya stderr ekler.<br /><br /> 2> &1<br /> stdout (1) ile aynı konuma stderr (2) çıktısı gönderir.<br /><br /> 1> &2<br /> stdout (1) çıkışını stderr (2) ile aynı konuma gönderir.<br /><br /> Çoğu durumda, bu işleçler yalnızca konsol uygulamaları için geçerlidir. |
| **Çalışma Dizini** | EXE'nizin bulunduğu proje dizinine göre hata ayıklaması yapılan programın çalışma dizinini belirtir. Bunu boş bırakırsanız çalışma dizini proje dizinidir. Uzaktan hata ayıklama için proje dizini uzak sunucudadır. |
| **Ekleme** (Yerel Windows Hata Ayıklayıcısı ve Uzak Windows Hata Ayıklayıcısı) | Uygulamanın başlat mı yoksa ekleme mi olduğunu belirtir. Varsayılan ayar Hayır'dır. |
| **Uzak Sunucu Adı** (Uzak Windows Hata Ayıklayıcısı) | Bir uygulamada hata ayıklamak istediğiniz bilgisayarın (sizinki dışında) adını belirtir.<br /><br /> RemoteMachine Derleme makrosu bu özelliğin değerine ayarlanır; Daha fazla bilgi için bkz. [Derleme komutları ve özellikleri için makrolar.](/cpp/build/reference/common-macros-for-build-commands-and-properties) |
| **Bağlantı** (Uzak Windows Hata Ayıklayıcısı) | Uzaktan hata ayıklama için standart ve kimlik doğrulamasız bağlantı türleri arasında geçiş işleminizi sağlar. Uzak Sunucu Adı kutusunda bir **uzak bilgisayar adı** belirtin. Bağlantı türleri aşağıdakileri içerir:<br /><br /> -   **Windows Kimlik Doğrulaması ile uzak**<br />-   **Kimlik Doğrulamasız Uzak**<br /><br /> **Not** Kimlik Doğrulaması Yok ile uzaktan hata ayıklama, uzak bilgisayarı güvenlik ihlallerine karşı savunmasız bırakabilirsiniz. Windows kimlik doğrulaması modu daha güvenlidir.<br /><br /> Daha fazla bilgi için [bkz. Uzaktan hata ayıklama kurulumu.](../debugger/remote-debugging.md) |
| **HTTP URL'si** (Web Hizmeti Hata Ayıklayıcısı ve Web Tarayıcısı Hata Ayıklayıcısı) | Hata ayıklamak istediğiniz projenin bulunduğu URL'yi belirtir. |
| **Hata Ayıklayıcı Türü** | Kullanılacak hata ayıklayıcısı türünü **belirtir:** Yalnızca **Yerel ,** Yalnızca Yönetilen , Yalnızca **GPU,** **Karma** **,** Otomatik (varsayılan) veya **Betik**.<br /><br /> -   **Yalnızca Yerel,** unmanaged C++ koduna göredir.<br />-   **Yalnızca Yönetilen,** ortak dil çalışma zamanı (yönetilen kod) altında çalışan koda göredir.<br />-   **Karma,** hem yönetilen hem de yönetilemeyen kod için hata ayıklayıcılarını çağırır.<br />-   **Derleyici** ve EXE bilgilerine göre hata ayıklayıcı türünü otomatik olarak belirler.<br />-   **Betik,** betikler için bir hata ayıklayıcı çağırır.<br />-   **GPU Yalnızca** GPU C++ AMP veya DirectX başvuru rasterizer üzerinde çalışan bir koda yöneliktir. Bkz. [GPU kodunda hata ayıklama.](../debugger/debugging-gpu-code.md) |
| **Ortam** (Yerel Windows Hata Ayıklayıcısı ve Uzak Windows Hata Ayıklayıcısı) | Hata ayıklamakta olduğunu program için ortam değişkenlerini belirtir. Standart ortam değişkeni söz dizimi (örneğin, ) `PATH="%SystemRoot%\..."` kullanın. Bu değişkenler, Ortamı Birleştir ayarına bağlı olarak sistem ortamını geçersiz kılar veya sistem **ortamıyla birleştirilir.** Ayarlar sütununa sol tıklarken bir "Düzenle..." görüntülenir. Ortam değişkenlerini düzenlemek için bu bağlantıyı seçin. |
| **Ortamı Birleştirme** (Yerel Windows Hata Ayıklayıcısı) | Ortam kutusunda belirtilen değişkenlerin işletim  sistemi tarafından tanımlanan ortamla birleştirilecek olup olmadığını belirler. Varsayılan ayar Evet'tir. |
| **SQL Ayıklama (MPI** Kümesi Hata Ayıklayıcısı'nın hepsi) | Uygulamanıza ilişkin SQL hata ayıklamayı [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] sağlar. Varsayılan ayar Hayır'dır. |
| **Hata Ayıklama Hızlandırıcısı Türü** (yalnızca GPU hata ayıklaması) | Hata ayıklama için kullanmak üzere GPU cihazı belirtir. Uyumlu GPU cihazları için cihaz sürücülerini yüklemek ek seçenekler ekler. Varsayılan ayar GPU **- Yazılım Emulator.** |
| **GPU Varsayılan Kesme Noktası Davranışı** (yalnızca GPU hata ayıklama) | SimD'de her iş parçacığı için bir kesme noktası olayı olup olmadığını belirtir. Varsayılan ayar, kesme noktası olaylarını her gün yalnızca bir kez yükseltmektir. |
| **Amp Varsayılan Hızlandırıcısı** | GPU kodunda hata ayıklarken varsayılan AMP hızlandırıcısını belirtir. Soruna **kodunuz** yerine donanımdan mı yoksa sürücüden mi kaynakıldığını araştırmak için BILGISAYAR yazılım hızlandırıcısını seçin. |
| **Dağıtım Dizini** (Uzak Windows Hata Ayıklayıcısı) | Proje çıkışını başlatmadan önce kopyalanan uzak bilgisayarda yolu belirtir. Yol, uzak bilgisayarda bir ağ paylaşımı veya uzak bilgisayarda bir klasörün yolu olabilir. Varsayılan ayar boştur, yani proje çıkışı bir ağ paylaşımına kopyalanmaz. Dosyaların dağıtımını etkinleştirmek için, Yapılandırma Yöneticisi iletişim  kutusunda Dağıt onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için, [bkz. How to: Create and edit configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Dağıtılan Ek Dosyalar** (Uzak Windows Hata Ayıklayıcısı) | Dağıtım Dizini özelliği ayarlanırsa, bu dağıtım dizinine kopyalanır ek dosyaların noktalı virgülle ayrılmış listesidir. Varsayılan ayar boştur, yani dağıtım dizinine başka bir dosya kopyalanmaz. Dosyaların dağıtımını etkinleştirmek için, Yapılandırma Yöneticisi iletişim  kutusunda Dağıt onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için, [bkz. How to: Create and edit configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Çalışma Visual C++ Kitaplıklarını Dağıtma (Uzak Windows** Hata Ayıklayıcısı) | Dağıtım Dizini özelliği ayarlanırsa, geçerli platform için Visual C++ hata ayıklama çalışma zamanı kitaplıklarını ağ paylaşımına kopyalanacak olup olmadığını belirtir. Varsayılan ayar Evet'tir. |

## <a name="cc-folder-general-category"></a>C/C++ klasörü (Genel kategori)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata Ayıklama Bilgileri Biçimi** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Proje için oluşturulacak hata ayıklama bilgileri türünü belirtir.<br /><br /> Varsayılan seçenek (/ZI), Düzenle ve DevamLa uyumlu biçimde bir program veritabanı (PDB) oluşturur. Daha fazla bilgi için bkz. [/Z7, /Zd, /Zi, /ZI (Hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>C/C++ klasörü (İyileştirme kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**İyileştirme**|Derleyicinin ürettiği kodu iyileştirmesi gerekip gerek olmadığını belirtir. İyileştirme, yürütülen kodu değiştirir. İyileştirilmiş kod artık kaynak kodla eşleşmez ve bu da hata ayıklamayı daha zor hale gelir.<br /><br /> Varsayılan seçenek (**Devre Dışı (/0d) )** iyileştirmeyi bastırıyor. İyileştirme gizlendi olarak geliştirebilir ve ardından kodunuzun üretim sürümünü oluşturmada bu sürümü açabilirsiniz.|

## <a name="linker-folder-debugging-category"></a>Linker klasörü (Hata ayıklama kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata Ayıklama Bilgisi Oluşturma** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Bağlantıcıya [/Z7, /Zd, Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)veya /ZI tarafından belirtilen biçime sahip olacak hata ayıklama bilgilerini dahil edin.|
|**Program Veritabanı Dosyası Oluşturma** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Bu kutuda bir program veritabanı (PDB) dosyasının adını belirtin. Hata Ayıklama Bilgileri Biçimi için ZI'yi veya /Zi'yi seçmeniz gerekir.|
|**Özel Sembolleri ŞeritLe** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|PDB dosyasına özel simgeler eklemek istemiyorsanız, bu kutuda bir PDB dosyasının adını belirtin. Bu seçenek, program görüntülerinizi /DEBUG, /Z7, /Zd gibi bir PDB dosyası oluşturan herhangi bir derleyici veya bağlantıcı seçeneğiyle derleseniz ikinci bir PDB dosyası oluşturur. Veya /Zi. Bu ikinci PDB dosyası, müşterilerinize sunmak istemeyebilirsiniz sembolleri atlar. Daha fazla bilgi için bkz. [/PDBSTRIPPED (Özel sembolleri şeritle)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Harita Dosyası Oluşturma** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Bağlantı oluşturma sırasında bağlantıcıya bir harita dosyası oluşturmasını söyler. Varsayılan ayar Hayır'dır. Daha fazla bilgi için bkz. [/MAP (Eşlem Dosyası Oluştur)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme Dosyası Adı** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*name*)|Eşleme Dosyası Oluştur'ı seçerseniz, bu kutuda harita dosyasını belirtebilirsiniz. Daha fazla bilgi için bkz. [/MAP (Eşlem Dosyası Oluştur)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme Dışarı Aktarmaları** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Eşleme dosyasına dışarı aktaran işlevleri içerir. Varsayılan ayar Hayır'dır. Daha fazla bilgi için bkz. [/MAPINFO (Bilgileri Eşlem Dosyasına Dahil Edin)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Hata Ayıklanabilir Derleme** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Linker /ASSEMBLYDEBUG seçeneğinin ayarlarını belirtir. Olası değerler şunlardır:<br /><br /> -   **hiçbir hata ayıklanabilir özniteliği yok.**<br />-   **Çalışma zamanı izleme ve devre dışı bırakma iyileştirmeleri (/ASSEMBLYDEBUG)**. Bu varsayılan ayardır,<br />-   **Çalışma zamanı izlemesi yok ve iyileştirmeleri etkinleştirme (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<inherit from parent or project defaults>**.<br />- Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (DebuggableAttribute Ekle)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings arabirimini kullanarak bu ayarları Yapılandırma Özellikleri klasöründe (Hata ayıklama kategorisi) program aracılığıyla değiştirebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Diğer proje ayarları

Statik kitaplıklar ve URL'ler gibi proje türlerinde hata ayıklamak Visual Studio projenizin doğru dosyaları bulması gerekir. Kaynak kodu kullanılabilir olduğunda, hata ayıklamayı kolaylaştırmak için statik kitaplıkları ve URL'leri aynı çözüme ayrı projeler olarak ekledik. Bu proje türlerini oluşturma hakkında bilgi için bkz. Dinamik Bağlantı Kitaplığı [(DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) oluşturma ve kullanma [ve Statik kitaplık kullanarak oluşturma.](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp) Kullanılabilir kaynak koduyla, Dosya Yeni Dosya Visual Studio Var Olan Koddan'Project yeni  >    >  **bir proje de oluşturabilirsiniz.**

Projenizin dışında yer alan DLL'lerde hata ayıklamak için bkz. [DLL projelerinde hata ayıklama.](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal) Kendi DLL projenizin hata ayıklaması gerekirse, ancak çağıran uygulama için projeye erişiminiz yoksa bkz. DLL projesinde [hata ayıklama.](../debugger/how-to-debug-from-a-dll-project.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [C++ projeleri oluşturma ve yönetme](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (DebuggableAttribute Ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Derleme komutları ve özellikleri için genel makrolar](/cpp/ide/common-macros-for-build-commands-and-properties)