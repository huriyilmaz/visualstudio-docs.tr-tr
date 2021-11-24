---
title: Geliştirme ve test ortamlarını yayımlamak için PowerShell kullanma
description: Geliştirme ve test Windows PowerShell yayımlamak için Visual Studio betikleri kullanmayı öğrenin.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/22/2021
ms.author: ghogen
ms.openlocfilehash: 412a8c46c632fc894b1410e207a6035077ff5b7c
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132994975"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Windows PowerShell betiklerini kullanarak geliştirme ve test ortamlarına yayımlama

Visual Studio'de bir web uygulaması sanız, daha sonra Windows PowerShell web sitenizin Azure App Service'da veya sanal makinede Web Uygulaması olarak Azure'da yayımını otomatikleştirmek için kullanabileceğiniz bir Azure App Service betiği oluşturabilirsiniz. Gereksinimlerinize uyacak şekilde Windows PowerShell düzenleyicisinde Visual Studio betiği düzenleyebilir ve genişletebilir ya da betiği mevcut derleme, test ve yayımlama betikleriyle tümleştirebilirsiniz.

Bu betikleri kullanarak, geçici kullanım için sitenizin özelleştirilmiş sürümlerini (geliştirme ve test ortamları olarak da bilinir) sabilirsiniz. Örneğin, web sitenizin belirli bir sürümünü Bir Azure sanal makinesi üzerinde veya bir web sitesinin hazırlama yuvasında bir test paketi çalıştırmak, bir hatayı yeniden oluşturmak, hata düzeltmesini test etmek, önerilen bir değişikliği deneme veya tanıtım ya da sunum için özel bir ortam ayarlamak için oluşturabilirsiniz. Projenizi yayımlayan bir betik oluşturduktan sonra, betiği gerektiğinde yeniden çalıştırarak aynı ortamları yeniden oluşturabilir veya betiği kendi web uygulama derlemeniz ile çalıştırarak test için özel bir ortam oluşturabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio iş yükünün yüklü olduğu 2015 veya sonraki bir sürümü ya da Visual Studio 2013 ve Azure SDK 2.3 veya sonraki bir sürümü.  Bkz. [Visual Studio İndirmeleri.](https://visualstudio.microsoft.com/downloads) (Web projelerine yönelik betikleri oluşturmak için Azure SDK'ya ihtiyacınız yoktur. Bu özellik, bulut hizmetlerinde web rollerine değil web projelerine yöneliktir.)
* Azure PowerShell 0.7.4 veya sonrası. Bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).
* [Windows PowerShell 3.0 veya](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)) sonrası.

## <a name="additional-tools"></a>Ek araçlar

Azure geliştirme için PowerShell ile çalışmaya Visual Studio ek araçlar ve kaynaklar mevcuttur. Bkz. [PowerShell Araçları Visual Studio.](https://marketplace.visualstudio.com/items?itemName=AdamRDriscoll.PowerShellToolsforVisualStudio2015)

## <a name="generating-the-publish-scripts"></a>Yayımlama betikleri oluşturma

Bu yönergeleri izleyerek web sitenizi barındıran bir sanal makine için yayımlama [](/azure/virtual-machines/windows/classic/web-app-visual-studio)betikleri oluşturabilirsiniz. Ayrıca, web [uygulamaları için yayımlama betikleri oluşturmak için Azure App Service.](/azure/app-service/scripts/app-service-powershell-deploy-github)

## <a name="scripts-that-visual-studio-generates"></a>Oluşturulan Visual Studio betikler

Visual Studio iki Windows PowerShell dosyası, sanal makineniz veya web siteniz için yayımlama betiği ve betiklerde kullanabileceğiniz işlevleri içeren bir modül içeren **PublishScripts** adlı bir çözüm düzeyinde klasör oluşturur. Visual Studio, dağıtıyorsanız projenin ayrıntılarını belirten JSON biçiminde bir dosya da üretir.

### <a name="windows-powershell-publish-script"></a>Windows PowerShell betiği yayımlama

Yayımlama betiği, bir web sitesine veya sanal makineye dağıtmak için belirli yayımlama adımlarını içerir. Visual Studio geliştirme için söz dizimi renklendirmesi Windows PowerShell sağlar. İşlevler için yardım mevcuttur ve betikte işlevleri değişen gereksinimlerinize uyacak şekilde serbestçe düzenleyebilirsiniz.

### <a name="windows-powershell-module"></a>Windows PowerShell modülü

Oluşturulan Windows PowerShell modülü Visual Studio betiğin kullandığı işlevleri içerir. Bu Azure PowerShell işlevlerin değiştirilmeleri amaçlanmaz. Bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).

