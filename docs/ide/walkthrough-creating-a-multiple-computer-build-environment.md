---
title: Birden çok bilgisayarda derleme ortamı oluşturma
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
ms.openlocfilehash: bec0ada652da4ac02c457cdc280778487e4b27a1
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743121"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>İzlenecek yol: Birden çok bilgisayarda derleme ortamı oluşturma

Kuruluşunuzda Visual Studio 'Yu bir ana bilgisayara yükleyerek ve sonra çeşitli dosya ve ayarları, yapılara katılabilecek şekilde başka bir bilgisayara kopyalayarak kuruluşunuz içinde bir yapı ortamı oluşturabilirsiniz. Visual Studio 'Yu diğer bilgisayara yüklemenize gerek yoktur.

Bu belge, yazılımı dışarıdan yeniden dağıtmak veya üçüncü taraflara derleme ortamları sağlamak için bir haklara sahip değildir.

> Disclaimer<br /><br /> Bu belge "olduğu gibi" esasına göre sunulmaktadır. Özetlenen adımları test etmemiz mümkün olsa da, her yapılandırmanın tamamen test etmeme. Belgeyi, öğrendiğimiz tüm ek bilgilerle güncel tutmaya çalışacaktır. Bu belgede ifade edilen, URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bilgiler ve görünümler bildirimde bulunmaksızın değiştirilebilir. Burada verilen bilgilerle ilgili olarak Microsoft açık veya zımni hiçbir garanti vermez. Kullanımlardan doğacak riskler size aittir.<br /><br /> Bu belge, herhangi bir Microsoft ürününde herhangi bir fikri mülkiyet için size yasal haklar sağlamaz. Bu belgeyi dahili, başvuru amaçlarınız için kopyalayıp kullanabilirsiniz.<br /><br /> Bu belgeyle ilgili olarak Microsoft 'a herhangi bir öneri, yorum veya geri bildirim ("geri bildirim") verme yükümlülüğü yoktur. Ancak, gönüllü olarak sağladığınız tüm geri bildirimler, Microsoft ürünlerinde ve ilgili belirtimlerde ya da başka belgelerde (topluca, "Microsoft teklifleri") kullanılabilir Buna uygun olarak, bu belgenin herhangi bir sürümünde ya da uygulandıkları Microsoft tekliflerinden Microsoft 'a geri bildirimde bulunmayı kabul etmiş olursunuz: (a) Microsoft, herhangi bir Microsoft teklifiyle ilgili görüşlerinizi ücretsiz olarak kullanabilir, yeniden üretebilir, lisanslayın, dağıtabilir ve başka bir şekilde ticari hale getirmenizi sağlar; (b) Ayrıca üçüncü taraflara ücretsiz olarak, diğer ürünlerin yalnızca geri bildiriminizi içeren bir Microsoft ürününün belirli bölümleriyle kullanmasını veya arabirimini kullanmasını sağlamak için gerekli olan patent haklarını de vermiş olursunuz; ve (c) Microsoft 'a geri bildirim (i), herhangi bir patent, telif hakkı veya diğer fikri mülkiyet talebine ya da herhangi bir üçüncü tarafın olduğuna inanmanızın bir sebebini sunmayacak; ya da (ii) bu geri bildirimde bulunan veya ondan türetilmiş herhangi bir Microsoft teklifini ya da başka bir Microsoft fikri mülkiyet ya da herhangi bir üçüncü tarafla lisanslanmasını gerektiren lisans koşullarına tabidir.

Bu izlenecek yol aşağıdaki işletim sistemlerine karşı onaylanmıştır:

- Windows 8 (x86 ve x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Bu izlenecek adımları tamamladıktan sonra, bu tür uygulamaları oluşturmak için birden çok bilgisayar ortamı kullanabilirsiniz:

- Windows 8 SDK kullanan C++ masaüstü uygulamaları
- .NET Framework 4,5 'yi hedefleyen Visual Basic veya C# masaüstü uygulamaları

Birden çok bilgisayar ortamı, bu tür uygulamaları oluşturmak için kullanılamaz:

- UWP uygulamaları. UWP uygulamaları oluşturmak için, Visual Studio 'Yu yapı bilgisayarına yüklemelisiniz.
- .NET Framework 4 veya önceki sürümleri hedefleyen masaüstü uygulamaları. Bu tür uygulamaları oluşturmak için, Yapı bilgisayarında Visual Studio 'Yu veya .NET başvuru derlemelerini ve araçlarını (Windows 7,1 SDK 'dan) yüklemelisiniz.

