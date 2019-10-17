---
title: C++ Hata ayıklama yapılandırması proje ayarları
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: bca39b97f6363d8b8fefcfd691b69baf85c32170
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450380"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ hata ayıklama yapılandırması proje ayarları
C++ **Özellik sayfaları** iletişim kutusunda bir C veya hata ayıklama yapılandırması Için proje ayarlarını, [nasıl yapılır: set hata ayıklama ve yayın yapılandırmalarını](../debugger/how-to-set-debug-and-release-configurations.md)açıklandığı gibi değiştirebilirsiniz. Aşağıdaki tablolarda, **Özellik sayfaları** iletişim kutusunda hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir.

> [!NOTE]
> **Yapılandırma özellikleri/hata ayıklama** kategorisindeki hata ayıklama Projesi Ayarları, UWP uygulamaları ve içinde C++yazılmış bileşenler için farklıdır. Bkz. [hata ayıklama oturumu başlatma (vb C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Çözümünüzü kaydettiğinizde her hata ayıklama özelliği ayarı otomatik olarak, çözümünüz için "Kullanıcı başına" dosyasına (. vcxproj. User) kaydedilir.

 Aşağıdaki tabloda açıklandığı gibi, **başlatma hata ayıklayıcısında** hangi hata ayıklayıcının kullanılacağını belirtin liste kutusunu seçin. Seçiminiz, hangi özelliklerin görünür olduğunu etkiler.

## <a name="configuration-properties-folder-debugging-category"></a>Yapılandırma özellikleri klasörü (hata ayıklama kategorisi)

| **Ayarlanmasını** | **Açıklama** |
| - | - |
| **Başlatılacak hata ayıklayıcı** | Aşağıdaki seçimlerle çalıştırılacak hata ayıklayıcıyı belirtir:<br /><br /> -   **yerel Windows hata ayıklayıcısı**<br />-   **uzak Windows hata ayıklayıcısı**<br />-   **Web tarayıcısı hata ayıklayıcı**<br />-   **Web hizmeti hata ayıklayıcısı** |
| **Komut** (yerel Windows hata ayıklayıcısı) | Yerel bilgisayarda hata ayıklaması yaptığınız programı başlatma komutunu belirtir. |
| **Uzak komut** (uzak Windows hata ayıklayıcı) | Uzak bilgisayardaki. exe dosyasının yolu. Yolu, uzak makineye girdiğiniz gibi girin. |
| **Komut bağımsız değişkenleri** (yerel Windows hata ayıklayıcı)<br /><br /> **Uzak komut bağımsız değişkenleri** (uzak Windows hata ayıklayıcı) | -Daha önce belirtilen komut için bağımsız değişkenleri belirtir.<br /><br /> Bu kutuda aşağıdaki yeniden yönlendirme işleçlerini kullanabilirsiniz:<br /><br /> < `file`<br /> Dosyadan stdin okur.<br /><br /> > `file`<br /> Stdout dosyasına yazar.<br /><br /> >> `file`<br /> Stdout 'ı dosyaya ekler.<br /><br /> 2 > `file`<br /> Dosya için stderr yazar.<br /><br /> 2 > > `file`<br /> Stderr 'i dosyaya ekler.<br /><br /> 2 > & 1<br /> Stderr (2) çıkışını stdout (1) ile aynı konuma gönderir.<br /><br /> 1 > & 2<br /> Stdout (1) çıkışını stderr (2) ile aynı konuma gönderir.<br /><br /> Çoğu durumda, bu işleçler yalnızca konsol uygulamaları için geçerlidir. |
| **Çalışma dizini** | EXE 'nizin bulunduğu proje dizinine göre, hata ayıklanan programın çalışma dizinini belirtir. Bu alanı boş bırakırsanız, çalışma dizini proje dizinidir. Uzaktan hata ayıklama için, proje dizini uzak sunucuda bulunur. |
| **Ekle** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı) | Uygulamanın başlatılıp başlatılmayacağını belirtir. Varsayılan ayar Hayır ' dır. |
| **Uzak sunucu adı** (uzak Windows hata ayıklayıcı) | Bir uygulamada hata ayıklamak istediğiniz bir bilgisayarın (sizinkinden başka) adını belirtir.<br /><br /> RemoteMachine derleme makrosu, bu özelliğin değerine ayarlanır; daha fazla bilgi için bkz. [derleme komutları ve özellikleri Için makrolar](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **Bağlantı** (uzak Windows hata ayıklayıcı) | Uzaktan hata ayıklama için standart ve kimlik doğrulama olmayan bağlantı türleri arasında geçiş yapmanıza olanak sağlar. **Uzak sunucu adı** kutusunda uzak bilgisayar adını belirtin. Bağlantı türleri şunları içerir:<br /><br /> **Windows kimlik doğrulamasıyla** -    uzak<br />**kimlik doğrulaması olmadan** -    uzak<br /><br /> **Göz önünde** Kimlik doğrulaması olmadan uzaktan hata ayıklama uzak bilgisayarı güvenlik ihlallerine karşı savunmasız bırakabilir. Windows kimlik doğrulama modu daha güvenlidir.<br /><br /> Daha fazla bilgi için bkz. [Uzaktan hata ayıklama kurulumu](../debugger/remote-debugging.md). |
| **Http URL 'si** (Web hizmeti hata ayıklayıcısı ve Web tarayıcısı hata ayıklayıcı) | Hata ayıkladığınız projenin bulunduğu URL 'YI belirtir. |
| **Hata ayıklayıcı türü** | Kullanılacak hata ayıklayıcı türünü belirtir: **yalnızca yerel**, yalnızca **yönetilen**, yalnızca **GPU**, **karma**, **Otomatik** (varsayılan) veya **komut dosyası**.<br /><br /> @no__t-**yalnızca yerel** , yönetilmeyen C++ kod içindir.<br />-   **yönetilen yalnızca** ortak dil çalışma zamanı (yönetilen kod) altında çalışan kod içindir.<br />-   **karışık** , hem yönetilen hem de yönetilmeyen kod için hata ayıklayıcıları çağırır.<br />-   , derleyici ve EXE bilgilerine göre hata ayıklayıcı türünü**Otomatik** olarak belirler.<br />-   **betiği** betikler için bir hata ayıklayıcı çağırır.<br />-   **GPU yalnızca** bir GPU C++ cihazında veya DirectX başvuru tarayıcısında çalışan amp koduna yöneliktir. Bkz. [GPU kodunda hata ayıklama](../debugger/debugging-gpu-code.md). |
| **Ortam** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı) | Hata ayıkladığınız program için ortam değişkenlerini belirtir. Standart ortam değişkeni sözdizimini kullanın (örneğin, `PATH="%SystemRoot%\..."`). Bu değişkenler, **birleştirme ortamı** ayarına bağlı olarak, sistem ortamını geçersiz kılar veya sistem ortamıyla birleştirilir. Ayarlar sütununu sol tıklattığınızda bir "Düzenle..." görüneceği. Ortam değişkenlerini düzenlemek için bu bağlantıyı seçin. |
| **Birleştirme ortamı** (yerel Windows hata ayıklayıcı) | **Ortam** kutusunda belirtilen değişkenlerin, işletim sistemi tarafından tanımlanan ortamla birleştirilip birleştirilmeyeceğini belirler. Varsayılan ayar Evet ' tir. |
| **SQL hata ayıklama** (tümü, MPI kümesi hata ayıklayıcısı) | @No__t-0 uygulamanızdan SQL yordamlarını hata ayıklamasına izin vermez. Varsayılan ayar Hayır ' dır. |
| **Hata ayıklama Hızlandırıcı türü** (yalnızca GPU hata ayıklama) | Hata ayıklama için kullanılacak GPU cihazını belirtir. Uyumlu GPU cihazları için cihaz sürücülerinin yüklenmesi, ek seçenekler ekler. Varsayılan ayar **GPU-yazılım öykünücüsü**' dir. |
| **GPU Varsayılan kesme noktası davranışı** (yalnızca GPU hata ayıklama) | SıMD warp 'daki her iş parçacığı için bir kesme noktası olayının yapılıp yapılmayacağını belirtir. Varsayılan ayar, kesme noktasını her çarpıtma için yalnızca bir kez tetiklemedir. |
| **Amp varsayılan Hızlandırıcı** | GPU kodunda hata ayıklarken varsayılan AMP hızlandırıcıyı belirtir. Kod yerine donanımdan veya bir sürücüden kaynaklanan bir sorun olup olmadığını araştırmak için **warp yazılım hızlandırıcıyı** seçin. |
| **Dağıtım dizini** (uzak Windows hata ayıklayıcı) | Proje çıkışının, başlamadan önce kopyalanacağı uzak bilgisayardaki yolu belirtir. Yol, uzak bilgisayardaki bir ağ paylaşımından olabilir veya uzak bilgisayardaki bir klasörün yolu olabilir. Varsayılan ayar boştur; bu, proje çıkışının bir ağ paylaşımında kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için, Configuration Manager iletişim kutusunda **Dağıt** onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md). |
| **Dağıtılacak ek dosyalar** (uzak Windows hata ayıklayıcı) | Dağıtım dizini özelliği ayarlanmışsa bu, dağıtım dizinine kopyalanacak ek dosyaların noktalı virgülle ayrılmış listesidir. Varsayılan ayar boştur; bu, dağıtım dizinine hiçbir ek dosya kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için, Configuration Manager iletişim kutusunda **Dağıt** onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md). |
| **Visual C++ hata ayıklama çalışma zamanı kitaplıklarını dağıtma** (uzak Windows hata ayıklayıcı) | Dağıtım dizini özelliği ayarlanmışsa, bu, geçerli platform için Visual C++ hata ayıklama çalışma zamanı kitaplıklarının ağ paylaşımında kopyalanıp kopyalanmayacağını belirtir. Varsayılan ayar Evet ' tir. |

