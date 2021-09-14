---
title: Geliştirme ve test ortamlarına yayımlamak için PowerShell 'i kullanma
description: geliştirme ve test ortamlarında yayımlamak için Visual Studio Windows PowerShell betikleri kullanmayı öğrenin.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 2e7b04c0411f5e07933cf4286edfcb112d6377e7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633062"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Windows PowerShell betiklerini kullanarak geliştirme ve test ortamlarına yayımlama

Visual Studio içinde bir web uygulaması oluşturduğunuzda, daha sonra web sitenizin Azure App Service veya bir sanal makinede bir web uygulaması olarak Azure 'a yayımlanmasını otomatikleştirmek için kullanabileceğiniz bir Windows PowerShell betiği oluşturabilirsiniz. Visual Studio düzenleyicisinde Windows PowerShell betiğini düzenleyebilir ve genişletebilirsiniz veya komut dosyasını mevcut derleme, test ve yayımlama betiklerine entegre edebilirsiniz.

Bu betikleri kullanarak, geçici kullanım için sitenizin özelleştirilmiş sürümlerini (geliştirme ve test ortamları olarak da bilinir) sağlayabilirsiniz. Örneğin, bir Azure sanal makinesinde veya bir Web sitesindeki hazırlama yuvasında bir test paketini çalıştırmak, bir hatayı yeniden oluşturmak, bir hata düzeltmesini test etmek, önerilen bir değişikliği denemek veya bir demo ya da sunum için özel bir ortam ayarlamak üzere Web sitenizin belirli bir sürümünü kurabilirsiniz. Projenizi yayımlayan bir betik oluşturduktan sonra, komut dosyasını gerektiği gibi yeniden çalıştırarak özdeş ortamları yeniden oluşturabilir veya test için özel bir ortam oluşturmak üzere betiği kendi Web uygulamanızın derlemesi ile çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* **azure iş yükü** yüklü olan veya Visual Studio 2013 ve azure SDK 2,3 veya üzeri ile Visual Studio 2015 veya üzeri. bkz. [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads). (Web projelerine yönelik betikleri oluşturmak için Azure SDK 'ya ihtiyacınız yoktur. Bu özellik, bulut hizmetlerinde Web rolleri değil Web projelerine yöneliktir.)
* Azure PowerShell 0.7.4 veya üzeri. Bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).
* [Windows PowerShell 3,0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)) veya üzeri.

## <a name="additional-tools"></a>Ek araçlar

Azure geliştirme için Visual Studio 'de PowerShell ile çalışmaya yönelik ek araçlar ve kaynaklar mevcuttur. Bkz. [Visual Studio Için PowerShell Araçları](https://marketplace.visualstudio.com/items?itemName=AdamRDriscoll.PowerShellToolsforVisualStudio2015).

## <a name="generating-the-publish-scripts"></a>Yayımlama betikleri oluşturuluyor

[Bu yönergeleri](/azure/virtual-machines/windows/classic/web-app-visual-studio)izleyerek yeni bir proje oluştururken Web sitenizi barındıran bir sanal makine için yayımlama betikleri oluşturabilirsiniz. Ayrıca, [Azure App Service Web uygulamaları için yayımlama betikleri](/azure/app-service/scripts/app-service-powershell-deploy-github)da oluşturabilirsiniz.

## <a name="scripts-that-visual-studio-generates"></a>Visual Studio oluşturduğu betikler

Visual Studio, iki Windows PowerShell dosya içeren **publishscripts** adlı çözüm düzeyinde bir klasör, sanal makineniz veya web siteniz için bir yayımlama betiği ve betiklerinizde kullanabileceğiniz işlevleri içeren bir modül oluşturur. Visual Studio ayrıca, dağıttığınız projenin ayrıntılarını belirten JSON biçiminde bir dosya oluşturur.

### <a name="windows-powershell-publish-script"></a>betik yayımla Windows PowerShell

Yayımla betiği, bir Web sitesine veya sanal makineye dağıtmaya yönelik belirli yayımlama adımlarını içerir. Visual Studio Windows PowerShell geliştirme için sözdizimi renklendirmesi sağlar. İşlevler için Yardım kullanılabilir ve değişen gereksinimlerinize uyacak şekilde betikteki işlevleri serbestçe düzenleyebilirsiniz.