## <a name="prerequisites"></a>Önkoşullar

**.Net masaüstü geliştirme** iş yükü yüklü Visual Studio.

## <a name="install-software-on-the-computers"></a>Bilgisayarlara yazılım yüklemesi

İlk olarak, ana bilgisayarı ayarlayın ve ardından yapı bilgisayarını ayarlayın.

Visual Studio 'Yu ana bilgisayara yükleyerek, daha sonra yapı bilgisayarına kopyalayacaksınız dosya ve ayarları oluşturursunuz. Visual Studio 'Yu bir x86 veya x64 bilgisayara yükleyebilirsiniz, ancak yapı bilgisayarının mimarisinin ana bilgisayar mimarisiyle eşleşmesi gerekir.

1. Ana bilgisayarda, Visual Studio 'Yu yükler.

2. Yapı bilgisayarında, 4,5 veya sonraki bir sürümü .NET Framework. Yüklendiğini doğrulamak için, **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** kayıt defteri alt anahtarındaki **Sürüm** girişinin **4,5** veya üzeri bir değere sahip olduğundan emin olun.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Dosyaları ana bilgisayardan yapı bilgisayarına Kopyala

Bu bölüm, ana bilgisayardan yapı bilgisayarına belirli dosyaları, derleyiciler, derleme araçları, MSBuild varlıkları ve kayıt defteri ayarlarının kopyalanmasını ele alır. Bu yönergeler, Visual Studio 'Yu ana bilgisayarda varsayılan konuma yüklediğinizi varsayar; başka bir konuma yüklediyseniz, adımları uygun şekilde ayarlayın.

- X86 bilgisayarda, varsayılan konum *C:\Program Files\Microsoft Visual Studio*
- X64 bilgisayarda, varsayılan konum *C:\Program Files (x86) \Microsoft Visual Studio* ' dır

*Program dosyaları* klasörünün adının yüklü olan işletim sistemine bağlı olduğuna dikkat edin. X86 bilgisayarda, ad *program dosyalarıdır*; x64 bilgisayarda, ad *Program Files (x86)*' dır. Sistem mimarisinden bağımsız olarak, Bu izlenecek yol *% ProgramFiles%* olarak *Program Files* klasörüne başvurur.

> [!NOTE]
> Yapı bilgisayarında, tüm ilgili dosyalar aynı sürücüde olmalıdır. Ancak, bu sürücünün sürücü harfi, Visual Studio 'nun ana bilgisayarda yüklü olduğu sürücünün sürücü harfinden farklı olabilir. Herhangi bir durumda, bu belgenin ilerleyen kısımlarında açıklandığı gibi kayıt defteri girişleri oluştururken dosyaların konumunu hesaba almalısınız.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Windows SDK dosyalarını yapı bilgisayarına kopyalayın

1. Yalnızca Windows 8 için Windows SDK yüklüyse, bu klasörleri, ana bilgisayardan yapı bilgisayarına özyinelemeli olarak kopyalayın:

   - %Kits\8.0\bin\

   - %Kits\8.0\catalogs\

   - %Kits\8.0\designtime\

   - %Kits\8.0\include\

   - %Kits\8.0\lib\

   - %Kits\8.0\redist\

   - %Kits\8.0\references\

   Ayrıca, bu diğer Windows 8 setlerine sahipseniz...

   - Microsoft Windows değerlendirme ve dağıtım seti

   - Microsoft Windows Sürücü Seti

   - Microsoft Windows donanım sertifikasyon seti

   ... Bunlar, önceki adımda listelenen *%Kits\8.0* klasörlerine dosya yüklemiş olabilirler ve lisans koşulları bu dosyalar için Build-Server haklarına izin vermiyor olabilir. Dosyaların yapı bilgisayarınıza kopyalanıp kopyalanmayacağını doğrulamak için, yüklü her Windows Kit 'in lisans koşullarını denetleyin. Lisans koşulları, Build-Server haklarına izin vermedikçe, dosyaları yapı bilgisayarından kaldırın.

