---
title: Yalıtılmış kabuk uygulaması yükleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0adc81cfe9ea4462940c31a02c6429be89709565
ms.sourcegitcommit: 9a66f1c31cc9eba0b5231af72da1d18761a9c56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75944258"
---
# <a name="installing-an-isolated-shell-application"></a>Yalıtılmış Kabuk Uygulaması Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kabuk uygulamasını yüklemek için aşağıdaki adımları gerçekleştirmeniz gerekir.  
  
- Çözümünüzü hazırlayın.  
  
- Uygulamanız için bir Windows Installer (MSI) paketi oluşturun.  
  
- Bir kurulum Önyükleyicisi oluşturun.  
  
  Bu belgedeki örnek kodun tamamı, MSDN Web sitesindeki kod galerisinden indirebileceğiniz [Kabuk dağıtım örneğinden](https://code.msdn.microsoft.com/Sample-setup-program-for-81ca73f7)gelir. Örnek, bu adımların her birini gerçekleştirme sonuçlarını gösterir.  
  
## <a name="prerequisites"></a>Prerequisites  
 Bu konunun açıkladığı yordamları gerçekleştirmek için, bilgisayarınızda aşağıdaki araçların yüklü olması gerekir.  
  
- Visual Studio SDK  
  
- [WINDOWS Installer XML araç takımı](https://documentation.help/WiX-Toolset/index.html/) 3,6 sürümü  
  
  Örnek ayrıca, tüm kabukların gerektirdiği Microsoft görselleştirme ve modelleme SDK 'sını de gerektirir.  
  
## <a name="preparing-your-solution"></a>Çözümünüzü hazırlama  
 Varsayılan olarak, kabuk şablonları VSıX paketleri için oluşturulur, ancak bu davranış öncelikli olarak hata ayıklama amacıyla hazırlanmıştır. Bir kabuk uygulaması dağıttığınızda, yükleme sırasında kayıt defteri erişimine ve yeniden başlatmalara izin vermek için MSI paketlerini kullanmanız gerekir. Uygulamanızı MSI dağıtımına hazırlamak için aşağıdaki adımları uygulayın.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>MSI dağıtımı için bir kabuk uygulaması hazırlamak üzere  
  
1. Çözümünüzde her. valtmanifest dosyasını düzenleyin.  
  
     `Identifier` öğesinde, bir `InstalledByMSI` öğesi ve bir `SystemComponent` öğesi ekleyin ve ardından değerlerini `true`olarak ayarlayın.  
  
     Bu öğeler VSıX yükleyicisinin, **uzantıları ve güncelleştirmeler** iletişim kutusunu kullanarak bileşenlerinizi yüklemeyi ve Kullanıcı tarafından kaldırılmasını engeller.  
  
2. VSıX bildirimi içeren her proje için, içeriği MSI 'nizin yükleneceği konuma çıkarmak üzere derleme görevlerini düzenleyin. Derleme çıktısına VSıX bildirimini ekleyin, ancak bir. VSIX dosyası oluşturmayın.  
  
## <a name="creating-an-msi-for-your-shell"></a>Kabuğunuz için MSI oluşturma  
 MSI paketinizi derlemek için, standart bir kurulum projesinden daha fazla esneklik sağladığından [WINDOWS Installer XML araç takımını](https://documentation.help/WiX-Toolset/index.html) kullanmanızı öneririz.  
  
 Ürün. WXS dosyanızda, algılama bloklarını ve kabuk bileşenlerinin yerleşimini ayarlayın.  
  
 Ardından, çözümünüz için. reg dosyasında ve ApplicationRegistry. WXS ' de kayıt defteri girişleri oluşturun.  
  
### <a name="detection-blocks"></a>Algılama blokları  
 Bir algılama bloğu, algılamak için önkoşulları belirten bir `Property` öğeden oluşur ve önkoşul bilgisayarda yoksa döndürülecek bir ileti belirten bir `Condition` öğesidir. Örneğin, kabuk uygulamanız Microsoft Visual Studio Shell yeniden dağıtılabilir ve algılama bloğu aşağıdaki biçimlendirmeye benzeyecektir.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Kabuk bileşenlerinin düzeni  
 Hedef dizin yapısını ve yüklenecek bileşenleri belirlemek için öğeleri eklemeniz gerekir.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Kabuk bileşenlerinin yerleşimini ayarlamak için  
  
1. Aşağıdaki örnekte gösterildiği gibi, hedef bilgisayardaki dosya sisteminde oluşturulacak tüm dizinleri temsil eden bir `Directory` öğeleri hiyerarşisi oluşturun.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Bu dizinlere, yüklenmesi gereken dosyalar belirtildiğinde `Id` tarafından başvurulur.  
  
2. Aşağıdaki örnekte gösterildiği gibi, kabuğun ve kabuk uygulamanızın gerektirdiği bileşenleri belirler.  
  
    > [!NOTE]
    > Bazı öğeler, diğer. WXS dosyalarındaki tanımlara başvurabilir.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. `ComponentRef` öğesi, geçerli bileşenin gerektirdiği dosyaları tanımlayan başka bir. WXS dosyası anlamına gelir. Örneğin, GeneralProfile, Helpate. WXS içinde aşağıdaki tanıma sahiptir.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef` öğesi bu dosyaların kullanıcının bilgisayarında nerede olduğunu belirtir. `Directory` öğesi, bir alt dizine yükleneceğini belirtir ve her bir `File` öğesi, çözümün bir parçası olarak oluşturulan ya da var olan bir dosyayı temsil eder ve MSI dosyası oluşturulduğunda dosyayı nerede bulabileceğini tanımlar.  
  
    2. `ComponentGroupRef` öğesi, başka bir bileşenler grubuna (veya bileşenler ve bileşen grupları) başvurur. Örneğin, ApplicationGroup altında `ComponentGroupRef` Application. WXS içinde aşağıdaki gibi tanımlanmıştır.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > Kabuk (yalıtılmış) uygulamalar için gerekli bağımlılıklar şunlardır: DebuggerProxy, MasterPkgDef, kaynaklar (özellikle. winprf dosyası), uygulama ve PkgDefs.  
  
### <a name="registry-entries"></a>Kayıt defteri girdileri  
 Kabuk (yalıtılmış) proje şablonu, yüklemede birleştirilecek kayıt defteri anahtarlarının bir *ProjectName*. reg dosyasını içerir. Bu kayıt defteri girdileri hem yükleme hem de Temizleme amaçları için MSI 'nin bir parçası olmalıdır. Ayrıca, ApplicationRegistry. WXS içinde eşleşen kayıt defteri blokları oluşturmanız gerekir.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Kayıt defteri girişlerini MSI ile tümleştirme  
  
1. **Kabuk özelleştirme** klasöründe, *ProjectName*. reg ' yi açın.  
  
2. $RootFolder $ belirtecinin tüm örneklerini hedef yükleme dizininin yoluyla değiştirin.  
  
3. Uygulamanızın gerektirdiği diğer tüm kayıt defteri girdilerini ekleyin.  
  
4. ApplicationRegistry. WXS dosyasını açın.  
  
5. *ProjectName*. reg içindeki her bir kayıt defteri girişi için, aşağıdaki örneklerde gösterildiği gibi, karşılık gelen bir kayıt defteri bloğu ekleyin.  
  
    |*ProjectName*. reg|Applicationkayıt. WXS|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT \CLSıD\\{bb431796-A179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "PhotoStudio DTE nesnesi"|\<RegistryKey ID = ' DteClsidRegKey ' root = ' HKCR ' Key = ' $ (var. DteClsidRegKey) ' Action = ' createAndRemoveOnUninstall ' ><br /><br /> \<RegistryValue Type = ' dize ' name = ' @ ' Value = ' $ (var. ShortProductName) DTE nesnesi '/><br /><br /> \</RegistryKey >|  
    |[HKEY_CLASSES_ROOT \CLSıD\\{bb431796-A179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey ID = ' DteLocSrv32RegKey ' root = ' HKCR ' Key = ' $ (var. DteClsidRegKey) \LocalServer32 ' Action = ' createAndRemoveOnUninstall ' ><br /><br /> \<RegistryValue Type = ' dize ' name = ' @ ' Value = ' [ıNSTALLDIR] $ (var. ShortProductName). exe '/><br /><br /> \</RegistryKey >|  
  
     Bu örnekte, var. DteClsidRegKey, en üst satırdaki kayıt defteri anahtarına çözümleniyor. Var. ShortProductName `PhotoStudio`çözümleniyor.  
  
## <a name="creating-a-setup-bootstrapper"></a>Kurulum Önyükleyicisi oluşturma  
 Tamamlanan MSI, yalnızca tüm önkoşulların yüklenmesi durumunda yüklenir. Son Kullanıcı deneyimini kolaylaştırmak için, uygulamanızı yüklemeden önce tüm önkoşulları toplayan ve yükleyen bir kurulum programı oluşturun. Yüklemenin başarılı olmasını sağlamak için aşağıdaki eylemleri gerçekleştirin:  
  
- Yüklemeyi yönetici ile zorunlu tutun.  
  
- Visual Studio Kabuğu 'nun (yalıtılmış) yüklü olup olmadığını algılar.  
  
- Kabuk yükleyicilerinin birini veya her ikisini sırayla çalıştırın.  
  
- Yeniden başlatma isteklerini işleyin.  
  
- MSI 'nizi çalıştırın.  
  
### <a name="enforcing-installation-by-administrator"></a>Yönetici tarafından yüklemeyi zorunlu tutma  
 Bu yordam, Kurulum programının \Program Files\\gibi gerekli dizinlere erişmesini etkinleştirmek için gereklidir.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Yüklemeyi yöneticiye zorlamak için  
  
1. Kurulum projesi için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **Yapılandırma özellikleri/bağlayıcı/bildirim dosyası**altında, **UAC yürütme düzeyi** ' ni **requireAdministrator**olarak ayarlayın.  
  
     Bu özellik, programın gömülü bildirim dosyasında yönetici olarak çalıştırılmasını gerektiren özniteliği koyar.  
  
### <a name="detecting-shell-installations"></a>Kabuk yüklemeleri algılanıyor  
 Visual Studio Kabuğu 'nun (yalıtılmış) yüklenmesi gerekip gerekmediğini öğrenmek için önce HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install. kayıt defteri değerini denetleyerek zaten yüklü olup olmadığını saptayın.  
  
> [!NOTE]
> Bu değerler ayrıca, Product. WXS içindeki kabuk algılama bloğu tarafından da okunabilir.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder, Visual Studio kabuğunun yüklendiği konumu belirtir ve burada dosyaları kontrol edebilirsiniz.  
  
 Bir kabuk yüklemesinin nasıl algılanacağını gösteren bir örnek için, Kabuk dağıtım örneğindeki Utilities. cpp ' nin `GetProductDirFromReg` işlevine bakın.  
  
 Paketinizin gerek duyduğu Visual Studio kabukların biri veya her ikisi bilgisayarda yüklü değilse, bunları yüklemek için bileşenleri listenize eklemeniz gerekir. Bir örnek için, Kabuk dağıtım örneğindeki ComponentsPage. cpp `ComponentsPage::OnInitDialog` işlevine bakın.  
  
### <a name="running-the-shell-installers"></a>Kabuk yükleyicilerini çalıştırma  
 Kabuk yükleyicilerini çalıştırmak için, doğru komut satırı bağımsız değişkenlerini kullanarak Visual Studio Shell yeniden dağıtılabilir 'i çağırın. En azından, bir sonraki yapmanız gerekenleri belirlemek için, **/norestart/q** komut satırı bağımsız değişkenlerini kullanmanız ve dönüş kodunu izlemeniz gerekir. Aşağıdaki örnek, yeniden dağıtılabilir kabuk (yalıtılmış) çalıştırır.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Shell Dil Paketi yükleyicilerini çalıştırma  
 Bunun yerine, kabuğun veya kabukların yüklendiğini ve yalnızca bir dil paketine ihtiyacınız olduğunu fark ederseniz, dil paketlerini aşağıdaki örnekte gösterildiği gibi yükleyebilirsiniz.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Dönüş değerlerini çözme  
 Bazı işletim sistemlerinde, Visual Studio Kabuğu (yalıtılmış) yüklemesi için yeniden başlatma gerekir. Bu durum `ExecCmd`çağrısının dönüş kodu tarafından belirlenebilir.  
  
|Dönüş Değeri|Açıklama|  
|------------------|-----------------|  
|ERROR_SUCCESS|Yükleme tamamlandı. Artık uygulamanızı yükleyebilirsiniz.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Yükleme tamamlandı. Bilgisayar yeniden başlatıldıktan sonra uygulamanızı yükleyebilirsiniz.|  
|3015|Yükleme devam ediyor. Yüklemeye devam etmek için bilgisayarın yeniden başlatılması gerekiyor.|  
  
### <a name="handling-restarts"></a>İşlem yeniden başlatmalar  
 Eğer **/norestart** bağımsız değişkenini kullanarak kabuk yükleyicisini çalıştırdığınızda bilgisayarı yeniden başlatmamış veya bilgisayarın yeniden başlatılmasını isteyeceğiz. Ancak yeniden başlatma gerekebilir ve bilgisayar yeniden başlatıldıktan sonra yükleyicinizin devam ettiğinden emin olmanız gerekir.  
  
 Yeniden başlatma işlemini doğru şekilde gerçekleştirmek için, yalnızca bir kurulum programının sürdürülecek olarak ayarlandığından ve özgeçmişin doğru bir şekilde işleneceğine emin olun.  
  
 ERROR_SUCCESS_REBOOT_REQUIRED veya 3015 döndürülürse, yükleme devam etmeden önce kodunuzun bilgisayarı yeniden başlatması gerekir.  
  
 Yeniden başlatmaları işlemek için aşağıdaki eylemleri gerçekleştirin:  
  
- Windows başladığında yüklemeyi sürdürmesini sağlamak için kayıt defterini ayarlayın.  
  
- Önyükleyici için çift yeniden başlatma gerçekleştirin.  
  
- Kabuk yükleyicisi ResumeData anahtarını silin.  
  
- Windows 'u yeniden başlatın.  
  
- MSI başlangıç yolunu sıfırlayın.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Windows başladığında kurulum 'U yeniden başlatmak için kayıt defterini ayarlama  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ kayıt defteri anahtarı, sistem başlangıcında yönetici izinleriyle yürütülür ve sonra silinir. HKEY_CURRENT_USER benzer bir anahtar içerir, ancak normal kullanıcı olarak çalışır ve yüklemeler için uygun değildir. Yükleyiciyi çağıran RunOnce anahtarına bir dize değeri koyarak yüklemeyi sürdürebilirsiniz. Bununla birlikte, uygulamayı başlatmak yerine bir **/restart yazın** veya benzer parametre kullanarak çağırmayı öneririz. Yükleme işleminde nerede olduğunu göstermek için parametreler de ekleyebilirsiniz. Bu, özellikle birden çok yeniden başlatma gerektirebilecek yüklemelerde yararlı olur.  
  
 Aşağıdaki örnek bir yüklemeyi sürdürmek için bir RunOnce kayıt defteri anahtarı değeri gösterir.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Önyükleyici 'nin çift yeniden başlatmasını yükleme  
 Kurulum doğrudan RunOnce 'ten kullanılıyorsa, masaüstü tamamen yüklenemez. Tam Kullanıcı arabirimini kullanılabilir hale getirmek için, kurulum 'un başka bir yürütmesi oluşturmanız ve RunOnce örneğini sonlandırmalısınız.  
  
 Kurulum programını doğru izinleri alacak şekilde yeniden yürütmeniz gerekir ve aşağıdaki örnekte gösterildiği gibi, yeniden başlatmadan önce durduysanız emin olmak için yeterli bilgi vermeniz gerekir.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Kabuk yükleyicisi ResumeData anahtarı siliniyor  
 Kabuk yükleyicisi, yeniden başlatmadan sonra kuruluma sürdürülecek, HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData kayıt defteri anahtarını verilerle ayarlar. Uygulamanız kabuk yükleyicisi değil, devam ettiğinden, aşağıdaki örnekte gösterildiği gibi bu kayıt defteri anahtarını silin.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Windows 'u yeniden başlatma  
 Gerekli kayıt defteri anahtarlarını ayarladıktan sonra Windows 'u yeniden başlatabilirsiniz. Aşağıdaki örnek farklı Windows işletim sistemleri için yeniden başlatma komutlarını çağırır.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>MSI başlangıç yolu sıfırlanıyor  
 Yeniden başlatmadan önce, geçerli dizin kurulum programınızın konumudur, ancak yeniden başlatmadan sonra konum System32 dizini olur. Aşağıdaki örnekte gösterildiği gibi, kurulum programınız her MSI çağrısından önce geçerli dizini sıfırlamalıdır.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Uygulama MSI 'sini çalıştırma  
 Visual Studio Kabuğu yükleyicisi ERROR_SUCCESS döndürdüğünde, uygulamanız için MSI 'yi çalıştırabilirsiniz. Kurulum programınız Kullanıcı arabirimini sağladığından, aşağıdaki örnekte gösterildiği gibi, MSI 'nizi sessiz modda ( **/q**) ve günlüğe kaydetme ( **/l**) ile başlatın.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Temel Yalıtılmış Kabuk Uygulaması Oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
