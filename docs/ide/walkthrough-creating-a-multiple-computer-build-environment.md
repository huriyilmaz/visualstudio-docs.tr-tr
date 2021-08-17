---
title: Birden çok bilgisayarda derleme ortamı oluşturma
description: bir konak bilgisayara Visual Studio yükleyerek ve sonra çeşitli dosya ve ayarları başka bir bilgisayara kopyalayarak kuruluşunuzda bir yapı ortamı oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6dcdf6b1b916a5f5f38137967d3d2a33072bca8f72d3ceb42b0b2ca27f7d6fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386543"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>İzlenecek yol: Birden çok bilgisayarda derleme ortamı oluşturma

kuruluşunuzda bir konak bilgisayara Visual Studio yükleyerek ve sonra çeşitli dosya ve ayarları, yapılara katılabilecek şekilde başka bir bilgisayara kopyalayarak kuruluşunuz içinde bir yapı ortamı oluşturabilirsiniz. diğer bilgisayara Visual Studio yüklemenize gerek yoktur.

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

- UWP uygulamaları. UWP uygulamaları oluşturmak için, yapı bilgisayarına Visual Studio yüklemelisiniz.
- .NET Framework 4 veya önceki sürümleri hedefleyen masaüstü uygulamaları. bu tür uygulamaları oluşturmak için, yapı bilgisayarında Visual Studio veya .net başvuru derlemelerini ve araçlarını (Windows 7,1 SDK 'sinden) yüklemelisiniz.

## <a name="prerequisites"></a>Önkoşullar

**.net masaüstü geliştirme** iş yükü yüklü Visual Studio.

## <a name="install-software-on-the-computers"></a>Bilgisayarlara yazılım yüklemesi

İlk olarak, ana bilgisayarı ayarlayın ve ardından yapı bilgisayarını ayarlayın.

ana bilgisayara Visual Studio yükleyerek, daha sonra yapı bilgisayarına kopyalayacaksınız dosya ve ayarları oluşturursunuz. Visual Studio bir x86 veya x64 bilgisayara yükleyebilirsiniz, ancak yapı bilgisayarının mimarisinin ana bilgisayar mimarisiyle eşleşmesi gerekir.

1. Ana bilgisayarda Visual Studio ' yi yükleyip.

2. yapı bilgisayarında, 4,5 veya sonraki bir sürümü .NET Framework. Yüklendiğini doğrulamak için, kayıt defteri alt **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** anahtarındaki **Sürüm** girişinin **4,5** veya daha yüksek bir değere sahip olduğundan emin olun.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Dosyaları ana bilgisayardan yapı bilgisayarına Kopyala

bu bölüm, ana bilgisayardan yapı bilgisayarına belirli dosyaların, derleyicilerin, derleme araçlarının, MSBuild varlıkların ve kayıt defteri ayarlarının kopyalanmasını ele alır. bu yönergelerde, ana bilgisayardaki varsayılan konuma Visual Studio yüklediğinizi varsayılmaktadır; başka bir konuma yüklediyseniz, adımları uygun şekilde ayarlayın.

- X86 bilgisayarda, varsayılan konum *C:\Program Files \ Microsoft Visual Studio*
- X64 bilgisayarda, varsayılan konum *C:\Program Files (x86) \ Microsoft Visual Studio*

*Program dosyaları* klasörünün adının yüklü olan işletim sistemine bağlı olduğuna dikkat edin. X86 bilgisayarda, ad *program dosyalarıdır*; x64 bilgisayarda, ad *Program Files (x86)*' dır. Sistem mimarisinden bağımsız olarak, Bu izlenecek yol *% ProgramFiles%* olarak *Program Files* klasörüne başvurur.

> [!NOTE]
> Yapı bilgisayarında, tüm ilgili dosyalar aynı sürücüde olmalıdır. ancak, bu sürücünün sürücü harfi, ana bilgisayara Visual Studio yüklendiği sürücü için sürücü harfinden farklı olabilir. Herhangi bir durumda, bu belgenin ilerleyen kısımlarında açıklandığı gibi kayıt defteri girişleri oluştururken dosyaların konumunu hesaba almalısınız.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Windows SDK dosyalarını yapı bilgisayarına kopyalayın

1. yalnızca Windows 8 Windows SDK yüklüyse, bu klasörleri konak bilgisayardan yapı bilgisayarına yinelemeli olarak kopyalayın:

   - % ProgramFiles% \ Windows Kits\8.0\bin\

   - % ProgramFiles% \ Windows kits\8.0\catalogs\

   - % ProgramFiles% \ Windows kits\8.0\designtime\

   - % ProgramFiles% \ Windows kits\8.0\include\

   - % ProgramFiles% \ Windows kits\8.0\lib\

   - % ProgramFiles% \ Windows kits\8.0\redist\

   - % ProgramFiles% \ Windows kits\8.0\references\

   ayrıca, bu diğer Windows 8 takımları da varsa...

   - Microsoft Windows değerlendirmesi ve dağıtım seti

   - Microsoft Windows sürücü seti

   - Microsoft Windows donanım sertifikasyon seti

   ... önceki adımda listelenen *% ProgramFiles% \ Windows kits\8.0* klasörlerine dosya yüklemiş olabilirler ve lisans koşulları bu dosyalar için yapı-sunucu haklarına izin vermiyor olabilir. dosyaların yapı bilgisayarınıza kopyalanıp kopyalanmayacağını doğrulamak için, yüklü her Windows kit 'in lisans koşullarını denetleyin. Lisans koşulları, Build-Server haklarına izin vermedikçe, dosyaları yapı bilgisayarından kaldırın.

2. Aşağıdaki klasörleri yinelemeli olarak ana bilgisayardan yapı bilgisayarına kopyalayın:

    - %programfiles%\microsoft sdk 'lar \ Windows \v8.0a\bin\netfx 4,0 Tools \

    - %ProgramFiles%\Common Files\Merge modülleri \

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition> \vc\

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\Tools\ProjectComponents\

    - % ProgramFiles% \ MSBuild \Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference, Lies\microsoft\framework \\ . Netcore\v4,\

    - %ProgramFiles%\Reference, Lies\microsoft\framework \\ . NETFramework\v4.5\

3. Bu dosyaları ana bilgisayardan yapı bilgisayarına kopyalayın:

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msobj110.dll

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdb110.dll

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbcore.dll

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbsrv.exe

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msvcdis110.dll

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\makehm.exe

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\VCVarsQueryRegistry.bat

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\vsvars32.bat

4. Aşağıdaki Visual C++ çalışma zamanı kitaplıkları yalnızca derleme bilgisayarında yapı çıktıları çalıştırırsanız gereklidir — Örneğin, otomatik testlerin bir parçası olarak. dosyalar genellikle sistem mimarisine bağlı olarak *% programfiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition> \vc\redist\x86* veya *% programfiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition> \vc\redist\x64* klasörü altındaki alt klasörlerde bulunur. x86 sistemlerinde, x86 ikililerini *Windows \system32* klasörüne kopyalayın. x64 sistemlerde, x86 ikililerini *Windows \SysWOW64* klasörüne ve x64 ikililerini *Windows \system32* klasörüne kopyalayın.

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

1. Kayıt defteri girdileri için üst klasörü belirler. Tüm kayıt defteri girdileri aynı üst anahtar altında oluşturulur. Bir x86 bilgisayarda, üst anahtar **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. X64 bilgisayarda, üst anahtar **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Sistem mimarisinden bağımsız olarak, Bu izlenecek yol% RegistryRoot% olarak ana anahtara başvurur.

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

   - <strong>% registryroot% \ Windows kits\yüklendiRoots@KitsRoot</strong>

   - <strong>% RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>% RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>% RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   X64 Yapı bilgisayarında Ayrıca, aşağıdaki kayıt defteri girişini oluşturun ve nasıl ayarlanacağını öğrenmek için ana bilgisayara başvurun.

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   yapı bilgisayarınız x64 ise ve MSBuild 64 bit sürümünü kullanmak istiyorsanız veya bir x64 bilgisayarda Team Foundation Server derleme hizmeti kullanıyorsanız, yerel 64 bit kayıt defterinde aşağıdaki kayıt defteri girdilerini oluşturun. Bu girişlerin nasıl ayarlanacağını öğrenmek için konak bilgisayara bakın.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Yapı bilgisayarında ortam değişkenlerini ayarlama

yapı bilgisayarında MSBuild kullanmak için, PATH ortam değişkenlerini ayarlamanız gerekir. Değişkenleri ayarlamak için *vcvarsall.bat* kullanabilir veya bunları el ile yapılandırabilirsiniz.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Ortam değişkenlerini ayarlamak için vcvarsall.bat kullanma

derleme bilgisayarında bir **komut istemi** penceresi açın ve *% Program Files% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\VC\vcvarsall.bat* çalıştırın. Kullanmak istediğiniz araç takımını (x86, yerel x64 veya x64 çapraz derleyicisi) belirtmek için bir komut satırı bağımsız değişkeni kullanabilirsiniz. Bir komut satırı bağımsız değişkeni belirtmezseniz, x86 araç takımı kullanılır.

Bu tabloda *vcvarsall.bat* için desteklenen bağımsız değişkenler açıklanmaktadır:

|Vcvarsall.bat bağımsız değişkeni|Derleyici|Bilgisayar mimarisi oluşturun|Derleme çıkış mimarisi|
| - |--------------| - | - |
|x86 (varsayılan)|32-bit yerel|x86, x64|x86|
|x86_amd64|x64 çapraz|x86, x64|x64|
|amd64|x64 yerel|x64|x64|

*vcvarsall.bat* başarıyla çalışırsa — diğer bir deyişle, bir hata iletisi görüntülenmediğinde, bir sonraki adımı atlayabilir ve bu belgenin [yapı bilgisayarı bölümünde genel derleme önbelleği 'ne (GAC)](#install-msbuild-to-gac) bu bir sonraki adımı atlayıp MSBuild devam edebilirsiniz.

### <a name="manually-set-environment-variables"></a>Ortam değişkenlerini el ile ayarlama

1. Komut satırı ortamını el ile yapılandırmak için bu yolu PATH ortam değişkenine ekleyin:

    - % Program dosyaları% \ Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE

2. isteğe bağlı olarak, çözümlerinizi oluşturmak için MSBuild kullanmayı kolaylaştırmak için yol değişkenine aşağıdaki yolları da ekleyebilirsiniz.

   yerel 32-bit MSBuild kullanmak istiyorsanız, bu yolları yol değişkenine ekleyin:

   - % Program files%\microsoft sdk \ Windows \v8.0a\bin\netfx 4,0 araçları

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   yerel 64-bit MSBuild kullanmak istiyorsanız, bu yolları yol değişkenine ekleyin:

   - % Program files%\microsoft sdk \ Windows \v8.0a\bin\netfx 4,0 tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" />derleme bilgisayarında genel derleme önbelleği 'ne (GAC) MSBuild derlemeleri yükler

MSBuild, derleme bilgisayarında GAC 'ye bazı ek derlemelerin yüklenmesini gerektirir.

1. Aşağıdaki derlemeleri ana bilgisayardan yapı bilgisayarına kopyalayın. Bunlar GAC 'ye yüklenebileceğinden, bunları yapı bilgisayarına nereye yerleştirdiğinizden bağımsız değildir.

    - % ProgramFiles% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - % ProgramFiles% \ Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. derlemeleri GAC 'ye yüklemek için derleme bilgisayarında *gacutil.exe* bulun — genellikle%programfiles%\microsoft sdk 'lar \ Windows \v8.0a\bin\netfx 4,0 araçları \\ . Bu klasörü bulamazsanız, Bu izlenecek yolun [ana bilgisayar bilgisayarındaki dosyaları Kopyala](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) bölümünde bulunan adımları yineleyin.

     Yönetici haklarına sahip bir **komut istemi** penceresi açın ve her dosya için bu komutu çalıştırın:

     **Gacutil-i \<file>**

    > [!NOTE]
    > Bir derlemenin GAC 'ye tam olarak yüklenmesi için yeniden başlatma gerekebilir.

## <a name="build-projects"></a>Yapı projeleri

Visual Studio projeleri ve çözümleri oluşturmak için Azure Pipelines kullanabilir veya bunları komut satırında oluşturabilirsiniz. projeleri oluşturmak için Azure Pipelines kullandığınızda, sistem mimarisine karşılık gelen MSBuild yürütülebiliri çağırır. Komut satırı üzerinde, 32 bit MSBuild veya 64 bit MSBuild kullanabilirsiniz ve PATH ortam değişkenlerini ayarerek veya mimariye özgü MSBuild yürütülebilir dosyasını doğrudan kullanarak MSBuild mimarisini seçebilirsiniz.

Komut *msbuild.exe* komutunu kullanmak için, *solution.sln'nin* çözüm adının yer tutucusu olduğu aşağıdaki komutu çalıştırın.

**msbuild** *solution.sln*

Komut satırı üzerinde komut satırı MSBuild hakkında daha fazla bilgi için [bkz. Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Kaynak denetimine iade etmek için derleme ortamı oluşturma

Çeşitli bilgisayarlara dağıtılabilir ve "GAC"-ing dosyaları gerektirmeyen veya kayıt defteri ayarlarını değiştirmeyen bir derleme ortamı oluşturabilirsiniz. Aşağıdaki adımlar bunu başarma yollarından yalnızca biridir. Bu adımları derleme ortamının benzersiz özelliklerine uyarlar.

> [!NOTE]
> Artımlı derlemeyi devre dışı bırakarak *tracker.exe* sırasında hata oluşturmasını geri alasınız. Artımlı derlemeyi devre dışı bırakmak için şu derleme parametresini ayarlayın:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Konak *bilgisayarda bir Depot* dizini oluşturun.

     Bu adımlar dizini %Depot% olarak ifade etmek için kullanılır.

2. Dizinleri ve dosyaları konak bilgisayardan [](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) derleme bilgisayarına kopyalama bölümünde açıklandığı gibi kopyalayın, ancak bunları yeni oluşturduğunuz *%Depot%* dizininin altına yapıştırın. Örneğin, *%ProgramFiles%\Windows Kits\8.0\bin* konumundan *%Depot%\Windows Kits\8.0\bin* dizinine kopyalayın.

3. Dosyalar *%Depot% içinde yapıştırıldıklarında* şu değişiklikleri yapın:

    - %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets , \\ \Microsoft.cppbuild.targets \\ ve \Microsoft.CppCommon.targets içinde, her örneğini \\ değiştirir

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         kullanıcısı

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         Önceki adlandırma, derlemenin GAC'ed olmasıyla ilgilidir.

    - %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets dizininde,

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         kullanıcısı

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. *Partner.AutoImports.props* gibi bir *.props* dosyası oluşturun ve projelerinizi içeren klasörün köküne yazın. Bu dosya, çeşitli kaynakları bulmak için MSBuild değişkenler ayarlamak için kullanılır. Değişkenler bu dosya tarafından ayarlanmazsa, kayıt defteri değerlerine güvenen diğer *.props* dosyaları ve *.targets* dosyaları tarafından ayarlanır. Hiçbir kayıt defteri değeri ayarlamaysak bu değişkenler boş olur ve derleme başarısız olur. Bunun yerine, bunu *Partner.AutoImports.props'a ekleyin:*

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

5. Proje dosyalarınızın her biri, en üstüne, satırın sonraya aşağıdaki satırı `<Project Default Targets...>` ekleyin.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - *1. adımda oluşturduğunuz Depot dizininin Depot= konumunu ayarlama*

    - path=%path%; *bilgisayarda MSBuild* konumu ;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 15.0\Common7\IDE\

       Yerel 64 bit bina için, 64 bit sürümüne işaret MSBuild.

::: moniker-end

::: moniker range=">=vs-2019"

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - *1. adımda oluşturduğunuz Depot dizininin Depot= konumunu ayarlama*

    - path=%path%; *bilgisayarda MSBuild* konumu ;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 16.0\Common7\IDE\

       Yerel 64 bit bina için, 64 bit sürümüne işaret MSBuild.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Yürütülebilir hata ayıklamayı çalıştırmak için test makinesi hazırlama](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)