2. Aşağıdaki klasörleri yinelemeli olarak ana bilgisayardan yapı bilgisayarına kopyalayın:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Araçları \

    - %ProgramFiles%\Common Files\Merge modülleri \

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference, Lies\microsoft\framework \\ . Netcore\v4,\

    - %ProgramFiles%\Reference, Lies\microsoft\framework \\ . NETFramework\v4.5\

3. Bu dosyaları ana bilgisayardan yapı bilgisayarına kopyalayın:

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\vsvars32.bat

4. Aşağıdaki Visual C++ çalışma zamanı kitaplıkları yalnızca derleme bilgisayarında yapı çıktıları çalıştırırsanız gereklidir — Örneğin, otomatik testlerin bir parçası olarak. Dosyalar genellikle, sistem mimarisine bağlı olarak *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \vc\redist\x86* veya *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \vc\redist\x64* klasörü altındaki alt klasörlerde bulunur. X86 sistemlerinde, x86 ikililerini *Windows\System32* klasörüne kopyalayın. X64 sistemlerde, x86 ikililerini *Windows\syswow64* klasörüne ve x64 ikililerini *Windows\System32* klasörüne kopyalayın.

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

5. [Bir hata ayıklama yürütülebilirini çalıştırmak için bir test makinesi hazırlama](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)bölümünde açıklandığı gibi, yalnızca aşağıdaki dosyaları *Debug_NonRedist \x86* veya *Debug_NonRedist \x64* klasöründen yapı bilgisayarına kopyalayın. Başka hiçbir dosya kopyalanmayabilir.

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

1. Kayıt defteri girdileri için üst klasörü belirler. Tüm kayıt defteri girdileri aynı üst anahtar altında oluşturulur. Bir x86 bilgisayarda, üst anahtar **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft**şeklindedir. X64 bilgisayarda, üst anahtar **HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft**şeklindedir. Sistem mimarisinden bağımsız olarak, Bu izlenecek yol% RegistryRoot% olarak ana anahtara başvurur.

    > [!NOTE]
    > Ana bilgisayarınızın mimarisi yapı bilgisayarınızdan farklıysa, her bilgisayarda uygun üst anahtarı kullandığınızdan emin olun. Dışarı aktarma işlemini otomatikleştiriyorsanız bu özellikle önemlidir.
    >
    > Ayrıca, Yapı bilgisayarında, ana bilgisayarda kullandığınızdan farklı bir sürücü harfi kullanıyorsanız, kayıt defteri girdilerinin değerlerini eşleşecek şekilde değiştirdiğinizden emin olun.

2. Yapı bilgisayarında aşağıdaki kayıt defteri girdilerini oluşturun. Tüm bu girdiler dizelerdir (Type = = "REG_SZ" kayıt defterinde). Bu girişlerin değerlerini konak bilgisayardaki karşılaştırılabilir girişlerin değerleriyle aynı olarak ayarlayın.

   - **% RegistryRoot% \\ . NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild public Assemblies@ (varsayılan)**

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **% RegistryRoot% \VisualStudio\11.0@Source dizinleri**

   - <strong>% RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>% RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>% RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>% RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>% RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **% RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **% RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\yüklendi Roots@KitsRoot</strong>

   - <strong>% RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>% RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>% RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   X64 Yapı bilgisayarında Ayrıca, aşağıdaki kayıt defteri girişini oluşturun ve nasıl ayarlanacağını öğrenmek için ana bilgisayara başvurun.

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Yapı Bilgisayarınız x64 ise ve MSBuild 'in 64 bit sürümünü kullanmak istiyorsanız veya bir x64 bilgisayarda Team Foundation Server derleme hizmeti kullanıyorsanız, yerel 64 bit kayıt defterinde aşağıdaki kayıt defteri girdilerini oluşturun. Bu girişlerin nasıl ayarlanacağını öğrenmek için konak bilgisayara bakın.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Yapı bilgisayarında ortam değişkenlerini ayarlama

