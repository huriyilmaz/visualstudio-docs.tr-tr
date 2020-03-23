---
title: 'İzlenecek yol: Birden çok bilgisayarda derleme ortamı oluşturma'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b158854a0026de28cb2fb0a582bbaf764eeaa4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461532"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>İzlenecek yol: Birden çok bilgisayarda derleme ortamı oluşturma

Visual Studio'yı ana bilgisayara yükleyerek ve ardından çeşitli dosyaları ve ayarları başka bir bilgisayara kopyalayarak kuruluşunuz içinde bir yapı ortamı oluşturabilirsiniz, böylece yapılara katılabilir. Visual Studio'yu diğer bilgisayara yüklemeniz gerekmez.

Bu belge, yazılımı dışarıdan yeniden dağıtma veya üçüncü taraflara yapı ortamları sağlama hakları vermez.

> Disclaimer<br /><br /> Bu belge "olduğu gibi" olarak sağlanır. Ana hatlarıyla yapılan adımları test etmiş olsak da, her yapılandırmayı kapsamlı bir şekilde test edemeyiz. Öğrenilen ek bilgilerle belgeyi güncel tutmaya çalışacağız. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu belgede ifade edilen bilgi ve görünümler önceden haber verilmeden değiştirilebilir. Burada verilen bilgilerle ilgili olarak Microsoft açık veya zımni hiçbir garanti vermez. Kullanımlardan doğacak riskler size aittir.<br /><br /> Bu belge, herhangi bir Microsoft ürününde herhangi bir fikri mülkiyet için size yasal haklar sağlamaz. Bu belgeyi dahili, başvuru amaçlarınız için kopyalayıp kullanabilirsiniz.<br /><br /> Microsoft'a bu belgeyle ilgili herhangi bir öneri, yorum veya diğer geri bildirim ("Geri bildirim") verme yükümlülüğüyoktur. Ancak, gönüllü olarak sağladığınız geri bildirimler Microsoft Ürünlerinde ve ilgili belirtimlerde veya diğer belgelerde (topluca "Microsoft Teklifleri") kullanılabilir ve bu da diğer üçüncü taraflarca kendi ürünlerini geliştirmeleri için güvenilebilir. Buna göre, bu belgenin veya geçerli oldukları Microsoft Teklifleri'nin herhangi bir sürümü hakkında Microsoft Geri Bildirimi verirseniz, (a) Microsoft Geri Bildiriminizi herhangi bir Microsoft'ta serbestçe kullanabilir, çoğaltabilir, lisanslayabilir, dağıtabilir ve başka bir şekilde ticarileştirebilir Teklif; (b) Üçüncü taraflara, yalnızca diğer ürünlerin Microsoft Ürünü'nün Geri Bildiriminizi içeren belirli bir parçasını kullanmasına veya bunlarla arayüz kurabilmesi için gerekli patent haklarını ücretsiz olarak vermiş siniz; ve (c) Microsoft'a herhangi bir patent, telif hakkı veya diğer fikri mülkiyet talebine veya üçüncü tarafın haklarına tabi olduğuna inandığınız herhangi bir Geri Bildirim (i) vermeyeceksiniz; veya (ii) herhangi bir Üçüncü Taraf'a lisanslanması veya üçüncü taraflarla paylaşılması nı gerektiren veya bu Geri Bildirimleri veya diğer Microsoft fikri mülkiyetlerinden türetilen microsoft tekliflerinin lisanslanmasına veya başka bir şekilde paylaşılmasını gerektiren lisans koşullarına tabidir.

Bu iz, aşağıdaki işletim sistemlerine karşı doğrulanmıştır:

- Windows 8 (x86 ve x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Bu izbin adımlarını tamamladıktan sonra, bu tür uygulamalar oluşturmak için birden çok bilgisayar ortamını kullanabilirsiniz:

- Windows 8 SDK kullanan C++ masaüstü uygulamaları
- .NET Framework 4.5'i hedefleyen Visual Basic veya C# masaüstü uygulamaları

Çoklu bilgisayar ortamı bu tür uygulamalar oluşturmak için kullanılamaz:

- UWP uygulamaları. UWP uygulamaları oluşturmak için Visual Studio'yu yapı bilgisayarına yüklemeniz gerekir.
- .NET Framework 4 veya daha öncesini hedefleyen masaüstü uygulamaları. Bu tür uygulamalar oluşturmak için, yapı bilgisayarına Visual Studio veya .NET Başvuru Derlemeleri ve Araçları 'nı (Windows 7.1 SDK'dan) yüklemeniz gerekir.

