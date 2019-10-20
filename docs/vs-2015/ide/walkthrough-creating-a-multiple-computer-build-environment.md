---
title: 'İzlenecek yol: birden çok bilgisayar derleme ortamı oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d0fccb5694e538cdf71844d2cc18640114ec735
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672305"
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>İzlenecek yol: Birden Çok Bilgisayarda Derleme Ortamı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kuruluşunuzda Visual Studio 'Yu bir ana bilgisayara yükleyerek ve sonra çeşitli dosya ve ayarları, yapılara katılabilecek şekilde başka bir bilgisayara kopyalayarak kuruluşunuz içinde bir yapı ortamı oluşturabilirsiniz. Visual Studio 'Yu diğer bilgisayara yüklemenize gerek yoktur.

 Bu belge, yazılımı dışarıdan yeniden dağıtmak veya üçüncü taraflara derleme ortamları sağlamak için bir haklara sahip değildir.

||
|-|
|Sorumluluk reddi<br /><br /> Bu belge "olduğu gibi" esasına göre sunulmaktadır. Özetlenen adımları test etmemiz mümkün olsa da, her yapılandırmanın tamamen test etmeme. Belgeyi, öğrendiğimiz tüm ek bilgilerle güncel tutmaya çalışacaktır. Bu belgede ifade edilen, URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bilgiler ve görünümler bildirimde bulunmaksızın değiştirilebilir. Microsoft, burada belirtilen bilgilere göre açık veya zımni hiçbir garanti vermez. Bunu kullanmanın riski size aittir.<br /><br /> Bu belge size herhangi bir Microsoft ürününde herhangi bir fikri mülkiyet hakkı sağlamaz. Bu belgeyi kendi dahili, başvuru amaçlarınız için kopyalayabilir ve kullanabilirsiniz.<br /><br /> Bu belgeyle ilgili olarak Microsoft 'a herhangi bir öneri, yorum veya geri bildirim ("geri bildirim") verme yükümlülüğü yoktur. Ancak, gönüllü olarak sağladığınız tüm geri bildirimler, Microsoft ürünlerinde ve ilgili belirtimlerde ya da başka belgelerde (topluca, "Microsoft teklifleri") kullanılabilir Buna uygun olarak, bu belgenin herhangi bir sürümünde veya uygulandıkları Microsoft tekliflerinden Microsoft 'a geri bildirimde bulunmayı kabul etmiş olursunuz: (a) Microsoft, görüşlerinizi herhangi bir Microsoft ile ücretsiz olarak kullanabilir, yeniden üretebilir, lisanslayın, dağıtabilir ve başka bir şekilde kullanabilir. Teklifi (b) Ayrıca üçüncü taraflara ücretsiz olarak, diğer ürünlerin yalnızca geri bildiriminizi içeren bir Microsoft ürününün belirli bölümleriyle kullanmasını veya arabirimini kullanmasını sağlamak için gerekli olan patent haklarını de vermiş olursunuz; ve (c) Microsoft 'a geri bildirim (i), herhangi bir patent, telif hakkı veya diğer fikri mülkiyet talebine ya da herhangi bir üçüncü tarafın olduğuna inanmanızın bir sebebini sunmayacak; ya da (ii) bu geri bildirimde bulunan veya ondan türetilmiş herhangi bir Microsoft teklifini ya da başka bir Microsoft fikri mülkiyet ya da herhangi bir üçüncü tarafla lisanslanmasını gerektiren lisans koşullarına tabidir.|

 Bu izlenecek yol, komut satırında ve Team Foundation Build kullanılarak MSBuild yürütülerek aşağıdaki işletim sistemlerine karşı onaylanır.

- Windows 8 (x86 ve x64)

- Windows 7 Ultimate

- Windows Server 2008 R2 Standard

  Bu izlenecek adımları tamamladıktan sonra, bu tür uygulamaları oluşturmak için birden çok bilgisayar ortamı kullanabilirsiniz:

- C++Windows 8 SDK kullanan masaüstü uygulamaları

- .NET Framework 4,5 C# 'yi hedefleyen Visual Basic veya masaüstü uygulamaları

  Birden çok bilgisayar ortamı, bu tür uygulamaları oluşturmak için kullanılamaz:

- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar. @No__t_0 uygulamalar oluşturmak için, Visual Studio 'Yu yapı bilgisayarına yüklemelisiniz.

- .NET Framework 4 veya önceki sürümleri hedefleyen masaüstü uygulamaları. Bu tür uygulamaları oluşturmak için, Yapı bilgisayarında Visual Studio 'Yu veya .NET başvuru derlemelerini ve araçlarını (Windows 7,1 SDK 'dan) yüklemelisiniz.

  Bu izlenecek yol aşağıdaki bölümlere ayrılmıştır:

- [Bilgisayarlara yazılım yükleme](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)

- [Dosyalar ana bilgisayardan yapı bilgisayarına kopyalanıyor](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)

- [Kayıt defteri ayarları oluşturma](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)

- [Yapı bilgisayarında ortam değişkenlerini ayarlama](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)

- [Yapı bilgisayarında genel derleme önbelleği 'ne (GAC) MSBuild derlemeleri yükleme](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)

- [Projeleri derleme](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)

- [Kaynak denetimine denetlenebilmesi için yapı ortamı oluşturuluyor](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)

## <a name="prerequisites"></a>Prerequisites

- Visual Studio Ultimate, Visual Studio Premium veya Visual Studio Professional lisanslı bir kopyası

- [Microsoft](https://www.microsoft.com/download/details.aspx?id=40779) Web sitesinden indirebileceğiniz .NET Framework 4.5.1 bir kopyası.

## <a name="InstallingSoftware"></a>Bilgisayarlara yazılım yükleme
 İlk olarak, ana bilgisayarı ayarlayın ve ardından yapı bilgisayarını ayarlayın.

 Visual Studio 'Yu ana bilgisayara yükleyerek, daha sonra yapı bilgisayarına kopyalayacaksınız dosya ve ayarları oluşturursunuz. Visual Studio 'Yu bir x86 veya x64 bilgisayara yükleyebilirsiniz, ancak yapı bilgisayarının mimarisinin ana bilgisayar mimarisiyle eşleşmesi gerekir.

#### <a name="to-install-software-on-the-computers"></a>Bilgisayarlara yazılım yüklemek için

1. Ana bilgisayarda, Visual Studio 'Yu yükler.

2. Yapı bilgisayarında .NET Framework 4,5 ' u yüklemelisiniz. Yüklendiğini doğrulamak için, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full@Version kayıt defteri anahtarı değerinin "4,5" ile başladığı emin olun.

## <a name="CopyingFiles"></a>Dosyalar ana bilgisayardan yapı bilgisayarına kopyalanıyor
 Bu bölüm, ana bilgisayardan yapı bilgisayarına belirli dosyaları, derleyiciler, derleme araçları, MSBuild varlıkları ve kayıt defteri ayarlarının kopyalanmasını ele alır. Bu yönergeler, Visual Studio 'Yu ana bilgisayarda varsayılan konuma yüklediğinizi varsayar; başka bir konuma yüklediyseniz, adımları uygun şekilde ayarlayın.

- X86 bilgisayarda, varsayılan konum C:\Program Files\Microsoft Visual Studio 11,0 \ ' dir

- X64 bilgisayarda, varsayılan konum C:\Program Files (x86) \Microsoft Visual Studio 11,0 \ ' dir

  Program dosyaları klasörünün adının yüklü olan işletim sistemine bağlı olduğuna dikkat edin. X86 bilgisayarda, ad \Program Files \\; x64 bilgisayarda, ad \Program Files (x86) \\. Sistem mimarisinden bağımsız olarak, Bu izlenecek yol% ProgramFiles% olarak Program Files klasörüne başvurur.

> [!NOTE]
> Yapı bilgisayarında, tüm ilgili dosyalar aynı sürücüde olmalıdır; Ancak, bu sürücünün sürücü harfi, Visual Studio 'nun ana bilgisayarda yüklü olduğu sürücünün sürücü harfinden farklı olabilir. Herhangi bir durumda, bu belgenin ilerleyen kısımlarında açıklandığı gibi kayıt defteri girişleri oluştururken dosyaların konumunu hesaba almalısınız.

#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>Windows SDK dosyalarını yapı bilgisayarına kopyalamak için

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

     ... Bunlar, önceki adımda listelenen%Kits\8.0\ klasörlerine dosya yüklemiş olabilirler ve lisans koşulları bu dosyalar için yapı-sunucu haklarına izin vermiyor olabilir. Dosyaların yapı bilgisayarınıza kopyalanıp kopyalanmayacağını doğrulamak için, yüklü her Windows Kit 'in lisans koşullarını denetleyin. Lisans koşulları, Build-Server haklarına izin vermedikçe, dosyaları yapı bilgisayarından kaldırın.

2. Aşağıdaki klasörleri yinelemeli olarak ana bilgisayardan yapı bilgisayarına kopyalayın:

   - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Araçları \

   - %ProgramFiles%\Common Files\Merge modülleri \

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ VC \

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\ProjectComponents\

   - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\

   - %ProgramFiles%\Reference Birleştirices\microsoft\framework \\. NETCore\v4.5\

   - %ProgramFiles%\Reference Birleştirices\microsoft\framework \\. NETFramework\v4.5\

3. Bu dosyaları ana bilgisayardan yapı bilgisayarına kopyalayın:

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\msobj110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\mspdb110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\mspdbcore.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\mspdbsrv.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\msvcdis110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\makehm.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\VCVarsQueryRegistry.bat

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\vsvars32.bat

4. Aşağıdaki görsel C++ çalışma zamanı kitaplıkları yalnızca derleme bilgisayarında yapı çıktıları çalıştırırsanız gereklidir — Örneğin, otomatik testlerin bir parçası olarak. Dosyalar genellikle, sistem mimarisine bağlı olarak%ProgramFiles%\Microsoft Visual Studio 11.0 \ VC\redist\x86\ veya%ProgramFiles%\Microsoft Visual Studio 11.0 \ VC\redist\x64\ klasörü altındaki alt klasörlerde bulunur. X86 sistemlerinde, x86 ikililerini \Windows\System32\ klasörüne kopyalayın. X64 sistemlerde, x86 ikililerini Windows\SysWOW64\ klasörüne ve x64 ikili dosyalarını Windows\System32\ klasörüne kopyalayın.

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

5. [Bir hata ayıklama yürütülebilirini çalıştırmak için bir test makinesi hazırlama](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)bölümünde açıklandığı gibi, \Debug_NonRedist\x86\ veya \Debug_NonRedist\x64\ klasöründen derleme bilgisayarına yalnızca aşağıdaki dosyaları kopyalayın. Başka hiçbir dosya kopyalanmayabilir.

   - \Microsoft.VC110.DebugCRT\msvcp110d.dll

   - \Microsoft.VC110.DebugCRT\msvcr110d.dll

   - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110ud.dll

   - \Microsoft.VC110.DebugMFC\mfcm110d.dll

   - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

   - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="CreatingRegistry"></a>Kayıt defteri ayarları oluşturma
 MSBuild ayarlarını yapılandırmak için kayıt defteri girişleri oluşturmanız gerekir.

#### <a name="to-create-registry-settings"></a>Kayıt defteri ayarları oluşturmak için

1. Kayıt defteri girdileri için üst klasörü belirler. Tüm kayıt defteri girdileri aynı üst anahtar altında oluşturulur. X86 bilgisayarda, üst anahtar HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft \\. X64 bilgisayarda, üst anahtar HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft \\. Sistem mimarisinden bağımsız olarak, Bu izlenecek yol% RegistryRoot% olarak ana anahtara başvurur.

   > [!NOTE]
   > Ana bilgisayarınızın mimarisi yapı bilgisayarınızdan farklıysa, her bilgisayarda uygun üst anahtarı kullandığınızdan emin olun. Dışarı aktarma işlemini otomatikleştiriyorsanız bu özellikle önemlidir.
   >
   >  Ayrıca, Yapı bilgisayarında, ana bilgisayarda kullandığınızdan farklı bir sürücü harfi kullanıyorsanız, kayıt defteri girdilerinin değerlerini eşleşecek şekilde değiştirdiğinizden emin olun.

2. Yapı bilgisayarında aşağıdaki kayıt defteri girdilerini oluşturun. Bu girdilerin hepsi dizelerdir (Type = = "REG_SZ" kayıt defterinde). Bu girişlerin değerlerini konak bilgisayardaki karşılaştırılabilir girişlerin değerleriyle aynı olarak ayarlayın.

   - % RegistryRoot% \\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild genel derlemeler @ (varsayılan)

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder

   - % RegistryRoot% \VisualStudio\11.0@Source dizinleri

   - % RegistryRoot% \VisualStudio\11.0\Setup\VC@ProductDir

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkDir32

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkDir64

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkVer32

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkVer64

   - % RegistryRoot% \VisualStudio\SxS\VC7@11.0

   - % RegistryRoot% \VisualStudio\SxS\VS7@11.0

   - %RegistryRoot%\Windows Kits\yüklü Roots@KitsRoot

   - % RegistryRoot% \MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - % RegistryRoot% \MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - % RegistryRoot% \MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

     X64 Yapı bilgisayarında Ayrıca, aşağıdaki kayıt defteri girişini oluşturun ve nasıl ayarlanacağını öğrenmek için ana bilgisayara başvurun.

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder

     Yapı Bilgisayarınız x64 ise ve MSBuild 'in 64 bit sürümünü kullanmak istiyorsanız veya bir x64 bilgisayarda Team Foundation Server derleme hizmeti kullanıyorsanız, yerel 64 bit kayıt defterinde aşağıdaki kayıt defteri girdilerini oluşturmanız gerekir. Bu girişlerin nasıl ayarlanacağını öğrenmek için konak bilgisayara bakın.

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

## <a name="SettingEnvVariables"></a>Yapı bilgisayarında ortam değişkenlerini ayarlama
 Yapı bilgisayarında MSBuild 'i kullanmak için, PATH ortam değişkenlerini ayarlamanız gerekir. Değişkenleri ayarlamak için vcvarsall. bat kullanabilirsiniz veya bunları el ile yapılandırabilirsiniz.

#### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>Ortam değişkenlerini ayarlamak için vcvarsall. bat dosyasını kullanma

- Yapı bilgisayarında bir komut Istemi penceresi açın ve% Program Files%\Microsoft Visual Studio 11.0 \ Vc\vcvarsall.exe komutunu çalıştırın. Kullanmak istediğiniz araç takımını (x86, yerel x64 veya x64 çapraz derleyicisi) belirtmek için bir komut satırı bağımsız değişkeni kullanabilirsiniz. Bir komut satırı bağımsız değişkeni belirtmezseniz, x86 araç takımı kullanılır.

     Bu tabloda, vcvarsall. bat için desteklenen bağımsız değişkenler açıklanmaktadır:

    |Vcvarsall. bat bağımsız değişkeni|Derleyici|Bilgisayar mimarisi oluşturun|Derleme çıkış mimarisi|
    |----------------------------|--------------|---------------------------------|-------------------------------|
    |x86 (varsayılan)|32-bit yerel|x86, x64|x86|
    |x86_amd64|x64 çapraz|x86, x64|X64|
    |amd64|x64 yerel|X64|X64|

     Vcvarsall. bat başarıyla çalışırsa — diğer bir deyişle, hata iletisi görüntülenmediğinde, bir sonraki adımı atlayabilir ve [MSBuild derlemelerini bu belgenin yapı bilgisayarı bölümünde genel derleme önbelleği 'ne (GAC) yüklemeye](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) devam edebilirsiniz.

#### <a name="to-manually-set-environment-variables"></a>Ortam değişkenlerini el ile ayarlamak için

1. Komut satırı ortamını el ile yapılandırmak için bu yolu PATH ortam değişkenine ekleyin:

   - % Program Files%\Microsoft Visual Studio 11.0 \ Common7\ıde

2. İsteğe bağlı olarak, çözümlerinizi oluşturmak için MSBuild 'in kullanılmasını kolaylaştırmak için yol değişkenine aşağıdaki yolları da ekleyebilirsiniz.

    Yerel 32 bit MSBuild 'i kullanmak istiyorsanız, bu yolları yol değişkenine ekleyin:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Araçları

   - %windir%\Microsoft.NET\Framework\v4.0.30319

     Yerel 64 bit MSBuild 'i kullanmak istiyorsanız, bu yolları yol değişkenine ekleyin:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="InstallingMSBuildToGAC"></a>Yapı bilgisayarında genel derleme önbelleği 'ne (GAC) MSBuild derlemeleri yükleme
 MSBuild, derleme bilgisayarında GAC 'ye bazı ek derlemeler yüklenmesini gerektirir.

#### <a name="to-copy-assemblies-from-the-host-computer-and-install-them-on-the-build-computer"></a>Ana bilgisayardan derlemeleri kopyalamak ve yapı bilgisayarına yüklemek için

1. Aşağıdaki derlemeleri ana bilgisayardan yapı bilgisayarına kopyalayın. Bunlar GAC 'ye yüklenebileceğinden, bunları yapı bilgisayarına nereye yerleştirdiğinizden bağımsız değildir.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Derlemeleri GAC 'ye yüklemek için, Yapı bilgisayarında Gacutil. exe ' yi bulun — genellikle%ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Araçlar \\. Bu klasörü bulamazsanız, Bu izlenecek yolun [ana bilgisayardaki dosyaları derleme bilgisayarına kopyalama](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) bölümündeki adımları yineleyin.

     Yönetici haklarına sahip bir komut Istemi penceresi açın ve her dosya için bu komutu çalıştırın:

     **Gacutil-i \<file >**

    > [!NOTE]
    > Bir derlemenin GAC 'ye tam olarak yüklenmesi için yeniden başlatma gerekebilir.

## <a name="BuildingProjects"></a>Projeleri derleme
 @No__t_0 projeleri ve çözümleri oluşturmak için Team Foundation Build ' i kullanabilir veya bunları komut satırında oluşturabilirsiniz. Projeleri oluşturmak için Team Foundation Build kullandığınızda, sistem mimarisine karşılık gelen MSBuild yürütülebiliri çağırır.  Komut satırında 32-bit MSBuild veya 64-bit MSBuild kullanabilirsiniz ve yol ortam değişkenini ayarlayarak ya da mimariye özgü MSBuild yürütülebilir dosyasını doğrudan çağırarak MSBuild mimarisini seçebilirsiniz.

 Komut isteminde MSBuild. exe ' yi kullanmak için aşağıdaki komutu çalıştırın *. burada çözüm* , çözümünüzün adı için bir yer tutucudur.

 **MSBuild** *Solution. sln*

 Komut satırında MSBuild 'i kullanma hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> @No__t_0 projeler oluşturmak için "v110" platform araç takımını kullanmanız gerekir. @No__t_0 proje dosyalarını düzenlemek istemiyorsanız, bu komut satırı bağımsız değişkenini kullanarak platform araç takımını ayarlayabilirsiniz:
>
> **MSBuild** *çözümü. sln* **/p: platformaraç takımı = v110**

## <a name="CreatingForSourceControl"></a>Kaynak denetimine denetlenebilmesi için yapı ortamı oluşturuluyor
 Çeşitli bilgisayarlara dağıtılabilecek ve GAC'ing dosyaları gerektirmeyen ya da kayıt defteri ayarlarını değiştirmekte olmayan bir yapı ortamı oluşturabilirsiniz. Aşağıdaki adımlar bunu gerçekleştirmenin yalnızca bir yoludur. Bu adımları yapı ortamınızın benzersiz özelliklerine uyarlayın.

> [!NOTE]
> İzleyici. exe ' nin bir derleme sırasında hata oluşturması için artımlı derlemeyi devre dışı bırakmanız gerekir. Artımlı derlemeyi devre dışı bırakmak için, bu derleme parametresini ayarlayın:
>
> **MSBuild** *çözümü. sln* **/p: TrackFileAccess = false**

#### <a name="to-create-a-build-environment-that-can-be-checked-into-source-control"></a>Kaynak denetimine iade edilebilir bir yapı ortamı oluşturmak için

1. Ana bilgisayarda bir "deposu" dizini oluşturun.

     Bu adımlar dizine% deposu% olarak başvurur.

2. Dizinleri ve dosyaları, Bu izlenecek yolda bulunan [dosyaları ana bilgisayardan yapı bilgisayarına](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) Kopyala bölümünde açıklandığı gibi kopyalayın, ancak bunları az önce oluşturduğunuz% deposu% dizininin altına yapıştırın. Örneğin,%Kits\8.0\bin\ ' den%Depot%\Windows Kits\8.0\Bin ' e kopyalayın \\.

3. Dosyalar% deposu% içine yapıştırılırken şu değişiklikleri yapın:

    - %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets \\, \Microsoft.cppbuild.targets \\ ve \Microsoft.CppCommon.targets \\ her örneğini değiştirin

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         to

         AssemblyFile = "$ (VCTargetsPath11) Microsoft. Build. CppTasks. Common. v110. dll".

         Eski adlandırma, GAC'ed olan derlemeye bağımlıdır.

    - % Deposu% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets içinde her örneğini değiştirin

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         to

         AssemblyFile = "$ (VCTargetsPath11) Microsoft. Build. CppTasks. Common. v110. dll".

4. Bir. props dosyası oluşturun — örneğin, partner. oto Imports. props — ve projelerinizi içeren klasörün köküne yerleştirin. Bu dosya, çeşitli kaynakları bulmak için MSBuild tarafından kullanılan değişkenleri ayarlamak için kullanılır. Değişkenler bu dosya tarafından ayarlanmamışsa, kayıt defteri değerlerini kullanan diğer. props dosyaları ve. targets dosyaları tarafından ayarlanır. Hiçbir kayıt defteri değeri ayarlamadığımızda, bu değişkenler boş olur ve derleme başarısız olur. Bunun yerine, bunu partner. oto Imports. props öğesine ekleyin:

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. Proje dosyalarınızın her birinde, `<Project Default Targets…>` satırdan sonra üst kısımdaki aşağıdaki satırı ekleyin.

    ```
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - *1. adımda oluşturduğunuz deposu dizininin* deposu = location öğesini ayarlayın

    - Küme yolu =% path%; *bilgisayardaki MSBuild 'in konumu*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 11.0 \ Common7\IDE\

         Yerel 64 bit oluşturma için 64 bit MSBuild üzerine gelin.

## <a name="see-also"></a>Ayrıca Bkz.
 Hata ayıklama yürütülebilir [komut satırı başvurusunu](../msbuild/msbuild-command-line-reference.md) [çalıştırmak Için test makinesi hazırlama](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