Yapı bilgisayarında MSBuild 'i kullanmak için, PATH ortam değişkenlerini ayarlamanız gerekir. Değişkenleri ayarlamak için *vcvarsall.bat* kullanabilir veya bunları el ile yapılandırabilirsiniz.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Ortam değişkenlerini ayarlamak için vcvarsall.bat kullanma

Yapı bilgisayarında bir **komut istemi** penceresi açın ve *% Program Files%\Microsoft Visual Studio \\ \<version> \\ \<edition>\VC\vcvarsall.bat*çalıştırın. Kullanmak istediğiniz araç takımını (x86, yerel x64 veya x64 çapraz derleyicisi) belirtmek için bir komut satırı bağımsız değişkeni kullanabilirsiniz. Bir komut satırı bağımsız değişkeni belirtmezseniz, x86 araç takımı kullanılır.

Bu tabloda *vcvarsall.bat*için desteklenen bağımsız değişkenler açıklanmaktadır:

|Vcvarsall.bat bağımsız değişkeni|Derleyici|Bilgisayar mimarisi oluşturun|Derleme çıkış mimarisi|
| - |--------------| - | - |
|x86 (varsayılan)|32-bit yerel|x86, x64|x86|
|x86_amd64|x64 çapraz|x86, x64|x64|
|amd64|x64 yerel|x64|x64|

