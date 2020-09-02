---
title: C++ hata ayıklama yapılandırması için proje ayarları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
- FSharp
- VB
- CSharp
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
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca9ff0678ba2c7abafa0d988efa09437ccd27dca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687566"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ Hata Ayıklama Yapılandırması Proje Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Özellik sayfaları** iletişim kutusundaki bir C veya Visual C++ hata ayıklama yapılandırması için proje ayarlarını, [nasıl yapılır: ayarlama hata ayıklama ve yayın yapılandırmalarını](../debugger/how-to-set-debug-and-release-configurations.md)açıklandığı gibi değiştirebilirsiniz. Aşağıdaki tablolarda, **Özellik sayfaları** iletişim kutusunda hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir.  
  
> [!WARNING]
> C++ dilinde yazılan Windows Mağazası uygulamaları ve bileşenleri için **yapılandırma özellikleri/hata ayıklama** kategorisindeki hata ayıklama Projesi Ayarları farklıdır. Bkz. Windows Geliştirme Merkezi 'nde [hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) .  
  
 **Hata ayıklayıcı 'nın başlatılması için** hangi hata ayıklayıcının kullanılacağını belirtin liste kutusu. Seçiminiz, hangi özelliklerin görünür olduğunu etkiler.  
  
 Her hata ayıklama özelliği ayarı, çözümünüzü kaydettiğiniz her seferinde çözümünüz için "Kullanıcı başına" dosyasına (. vcxproj. User) otomatik olarak yazılır ve kaydedilir.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Yapılandırma özellikleri klasörü (hata ayıklama kategorisi)  
  