### <a name="windows-powershell-module"></a>Windows PowerShell modülü

Visual Studio üreten Windows PowerShell modülü, yayımlama betiğinin kullandığı işlevleri içerir. bu Azure PowerShell işlevlerinin değiştirilmesi amaçlanmamaktadır. Bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).

### <a name="json-configuration-file"></a>JSON yapılandırma dosyası

JSON dosyası **yapılandırmalar** klasöründe oluşturulur ve Azure 'a tam olarak hangi kaynakların dağıtılacağını belirten yapılandırma verilerini içerir. Visual Studio oluşturduğu dosyanın adı proje-adı-waws-dev. json, bir web sitesi oluşturduysanız veya bir sanal makine oluşturduysanız VM-dev. json. Bir Web sitesi oluştururken oluşturulan JSON yapılandırma dosyasına bir örnek aşağıda verilmiştir. Değerlerin çoğu kendi kendine açıklayıcıdır. Web sitesi adı Azure tarafından oluşturulduğundan proje adınızla eşleşmeyebilir.

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

Bir sanal makine oluşturduğunuzda, JSON yapılandırma dosyası aşağıdakine benzer şekilde görünür. Bir bulut hizmeti, sanal makine için kapsayıcı olarak oluşturulur. Sanal makine, HTTP ve HTTPS üzerinden Web erişimi için her zamanki uç noktaları ve Web Dağıtımı için uç noktaları içerir. Bu, yerel makinenizden, uzak masaüstünüzden ve Windows PowerShell Web sitesinde yayımlama yapmanızı sağlar.

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

Yayımlama betiklerini çalıştırdığınızda ne olacağını değiştirmek için JSON yapılandırmasını düzenleyebilirsiniz. `cloudService`Ve `virtualMachine` bölümleri gereklidir, ancak `databases` gerekmiyorsa bölümünü silebilirsiniz. Visual Studio üreten varsayılan yapılandırma dosyasında boş olan özellikler isteğe bağlıdır; Varsayılan yapılandırma dosyasında değerleri olan özellikler gereklidir.

Azure 'da tek bir üretim sitesi yerine birden çok dağıtım ortamına (yuva olarak bilinir) sahip bir Web siteniz varsa, yuva adını JSON yapılandırma dosyasına Web sitesinin adına ekleyebilirsiniz. Örneğin, **sitem** adlı bir Web siteniz ve **Test** adlı BT için BIR yuva varsa, URI olur `mysite-test.cloudapp.net` , ancak yapılandırma dosyasında kullanılacak doğru ad sitem (test) olur. Bunu yalnızca, Web sitesi ve yuvaları aboneliğinizde zaten mevcutsa yapabilirsiniz. Mevcut değilse, yuvası belirtmeden betiği çalıştırarak Web sitesini oluşturun, ardından [Azure Portal](https://portal.azure.com/)yuvasını oluşturun ve ardından betiği değiştirilen Web sitesi adıyla çalıştırın. Web Apps için dağıtım yuvaları hakkında daha fazla bilgi için, bkz. [Azure App Service Web Apps için hazırlama ortamlarını ayarlama](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Yayımlama betikleri nasıl çalıştırılır

daha önce hiç bir Windows PowerShell komut dosyası çalıştırmadıysanız, önce komut dosyalarının çalıştırılmasını sağlamak için yürütme ilkesini ayarlamanız gerekir. ilke, kullanıcıların komut dosyalarını yürütmeyi içeren kötü amaçlı yazılımlara veya virüslere karşı savunmasız olmaları durumunda Windows PowerShell betikleri çalıştırmasını engelleyen bir güvenlik özelliğidir.

### <a name="run-the-script"></a>Betiği çalıştırın