## <a name="cc-folder-general-category"></a>C/C++ klasör (genel kategori)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata ayıklama bilgi biçimi** ([/Z7,/ZD, Zi,/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format))|Proje için oluşturulacak hata ayıklama bilgilerinin türünü belirtir.<br /><br /> Varsayılan seçenek (/ZI) Düzenle ve devam et uyumlu biçimde bir program veritabanı (PDB) oluşturur. Daha fazla bilgi için bkz. [/Z7,/ZD,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>C/C++ klasör (İyileştirme kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**İyileştirme**|Derleyicinin ürettiği kodu iyileştiregerekip gerekmediğini belirtir. İyileştirme, yürütülen kodu değiştirir. İyileştirilmiş kod artık kaynak kodla eşleşmez, bu da hata ayıklamayı daha zor hale getirir.<br /><br /> Varsayılan seçenek (**devre dışı (/0d)** ) iyileştirme 'yi bastırır. İyileştirme bastırıldığınızda geliştirme yapabilir ve sonra kodunuzun üretim sürümünü oluştururken bunu açabilirsiniz.|

## <a name="linker-folder-debugging-category"></a>Bağlayıcı klasörü (hata ayıklama kategorisi)

|Ayar|Açıklama|
|-------------|-----------------|
|**Hata ayıklama bilgisi oluştur** ([/Debug](/cpp/build/reference/debug-generate-debug-info))|Bağlayıcının [/Z7,/ZD, Zi veya/ZI](/cpp/build/reference/z7-zi-zi-debug-information-format)tarafından belirtilen biçime sahip hata ayıklama bilgilerini içermesini söyler.|
|**Program veritabanı dosyası oluştur** ([/pdb: ad](/cpp/build/reference/pdb-use-program-database))|Bu kutudaki program veritabanı (PDB) dosyasının adını belirtin. Hata ayıklama bilgileri biçimi için ZI veya/Zi seçmeniz gerekir.|
|**Özel sembolleri** çıkar ([/pdbçıkarıldı: filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|PDB dosyasına özel semboller eklemek istemiyorsanız, bu kutudaki PDB dosyasının adını belirtin. Bu seçenek, program görüntünüzü,/DEBUG,/Z7,/Zdgibi bir PDB dosyası üreten derleyici veya bağlayıcı seçeneklerinden biriyle oluşturduğunuzda ikinci bir PDB dosyası oluşturur. Ya da/Zi. Bu ikinci PDB dosyası, müşterilerinize göndermek istemediğiniz sembolleri atlar. Daha fazla bilgi için bkz. [/Pdbçıkarıldı (özel sembolleri Strip)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Eşleme dosyası oluştur** ([/map](/cpp/build/reference/map-generate-mapfile))|Bağlayıcının bağlama sırasında bir eşleme dosyası oluşturmasını söyler. Varsayılan ayar Hayır ' dır. Daha fazla bilgi için bkz. [/Map (mapfile üret)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme dosyası adı** ([/map:](/cpp/build/reference/map-generate-mapfile)*ad*)|Eşleme dosyası oluştur ' u seçerseniz, bu kutuda eşleme dosyasını belirtebilirsiniz. Daha fazla bilgi için bkz. [/Map (mapfile üret)](/cpp/build/reference/map-generate-mapfile).|
|**Eşleme dışarı aktarmaları** ([/MapInfo: dışarı aktarmalar](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Eşleme dosyasına aktarılmış işlevleri içerir. Varsayılan ayar Hayır ' dır. Daha fazla bilgi için bkz. [/MapInfo (mapfile Içine bilgi ekleme)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Hata ayıklanabilir derlemesi** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Bağlayıcı/ASSEMBLYDEBUG seçeneğinin ayarlarını belirtir. Olası değerler şunlardır:<br /><br /> -   **hiçbir hata ayıklanabilir özniteliği yayılmadı**.<br />-   **çalışma zamanı izleme ve devre dışı bırakma (/ASSEMBLYDEBUG)** . Bu, varsayılan ayardır,<br />-   **çalışma zamanı Izleme yok ve iyileştirmeleri etkinleştir (/ASSEMBLYDEBUG: DISABLE)** .<br />-    **\< üst veya proje varsayılanlarından al >** .<br />-Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (hata ayıklama Ggableattribute Ekle)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Yapılandırma özellikleri klasöründeki (hata ayıklama kategorisi) bu ayarları, Microsoft. VisualStudio. VCProjectEngine. VCDebugSettings arabirimini kullanarak programlı bir şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Diğer proje ayarları

Statik kitaplıklar ve DLL 'Ler gibi proje türlerinde hata ayıklamak için, Visual Studio projenizin doğru dosyaları bulabilmeleri gerekir. Kaynak kodu kullanılabilir olduğunda, hata ayıklamayı daha kolay hale getirmek için aynı çözüme ayrı projeler olarak statik kitaplıklar ve DLL 'Ler ekleyebilirsiniz. Bu proje türlerini oluşturma hakkında bilgi için, bkz. [dinamik bağlantı kitaplığı (dll) oluşturma ve kullanma](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) ve [statik kitaplık kullanarak oluşturma](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Kaynak kodu kullanılabilir olduğunda,**mevcut koddan** **@no__t-** 1**Yeni** >  projesini seçerek yeni bir Visual Studio projesi de oluşturabilirsiniz.

Projenizin dışındaki dll 'Lerde hata ayıklamak için bkz. [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Kendi DLL projenizde hata ayıklaması yapmanız, ancak çağıran uygulama için projeye erişiminiz yoksa, bkz. [DLL projesinden hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Projeleri oluşturma ve C++ yönetme](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (DebuggableAttribute Ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Derleme komutları ve özellikleri için genel makrolar](/cpp/ide/common-macros-for-build-commands-and-properties)