|**Ayar**|**Açıklama**|  
|-----------------|---------------------|  
|**Başlatılacak hata ayıklayıcı**|Aşağıdaki seçimlerle çalıştırılacak hata ayıklayıcıyı belirtir:<br /><br /> -   **Yerel Windows hata ayıklayıcısı**<br />-   **Uzak Windows hata ayıklayıcısı**<br />-   **Web tarayıcısı hata ayıklayıcı**<br />-   **Web hizmeti hata ayıklayıcısı**|  
|**Komut** (yerel Windows hata ayıklayıcısı)|Yerel bilgisayarda hata ayıklaması yaptığınız programı başlatma komutunu belirtir.|  
|**Uzak komut** (uzak Windows hata ayıklayıcı)|Uzak bilgisayardaki. exe dosyasının yolu. Yolu, uzak makineye girdiğiniz gibi girin.|  
|**Komut bağımsız değişkenleri** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı)|-Daha önce belirtilen komut için bağımsız değişkenleri belirtir.<br /><br /> Bu kutuda aşağıdaki yeniden yönlendirme işleçlerini kullanabilirsiniz:<br /><br /> < `file`<br /> Dosyadan stdin okur.<br /><br /> > `file`<br /> Stdout dosyasına yazar.<br /><br /> >> `file`<br /> Stdout 'ı dosyaya ekler.<br /><br /> 2> `file`<br /> Dosya için stderr yazar.<br /><br /> 2>> `file`<br /> Stderr 'i dosyaya ekler.<br /><br /> 2> &1<br /> Stderr (2) çıkışını stdout (1) ile aynı konuma gönderir.<br /><br /> 1> &2<br /> Stdout (1) çıkışını stderr (2) ile aynı konuma gönderir.<br /><br /> Çoğu durumda, bu işleçler yalnızca konsol uygulamaları için geçerlidir.|  
|**Çalışma dizini**|EXE 'nizin bulunduğu proje dizinine göre, hata ayıklanan programın çalışma dizinini belirtir. Bu alanı boş bırakırsanız, çalışma dizini proje dizinidir. Uzaktan hata ayıklama için, proje dizini uzak sunucuda olur.|  
|**Ekle** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı)|Uygulamanın başlatılıp başlatılmayacağını belirtir. Varsayılan ayar Hayır ' dır.|  
|**Uzak sunucu adı** (uzak Windows hata ayıklayıcı)|Bir uygulamada hata ayıklamak istediğiniz bir bilgisayarın (sizinkinden başka) adını belirtir.<br /><br /> RemoteMachine derleme makrosu, bu özelliğin değerine ayarlanır; daha fazla bilgi için bkz. [derleme komutları ve özellikleri Için makrolar](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Bağlantı** (uzak Windows hata ayıklayıcı)|Uzaktan hata ayıklama için standart ve kimlik doğrulama olmayan bağlantı türleri arasında geçiş yapmanıza olanak sağlar. **Uzak sunucu adı** kutusunda uzak bilgisayar adını belirtin. Bağlantı türleri şunları içerir:<br /><br /> -   **Windows kimlik doğrulaması ile uzaktan**<br />-   **Kimlik doğrulaması olmadan uzak (yalnızca yerel)**<br /><br /> **Göz önünde** Kimlik doğrulaması olmadan uzaktan hata ayıklama uzak bilgisayarı güvenlik ihlallerine karşı savunmasız bırakabilir. Windows kimlik doğrulama modu daha güvenlidir.<br /><br /> Daha fazla bilgi için bkz. [Uzaktan hata ayıklama kurulumu](../debugger/remote-debugging.md).|  
|**Http URL 'si** (Web hizmeti hata ayıklayıcısı ve Web tarayıcısı hata ayıklayıcı)|Hata ayıkladığınız projenin bulunduğu URL 'YI belirtir.|  
|**Hata ayıklayıcı türü**|Kullanılacak hata ayıklayıcı türünü belirtir: **yalnızca yerel**, yalnızca **yönetilen**, yalnızca **GPU**, **karma**, **Otomatik** (varsayılan) veya **komut dosyası**.<br /><br /> -   **Yalnızca yerel** , yönetilmeyen C++ kodu içindir.<br />-   **Yalnızca yönetilen** , ortak dil çalışma zamanı (yönetilen kod) altında çalışan koda yöneliktir.<br />-   Hem yönetilen hem de yönetilmeyen kod için **karışık** hata ayıklayıcıları çağırır.<br />-   Derleyici ve EXE bilgilerine göre hata ayıklayıcı türünü **Otomatik** olarak belirler.<br />-   **Betik** , betikler için bir hata ayıklayıcı çağırır.<br />-   **Yalnızca GPU** , bir GPU aygıtında veya DirectX başvuru tarayıcısı üzerinde çalışan C++ amp kod içindir. Bkz. [GPU kodunda hata ayıklama](../debugger/debugging-gpu-code.md).|  
|**Ortam** (yerel Windows hata ayıklayıcı)|Hata ayıkladığınız program için ortam değişkenlerini belirtir. Standart ortam değişkeni sözdizimini kullanın (örneğin, `PATH="%SystemRoot%\..."` ). Bu değişkenler, **birleştirme ortamı** ayarına bağlı olarak, sistem ortamını geçersiz kılar veya sistem ortamıyla birleştirilir. Ayarlar sütununa tıkladığınızda bir "Düzenle..." görüneceği. Ortam değişkenlerini düzenlemek için bu bağlantıya tıklayın.|  
|**Birleştirme ortamı** (yerel Windows hata ayıklayıcı)|**Ortam** kutusunda belirtilen değişkenlerin, işletim sistemi tarafından tanımlanan ortamla birleştirilip birleştirilmeyeceğini belirler. Varsayılan ayar Evet ' tir.|  
|**SQL hata ayıklama** (tümü, MPI kümesi hata ayıklayıcısı)|Uygulamanızdan SQL yordamlarını hata ayıklamasına izin vermez [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] . Varsayılan ayar Hayır ' dır.|  
|**Hata ayıklama Hızlandırıcı türü** (yalnızca GPU hata ayıklama)|Hata ayıklama için kullanılacak GPU cihazını belirtir. Uyumlu GPU cihazları için cihaz sürücülerinin yüklenmesi, ek seçenekler ekler. Varsayılan ayar "GPU-yazılım öykünücüsü" dir.|  
|**GPU Varsayılan kesme noktası davranışı** (yalnızca GPU hata ayıklama)|SıMD warp 'daki her iş parçacığı için bir kesme noktası olayının yapılıp yapılmayacağını belirtir. Varsayılan ayar, kesme noktasını her çarpıtma için yalnızca bir kez tetiklemedir.|  
|**Amp varsayılan Hızlandırıcı** (yalnızca GPU hata ayıklama)|GPU kodunda hata ayıklarken varsayılan AMP hızlandırıcıyı belirtir. Kod yerine donanımdan veya bir sürücüden kaynaklanan bir sorun olup olmadığını araştırmak için **warp yazılım hızlandırıcıyı** seçin.|  
|**Dağıtım dizini** (uzak Windows hata ayıklayıcı)|Proje çıkışının, başlamadan önce kopyalanacağı uzak bilgisayardaki yolu belirtir. Yol, uzak bilgisayardaki bir ağ paylaşımından olabilir veya uzak bilgisayardaki bir klasörün yolu olabilir. Varsayılan ayar boştur; bu, proje çıkışının bir ağ paylaşımında kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için, Configuration Manager iletişim kutusunda **Dağıt** onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).|  
|**Dağıtılacak ek dosyalar** (uzak Windows hata ayıklayıcı)|Dağıtım dizini özelliği ayarlanmışsa bu, dağıtım dizinine kopyalanacak ek dosyaların noktalı virgülle ayrılmış listesidir. Varsayılan ayar boştur; bu, dağıtım dizinine hiçbir ek dosya kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için, Configuration Manager iletişim kutusunda **Dağıt** onay kutusunu da seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).|  
|**Visual C++ hata ayıklama çalışma zamanı kitaplıklarını dağıtma** (uzak Windows hata ayıklayıcı)|Dağıtım dizini özelliği ayarlanmışsa bu, geçerli platform için Visual C++ hata ayıklama çalışma zamanı kitaplıklarının ağ paylaşımında kopyalanıp kopyalanmayacağını belirtir. Varsayılan ayar Evet ' tir.|  
  