1. Projeniz için Web Dağıtımı paketini oluşturun. Web Dağıtımı Paket, Web sitenize veya sanal makinenize kopyalamak istediğiniz dosyaları içeren sıkıştırılmış bir arşiv (.zip dosyasıdır). herhangi bir Web uygulaması için Visual Studio Web Dağıtımı paketleri oluşturabilirsiniz.

   ![Web Dağıtımı Paketi Oluştur](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Web dağıtım paketi oluşturma](/previous-versions/aspnet/dd465323(v=vs.110)). Ayrıca, [Yayımlama betiklerini özelleştirme ve genişletme](#customizing-and-extending-the-publish-scripts)bölümünde açıklandığı gibi Web dağıtımı paketinizin oluşturulmasını otomatik hale getirebilirsiniz.

1. **Çözüm Gezgini**' de, betiğin bağlam menüsünü açın ve ardından **PowerShell ISE ile aç**' ı seçin.
1. bu bilgisayarda ilk kez Windows PowerShell betikleri çalıştırıyorsanız, yönetici ayrıcalıklarıyla bir komut istemi penceresi açın ve aşağıdaki komutu yazın:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Aşağıdaki komutu kullanarak Azure 'da oturum açın.

    ```powershell
    Add-AzureAccount
    ```

    İstendiğinde, Kullanıcı adınızı ve parolanızı girin.

    Betiği otomatikleştirdiğiniz zaman, Azure kimlik bilgilerini sağlamaya yönelik bu yöntem işe yaramadığını unutmayın. Bunun yerine, `.publishsettings` kimlik bilgilerini sağlamak için dosyasını kullanmanız gerekir. Yalnızca bir kez, dosyayı Azure 'dan indirmek için **Get-Azuikinci dosya SettingsFile** komutunu kullanın ve bundan sonra dosyayı içeri aktarmak için **Import-Azuyeniden yayımcı SettingsFile** komutunu kullanın. Ayrıntılı yönergeler için bkz. [Azure PowerShell'i yükleme ve yapılandırma](/powershell/azure/overview).

1. Seçim Web uygulamanızı yayımlamadan sanal makine, veritabanı ve Web sitesi gibi Azure kaynakları oluşturmak istiyorsanız, JSON yapılandırma dosyası olarak ayarlanan **-Configuration** bağımsız değişkeniyle birlikte **Publish-WebApplication.ps1** komutunu kullanın. Bu komut satırı, hangi kaynakların oluşturulacağını belirleyen JSON yapılandırma dosyasını kullanır. Diğer komut satırı bağımsız değişkenleri için varsayılan ayarları kullandığından, kaynakları oluşturur, ancak Web uygulamanızı yayımlamaz. – Verbose seçeneği, neler olduğu hakkında daha fazla bilgi sağlar.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Komut dosyasını çağırmak ve Web uygulamanızı yayımlamak için aşağıdaki örneklerden birinde gösterildiği gibi **Publish-WebApplication.ps1** komutunu kullanın. Abonelik adı, yayımlama paketi adı, sanal makine kimlik bilgileri veya veritabanı sunucusu kimlik bilgileri gibi diğer bağımsız değişkenlerden herhangi biri için varsayılan ayarları geçersiz kılmanız gerekiyorsa, bu parametreleri belirtebilirsiniz. Yayımlama sürecinin ilerlemesi hakkında daha fazla bilgi görmek için **– verbose** seçeneğini kullanın.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Bir sanal makine oluşturuyorsanız, komut aşağıdaki gibi görünür. Bu örnek ayrıca birden çok veritabanı için kimlik bilgilerinin nasıl kullanılacağını gösterir. Bu betiklerin oluşturmakta olduğu sanal makineler için, SSL sertifikası güvenilen bir kök yetkilisinden değildir. Bu nedenle, **– Allowgüvenilmeyen** seçeneğini kullanmanız gerekir.

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

    Betik veritabanları oluşturabilir, ancak veritabanı sunucuları oluşturmaz. Bir veritabanı sunucusu oluşturmak istiyorsanız, Azure modülündeki **New-Azuressqldatabaseserver** işlevini kullanabilirsiniz.

## <a name="customizing-and-extending-the-publish-scripts"></a>Yayımlama betiklerini özelleştirme ve genişletme

Yayımlama betiğini ve JSON yapılandırma dosyasını özelleştirebilirsiniz. **AzureWebAppPublishModule. psm1** modülündeki Windows PowerShell işlevlerin değiştirilmesi amaçlanmamaktadır. Yalnızca farklı bir veritabanı belirtmek veya sanal makinenin bazı özelliklerini değiştirmek istiyorsanız, JSON yapılandırma dosyasını düzenleyin. Projenizin oluşturulmasını ve test edilmesini otomatikleştirmek için betiğin işlevlerini genişletmek istiyorsanız, **Publish-WebApplication.ps1** işlev saplamalarını uygulayabilirsiniz.