## <a name="prerequisites"></a>Önkoşullar

.NET **masaüstü geliştirme** iş yükü yüklü Visual Studio.

## <a name="install-software-on-the-computers"></a>Bilgisayarlara yazılım yükleme

Önce ana bilgisayarı ayarlayın ve ardından yapı bilgisayarını ayarlayın.

Visual Studio'yu ana bilgisayara yükleyerek, daha sonra yapı bilgisayarına kopyalayabildiğiniz dosyaları ve ayarları oluşturursunuz. Visual Studio'yu bir x86 veya x64 bilgisayara yükleyebilirsiniz, ancak yapı bilgisayarının mimarisi ana bilgisayarın mimarisiyle eşleşmelidir.

1. Ana bilgisayarda Visual Studio'yu yükleyin.

2. Yapı bilgisayarında .NET Framework 4.5 veya sonraki leri yükleyin. Yüklü olduğunu doğrulamak için, kayıt defteri alt **HKEY_LOCAL_MACHINE/SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full'daki** **Sürüm** girişinin **4,5** veya daha yüksek bir değere sahip olup olmadığını denetleyin.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Dosyaları ana bilgisayardan yapı bilgisayarına kopyalama

Bu bölümde, ana bilgisayardan yapı bilgisayarına belirli dosyaların, derleyicilerin, yapı araçlarının, MSBuild varlıklarının ve kayıt defteri ayarlarının kopyalanması yer almaktadır. Bu yönergeler, Visual Studio'yu ana bilgisayardaki varsayılan konumda yüklediğinizi varsayar; başka bir konuma yüklediyseniz, adımları buna göre ayarlayın.

- Bir x86 bilgisayarda varsayılan konum *C:\Program Files\Microsoft Visual Studio*
- Bir x64 bilgisayarda varsayılan konum *C:\Program Dosyaları (x86)\Microsoft Visual Studio*

*Program Dosyaları* klasörünün adının yüklenen işletim sistemine bağlı olduğuna dikkat edin. Bir x86 bilgisayarda, adı *Program Files*olduğunu; bir x64 bilgisayarda, adı *Program Dosyaları (x86)* olduğunu. Sistem mimarisinden bağımsız olarak, bu izleme *Program Dosyaları* klasörünü *%ProgramFiles%* olarak ifade eder.

> [!NOTE]
> Yapı bilgisayarında, ilgili tüm dosyaların aynı sürücüde olması gerekir. Ancak, bu sürücü için sürücü harfi, Visual Studio'nun ana bilgisayara yüklendiği sürücünün sürücü mektubundan farklı olabilir. Her durumda, bu belgede daha sonra açıklandığı gibi kayıt defteri girişleri oluştururken dosyaların konumunu hesaba katmalısınız.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Windows SDK dosyalarını yapı bilgisayarına kopyalama

1. Yalnızca Windows 8 için Windows SDK yüklüyse, bu klasörleri ana bilgisayardan yapı bilgisayarına özyinelemeyle kopyalayın:

   - %ProgramFiles%\Windows Kitleri\8.0\bin\

   - %ProgramFiles%\Windows Kitleri\8.0\Kataloglar\

   - %ProgramFiles%\Windows Kitleri\8.0\DesignTime\

   - %ProgramFiles%\Windows Kitleri\8.0\,

   - %ProgramFiles%\Windows Kitleri\8.0\Lib\

   - %ProgramFiles%\Windows Kitleri\8.0\Redist\

   - %ProgramFiles%\Windows Kitleri\8.0\Başvurular\

   Ayrıca bu diğer Windows 8 kitleri varsa ...

   - Microsoft Windows Değerlendirme ve Dağıtım Kiti

   - Microsoft Windows Sürücü Kiti

   - Microsoft Windows Donanım Sertifika Seti

   ... önceki adımda listelenen *%ProgramFiles%\Windows Kitleri\8.0* klasörlerine dosya yüklemiş olabilirler ve lisans koşulları bu dosyalar için yapı sunucusu haklarına izin vermeyebilir. Dosyaların yapı bilgisayarınıza kopyalanıp kopyalanamayacağını doğrulamak için yüklü her Windows kitinin lisans koşullarını denetleyin. Lisans koşulları yapı sunucusu haklarına izin vermiyorsa, dosyaları yapı bilgisayarından kaldırın.