### <a name="json-configuration-file"></a>JSON yapılandırma dosyası

JSON dosyası Yapılandırmalar klasöründe **oluşturulur** ve Azure'a dağıtacak kaynakları tam olarak belirten yapılandırma verilerini içerir. Bir web sitesi oluşturduysanız Visual Studio dosyanın adı project-name-WAWS-dev.json veya bir sanal makine oluşturduysanız proje adı-VM-dev.json'tur. Burada bir web sitesi yapılandırmasını 7.000.000'den önce oluşturulan JSON yapılandırma dosyasının bir örneğini bulabilirsiniz. Değerlerin çoğu kendi kendine açıklayıcıdır. Web sitesi adı Azure tarafından oluşturulur, bu nedenle proje adınızla eşleşmeyebilirsiniz.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Bir sanal makine sanız, JSON yapılandırma dosyası aşağıdakine benzer. Sanal makine için kapsayıcı olarak bir bulut hizmeti oluşturulur. Sanal makine HTTP ve HTTPS üzerinden web erişimi için normal uç noktaların yanı sıra Web Dağıtımı için uç noktaları içerir. Bu uç noktalar web sitesine yerel makineniz, Uzak Masaüstü ve Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Yayımlama betiklerini çalıştırarak ne olacağını değiştirmek için JSON yapılandırmasını düzenleyebilirsiniz. `cloudService`ve `virtualMachine` bölümleri gereklidir, ancak ihtiyacınız `databases` yoksa bölümü silebilirsiniz. Oluşturulan varsayılan yapılandırma dosyasında boş olan Visual Studio isteğe bağlıdır; varsayılan yapılandırma dosyasında değerleri olan özellikler gereklidir.

Azure'da tek bir üretim sitesi yerine birden çok dağıtım ortamlı (yuva olarak bilinir) olan bir web siteniz varsa, yuva adını JSON yapılandırma dosyasına web sitesinin adına dahil edebilirsiniz. Örneğin, **mysite** adlı bir web siteniz ve **test** adlı bir yuvanız varsa URI olur, ancak yapılandırma dosyasında kullanmak için doğru ad `mysite-test.cloudapp.net` mysite(test) olur. Bunu yalnızca aboneliğinize web sitesi ve yuvalar zaten varsa ebilirsiniz. Yoksa, yuvayı belirtmeden betiği çalıştırarak web sitesini oluşturun, sonra [Azure portal](https://portal.azure.com/)içinde yuvayı oluşturun ve ardından değiştirilen web sitesi adıyla betiği çalıştırın. Web uygulamaları için dağıtım yuvaları hakkında daha fazla bilgi için bkz. Web uygulamaları için hazırlama [ortamlarını Azure App Service.](/azure/app-service/web-sites-staged-publishing)

## <a name="how-to-run-the-publish-scripts"></a>Yayımlama betiklerini çalıştırma

Daha önce hiç bir Windows PowerShell çalıştırmadıysanız, önce betiklerin çalışmasına olanak sağlamak için yürütme ilkesi ayarlamanız gerekir. İlke, kullanıcıların betikleri yürütmeyi içeren kötü amaçlı yazılımlara veya virüslere karşı Windows PowerShell betikleri çalıştırmasını engelleyen bir güvenlik özelliğidir.

### <a name="run-the-script"></a>Betiği çalıştırın