projenizi oluşturmaya otomatik hale getirmek için, `New-WebDeployPackage` bu kod örneğinde gösterildiği gibi MSBuild çağıran kodu ekleyin. MSBuild komutunun yolu, yüklediğiniz Visual Studio sürümüne bağlı olarak farklılık açmış. Doğru yolu almak için, **Get-MSBuildCmd** işlevini Bu örnekte gösterildiği gibi kullanabilirsiniz.

### <a name="to-automate-building-your-project"></a>Projenizi oluşturmaya otomatik hale getirmek için

1. `$ProjectFile`Parametresini genel param bölümüne ekleyin.

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

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. `New-WebDeployPackage`Aşağıdaki kodla değiştirin ve satır oluşturulurken yer tutucuları değiştirin `$msbuildCmd` . bu kod Visual Studio 2019 içindir. Visual Studio 2017 kullanıyorsanız, **VisualStudioVersion** özelliğini `15.0` , Visual Studio 2015 için ' 14,0 ' veya `12.0` Visual Studio 2013) olarak değiştirin.

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Web uygulamanızı derlemek için MsBuild.exe kullanın. yardım için bkz. [MSBuild Command-Line başvurusu](../msbuild/msbuild-command-line-reference.md)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=16.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Build komutunun yürütülmesini Başlat

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

1. `New-WebDeployPackage`Bu satırdan önce işlevi çağırın: `$Config = Read-ConfigFile $Configuration` Web uygulamaları veya `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` sanal makineler için.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. `$Project`Aşağıdaki örnekte gösterildiği gibi bağımsız değişkeni geçirerek komut satırından özelleştirilmiş betiği çağırın:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Uygulama testini otomatikleştirmek için uygulamasına kod `Test-WebApplication` ekleyin. Bu işlevlerin çağrıldı olduğu birPublish-WebApplication.ps1 **satırlarda** yer alan ifadelerden emin olun. Uygulama sağlansa bile projenizi Visual Studio derlemeniz ve ardından yayımlama betiği çalıştırarak Azure'da yayımlamanız gerekir.

## <a name="publishing-function-summary"></a>Yayımlama işlevi özeti
komut isteminde kullanabileceğiniz işlevlerle ilgili yardım Windows PowerShell komutunu `Get-Help function-name` kullanın. Yardım, parametre yardımı ve örnekleri içerir. Aynı yardım metni, **AzureWebAppPublishModule.psm1** betik kaynak dosyalarında da yer alır ve **Publish-WebApplication.ps1.** Betik ve yardım, kendi dilinize Visual Studio.

**AzureWebAppPublishModule**