### <a name="cc-folder-general-category"></a>C/C++ klasörü (genel kategori)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Hata ayıklama bilgi biçimi** ([/Z7,/ZD, Zi,/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Proje için oluşturulacak hata ayıklama bilgilerinin türünü belirtir.<br /><br /> Varsayılan seçenek (/ZI) Düzenle ve devam et uyumlu biçimde bir program veritabanı (PDB) oluşturur. Daha fazla bilgi için bkz. [/Z7,/ZD,/Zi,/ZI (hata ayıklama bilgileri biçimi)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>C/C++ klasörü (Iyileştirme kategorisi)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**İyileştirme**|Derleyicinin ürettiği kodu iyileştiregerekip gerekmediğini belirtir. İyileştirme, yürütülen kodu değiştirir. İyileştirilmiş kod artık kaynak kodla eşleşmiyor. Bu nedenle, hata ayıklama zordur.<br /><br /> Varsayılan seçenek (**devre dışı (/0d**) iyileştirme 'yi bastırır. İyileştirme bastırıldığınızda geliştirme yapabilir ve sonra kodunuzun üretim sürümünü oluştururken bunu açabilirsiniz.|  
  
### <a name="linker-folder-debugging-category"></a>Bağlayıcı klasörü (hata ayıklama kategorisi)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Hata ayıklama bilgisi oluştur** ([/Debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Bağlayıcının/Z7,/ZD, Zi veya/zitarafından belirtilen biçime sahip hata ayıklama bilgilerini içermesini söyler.|  
|**Program veritabanı dosyası oluştur** ([/pdb: ad](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|Bu kutudaki PDB dosyasının adını belirtin. Hata ayıklama bilgileri biçimi için ZI veya/Zi seçmeniz gerekir.|  
|**Özel sembolleri** çıkar ([/pdbçıkarıldı: filename](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|PDB dosyasına özel semboller eklemek istemiyorsanız, bu kutudaki PDB dosyasının adını belirtin. Bu seçenek/DEBUG,/Z7,/Zd gibi bir PDB dosyası oluşturan derleyici veya bağlayıcı seçeneklerinden herhangi biriyle program görüntünüzü oluştururken ikinci program veritabanı (PDB) dosyası oluşturur. Ya da/Zi. Bu ikinci PDB dosyası, müşterilerinize göndermek istemediğiniz sembolleri atlar. Daha fazla bilgi için bkz. [/Pdbçıkarıldı (özel sembolleri Strip)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Eşleme dosyası oluştur** ([/map](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Bağlayıcının bağlama sırasında bir eşleme dosyası oluşturmasını söyler. Varsayılan ayar Hayır ' dır. Daha fazla bilgi için bkz. [/Map (mapfile üret)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Eşleme dosyası adı** ([/map:](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*ad*)|Eşleme dosyası oluştur ' u seçerseniz, bu kutuda eşleme dosyasını belirtebilirsiniz. Daha fazla bilgi için bkz. [/Map (mapfile üret)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Eşleme dışarı aktarmaları** ([/MapInfo: dışarı aktarmalar](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Eşleme dosyasına aktarılmış işlevleri içerir. Varsayılan ayar Hayır ' dır. Daha fazla bilgi için bkz. [/MapInfo (mapfile Içine bilgi ekleme)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Hata ayıklanabilir derlemesi** ([/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Bağlayıcı/ASSEMBLYDEBUG seçeneğinin ayarlarını belirtir. Olası değerler aşağıdaki gibidir:<br /><br /> -   **Hata ayıklanabilir özniteliği yayılmadı**.<br />-   **Çalışma zamanı izleme ve devre dışı bırakma (/ASSEMBLYDEBUG)**. Bu, varsayılan ayardır,<br />-   **Çalışma zamanı Izleme yok ve iyileştirmeleri etkinleştir (/ASSEMBLYDEBUG: DISABLE)**.<br />-   **\<inherit from parent or project defaults>**.<br />-Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (hata ayıklama Ggableattribute Ekle)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Yapılandırma özellikleri klasöründeki (hata ayıklama kategorisi) bu ayarları, Microsoft. VisualStudio. VCProjectEngine. VCDebugSettings arabirimini kullanarak programlı bir şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Visual C++ projeleri oluşturma ve yönetme](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (hata ayıklama Ggableattribute Ekle)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Derleme komutları ve özellikleri için ortak makrolar](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)