1. Projeniz Web Dağıtımı paketi oluşturun. Bir Web Dağıtımı paketi, web sitenize veya sanal makinenize kopyalamak istediğiniz dosyaları içeren sıkıştırılmış bir arşivdir (.zip dosyası). Herhangi bir web Web Dağıtımı için Visual Studio paket oluşturabilirsiniz.

   ![Web Dağıtımı Paketi Oluşturma](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Daha fazla bilgi için, [bkz. How to: Create a Web Deployment Package in Visual Studio.](/previous-versions/aspnet/dd465323(v=vs.110)) Yayımlama betiklerini özelleştirme ve genişletme konusunda Web Dağıtımı paketinizin [oluşturulmasını da otomatik hale getirirsiniz.](#customizing-and-extending-the-publish-scripts)

1. Bu **Çözüm Gezgini** betiğin bağlam menüsünü açın ve **PowerShell ISE'Birlikte aç seçin.**
1. Bu bilgisayarda Windows PowerShell betikleri ilk kez çalıştıracaksanız, Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın ve aşağıdaki komutu yazın:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Aşağıdaki komutu kullanarak Azure'da oturum açma.

    ```powershell
    Add-AzureAccount
    ```

    İstendiğinde kullanıcı adınızı ve parolanızı girin.

    Betiği otomatikleştirtiğiniz zaman Azure kimlik bilgilerini sağlama yönteminin çalışmay olduğunu unutmayın. Bunun yerine, kimlik bilgilerini `.publishsettings` sağlamak için dosyasını kullansanız iyi olur. Yalnızca bir kez, Dosyayı Azure'dan indirmek için **Get-AzurePublishSettingsFile** komutunu kullanın ve ardından **import-AzurePublishSettingsFile** komutunu kullanarak dosyayı içeri aktarın. Ayrıntılı yönergeler için bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).

1. (İsteğe bağlı) Web uygulamasını yayımlamadan sanal makine, veritabanı ve web sitesi gibi Azure kaynakları oluşturmak için **JSON** yapılandırma dosyasına **ayarlanmış -Configuration** bağımsız değişkeniylePublish-WebApplication.ps1komutunu kullanın. Bu komut satırı, oluşturulecek kaynakları belirlemek için JSON yapılandırma dosyasını kullanır. Diğer komut satırı bağımsız değişkenleri için varsayılan ayarları kullandığı için kaynakları oluşturur, ancak web uygulamanızı yayımlamaz. –Verbose seçeneği, neler olduğu hakkında daha fazla bilgi sağlar.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Betiği **Publish-WebApplication.ps1** web uygulamanızı yayımlamak için aşağıdaki örneklerden biri ile gösterildiği gibiPublish-WebApplication.ps1komutunu kullanın. Abonelik adı, paket adını yayımlama, sanal makine kimlik bilgileri veya veritabanı sunucusu kimlik bilgileri gibi diğer bağımsız değişkenler için varsayılan ayarları geçersiz kılmanız gerekirse, bu parametreleri belirtebilirsiniz. Yayımlama işleminin ilerleme durumu hakkında daha fazla bilgi görmek için **–Verbose** seçeneğini kullanın.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Bir sanal makine oluşturuyorsanız, komut aşağıdaki gibi görünüyor. Bu örnekte ayrıca birden çok veritabanı için kimlik bilgilerinin nasıl belirtnerek belirtebilirsiniz. Bu betiklerin oluşturdukları sanal makineler için SSL sertifikası güvenilen bir kök yetkiliden değildir. Bu nedenle– **AllowUntrusted seçeneğini kullansanız gerekir.**

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Betik veritabanları oluşturabilir ancak veritabanı sunucusu oluşturmaz. Veritabanı sunucusu oluşturmak için Azure modülünde **New-AzureSqlDatabaseServer** işlevini kullanabilirsiniz.

## <a name="customizing-and-extending-the-publish-scripts"></a>Yayımlama betiklerini özelleştirme ve genişletme

Yayımlama betiği ve JSON yapılandırma dosyasını özelleştirebilirsiniz. **AzureWebAppPublishModule.psm1** Windows PowerShell modülünde yer alan işlevlerin değiştirilmeleri amaçlanmamıştır. Yalnızca farklı bir veritabanı belirtmek veya sanal makinenin bazı özelliklerini değiştirmek için JSON yapılandırma dosyasını düzenleyin. Projenizi bina ve test etme işlemini otomatikleştirmek için betiğin işlevselliğini genişletmek için, içinde işlev saplamaları **Publish-WebApplication.ps1.**

Projenizi otomatikleştirmek için, bu kod örneğinde gösterildiği MSBuild `New-WebDeployPackage` çağrısında bulunan kodu ekleyin. MSBuild komutunun yolu, yüklü Visual Studio sürümüne bağlı olarak farklıdır. Doğru yolu almak için bu örnekte gösterildiği gibi **Get-MSBuildCmd** işlevini kullanabilirsiniz.

### <a name="to-automate-building-your-project"></a>Projenizi otomatikleştirmek için

1. parametresini `$ProjectFile` genel parametre bölümüne ekleyin.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. İşlevi `Get-MSBuildCmd` betik dosyanıza kopyalayın.

    ```powershell
    function Get-MSBuildCmd
    {
       process
       {
        $StartInfo  = New-Object System.Diagnostics.ProcessStartInfo;
        $StartInfo.Filename = ${Env:ProgramFiles(x86)} + "\\Microsoft Visual Studio\\Installer\\vswhere.exe"
        $StartInfo.Arguments = " -latest -requires Microsoft.Component.MSBuild -find MSBuild\\**\\Bin\\MSBuild.exe"
        $StartInfo.RedirectStandardOutput = $True
        $StartInfo.UseShellExecute = $False
        [System.Diagnostics.Process] $VSWhere = [Diagnostics.Process]::Start($StartInfo)
        $VSWhere.WaitForExit()
        return $VSWhere.StandardOutput.ReadToEnd();
        }
    }
    ```

1. yerine `New-WebDeployPackage` aşağıdaki kodu girin ve oluşturma satırındaki yer tutucularını `$msbuildCmd` değiştirin.

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Web uygulamanızı oluşturmak için MsBuild.exe. Yardım için [bkz. MSBuild Command-Line Başvurusu](../msbuild/msbuild-command-line-reference.md)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Derleme komutunun yürütülmesini başlatma

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. İşlevi `New-WebDeployPackage` şu satırdan önce çağır: `$Config = Read-ConfigFile $Configuration` web uygulamaları veya sanal makineler `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` için.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Aşağıdaki örnekte olduğu gibi bağımsız değişkenlerini geçirmeyi kullanarak `$Project` komut satırına özelleştirilmiş betiği çağırma:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Uygulama testini otomatikleştirmek için uygulamasına kod `Test-WebApplication` ekleyin. Bu işlevlerin çağrıldı olduğu birPublish-WebApplication.ps1 **satırlarda** yer alan ifadelerden emin olun. Bir uygulama sağlanmasa, projenizi Visual Studio el ile Visual Studio azure'da yayımlamak için yayımlama betiği çalıştırabilirsiniz.

## <a name="publishing-function-summary"></a>Yayımlama işlevi özeti
komut isteminde kullanabileceğiniz işlevlerle ilgili yardım Windows PowerShell komutunu `Get-Help function-name` kullanın. Yardım, parametre yardımı ve örnekleri içerir. Aynı yardım metni, **AzureWebAppPublishModule.psm1** betik kaynak dosyalarında da yer alır ve **Publish-WebApplication.ps1.** Betik ve yardım, kendi dilinize Visual Studio.

**AzureWebAppPublishModule**

| İşlev adı | Description |
| --- | --- |
| Add-AzureSQLDatabase |Yeni bir Azure SQL oluşturur. |
| Add-AzureSQLDatabases |Azure SQL JSON yapılandırma dosyasında oluşturulan değerlerden Visual Studio oluşturur. |
| Add-AzureVM |Bir Azure sanal makinesi oluşturur ve dağıtılan VM'nin URL'sini döndürür. İşlev önkoşulları ayarlar ve yeni bir sanal makine oluşturmak için **New-AzureVM** işlevini (Azure modülü) arar. |
| Add-AzureVMEndpoints |Sanal makineye yeni giriş uç noktaları ekler ve sanal makineyi yeni uç noktayla döndürür. |
| Add-AzureVMStorage |Geçerli abonelikte yeni bir Azure depolama hesabı oluşturur. Hesabın adı "devtest" ve ardından benzersiz bir alfasayısal dize ile başlar. İşlev, yeni depolama hesabının adını döndürür. Yeni depolama hesabı için bir konum veya benzeşm grubu belirtin. |
| Add-AzureWebsite |Belirtilen ad ve konuma sahip bir web sitesi oluşturur. Bu işlev, Azure **modülünde New-AzureWebsite** işlevini çağıran bir işlevdir. Abonelikte belirtilen adla bir web sitesi yoksa bu işlev web sitesini oluşturur ve bir web sitesi nesnesi döndürür. Aksi takdirde `$null` döndürür. |
| Backup-Subscription |Geçerli Azure aboneliğini betik `$Script:originalSubscription` kapsamındaki değişkenine kaydeder. Bu işlev, geçerli Azure aboneliğini (tarafından edinilen şekilde) ve depolama hesabını ve bu betik tarafından değiştirilen aboneliği (değişkende depolanır) ve depolama hesabını betik kapsamında `Get-AzureSubscription -Current` `$UserSpecifiedSubscription` kaydeder. Değerleri kaydederek, geçerli durum değişti ise özgün geçerli aboneliği ve depolama hesabını geçerli durumuna geri yüklemek için gibi bir `Restore-Subscription` işlev kullanabilirsiniz. |
| Find-AzureVM |Belirtilen Azure sanal makinesini alır. |
| Format-DevTestMessageWithTime |Bir iletinin tarihini ve saatlerini hazırlar. Bu işlev, Hata ve Ayrıntılı akışlara yazılan iletiler için tasarlanmıştır. |
| Get-AzureSQLDatabaseConnectionString |Azure veritabanına bağlanmak için bir bağlantı dizesi SQL oluşturur. |
| Get-AzureVMStorage |Belirtilen konum veya benzeşm grubunda "devtest" (büyük/büyük/büyük harfe duyarlı değil) ad deseniyle ilk depolama *hesabının adını döndürür. "devtest"* depolama hesabı konum veya benzeşm grubuyla eşlenemse işlev bunu yoksayar. Bir konum veya benzeşm grubu belirtin. |
| Get-MSDeployCmd |MsDeploy.exe aracını çalıştırmak için MsDeploy.exe döndürür. |
| New-AzureVMEnvironment |Abonelikte JSON yapılandırma dosyasındaki değerlerle eşleşen bir sanal makine bulur veya oluşturur. |
| Publish-WebPackage |Kaynakları MsDeploy.exe dağıtmak için bir web .Zip paketi ve web yayımlama paketi dosyası kullanır. Bu işlev herhangi bir çıkış oluşturmaz. MSDeploy.exe çağrısı başarısız olursa, işlev bir özel durum oluşturur. Daha ayrıntılı bir çıkış elde etmek için **-Verbose seçeneğini** kullanın. |
| Publish-WebPackageToVM |Parametre değerlerini doğrular ve ardından **Publish-WebPackage işlevini** çağırır. |
| Read-ConfigFile |JSON yapılandırma dosyasını doğrular ve seçilen değerlerin karma bir tablosu döndürür. |
| Restore-Subscription |Geçerli aboneliği özgün aboneliğe sıfırlar. |
| Test-AzureModule |Yüklü `$true` Azure modülü sürümü 0.7.4 veya sonraki bir sürümse döndürür. Modül `$false` yüklü değilse veya önceki bir sürümdeyse döndürür. Bu işlevin parametresi yoktur. |
| Test-AzureModuleVersion |`$true`Azure modülünün sürümü 0.7.4 veya sonraki bir sürümse döndürür. Modül `$false` yüklü değilse veya önceki bir sürümdeyse döndürür. Bu işlevin parametresi yoktur. |
| Test-HttpsUrl |Giriş URL'sini System.Uri nesnesine dönüştürür. `$True`URL mutlak ise ve şeması https ise döndürür. URL göreli ise, şeması HTTPS değilse veya giriş `$false` dizesi BIR URL'ye dönüştürüle değilse döndürür. |
| Test-Member |Bir `$true` özellik veya yöntem nesnenin üyesi ise döndürür. Aksi takdirde `$false` döndürür. |
| Write-ErrorWithTime |Geçerli saat ön ekli bir hata iletisi yazar. Bu işlev, İletiyi Hata akışına yazmadan önce zamanı sona hazırlamak için **Format-DevTestMessageWithTime** işlevini arar. |
| Write-HostWithTime |Ana bilgisayar programına (**Write-Host**) geçerli saat ön ekli bir ileti yazar. Konak programına yazmanın etkisi değişir. Bu iletileri barındıran çoğu Windows PowerShell standart çıkışa yazar. |
| Write-VerboseWithTime |Geçerli saat ön ekli ayrıntılı bir ileti yazar. **Write-Verbose** çağıran ileti yalnızca betik **Ayrıntılı** parametresiyle çalıştır kullanıldığında veya **VerbosePreference** tercihi Devam olarak ayarlanmış **olduğunda görüntülenir.** |

**Publish-WebApplication**

| İşlev adı | Description |
| --- | --- |
| New-AzureWebApplicationEnvironment |Web sitesi veya sanal makine gibi Azure kaynakları oluşturur. |
| New-WebDeployPackage |Bu işlev uygulanmaz. Projenizi derlemek için bu işleve komut abilirsiniz. |
| Publish-AzureWebApplication |Azure'da bir web uygulaması yayımlar. |
| Publish-WebApplication |Web projesi için Web Apps, sanal makineler, SQL veritabanları ve depolama hesapları oluşturur ve Visual Studio dağıtır. |
| Test-WebApplication |Bu işlev uygulanmaz. Bu işleve, uygulamanızı test etmek için komut abilirsiniz. |

## <a name="next-steps"></a>Sonraki adımlar
PowerShell betiği yazma hakkında [](/powershell/scripting/overview) daha fazla bilgi edinmek için Windows PowerShell Betik Merkezi'nde Azure PowerShell betiklerini [öğrenin.](https://azure.microsoft.com/documentation/scripts/)