| İşlev adı | Description |
| --- | --- |
| Add-AzureSQLDatabase |Yeni bir Azure SQL oluşturur. |
| Add-AzureSQLDatabases |Azure SQL JSON yapılandırma dosyasında oluşturulan değerlerden Visual Studio oluşturur. |
| Add-AzureVM |Bir Azure sanal makinesi oluşturur ve dağıtılan VM'nin URL'sini döndürür. İşlev önkoşulları ayarlar ve ardından yeni bir sanal makine oluşturmak için **New-AzureVM** işlevini (Azure modülü) arar. |
| Add-AzureVMEndpoints |Sanal makineye yeni giriş uç noktaları ekler ve sanal makineyi yeni uç noktayla döndürür. |
| Add-AzureVMStorage |Geçerli abonelikte yeni bir Azure depolama hesabı oluşturur. Hesabın adı "devtest" ve ardından benzersiz bir alfasayısal dize ile başlar. İşlev, yeni depolama hesabının adını döndürür. Yeni depolama hesabı için bir konum veya benzeşm grubu belirtin. |
| Add-AzureWebsite |Belirtilen ad ve konuma sahip bir web sitesi oluşturur. Bu işlev, Azure **modülünde New-AzureWebsite** işlevini çağıran bir işlevdir. Abonelikte belirtilen adla bir web sitesi yoksa bu işlev web sitesini oluşturur ve bir web sitesi nesnesi döndürür. Aksi takdirde `$null` döndürür. |
| Backup-Subscription |Geçerli Azure aboneliğini betik `$Script:originalSubscription` kapsamındaki değişkenine kaydeder. Bu işlev, geçerli Azure aboneliğini (tarafından edinilen şekilde) ve depolama hesabını ve bu betik tarafından değiştirilen aboneliği (değişkende depolanır) ve depolama hesabını betik kapsamında `Get-AzureSubscription -Current` `$UserSpecifiedSubscription` kaydeder. Değerleri kaydederek, geçerli durum değişti ise özgün geçerli aboneliği ve depolama hesabını geçerli durumuna geri yüklemek için gibi bir `Restore-Subscription` işlev kullanabilirsiniz. |
| Find-AzureVM |Belirtilen Azure sanal makinesini alır. |
| Format-DevTestMessageWithTime |Bir iletinin tarihini ve saatlerini hazırlar. Bu işlev, Hata ve Ayrıntılı akışlara yazılan iletiler için tasarlanmıştır. |
| Get-AzureSQLDatabaseConnectionString |Azure SQL veritabanına bağlanmak için bir bağlantı dizesi oluşturur. |
| Get-AzureVMStorage |Belirtilen konum veya benzeşm grubunda "devtest" (büyük/büyük/büyük harfe duyarlı değil) ad deseniyle ilk depolama *hesabının adını döndürür. "devtest"* depolama hesabı konum veya benzeşm grubuyla eşlenemse işlev bunu yoksayar. Bir konum veya benzeşm grubu belirtin. |
| Get-MSDeployCmd |MsDeploy.exe aracını çalıştırmak için MsDeploy.exe döndürür. |
| New-AzureVMEnvironment |Abonelikte JSON yapılandırma dosyasındaki değerlerle eşleşen bir sanal makine bulur veya oluşturur. |
| Publish-WebPackage |Kaynakları MsDeploy.exe dağıtmak için web .Zip paketi ve web yayımlama paketi dosyası kullanır. Bu işlev herhangi bir çıkış oluşturmaz. MSDeploy.exe çağrısı başarısız olursa işlev bir özel durum oluşturur. Daha ayrıntılı bir çıkış elde etmek için **-Verbose seçeneğini** kullanın. |
| Publish-WebPackageToVM |Parametre değerlerini doğrular ve ardından **Publish-WebPackage işlevini** çağırır. |
| Read-ConfigFile |JSON yapılandırma dosyasını doğrular ve seçilen değerlerin karma bir tablosu döndürür. |
| Restore-Subscription |Geçerli aboneliği özgün aboneliğe sıfırlar. |
| Test-AzureModule |Yüklü `$true` Azure modülü sürümü 0.7.4 veya sonraki bir sürümse döndürür. Modül `$false` yüklü değilse veya önceki bir sürümdeyse döndürür. Bu işlevin parametresi yoktur. |
| Test-AzureModuleVersion |`$true`Azure modülünün sürümü 0.7.4 veya sonraki bir sürümse döndürür. Modül `$false` yüklü değilse veya önceki bir sürümdeyse döndürür. Bu işlevin parametresi yoktur. |
| Test-HttpsUrl |Giriş URL'sini System.Uri nesnesine dönüştürür. `$True`URL mutlak ise ve şeması https ise döndürür. URL göreli ise, şeması HTTPS değilse veya giriş `$false` dizesi URL'ye dönüştürüle değilse döndürür. |
| Test-Member |Bir `$true` özellik veya yöntem nesnenin üyesi ise döndürür. Aksi takdirde `$false` döndürür. |
| Write-ErrorWithTime |Geçerli saat ön ekli bir hata iletisi yazar. Bu işlev, iletiyi Hata akışına yazmadan önce zamanı sona hazırlamak için **Format-DevTestMessageWithTime** işlevini arar. |
| Write-HostWithTime |Ana bilgisayar programına (**Write-Host**) geçerli saat ön ekli bir ileti yazar. Konak programına yazmanın etkisi değişir. Bu iletileri barındıran Windows PowerShell standart çıkışa yazar. |
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
PowerShell betiği yazma hakkında daha fazla bilgi edinmek için [Windows PowerShell Betik](/powershell/scripting/overview) Merkezi'nde Azure PowerShell betiklerini [öğrenin.](https://azure.microsoft.com/documentation/scripts/)