---
title: C++ hata ayıklama yapılandırması için proje ayarları
description: Özellik Sayfalarında C ve C++ hata ayıklamasını yapılandırma. Bu makalede ayarlar açıklanmıştır ve size kategorilerini anlatabilirsiniz.
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
ms.workload:
- cplusplus
ms.openlocfilehash: 34dd9b82a642c9e9ec32dde383a8c2e02ac57aa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385194"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ hata ayıklama yapılandırması proje ayarları
Özellik Sayfaları iletişim kutusunda bir C veya C++  hata ayıklama yapılandırmasının proje ayarlarını, Nasıl kullanılır: Hata ayıklama ve sürüm yapılandırmalarını ayarlama içinde ele [alınarak değiştirebilirsiniz.](../debugger/how-to-set-debug-and-release-configurations.md) Aşağıdaki tablolarda, Özellik Sayfaları iletişim kutusunda hata ayıklayıcıyla ilgili **ayarların nerede bulunamaz olduğu** gösterir.

> [!NOTE]
> Yapılandırma **Özellikleri/Hata** Ayıklama kategorisindeki hata ayıklama projesi ayarları, UWP uygulamaları ve C++ ile yazılmış bileşenler için farklıdır. Bkz. [Hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Her hata ayıklama özelliği ayarı otomatik olarak yazılır ve çözümlerinizi kaydeden çözümünüz için "kullanıcı başına" dosyasına (.vcxproj.user) kaydedilir.

 Aşağıdaki tabloda açıklandığı gibi, Hata **Ayıklayıcı'da** liste kutusunu başlatmak için hangi hata ayıklayıcının kullanılacı olduğunu belirtin. Hangi özelliklerin görünür olduğunu sizin seçiminiz etkiler.

## <a name="configuration-properties-folder-debugging-category"></a>Yapılandırma Özellikleri klasörü (Hata ayıklama kategorisi)

| **Ayar** | **Açıklama** |
| - | - |
| **Başlat için hata ayıklayıcı** | Çalıştıracak hata ayıklayıcısını aşağıdaki seçeneklerle belirtir:<br /><br /> -   **Yerel Windows Hata Ayıklayıcısı**<br />-   **Uzak Windows Hata Ayıklayıcısı**<br />-   **Web Tarayıcısı Hata Ayıklayıcısı**<br />-   **Web Hizmeti Hata Ayıklayıcısı** |
| **Komut** (Yerel Windows Hata Ayıklayıcısı) | Yerel bilgisayarda hata ayıklarken program başlatma komutunu belirtir. |
| **Uzak Komut** (Uzak Windows Hata Ayıklayıcısı) | Uzak bilgisayarda .exe için yol. Yolu, uzak makineye girer gibi girin. |
| **Komut Bağımsız Değişkenleri** (Yerel Windows Hata Ayıklayıcısı)<br /><br /> **Uzak Komut Bağımsız Değişkenleri** (Uzak Windows Hata Ayıklayıcısı) | - Daha önce belirtilen komut için bağımsız değişkenleri belirtir.<br /><br /> Bu kutuda aşağıdaki yeniden yönlendirme işleçlerini kullanabilirsiniz:<br /><br /> < `file`<br /> dosyadan stdin okur.<br /><br /> > `file`<br /> stdout dosyasını dosyaya yazar.<br /><br /> >> `file`<br /> dosyaya stdout ekler.<br /><br /> 2> `file`<br /> stderr dosyasını dosyaya yazar.<br /><br /> 2>> `file`<br /> Dosyaya stderr ekler.<br /><br /> 2> &1<br /> stdout (1) ile aynı konuma stderr (2) çıktısı gönderir.<br /><br /> 1> &2<br /> stdout (1) çıkışını stderr (2) ile aynı konuma gönderir.<br /><br /> Çoğu durumda, bu işleçler yalnızca konsol uygulamaları için geçerlidir. |
| **Çalışma Dizini** | EXE'nizin bulunduğu proje dizinine göre hata ayıklama yapılan programın çalışma dizinini belirtir. Bunu boş bırakırsanız çalışma dizini proje dizinidir. Uzaktan hata ayıklama için proje dizini uzak sunucudadır. |
| **Ekleme** (Yerel Windows Hata Ayıklayıcısı ve Uzak Windows Hata Ayıklayıcısı) | Uygulamanın başlat mı yoksa ekleme mi olduğunu belirtir. Varsayılan ayar Hayır'dır. |
| **Uzak Sunucu Adı** (Uzak Windows Hata Ayıklayıcısı) | Bir uygulamada hata ayıklamak istediğiniz bilgisayarın (sizinki dışında) adını belirtir.<br /><br /> RemoteMachine Derleme makrosu bu özelliğin değerine ayarlanır; Daha fazla bilgi için bkz. [Derleme komutları ve özellikleri için makrolar.](/cpp/build/reference/common-macros-for-build-commands-and-properties) |
| **Bağlantı** (Uzak Windows Hata Ayıklayıcısı) | Uzaktan hata ayıklama için standart ve kimlik doğrulamasız bağlantı türleri arasında geçiş işleminizi sağlar. Uzak Sunucu Adı kutusunda bir **uzak bilgisayar adı** belirtin. Bağlantı türleri aşağıdakileri içerir:<br /><br /> -   **Windows Kimlik Doğrulaması ile Uzak**<br />-   **Kimlik Doğrulamasız Uzak**<br /><br /> **Not** Kimlik Doğrulaması Yok ile uzaktan hata ayıklama, uzak bilgisayarı güvenlik ihlallerine karşı savunmasız bırakabilirsiniz. Windows Kimlik Doğrulaması modu daha güvenlidir.<br /><br /> Daha fazla bilgi için [bkz. Uzaktan hata ayıklama kurulumu.](../debugger/remote-debugging.md) |
| **HTTP URL'si** (Web Hizmeti Hata Ayıklayıcısı ve Web Tarayıcısı Hata Ayıklayıcısı) | Hata ayıklamakta olduğunu projenin bulunduğu URL'yi belirtir. |
| **Hata Ayıklayıcı Türü** | Kullanılacak hata ayıklayıcısı türünü **belirtir:** Yalnızca **Yerel ,** Yalnızca Yönetilen , Yalnızca **GPU,** **Karma** **,** Otomatik (varsayılan) veya **Betik**.<br /><br /> -   **Yalnızca Yerel,** unmanaged C++ koduna göredir.<br />-   **Yalnızca Yönetilen,** ortak dil çalışma zamanı (yönetilen kod) altında çalışan koda göredir.<br />-   **Karma,** hem yönetilen hem de yönetilemeyen kod için hata ayıklayıcılarını çağırır.<br />-   **Derleyici** ve EXE bilgilerine göre hata ayıklayıcı türünü otomatik olarak belirler.<br />-   **Betik,** betikler için bir hata ayıklayıcı çağırır.<br />-   **GPU Yalnızca** GPU C++ AMP veya DirectX başvuru rasterizer üzerinde çalışan bir koda yöneliktir. Bkz. [GPU kodunda hata ayıklama.](../debugger/debugging-gpu-code.md) |
| **Ortam** (Yerel Windows Hata Ayıklayıcısı ve Uzak Windows Hata Ayıklayıcısı) | Hata ayıklamakta olduğunu program için ortam değişkenlerini belirtir. Standart ortam değişkeni söz dizimi kullanın (örneğin, `PATH="%SystemRoot%\..."` ). Bu değişkenler, Ortamı Birleştir ayarına bağlı olarak sistem ortamını geçersiz kılar veya sistem **ortamıyla birleştirilir.** Ayarlar sütununa sol tıklarken bir "Düzenle..." görüntülenir. Ortam değişkenlerini düzenlemek için bu bağlantıyı seçin. |
| **Ortamı Birleştirme** (Yerel Windows Hata Ayıklayıcısı) | Ortam kutusunda belirtilen değişkenlerin işletim  sistemi tarafından tanımlanan ortamla birleştirilecek olup olmadığını belirler. Varsayılan ayar Evet'tir. |
| **SQL Hata Ayıklama** (MPI Küme Hata Ayıklayıcısı'nın hepsi) | Sql yordamlarının uygulamanıza göre hata ayıklamasını [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] sağlar. Varsayılan ayar Hayır'dır. |
| **Hata Ayıklama Hızlandırıcısı Türü** (yalnızca GPU hata ayıklama) | Hata ayıklama için kullanmak üzere GPU cihazı belirtir. Uyumlu GPU cihazları için cihaz sürücülerini yüklemek ek seçenekler ekler. Varsayılan ayar GPU **- Yazılım Öykünücüsü'dür.** |
| **GPU Varsayılan Kesme Noktası Davranışı** (yalnızca GPU hata ayıklama) | Bir SIMD iş parçacığında her iş parçacığı için bir kesme noktası olayı olup olmadığını belirtir. Varsayılan ayar, kesme noktası olaylarını her gün yalnızca bir kez yükseltmektir. |
| **Amp Varsayılan Hızlandırıcısı** | GPU kodunda hata ayıklarken varsayılan AMP hızlandırıcısını belirtir. Soruna **kodunuz** yerine donanımdan mı yoksa sürücüden mi kaynakıldığını araştırmak için BILGISAYAR YAZıLıM Hızlandırıcısı'ı seçin. |
| **Dağıtım Dizini** (Uzak Windows Hata Ayıklayıcısı) | Proje çıkışını başlatmadan önce kopyalanan uzak bilgisayarda yolu belirtir. Yol, uzak bilgisayarda bir ağ paylaşımı veya uzak bilgisayarda bir klasörün yolu olabilir. Varsayılan ayar boştur, yani proje çıkışı bir ağ paylaşımına kopyalanmaz. Dosyaların dağıtımını etkinleştirmek için Dağıt iletişim kutusundaki Dağıt **onay** kutusunu da Yapılandırma Yöneticisi gerekir. Daha fazla bilgi için, [bkz. How to: Create and edit configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Dağıtılan Ek Dosyalar** (Uzak Windows Hata Ayıklayıcısı) | Dağıtım dizini özelliği ayarlanmışsa bu, dağıtım dizinine kopyalanacak ek dosyaların noktalı virgülle ayrılmış listesidir. Varsayılan ayar boştur; bu, dağıtım dizinine hiçbir ek dosya kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için, Configuration Manager iletişim kutusunda **Dağıt** onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md). |
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

Statik kitaplıklar ve DLL 'Ler gibi proje türlerinde hata ayıklamak için, Visual Studio projenizin doğru dosyaları bulabilmeleri gerekir. Kaynak kodu kullanılabilir olduğunda, hata ayıklamayı daha kolay hale getirmek için aynı çözüme ayrı projeler olarak statik kitaplıklar ve DLL 'Ler ekleyebilirsiniz. Bu proje türlerini oluşturma hakkında bilgi için, bkz. [dinamik bağlantı kitaplığı (dll) oluşturma ve kullanma](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) ve [statik kitaplık kullanarak oluşturma](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Kaynak kodu kullanılabilir olduğunda,   >    >  **mevcut koddan** dosya yeni proje ' yi seçerek yeni bir Visual Studio projesi de oluşturabilirsiniz.

Projenizin dışındaki dll 'Lerde hata ayıklamak için bkz. [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Kendi DLL projenizde hata ayıklaması yapmanız, ancak çağıran uygulama için projeye erişiminiz yoksa, bkz. [DLL projesinden hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [C++ projeleri oluşturma ve yönetme](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (DebuggableAttribute Ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Derleme komutları ve özellikleri için genel makrolar](/cpp/ide/common-macros-for-build-commands-and-properties)