2. Aşağıdaki klasörleri ana bilgisayardan yapı bilgisayarına özyinelemeli olarak kopyalayın:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Araçlar\

    - %ProgramFiles%\Ortak Dosyalar\Birleştirme Modülleri\

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\VC\

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference Derlemeler\Microsoft\Framework\\. NETCore\v4.5\

    - %ProgramFiles%\Reference Derlemeler\Microsoft\Framework\\. NETFramework\v4.5\

3. Bu dosyaları ana bilgisayardan yapı bilgisayarına kopyalayın:

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürüm>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\Tools\vsvars32.bat

4. Aşağıdaki Visual C++ çalışma zamanı kitaplıkları, yalnızca yapı bilgisayarında (örneğin, otomatik sınamanın bir parçası olarak) yapı çıktıları çalıştırıyorsanız gereklidir. Dosyalar genellikle sistem mimarisine bağlı olarak *%ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\VC\redist\x86* veya *%ProgramFiles%\Microsoft\\\<Visual Studio sürümü>\\ \<sürümü>\VC\redist\x64* klasörü altında alt klasörlerde bulunur. x86 sistemlerinde x86 ikililerini *Windows\System32* klasörüne kopyalayın. x64 sistemlerinde, x86 ikililerini *Windows\SysWOW64* klasörüne, x64 ikililerini de *Windows\System32* klasörüne kopyalayın.

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Hata [ayıklama çalıştırılabilir çalıştırmak](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)için bir test makinesi hazırlayın açıklandığı gibi, *Debug_NonRedist\x86* veya *Debug_NonRedist\x64* klasöründen yalnızca aşağıdaki dosyaları yapı bilgisayarına kopyalayın. Başka hiçbir dosya kopyalanamaz.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Kayıt defteri ayarları oluşturma

MSBuild ayarlarını yapılandırmak için kayıt defteri girişleri oluşturmanız gerekir.

1. Kayıt defteri girişleri için üst klasörü tanımlayın. Kayıt defteri girişlerinin tümü aynı ana anahtar altında oluşturulur. X86 bilgisayarında ana anahtar **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft'tu.** X64 bilgisayarında ana anahtar **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft'tu.** Sistem mimarisinden bağımsız olarak, bu gözden geçirme üst anahtarı %RegistryRoot% olarak ifade eder.

    > [!NOTE]
    > Ana bilgisayarınızın mimarisi yapı bilgisayarınızın mimarisinden farklıysa, her bilgisayarda uygun ana anahtarı kullandığınızdan emin olun. Bu, özellikle dışa aktarma işlemini otomatikleştiriyorsanız önemlidir.
    >
    > Ayrıca, yapı bilgisayarında ana bilgisayarda kullandığınızdan farklı bir sürücü harfi kullanıyorsanız, kayıt defteri girişlerinin değerlerini eşleşecek şekilde değiştirdiğinden emin olun.

2. Yapı bilgisayarında aşağıdaki kayıt defteri girişlerini oluşturun. Bu girişlerin tümü dizeleri (Type == "REG_SZ" kayıt defterinde). Bu girişlerin değerlerini ana bilgisayardaki karşılaştırılabilir girişlerin değerleriyle aynı şekilde ayarlayın.

   - **%RegistryRoot%\\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSYapı Genel Assemblies@(Varsayılan)**

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **%RegistryRoot%\VisualStudio\11.0@Source Dizinleri**

   - <strong>%RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **%RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kitleri\YüklüRoots@KitsRoot</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   X64 yapılı bir bilgisayarda, aşağıdaki kayıt defteri girişini de oluşturun ve nasıl ayarlanıncaya kadar belirlemek için ana bilgisayara başvurun.

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Yapı bilgisayarınız x64 ise ve MSBuild'in 64 bit sürümünü kullanmak istiyorsanız veya Team Foundation Server Build Service'i x64 bilgisayarda kullanıyorsanız, yerel 64 bit kayıt defterinde aşağıdaki kayıt defteri girişlerini oluşturun. Bu girişlerin nasıl ayarlan olduğunu belirlemek için ana bilgisayara başvurun.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Yapı bilgisayarında ortam değişkenlerini ayarlama

