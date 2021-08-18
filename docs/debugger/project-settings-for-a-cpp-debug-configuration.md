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
ms.openlocfilehash: 44285acc479fc9fb60caa1f9f82e12796f609012
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146790"
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
| **dağıtılacak ek dosyalar** (uzaktan Windows hata ayıklayıcı) | Dağıtım Dizini özelliği ayarlanırsa, bu dağıtım dizinine kopyalanır ek dosyaların noktalı virgülle ayrılmış listesidir. Varsayılan ayar boştur, yani dağıtım dizinine başka bir dosya kopyalanmaz. Dosyaların dağıtımını etkinleştirmek için, Yapılandırma Yöneticisi iletişim  kutusunda Dağıt onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için, [bkz. How to: Create and edit configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Çalışma Visual C++ Kitaplıklarını Dağıtma (Uzak Windows** Hata Ayıklayıcısı) | Dağıtım Dizini özelliği ayarlanırsa, geçerli platform için Visual C++ hata ayıklama çalışma zamanı kitaplıklarını ağ paylaşımına kopyalanacak olup olmadığını belirtir. Varsayılan ayar Evet'tir. |

## <a name="cc-folder-general-category"></a>C/C++ klasörü (Genel kategori)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata Ayıklama Bilgileri Biçimi** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Proje için oluşturulacak hata ayıklama bilgileri türünü belirtir.<br /><br /> Varsayılan seçenek (/ZI), Düzenle ve DevamLa uyumlu biçimde bir program veritabanı (PDB) oluşturur. Daha fazla bilgi için bkz. [/Z7, /Zd, /Zi, /ZI (Hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>C/C++ klasörü (İyileştirme kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**İyileştirme**|Derleyicinin ürettiği kodu iyileştirmesi gerekip gerek olmadığını belirtir. İyileştirme, yürütülen kodu değiştirir. İyileştirilmiş kod artık kaynak kodla eşleşmez ve bu da hata ayıklamayı daha zor hale gelir.<br /><br /> Varsayılan seçenek (**Devre Dışı (/0d) )** iyileştirmeyi bastırıyor. İyileştirme gizlendi olarak geliştirebilir ve ardından kodunuzun üretim sürümünü oluşturmadan bu sürümü açabilirsiniz.|

## <a name="linker-folder-debugging-category"></a>Linker klasörü (Hata ayıklama kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata Ayıklama Bilgileri Oluşturma** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Bağlantıcıya [/Z7, /Zd, Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)veya /ZI tarafından belirtilen biçime sahip olacak hata ayıklama bilgilerini dahil edin.|
|**Program Veritabanı Dosyası Oluşturma** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Bu kutuda bir program veritabanı (PDB) dosyasının adını belirtin. Hata Ayıklama Bilgileri Biçimi için ZI'yi veya /Zi'yi seçmeniz gerekir.|
|**Özel Sembolleri ŞeritLe** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|PDB dosyasına özel simgeler eklemek istemiyorsanız, bu kutuda bir PDB dosyasının adını belirtin. Bu seçenek, program görüntülerinizi /DEBUG, /Z7, /Zd gibi bir PDB dosyası oluşturan herhangi bir derleyici veya bağlantıcı seçeneğiyle derleseniz ikinci bir PDB dosyası oluşturur. Veya /Zi. Bu ikinci PDB dosyası, müşterilerinize sunmak istemeyebilirsiniz sembolleri atlar. Daha fazla bilgi için bkz. [/PDBSTRIPPED (Özel sembolleri şeritle)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Eşleme Dosyası Oluşturma** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Bağlantı oluşturma sırasında bağlantıcıya bir harita dosyası oluşturmasını söyler. Varsayılan ayar Hayır'dır. Daha fazla bilgi için bkz. [/MAP (Eşlem Dosyası Oluştur)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme Dosyası Adı** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*name*)|Eşleme Dosyası Oluştur'ı seçerseniz, bu kutuda harita dosyasını belirtebilirsiniz. Daha fazla bilgi için bkz. [/MAP (Eşlem Dosyası Oluştur)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme Dışarı Aktarmaları** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Eşleme dosyasına dışarı aktaran işlevleri içerir. Varsayılan ayar Hayır'dır. Daha fazla bilgi için bkz. [/MAPINFO (Bilgileri Eşlem Dosyasına Dahil Edin)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Hata Ayıklanabilir Derleme** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Linker /ASSEMBLYDEBUG seçeneğinin ayarlarını belirtir. Olası değerler şunlardır:<br /><br /> -   **herhangi bir hata ayıklanabilir özniteliği yok.**<br />-   **Çalışma zamanı izleme ve devre dışı bırakma iyileştirmeleri (/ASSEMBLYDEBUG)**. Bu varsayılan ayardır,<br />-   **Çalışma zamanı izlemesi yok ve iyileştirmeleri etkinleştirme (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<inherit from parent or project defaults>**.<br />- Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (DebuggableAttribute Ekle)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings arabirimini kullanarak bu ayarları Yapılandırma Özellikleri klasöründe (Hata ayıklama kategorisi) program aracılığıyla değiştirebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Diğer proje ayarları

Statik kitaplıklar ve URL'ler gibi proje türlerinde hata ayıklamak Visual Studio projenizin doğru dosyaları bulması gerekir. Kaynak kodu kullanılabilir olduğunda, hata ayıklamayı kolaylaştırmak için statik kitaplıkları ve URL'leri aynı çözüme ayrı projeler olarak ekledik. Bu proje türlerini oluşturma hakkında bilgi için bkz. Dinamik Bağlantı Kitaplığı [(DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) oluşturma ve kullanma [ve Statik kitaplık kullanarak oluşturma.](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp) Kaynak kodu kullanılabilirken, Dosya Yeni dosya Visual Studio Mevcut Koddan'Project yeni  >    >  **bir proje de oluşturabilirsiniz.**

Projenizin dışında yer alan DLL'lerde hata ayıklamak için bkz. [DLL projelerinde hata ayıklama.](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal) Kendi DLL projenizin hata ayıklaması gerekirse, ancak çağıran uygulama için projeye erişiminiz yoksa bkz. DLL projesinde [hata ayıklama.](../debugger/how-to-debug-from-a-dll-project.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [C++ projeleri oluşturma ve yönetme](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (DebuggableAttribute Ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Derleme komutları ve özellikleri için genel makrolar](/cpp/ide/common-macros-for-build-commands-and-properties)