*vcvarsall.bat* başarıyla çalışırsa — diğer bir deyişle, hata iletisi görüntülenmediğinde, sonraki adımı atlayabilir ve [MSBuild derlemelerini bu belgenin yapı bilgisayarı bölümünde genel derleme ÖNBELLEĞI 'ne (GAC) yüklemeye](#install-msbuild-to-gac) devam edebilirsiniz.

### <a name="manually-set-environment-variables"></a>Ortam değişkenlerini el ile ayarlama

1. Komut satırı ortamını el ile yapılandırmak için bu yolu PATH ortam değişkenine ekleyin:

    - % Program Files%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE

2. İsteğe bağlı olarak, çözümlerinizi oluşturmak için MSBuild 'in kullanılmasını kolaylaştırmak için yol değişkenine aşağıdaki yolları da ekleyebilirsiniz.

   Yerel 32 bit MSBuild 'i kullanmak istiyorsanız, bu yolları yol değişkenine ekleyin:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Araçları

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Yerel 64 bit MSBuild 'i kullanmak istiyorsanız, bu yolları yol değişkenine ekleyin:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" /> Yapılandırma bilgisayarında genel derleme önbelleği 'ne (GAC) MSBuild derlemeleri yükler

MSBuild, derleme bilgisayarında GAC 'ye bazı ek derlemeler yüklenmesini gerektirir.

1. Aşağıdaki derlemeleri ana bilgisayardan yapı bilgisayarına kopyalayın. Bunlar GAC 'ye yüklenebileceğinden, bunları yapı bilgisayarına nereye yerleştirdiğinizden bağımsız değildir.

    - % ProgramFiles% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Derlemeleri GAC 'ye yüklemek için derleme bilgisayarında *gacutil.exe* bulun — genellikle%ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Araçları \\ . Bu klasörü bulamazsanız, Bu izlenecek yolun [ana bilgisayar bilgisayarındaki dosyaları Kopyala](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) bölümünde bulunan adımları yineleyin.

     Yönetici haklarına sahip bir **komut istemi** penceresi açın ve her dosya için bu komutu çalıştırın:

     **Gacutil-i \<file>**

    > [!NOTE]
    > Bir derlemenin GAC 'ye tam olarak yüklenmesi için yeniden başlatma gerekebilir.

## <a name="build-projects"></a>Yapı projeleri

Azure Pipelines kullanarak Visual Studio projeleri ve çözümleri oluşturabilir veya bunları komut satırında oluşturabilirsiniz. Projeleri oluşturmak için Azure Pipelines kullandığınızda, sistem mimarisine karşılık gelen MSBuild yürütülebiliri çağırır. Komut satırında 32-bit MSBuild veya 64-bit MSBuild kullanabilirsiniz ve yol ortam değişkenini ayarlayarak ya da mimariye özgü MSBuild yürütülebilir dosyasını doğrudan çağırarak MSBuild mimarisini seçebilirsiniz.

Komut isteminde *msbuild.exe* kullanmak için aşağıdaki komutu çalıştırın, burada *çözüm. sln* , çözümünüzün adı için bir yer tutucudur.

**MSBuild** *Solution. sln*

Komut satırında MSBuild 'i kullanma hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Kaynak denetimine denetlenebilmesi için derleme ortamını oluşturun

Çeşitli bilgisayarlara dağıtılabilecek ve "GAC" dosyaları gerektirmeyen ya da kayıt defteri ayarlarını değiştiren bir yapı ortamı oluşturabilirsiniz. Aşağıdaki adımlar bunu gerçekleştirmenin yalnızca bir yoludur. Bu adımları yapı ortamınızın benzersiz özelliklerine uyarlayın.

> [!NOTE]
> *tracker.exe* , derleme sırasında bir hata oluşturmayacak şekilde artımlı derlemeyi devre dışı bırakmanız gerekir. Artımlı derlemeyi devre dışı bırakmak için, bu derleme parametresini ayarlayın:
>
> **MSBuild** *çözümü. sln* **/p: TrackFileAccess = false**

1. Ana bilgisayarda bir *deposu* dizini oluşturun.

     Bu adımlar dizine% deposu% olarak başvurur.

2. Dizinleri ve dosyaları, Bu izlenecek yolun [dosyaları ana bilgisayardan yapı bilgisayarına](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) Kopyala bölümünde açıklandığı gibi kopyalayın, ancak bunları az önce oluşturduğunuz *% deposu%* dizininin altına yapıştırın. Örneğin, *%Kits\8.0\Bin* konumundan *%Depot%\Windows Kits\8.0\Bin dizinine*kopyalayın.

3. Dosyalar *% deposu%* içine yapıştırılırken şu değişiklikleri yapın:

    - %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets \\ , \Microsoft.cppbuild.targets \\ ve \Microsoft.CppCommon.targets içindeki \\ her örneğini değiştirin

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         şöyle değiştirin:

         AssemblyFile = "$ (VCTargetsPath11) Microsoft.Build.CppTasks.Common.v110.dll".

         Eski adlandırma, GAC'ed olan derlemeye bağımlıdır.

    - % Deposu% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets içinde her örneğini değiştirin

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         şöyle değiştirin:

         AssemblyFile = "$ (VCTargetsPath11) Microsoft.Build.CppTasks.Common.v110.dll".

4. Bir *. props* dosyası oluşturun — örneğin, *partner. oto Imports. props*— ve projelerinizi içeren klasörün köküne yerleştirin. Bu dosya, çeşitli kaynakları bulmak için MSBuild tarafından kullanılan değişkenleri ayarlamak için kullanılır. Değişkenler bu dosya tarafından ayarlanmamışsa, kayıt defteri değerlerini kullanan diğer *. props* dosyaları ve *. targets* dosyaları tarafından ayarlanır. Hiçbir kayıt defteri değeri ayarlamadığımızda, bu değişkenler boş olur ve derleme başarısız olur. Bunun yerine, bunu *partner. oto Imports. props*öğesine ekleyin:

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

5. Her proje dosyasında, satırın arkasına aşağıdaki satırı ekleyin `<Project Default Targets...>` .

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - *1. adımda oluşturduğunuz deposu dizininin* deposu = location öğesini ayarlayın

    - Küme yolu =% path%; *bilgisayardaki MSBuild 'in konumu*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 15.0 \ Common7\IDE\

       Yerel 64 bit oluşturma için MSBuild 'in 64 bit sürümüne işaret edin.

::: moniker-end

::: moniker range=">=vs-2019"

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - *1. adımda oluşturduğunuz deposu dizininin* deposu = location öğesini ayarlayın

    - Küme yolu =% path%; *bilgisayardaki MSBuild 'in konumu*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 16.0 \ Common7\IDE\

       Yerel 64 bit oluşturma için MSBuild 'in 64 bit sürümüne işaret edin.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Yürütülebilir hata ayıklamayı çalıştırmak için test makinesi hazırlama](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)