Yapı bilgisayarında MSBuild'i kullanmak için PATH ortamı değişkenlerini ayarlamanız gerekir. Değişkenleri ayarlamak için *vcvarsall.bat'ı* kullanabilir veya bunları el ile yapılandırabilirsiniz.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Çevre değişkenlerini ayarlamak için vcvarsall.bat kullanın

Yapı bilgisayarında Komut **İstem** penceresini açın ve *%Program\\\<Dosyaları\Microsoft Visual Studio sürümünü \\ \<>sürümü>\VC\vcvarsall.bat çalıştırın.* Kullanmak istediğiniz araç kümesini belirtmek için komut satırı bağımsız değişkeni kullanabilirsiniz—x86, yerel x64 veya x64 çapraz derleyici. Komut satırı bağımsız değişkeni belirtmezseniz, x86 araç kümesi kullanılır.

Bu tablo *vcvarsall.bat*için desteklenen bağımsız değişkenleri açıklar:

|Vcvarsall.bat argümanı|Derleyici|Bilgisayar mimarisi oluşturma|Çıktı mimarisi oluşturma|
| - |--------------| - | - |
|x86 (varsayılan)|32 bit Yerli|x86, x64|x86|
|x86_amd64|x64 Çapraz|x86, x64|x64|
|amd64|x64 Yerli|x64|x64|

*Vcvarsall.bat* başarılı bir şekilde çalışırsa-yani hiçbir hata iletisi görüntülenmez-bir sonraki adımı atlayabilir ve bu belgenin yapı bilgisayar bölümündeki [Genel Derleme Önbelleğine (GAC) Yükleme MSBuild derlemelerine](#install-msbuild-to-gac) devam edebilirsiniz.

### <a name="manually-set-environment-variables"></a>Ortam değişkenlerini el ile ayarlayın

1. Komut satırı ortamını el ile yapılandırmak için, bu yolu PATH ortamı değişkenine ekleyin:

    - %Program Dosyaları%\Microsoft\\\<Visual \\ \<Studio sürümü>sürümü>\Common7\IDE

2. İsteğe bağlı olarak, çözümlerinizi oluşturmak için MSBuild'i kullanmayı kolaylaştırmak için PATH değişkenine aşağıdaki yolları da ekleyebilirsiniz.

   Yerel 32 bit MSBuild'i kullanmak istiyorsanız, bu yolları PATH değişkenine ekleyin:

   - %Program Dosyaları%\Microsoft SDK'lar\Windows\v8.0A\bin\NETFX 4.0 Araçlar

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Yerel 64 bit MSBuild'i kullanmak istiyorsanız, bu yolları PATH değişkenine ekleyin:

   - %Program Dosyaları%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Araçlar\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" />MSBuild derlemelerini yapı bilgisayarındaki Global Assembly Önbelleğine (GAC) yükleme

MSBuild, yapı bilgisayarında GAC'ye yüklenmesi için bazı ek derlemeler gerektirir.

1. Aşağıdaki derlemeleri ana bilgisayardan yapı bilgisayarına kopyalayın. GAC'ye yüklenecektir, çünkü bunları yapı bilgisayarına nereye koyduğunuz önemli değildir.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio \\ \<sürümü>sürümü>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Derlemeleri GAC'ye yüklemek için, *gacutil.exe'yi* yapı bilgisayarında bulun— genellikle %ProgramFiles%\Microsoft SDK'lar\Windows\v8.0A\bin\NETFX\\4.0 Tools'ta bulunur. Bu klasörü bulamıyorsanız, ana bilgisayardan bu bölümün [yapı bilgisayarı bölümüne kopyala dosyalarındaki](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) adımları yineleyin.

     Yönetim haklarına sahip bir **Komut İstemi** penceresi açın ve her dosya için bu komutu çalıştırın:

     **gacutil -i \<dosya>**

    > [!NOTE]
    > Bir derlemenin GAC'ye tam olarak yüklenmesi için yeniden başlatma gerekebilir.

## <a name="build-projects"></a>Projeler oluşturun

Visual Studio projeleri ve çözümleri oluşturmak için Azure Ardışık Düzenlerini kullanabilir veya bunları komut satırında oluşturabilirsiniz. Proje oluşturmak için Azure Pipelines'ı kullandığınızda, sistem mimarisine karşılık gelen MSBuild yürütülebilirliğini çağırır. Komut satırında, 32 bit MSBuild veya 64 bit MSBuild'i kullanabilir ve PATH ortamı değişkenini ayarlayarak veya doğrudan mimariye özgü MSBuild çalıştırılabilir'i çağırarak MSBuild mimarisini seçebilirsiniz.

komut isteminde *msbuild.exe'yi* kullanmak için *solution.sln'nin* çözümünüzünüzün adı için bir yer tutucu olduğu aşağıdaki komutu çalıştırın.

**msbuild** *çözüm.sln*

Komut satırında MSBuild'in nasıl kullanılacağı hakkında daha fazla bilgi için [Komut satırı başvurusuna](../msbuild/msbuild-command-line-reference.md)bakın.

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Kaynak denetimine denetlenebilmeleri için yapı ortamını oluşturma

Çeşitli bilgisayarlara dağıtılabilen ve "GAC" dosyaları oluşturma veya kayıt defteri ayarlarını değiştirme gerektirmeyen bir yapı ortamı oluşturabilirsiniz. Aşağıdaki adımlar bunu gerçekleştirmek için sadece bir yoludur. Bu adımları yapı ortamınızın benzersiz özelliklerine uyarlayın.

> [!NOTE]
> *Tracker.exe'nin* bir yapı sırasında hata atmayabilmesi için artımlı binayı devre dışı bıraktınız. Artımlı binayı devre dışı kalmak için bu yapı parametresini ayarlayın:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Ana bilgisayarda bir *Depo* dizini oluşturun.

     Bu adımlar dizini %Depo% olarak ifade eder.

2. Yeni oluşturduğunuz *%Depo%* dizininin altına yapıştırmak dışında, ana bilgisayardan bu gözden geçirmenin [yapı bilgisayarı bölümüne kopyala dosyalarına](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) kopyalayın. Örneğin, *%ProgramFiles%\Windows Kitleri\8.0\bin'den* *%Depo%\Windows Kitleri\8.0\bin'* e kopyalayın.

3. Dosyalar *%Depo%* olarak yapıştırıldığında, aşağıdaki değişiklikleri yapın:

    - %Depo%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ve \Microsoft.CppCommon.targets\\, her örneğini değiştirin

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         -

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         Eski adlandırma, derlemenin GAC'ed olmasına dayanır.

    - %Depo% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets olarak, her örneğini değiştirmek

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         -

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Bir *.props* dosyası oluşturun —örneğin, *Partner.AutoImports.props*— ve projelerinizi içeren klasörün köküne koyun. Bu dosya, çeşitli kaynakları bulmak için MSBuild tarafından kullanılan değişkenleri ayarlamak için kullanılır. Değişkenler bu dosya tarafından ayarlanmaz, bunlar diğer *.props* dosyaları ve *.hedef* dosyaları tarafından ayarlanır. Herhangi bir kayıt defteri değeri ayarlamadığımız için, bu değişkenler boş olur ve yapı başarısız olur. Bunun yerine, *Partner.AutoImports.props*bu ekleyin:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio\2017\Enterprise\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. Proje dosyalarınızın her birinde, `<Project Default Targets...>` satırdan sonra en üste aşağıdaki satırı ekleyin.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - *Depo=Adım 1'de oluşturduğunuz Depo dizininin konumunu* ayarlayın

    - Yolu ayarla=%yol%; *MSBuild'in bilgisayardaki konumu*;%D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D epot%\Microsoft Visual Studio 15.0\Common7\IDE\

       Yerli 64 bit bina için MSBuild'in 64 bit sürümüne işaret edin.

::: moniker-end

::: moniker range=">=vs-2019"

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - *Depo=Adım 1'de oluşturduğunuz Depo dizininin konumunu* ayarlayın

    - Yolu ayarla=%yol%; *MSBuild'in bilgisayardaki konumu*;%D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D epot%\Microsoft Visual Studio 16.0\Common7\IDE\

       Yerli 64 bit bina için MSBuild'in 64 bit sürümüne işaret edin.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Yürütülebilir hata ayıklamayı çalıştırmak için test makinesi hazırlama](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)